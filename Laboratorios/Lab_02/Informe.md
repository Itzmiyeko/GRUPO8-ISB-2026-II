# INFORMES DE LABORATORIO 2 — INTRODUCCIÓN A SEÑALES BIOMÉDICAS

**Facultad - Carrera:** Facultad de Ciencias e Ingeniería — Ingeniería Biomédica

**Laboratorio:** Laboratorio 2 

***Integrantes:***

- ARIANA CRISTINA LOZANO REGUERA

- EMMA LISBETH RIVERA JARA

- ITZEL MIYEKO DE LA CRUZ GALVEZ

- RENZO WILLIAM LUNA ALIAGA

- VIVIANA NINOSKA RIVERA GUILLEN

**Profesores**:

- Moisés Meza

- José Cáceres

---

## <u>**Lab001:Introduccion Señales Biomedicas PhysioNet** </u>

### 1. Identificación de la base de datos

- **Base de datos:** `mitdb` — **MIT-BIH Arrhythmia Database** (PhysioNet).
- Base de datos de referencia que contiene registros EKG anotados.
- Acceso realizado mediante la librería `wfdb` de Python, usando el argumento `pn_dir="mitdb"`.

### 2. Identificación del registro

- **Registro seleccionado (RECORD):** `111`
- Siguiendo el concepto **DATABASE + RECORD**, el registro analizado se identifica de forma única como `mitdb/111`, ya que el mismo número de registro podría existir (con contenido distinto) en otra base de datos.
- Número total de muestras del registro completo: **650 000**.
- Canales disponibles en el registro: **2** → `MLII` y `V1` (ambos en mV).

### 3. Frecuencia de muestreo

- **Frecuencia de muestreo (fs):** `360 Hz`
- **Periodo de muestreo (Ts = 1/fs):** `0.002778 s` (≈ 2.78 ms)
- Con esta frecuencia, en 1 segundo se adquieren 360 muestras, y en un segmento de 10 segundos se adquieren 3600 muestras.
- **Duración total del registro:** 650 000 / 360 Hz ≈ **1805.56 segundos** (≈ 30 minutos).

### 4. Canal seleccionado

| Canal | Nombre | Unidad |
|:---:|:---:|:---:|
| 0 | MLII | mV |
| **1** | **V1** | **mV** |

- **Canal seleccionado (CHANNEL = 1):** `V1`.
- A diferencia del canal `MLII` (derivación modificada más usada para observar el complejo QRS y el eje eléctrico general), `V1` es una derivación precordial que resalta mejor la actividad eléctrica del lado derecho del corazón y la morfología del segmento auricular, por lo que su forma de onda difiere de la vista habitual de `MLII`.

### 5. Duración analizada

- **Duración del segmento (DURATION):** `10 segundos`
- **Número de muestras del segmento:** `N = DURATION × fs = 10 × 360 = 3600 muestras`
- Rango temporal analizado: de `t = 0 s` a `t = 9.997 s` (primeros 10 segundos del registro).

### 6. Las 4 gráficas

#### Gráfica 1 — ECG completo (vista ampliada del registro)

<img width="1489" height="490" alt="l21" src="https://github.com/user-attachments/assets/5a83f853-0bac-406e-8290-b52ce0986e60" />

El código grafica la señal completa (`t` vs `signal`), pero el eje `x` se restringe mediante `plt.xlim(1515, 1750)`, por lo que en realidad se visualiza una **ventana de 5 segundos** ubicada cerca del final del registro (entre 1515 s y 1750 s), y no las 30 minutos completas. En esa ventana se observan con claridad **seis latidos consecutivos**, cada uno con una deflexión negativa pronunciada (compatible con el complejo QRS visto desde la derivación V1) seguida de una fase de recuperación más lenta.

#### Gráfica 2 — Segmento ECG ampliado (primeros 10 s)

<img width="1489" height="490" alt="l1" src="https://github.com/user-attachments/assets/2f320e91-d616-463f-ba5c-c61d46f58cd0" />

Se aíslan los primeros 10 segundos del registro (3600 muestras). Se identifican aproximadamente **10 ciclos cardiacos**, cada uno con: una fase basal relativamente plana, una deflexión brusca hacia amplitudes negativas (entre -0.7 mV y -0.95 mV, compatible con el complejo QRS visto en V1), y una elevación posterior hacia valores positivos (0.4 mV a 0.6 mV) que decae progresivamente hasta el siguiente ciclo. El ritmo es regular, con periodos entre picos de aproximadamente 0.8-0.9 s (equivalente a una frecuencia cardiaca de ~70-75 lpm).

#### Gráfica 3 — Histograma de amplitudes

<img width="889" height="490" alt="l3" src="https://github.com/user-attachments/assets/db97ce5b-11b3-4dbd-a50b-5456ba0b9ced" />

La distribución de amplitudes del segmento de 10 segundos muestra una **concentración marcada alrededor de 0.05-0.15 mV** (la fase basal entre latidos, que es la que más tiempo ocupa dentro de cada ciclo). Existe una **cola extendida hacia valores negativos** (entre -0.6 mV y -0.95 mV), correspondiente a las deflexiones del complejo QRS, y una dispersión moderada hacia valores positivos (0.2 mV a 0.6 mV) asociada a la fase de repolarización. La distribución es **asimétrica (no gaussiana)**, como es esperable en una señal ECG, ya que combina una fase de reposo predominante con eventos transitorios de gran amplitud.

#### Gráfica 4 — Representación discreta (primeras 100 muestras)

<img width="1490" height="490" alt="l4" src="https://github.com/user-attachments/assets/d77d241d-b13a-4947-b055-d54854a8a0e8" />

Se muestran las primeras 100 muestras (equivalentes a ~0.275 s) como puntos discretos `x[n]` unidos por una línea. Se aprecia claramente que la señal está formada por **valores individuales tomados a intervalos regulares de 1/360 s**, y no por una curva continua. En este tramo se observa parte de un complejo QRS (pico cercano a 0.085 mV alrededor de n≈7) seguido de fluctuaciones de menor amplitud típicas de la actividad basal/ruido de fondo.

### 7. Estadísticas

Calculadas sobre el segmento analizado de 10 segundos (3600 muestras, canal V1):

| Estadístico | Valor |
|---|---|
| Media | 0.1019 mV |
| Desviación estándar | 0.2692 mV |
| Mínimo | -0.9400 mV |
| Máximo | 0.5850 mV |
| Rango (Máx - Mín) | 1.5250 mV |

La media positiva (≈0.10 mV) refleja que la señal pasa más tiempo en la fase basal/de reposo (ligeramente por encima de 0) que en los picos QRS negativos, aunque estos últimos son los que determinan la mayor dispersión (desviación estándar de ~0.27 mV) y el amplio rango dinámico de la señal (1.525 mV).

### 8. Archivo WAV

- **Proceso de conversión:**
  1. Se tomó el segmento de 10 s del canal `V1`.
  2. Se eliminó la componente DC restando la media (`ecg_for_wav - mean`).
  3. Se normalizó dividiendo entre el valor absoluto máximo, dejando la señal en el rango [-1, 1].
  4. Se guardó como WAV usando `scipy.io.wavfile.write`, empleando `fs = 360 Hz` como frecuencia de muestreo del audio (igual a la del ECG), para conservar la relación temporal entre muestras.

- **Archivo generado:** `ecg_record_111_channel_1.wav`
- **Verificación del rango int16:** mínimo = -32767, máximo = 15195 (dentro del rango válido de `int16`: -32768 a 32767).
- Al reproducirlo, el resultado es un sonido pulsante y de tono grave, cuyos "golpes" corresponden a los complejos QRS de cada latido; sin embargo, no es un sonido fisiológico real, sino una representación audible de las variaciones eléctricas del ECG.

### 9. Interpretación de los resultados

- El registro `111`, en el canal `V1` presenta una señal ECG con un **ritmo regular**, sin cambios evidentes de morfología entre ciclos dentro de la ventana analizada.
- La derivación `V1` produce complejos con **deflexión predominantemente negativa** (a diferencia de `MLII`, donde el QRS suele ser mayormente positivo), lo cual es consistente con la orientación de esta derivación precordial respecto al vector eléctrico cardiaco.
- El histograma confirma que la mayor parte del tiempo la señal permanece cerca de la línea basal, y que los valores extremos (positivos y negativos) son eventos poco frecuentes pero de gran amplitud, correspondientes a los complejos QRS y a la fase de repolarización (onda T).
- La representación discreta evidencia que, pese a la apariencia "continua" de las Gráficas 1 y 2, la señal ECG es en realidad una **secuencia de muestras discretas** `x[n]` tomadas cada 2.78 ms, y que la fidelidad de la forma de onda depende directamente de `fs`.
- Al convertir la señal a formato WAV se preserva la variación temporal de amplitud, pero se pierde la posibilidad de interpretar visualmente la morfología de las ondas P, QRS y T; el análisis auditivo permite únicamente percibir la periodicidad del ritmo cardiaco, no su morfología clínica.

---

## <u>**Lab002: Introduccion Señales Biomedicas PhysioNet** </u>
 

**Registro Seleccionado:** 16272

### **1\. Datos Básicos del Registro**

> * **Registro seleccionado:** 16272 (PhysioNet)  
> * **Frecuencia de muestreo (fs):** 128 Hz  
> * **Canal analizado:** Canal 0 (correspondiente a la primera derivación electrocardiográfica, ECG1)

### **2\. Representación Temporal**

A continuación se presenta la gráfica de la señal en el dominio del tiempo obtenida a partir del canal 0 del registro 16272:  
Frecuencia de muestreo: 128 Hz

<img width="796" height="305" alt="aa1" src="https://github.com/user-attachments/assets/f61483e3-340f-464b-917f-6c30acebb9a8" />


### **3\. Transformada Rápida de Fourier (FFT)**

#### **3.1. FFT con Componente DC**

Espectro de frecuencia de la señal original donde se conserva el nivel medio o componente continua (DC):

<img width="782" height="300" alt="aa2" src="https://github.com/user-attachments/assets/a3c6e494-d9be-46af-b15d-3cbbe2c82243" />

#### **3.2. FFT sin Componente DC**

Espectro de frecuencia tras restar la media de la señal   

<img width="781" height="290" alt="aa3" src="https://github.com/user-attachments/assets/dd8fe8af-780a-4efa-b471-77ec2aa3ad8b" />

**4\. Transformada de Fourier de Tiempo Reducido (STFT)**  
Espectrograma generado utilizando una ventana de 128 muestras (nperseg \= 128\) para analizar la variación frecuencial a lo largo del tiempo:  

<img width="777" height="396" alt="aa4" src="https://github.com/user-attachments/assets/5fc99b45-676e-4022-b10c-6cdd1ad76261" />

### **5\. Análisis del Espectrograma e Interpretación de Resultados**

Al observar la **señal temporal**, se nota un ritmo cardíaco claro y regular con los complejos QRS bien definidos. Sin embargo, hacia la mitad del registro (entre los 15 y 20 segundos) hay una pequeña elevación o bamboleo en la línea base, lo cual suele deberse a un artefacto por movimiento o por la respiración del paciente.  
En el espectro de la **FFT**, se ve que casi toda la energía del ECG se concentra en las frecuencias bajas (por debajo de los 30 Hz). Aparece un primer pico muy marcado en la frecuencia fundamental de los latidos y luego otros picos más pequeños correspondientes a sus armónicos. Al eliminar la componente continua (DC), el pico inicial pegado al cero disminuye, lo que permite ver con mayor claridad las demás frecuencias.  
Por último, el **espectrograma de la STFT** muestra unas franjas verticales delgadas que se repiten periódicamente, las cuales coinciden exactamente con cada latido del corazón en el tiempo. Además, en el tramo de los 15 a 20 segundos se nota un aumento de color brillante en la zona de frecuencias muy bajas, lo que confirma que el movimiento de la línea base que vimos en la señal temporal era un evento de baja frecuencia localizado en ese momento preciso.

### **6\. Comparación de Resultados**

> * **Dominio temporal:** Permite identificar de manera directa la forma de onda de cada latido (complejos QRS) y notar cuando la línea base se mueve o se desvía por artefactos.  
> * **Dominio frecuencial (FFT):** Muestra con claridad dónde está concentrada la energía de la señal (por debajo de los 30 Hz) y los armónicos principales, pero no nos dice en qué momento específico ocurren las variaciones o el ruido.  
> * **Dominio tiempo-frecuencia (STFT):** Combina lo mejor de los dos análisis anteriores. Nos permite relacionar el salto de energía en frecuencias muy bajas (0 a 3 Hz) exactamente con el tramo de 15 a 20 segundos donde la línea base se elevó en el tiempo.

### **7\. Respuestas a las Preguntas de Análisis**

#### **Preguntas de análisis 1: Parámetros de la Señal**

> 1. **Frecuencia de muestreo (fs):** Es de 128 Hz.  
> 2. **Igualdad de fs:** Sí, los registros analizados en el laboratorio comparten la misma frecuencia de muestreo.  
> 3. **Número de canales:** El registro cuenta con 2 canales.  
> 4. **Canal 0:** Corresponde al primer canal de registro electrocardiográfico (ECG1).  
> 5. **Número de muestras:** Contiene 3600 muestras para un tramo de 10 segundos grabado a 360 Hz (o la cantidad equivalente según la duración del tramo extraído).  
> 6. **Relación entre parámetros:** Se relacionan por la fórmula Tiempo \= Muestras / f\_s. Por ejemplo, 3600 muestras divididas entre 360 Hz dan una duración de 10 segundos.

#### **Preguntas de análisis 2: Dominio Temporal**

> 1. **Morfología:** No son exactamente iguales. Aunque todos son registros de ECG, la forma de la onda cambia según el paciente, la frecuencia cardíaca y la presencia de artefactos.  
> 2. **Mayor variación:** El registro 16272 es el que muestra una mayor variación de amplitud pico a pico.  
> 3. **Patrones periódicos:** Sí, la repetición periódica de los picos de la onda R marca un ritmo claro.  
> 4. **Eventos particulares:** Entre los 17 s y 19 s se observa una desviación clara en la línea base debido a movimiento o respiración.  
> 5. **Información rápida:** Permite estimar a simple vista la frecuencia cardíaca, la amplitud de las ondas y si el ritmo es regular o irregular.

#### **Preguntas de análisis 3: Dominio Frecuencial (FFT)**

> 1. **Efecto al eliminar la media:** El pico gigante que aparece pegado a los 0 Hz cae casi a cero, lo que elimina el nivel de offset continuo de la señal.  
> 2. **Diferencias en los espectros:** El registro 16272 muestra picos bien definidos en bajas frecuencias y energía dispersa hasta los 30 Hz, a diferencia de otros registros que tienen su energía distribuida de otra forma.  
> 3. **Intervalo de mayor energía:** Se concentra principalmente entre los 0.5 Hz y los 25 Hz.  
> 4. **Pérdida de información temporal en la FFT:** Porque la FFT calcula las frecuencias promediando todo el registro completo de principio a fin, por lo que pierde la noción de en qué segundo ocurrió cada evento.  
> 5. **Ventaja del dominio frecuencial:** Permite detectar fácilmente armónicos y ruidos (como la interferencia de la red eléctrica) que en el tiempo no se notan con claridad.

#### **Preguntas de analisis 4: Análisis Tiempo-Frecuencia (STFT)**

> 1. **Información adicional de la STFT:** Nos da la localización temporal, permitiendo saber en qué segundo específico aparece o cambia una determinada frecuencia.  
> 2. **Momentos de cambio de energía:** Se ven franjas verticales por cada latido y un aumento brillante de energía cerca a 0-3 Hz entre los 15 s y 20 s.  
> 3. **Diferencias entre espectrogramas:** Cambia la forma en que se distribuyen las manchas de color (líneas verticales delgadas para eventos rápidos o bandas horizontales para frecuencias continuas).  
> 4. **Efecto de una ventana de 32 muestras:** Se prioriza la resolución en el tiempo, ideal para detectar cambios rápidos como los picos QRS, aunque se pierde un poco de detalle en las frecuencias.  
> 5. **Efecto de una ventana muy grande:** Mejora la resolución en frecuencia, pero la resolución temporal empeora y los latidos se ven borrosos en el tiempo.  
> 6. **Efecto de una ventana muy pequeña:** Mejora la precisión en el tiempo, pero la resolución en frecuencia se vuelve muy baja y las bandas se ven muy anchas.

---

## <u>**Lab003: Introducción a Filtros FIR, IIR, y Transformada Z** </u>
### Introducción

En este laboratorio se realizó el análisis y procesamiento digital de una señal ECG con el objetivo de identificar sus principales componentes frecuenciales, detectar interferencias y diseñar filtros digitales que permitan reducir el ruido sin perder información fisiológica relevante.

El trabajo siguió el proceso:

**Señal → análisis temporal → FFT → identificación del ruido → diseño del filtro → filtrado → validación → interpretación fisiológica.**

### Objetivos

- Analizar una señal ECG en el dominio temporal y frecuencial.
- Utilizar la FFT para identificar componentes de frecuencia.
- Comprender la relación entre la Transformada de Fourier y la Transformada Z.
- Diseñar y comparar filtros FIR e IIR.
- Seleccionar una frecuencia de corte a partir de las características de la señal.
- Evaluar el efecto del filtrado sobre la morfología del ECG.
- Validar cuantitativamente la calidad de la señal filtrada.

### Herramientas utilizadas

- Python 3.x
- NumPy
- SciPy
- Matplotlib
- Pandas
- NeuroKit2
- Jupyter Notebook / Google Colab

### 1. Generación y caracterización de la señal

Se generó una señal ECG sintética utilizando `NeuroKit2` con los siguientes parámetros:

- Duración: **10 s**
- Frecuencia de muestreo: **250 Hz**
- Frecuencia cardíaca: **70 bpm**
- Número de muestras: **2500**

En el dominio temporal se identificaron los principales elementos de la morfología ECG, incluyendo las ondas **P y T** y el complejo **QRS**.

La frecuencia de muestreo determina la frecuencia máxima observable según el criterio de Nyquist:

fNyquist= fs/2
fNyquist= 125Hz
### 2. Análisis frecuencial mediante FFT

Se utilizó la FFT para analizar el contenido frecuencial de la señal.

Las principales componentes detectadas se encontraron aproximadamente entre **1.2 y 10.5 Hz**, destacando:

- 2.30 Hz
- 4.70 Hz
- 3.50 Hz
- 7.00 Hz
- 1.20 Hz
- 5.80 Hz
- 10.50 Hz
- 8.20 Hz

La mayor parte de la energía se concentró en las bajas frecuencias, asociadas principalmente al contenido fisiológico del ECG.

El análisis frecuencial permitió establecer una frecuencia de corte adecuada evitando eliminar componentes importantes del complejo QRS.

### 3. Diseño y comparación de filtros FIR e IIR

Se diseñaron dos filtros pasa-bajas:

#### Filtro FIR

- Tipo: **Pasa-bajas**
- Número de taps: **101**
- Frecuencia de corte: **40 Hz**
- Diseño mediante `firwin`

El filtro FIR no utiliza realimentación y permite obtener una respuesta de fase lineal con mayor facilidad.

#### Filtro IIR

- Tipo: **Butterworth pasa-bajas**
- Orden: **4**
- Frecuencia de corte: **40 Hz**
- Representación: **SOS**
- Aplicación: `sosfiltfilt`

El filtro IIR utiliza realimentación, por lo que puede alcanzar respuestas similares utilizando un orden menor. Se utilizó `sosfiltfilt` para evitar desplazamientos temporales asociados al filtrado en un solo sentido.

#### Comparación

El MSE obtenido respecto a la señal original fue:

| Filtro | MSE |
|---|---:|
| FIR | \(1.359*10^{-6}\) |
| IIR | \(8.745*10^{-7}\) |

En este caso, el filtro IIR presentó un MSE ligeramente menor respecto a la señal ECG original.

### 4. Procesamiento de ECG contaminado

Para evaluar el desempeño del filtrado se agregó una interferencia sinusoidal de:

- Amplitud: **0.20**
- Frecuencia: **35 Hz**

La señal contaminada se modeló como:
<img width="742" height="225" alt="image" src="https://github.com/user-attachments/assets/7f64a5c4-d53c-4cdc-9545-410e75d56c38" />


<img width="1106" height="382" alt="image" src="https://github.com/user-attachments/assets/b542ce4f-1d51-43b8-8ecc-3dd21d97a0ed" />

Mediante la FFT se identificó un pico de interferencia aproximadamente en **35 Hz**.

A partir de este análisis se diseñó un filtro Butterworth pasa-bajas de:

- Frecuencia de corte: **25 Hz**
- Orden: **4**
- Filtrado: `sosfiltfilt`

La frecuencia de corte se seleccionó por debajo de la interferencia de 35 Hz, buscando reducir el ruido y conservar la mayor parte de la información fisiológica del ECG.
<img width="880" height="368" alt="image" src="https://github.com/user-attachments/assets/1f39f24d-9a59-420d-bb4b-a90e21c611e7" />

### 5. Validación del filtrado

Se compararon la señal contaminada y la señal recuperada tanto en el dominio temporal como en el frecuencial.

Los resultados obtenidos fueron:

- **MSE:** 9.381 × 10⁻⁵
- **RMSE:** 0.00969
- **SNR antes del filtrado:** **5.10 dB**
- **SNR después del filtrado:** **28.39 dB**

El aumento considerable del SNR indica una mejora importante de la relación señal-ruido.

Además, la FFT mostró una reducción significativa del pico correspondiente a la interferencia de 35 Hz.

La morfología general del ECG se mantuvo, incluyendo los complejos QRS y las ondas P y T, y los intervalos R-R permanecieron sin desplazamientos apreciables.

### 6. Errores de diseño del filtro

También se evaluaron situaciones en las que el filtro está mal diseñado.

#### Frecuencia de corte demasiado baja

Se utilizó una frecuencia de corte de **5 Hz**. Como consecuencia, el complejo QRS perdió su característica forma rápida y se observó más aplanado y ensanchado.

El MSE aumentó hasta:

MSE=2.715*10^{-2}

Esto demuestra que una frecuencia de corte demasiado baja puede eliminar información fisiológica relevante.

#### Desplazamiento de fase

También se comparó el filtrado mediante `sosfilt` frente a `sosfiltfilt`.

El filtrado en un solo sentido puede producir un desplazamiento temporal de la señal debido a la respuesta de fase del filtro IIR. Esto puede afectar la ubicación temporal de los picos R y, por lo tanto, las mediciones de intervalos fisiológicos.

El uso de `sosfiltfilt` permite realizar un filtrado de fase cero, evitando este desplazamiento.

### 7. Transformada Z

La Transformada Z permitió analizar los filtros como sistemas discretos mediante su función de transferencia:


H(z)=Y(z)/X(z)

A través de la función de transferencia se pueden estudiar los **polos, ceros, estabilidad y respuesta en frecuencia**.

La relación con Fourier se obtiene evaluando la función de transferencia sobre el círculo unitario:

<img width="110" height="55" alt="image" src="https://github.com/user-attachments/assets/90ef7232-1e8d-49c6-a1ee-8362bc4f1880" />

Por ello:

**Transformada Z → análisis general de sistemas discretos**

**Transformada de Fourier → análisis frecuencial**

## Conclusiones de los laboratorios
**LAB001**
  - La identificación correcta de una señal biomédica en PhysioNet requiere siempre especificar tanto la **base de datos** como el **número de registro**, ya que el mismo identificador de registro puede tener significados distintos en diferentes bases de datos.
  - La frecuencia de muestreo (`fs = 360 Hz`) determina la resolución temporal de la señal: a mayor `fs`, mayor capacidad de capturar detalles finos de la morfología del ECG (como el complejo QRS); a menor `fs`, se corre el riesgo de perder información relevante.
  - Las distintas formas de visualización (señal completa, segmento ampliado, histograma y representación discreta) aportan información complementaria: la vista temporal permite evaluar ritmo y morfología, el histograma resume la distribución estadística de amplitudes, y la vista discreta hace explícito el carácter muestreado (`x[n]`) de toda señal biomédica digital.
  - Las estadísticas básicas (media, desviación estándar, mínimo, máximo y rango) permiten caracterizar cuantitativamente la señal, aunque no sustituyen el análisis morfológico visual, ya que no conservan información sobre la secuencia temporal de los eventos.
  - Convertir un ECG a formato WAV es posible porque ambas son señales digitales. La conversión a formato WAV facilita la exploración auditiva del ritmo cardiaco, aunque con pérdida de la información morfológica fina que sí se aprecia en la representación gráfica.

**LAB002**
  - El análisis temporal es esencial para observar directamente la forma de las ondas del ECG y evaluar el ritmo cardíaco, pero por sí solo no permite aislar ruidos o componentes de frecuencia superpuestos.  
  - La FFT es una herramienta muy útil para conocer las frecuencias principales de la señal y eliminar componentes no deseadas (como el offset DC), aunque tiene la limitación de no mostrar en qué momento ocurre cada frecuencia.  
  - La STFT es el método más completo para señales biomédicas variables en el tiempo, ya que logra equilibrar la resolución en tiempo y frecuencia, permitiendo identificar eventos transitorios y artefactos localizados.

**LAB003**

  - El laboratorio permitió comprobar que el diseño de un filtro para señales biomédicas debe basarse en un análisis previo de la señal y no en la eliminación indiscriminada de frecuencias.
  
  - La FFT permitió identificar las componentes frecuenciales y detectar la interferencia de **35 Hz**, a partir de la cual se seleccionó una frecuencia de corte de **25 Hz** para recuperar el ECG contaminado.
  
  - La comparación FIR-IIR mostró que ambos filtros pueden reducir componentes no deseadas, pero presentan diferencias en realimentación, orden, fase, estabilidad y costo computacional.
  
  - Finalmente, las métricas obtenidas mostraron una mejora significativa después del filtrado, aumentando el SNR de **5.10 dB a 28.39 dB**, mientras se conservó la morfología general del ECG. Por ello, la validación debe considerar simultáneamente el análisis temporal, frecuencial y cuantitativo para asegurar que el ruido sea reducido sin perder información fisiológica relevante.
