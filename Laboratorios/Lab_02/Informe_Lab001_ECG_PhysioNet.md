# Informe de Laboratorio — Introducción a Señales Biomédicas con PhysioNet

**Universidad:** Universidad Peruana Cayetano Heredia — Ingeniería Biomédica

**Laboratorio:** LAB 2

***Integrantes:***

**- ARIANA CRISTINA LOZANO REGUERA**

**- EMMA LISBETH RIVERA JARA**

**- ITZEL MIYEKO DE LA CRUZ GALVEZ**

**- RENZO WILLIAM LUNA ALIAGA**

**- VIVIANA NINOSKA RIVERA GUILLEN**

---

## 1. Identificación de la base de datos

- **Base de datos:** `mitdb` — **MIT-BIH Arrhythmia Database** (PhysioNet).
- Base de datos de referencia que contiene registros electrocardiográficos anotados.
- Acceso realizado mediante la librería `wfdb` de Python, usando el argumento `pn_dir="mitdb"`.

## 2. Identificación del registro

- **Registro seleccionado (RECORD):** `111`
- Siguiendo el concepto **DATABASE + RECORD**, el registro analizado se identifica de forma única como `mitdb/111`, ya que el mismo número de registro podría existir (con contenido distinto) en otra base de datos.
- Número total de muestras del registro completo: **650 000**.
- Canales disponibles en el registro: **2** → `MLII` y `V1` (ambos en mV).

## 3. Frecuencia de muestreo

- **Frecuencia de muestreo (fs):** `360 Hz`
- **Periodo de muestreo (Ts = 1/fs):** `0.002778 s` (≈ 2.78 ms)
- Con esta frecuencia, en 1 segundo se adquieren 360 muestras, y en un segmento de 10 segundos se adquieren 3600 muestras.
- **Duración total del registro:** 650 000 / 360 Hz ≈ **1805.56 segundos** (≈ 30 minutos).

## 4. Canal seleccionado

| Canal | Nombre | Unidad |
|:---:|:---:|:---:|
| 0 | MLII | mV |
| **1** | **V1** | **mV** |

- **Canal seleccionado (CHANNEL = 1):** `V1`.
- A diferencia del canal `MLII` (derivación modificada más usada para observar el complejo QRS y el eje eléctrico general), `V1` es una derivación precordial que resalta mejor la actividad eléctrica del lado derecho del corazón y la morfología del segmento auricular, por lo que su forma de onda difiere de la vista habitual de `MLII`.

## 5. Duración analizada

- **Duración del segmento (DURATION):** `10 segundos`
- **Número de muestras del segmento:** `N = DURATION × fs = 10 × 360 = 3600 muestras`
- Rango temporal analizado: de `t = 0 s` a `t = 9.997 s` (primeros 10 segundos del registro).

## 6. Las 4 gráficas

### Gráfica 1 — ECG completo (vista ampliada del registro)

<img width="1489" height="490" alt="l21" src="https://github.com/user-attachments/assets/5a83f853-0bac-406e-8290-b52ce0986e60" />

El código grafica la señal completa (`t` vs `signal`), pero el eje `x` se restringe mediante `plt.xlim(1515, 1750)`, por lo que en realidad se visualiza una **ventana de 5 segundos** ubicada cerca del final del registro (entre 1515 s y 1750 s), y no las 30 minutos completas. En esa ventana se observan con claridad **seis latidos consecutivos**, cada uno con una deflexión negativa pronunciada (compatible con el complejo QRS visto desde la derivación V1) seguida de una fase de recuperación más lenta.

### Gráfica 2 — Segmento ECG ampliado (primeros 10 s)

<img width="1489" height="490" alt="l1" src="https://github.com/user-attachments/assets/2f320e91-d616-463f-ba5c-c61d46f58cd0" />

Se aíslan los primeros 10 segundos del registro (3600 muestras). Se identifican aproximadamente **10 ciclos cardiacos**, cada uno con: una fase basal relativamente plana, una deflexión brusca hacia amplitudes negativas (entre -0.7 mV y -0.95 mV, compatible con el complejo QRS visto en V1), y una elevación posterior hacia valores positivos (0.4 mV a 0.6 mV) que decae progresivamente hasta el siguiente ciclo. El ritmo es regular, con periodos entre picos de aproximadamente 0.8-0.9 s (equivalente a una frecuencia cardiaca de ~70-75 lpm).

### Gráfica 3 — Histograma de amplitudes

<img width="889" height="490" alt="l3" src="https://github.com/user-attachments/assets/db97ce5b-11b3-4dbd-a50b-5456ba0b9ced" />

La distribución de amplitudes del segmento de 10 segundos muestra una **concentración marcada alrededor de 0.05-0.15 mV** (la fase basal entre latidos, que es la que más tiempo ocupa dentro de cada ciclo). Existe una **cola extendida hacia valores negativos** (entre -0.6 mV y -0.95 mV), correspondiente a las deflexiones del complejo QRS, y una dispersión moderada hacia valores positivos (0.2 mV a 0.6 mV) asociada a la fase de repolarización. La distribución es **asimétrica (no gaussiana)**, como es esperable en una señal ECG, ya que combina una fase de reposo predominante con eventos transitorios de gran amplitud.

### Gráfica 4 — Representación discreta (primeras 100 muestras)

<img width="1490" height="490" alt="l4" src="https://github.com/user-attachments/assets/d77d241d-b13a-4947-b055-d54854a8a0e8" />

Se muestran las primeras 100 muestras (equivalentes a ~0.275 s) como puntos discretos `x[n]` unidos por una línea. Se aprecia claramente que la señal está formada por **valores individuales tomados a intervalos regulares de 1/360 s**, y no por una curva continua. En este tramo se observa parte de un complejo QRS (pico cercano a 0.085 mV alrededor de n≈7) seguido de fluctuaciones de menor amplitud típicas de la actividad basal/ruido de fondo.

## 7. Estadísticas

Calculadas sobre el segmento analizado de 10 segundos (3600 muestras, canal V1):

| Estadístico | Valor |
|---|---|
| Media | 0.1019 mV |
| Desviación estándar | 0.2692 mV |
| Mínimo | -0.9400 mV |
| Máximo | 0.5850 mV |
| Rango (Máx - Mín) | 1.5250 mV |

La media positiva (≈0.10 mV) refleja que la señal pasa más tiempo en la fase basal/de reposo (ligeramente por encima de 0) que en los picos QRS negativos, aunque estos últimos son los que determinan la mayor dispersión (desviación estándar de ~0.27 mV) y el amplio rango dinámico de la señal (1.525 mV).

## 8. Archivo WAV

- **Proceso de conversión:**
  1. Se tomó el segmento de 10 s del canal `V1`.
  2. Se eliminó la componente DC restando la media (`ecg_for_wav - mean`).
  3. Se normalizó dividiendo entre el valor absoluto máximo, dejando la señal en el rango [-1, 1].
  4. Se escaló y convirtió a enteros de 16 bits (`int16`) multiplicando por 32767.
  5. Se guardó como WAV usando `scipy.io.wavfile.write`, empleando `fs = 360 Hz` como frecuencia de muestreo del audio (igual a la del ECG), para conservar la relación temporal entre muestras.

- **Archivo generado:** `ecg_record_111_channel_1.wav`
- **Verificación del rango int16:** mínimo = -32767, máximo = 15195 (dentro del rango válido de `int16`: -32768 a 32767).
- Al reproducirlo, el resultado es un sonido pulsante y de tono grave, cuyos "golpes" corresponden a los complejos QRS de cada latido; sin embargo, no es un sonido fisiológico real, sino una representación audible de las variaciones eléctricas del ECG.

## 9. Interpretación de los resultados

- El registro `111`, en el canal `V1` presenta una señal ECG con un **ritmo regular**, sin cambios evidentes de morfología entre ciclos dentro de la ventana analizada.
- La derivación `V1` produce complejos con **deflexión predominantemente negativa** (a diferencia de `MLII`, donde el QRS suele ser mayormente positivo), lo cual es consistente con la orientación de esta derivación precordial respecto al vector eléctrico cardiaco.
- El histograma confirma que la mayor parte del tiempo la señal permanece cerca de la línea basal, y que los valores extremos (positivos y negativos) son eventos poco frecuentes pero de gran amplitud, correspondientes a los complejos QRS y a la fase de repolarización (onda T).
- La representación discreta evidencia que, pese a la apariencia "continua" de las Gráficas 1 y 2, la señal ECG es en realidad una **secuencia de muestras discretas** `x[n]` tomadas cada 2.78 ms, y que la fidelidad de la forma de onda depende directamente de `fs`.
- Al convertir la señal a formato WAV se preserva la variación temporal de amplitud, pero se pierde la posibilidad de interpretar visualmente la morfología de las ondas P, QRS y T; el análisis auditivo permite únicamente percibir la periodicidad del ritmo cardiaco, no su morfología clínica.

## 10. Conclusiones

1. La identificación correcta de una señal biomédica en PhysioNet requiere siempre especificar tanto la **base de datos** como el **número de registro**, ya que el mismo identificador de registro puede tener significados distintos en diferentes bases de datos.
2. La frecuencia de muestreo (`fs = 360 Hz`) determina la resolución temporal de la señal: a mayor `fs`, mayor capacidad de capturar detalles finos de la morfología del ECG (como el complejo QRS); a menor `fs`, se corre el riesgo de perder información relevante.
3. Las distintas formas de visualización (señal completa, segmento ampliado, histograma y representación discreta) aportan información complementaria: la vista temporal permite evaluar ritmo y morfología, el histograma resume la distribución estadística de amplitudes, y la vista discreta hace explícito el carácter muestreado (`x[n]`) de toda señal biomédica digital.
4. Las estadísticas básicas (media, desviación estándar, mínimo, máximo y rango) permiten caracterizar cuantitativamente la señal, aunque no sustituyen el análisis morfológico visual, ya que no conservan información sobre la secuencia temporal de los eventos.
5. Convertir un ECG a formato WAV es posible porque ambas son señales digitales. La conversión a formato WAV facilita la exploración auditiva del ritmo cardiaco, aunque con pérdida de la información morfológica fina que sí se aprecia en la representación gráfica.

