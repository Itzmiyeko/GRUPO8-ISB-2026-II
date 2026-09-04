# INFORMES DE LABORATORIO 2 — INTRODUCCIÓN A LAS SEÑALES MÉDICAS

**Universidad:** Universidad Peruana Cayetano Heredia — Ingeniería Biomédica

**Laboratorio:** Laboratorio 2 - LAB001

***Integrantes:***

- ARIANA CRISTINA LOZANO REGUERA

- EMMA LISBETH RIVERA JARA

- ITZEL MIYEKO DE LA CRUZ GALVEZ

- RENZO WILLIAM LUNA ALIAGA

- VIVIANA NINOSKA RIVERA GUILLEN

**Profesores**:

- Moises Meza

- José Cáceres

## <u>**Lab001** </u>

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

## <u>**Lab002** </u>
 

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

## <u>**Lab003** </u>

