# LAB 3 — Filtros FIR, IIR y Transformada Z

## Introducción

En este laboratorio se realizó el análisis y procesamiento digital de una señal ECG con el objetivo de identificar sus principales componentes frecuenciales, detectar interferencias y diseñar filtros digitales que permitan reducir el ruido sin perder información fisiológica relevante.

El trabajo siguió el proceso:

**Señal → análisis temporal → FFT → identificación del ruido → diseño del filtro → filtrado → validación → interpretación fisiológica.**

## Objetivos

- Analizar una señal ECG en el dominio temporal y frecuencial.
- Utilizar la FFT para identificar componentes de frecuencia.
- Comprender la relación entre la Transformada de Fourier y la Transformada Z.
- Diseñar y comparar filtros FIR e IIR.
- Seleccionar una frecuencia de corte a partir de las características de la señal.
- Evaluar el efecto del filtrado sobre la morfología del ECG.
- Validar cuantitativamente la calidad de la señal filtrada.

## Herramientas utilizadas

- Python 3.x
- NumPy
- SciPy
- Matplotlib
- Pandas
- NeuroKit2
- Jupyter Notebook / Google Colab

## 1. Generación y caracterización de la señal

Se generó una señal ECG sintética utilizando `NeuroKit2` con los siguientes parámetros:

- Duración: **10 s**
- Frecuencia de muestreo: **250 Hz**
- Frecuencia cardíaca: **70 bpm**
- Número de muestras: **2500**

En el dominio temporal se identificaron los principales elementos de la morfología ECG, incluyendo las ondas **P y T** y el complejo **QRS**.

La frecuencia de muestreo determina la frecuencia máxima observable según el criterio de Nyquist:

fNyquist= fs/2

## 2. Análisis frecuencial mediante FFT

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

## 3. Diseño y comparación de filtros FIR e IIR

Se diseñaron dos filtros pasa-bajas:

### Filtro FIR

- Tipo: **Pasa-bajas**
- Número de taps: **101**
- Frecuencia de corte: **40 Hz**
- Diseño mediante `firwin`

El filtro FIR no utiliza realimentación y permite obtener una respuesta de fase lineal con mayor facilidad.

### Filtro IIR

- Tipo: **Butterworth pasa-bajas**
- Orden: **4**
- Frecuencia de corte: **40 Hz**
- Representación: **SOS**
- Aplicación: `sosfiltfilt`

El filtro IIR utiliza realimentación, por lo que puede alcanzar respuestas similares utilizando un orden menor. Se utilizó `sosfiltfilt` para evitar desplazamientos temporales asociados al filtrado en un solo sentido.

### Comparación

El MSE obtenido respecto a la señal original fue:

| Filtro | MSE |
|---|---:|
| FIR | \(1.359*10^{-6}\) |
| IIR | \(8.745*10^{-7}\) |

En este caso, el filtro IIR presentó un MSE ligeramente menor respecto a la señal ECG original.

## 4. Procesamiento de ECG contaminado

Para evaluar el desempeño del filtrado se agregó una interferencia sinusoidal de:

- Amplitud: **0.20**
- Frecuencia: **35 Hz**

La señal contaminada se modeló como:
noise = A * np.sin(2* np.pi * f_noise * t)
ecg_contaminated = ecg_clean + noise

<img width="1106" height="382" alt="image" src="https://github.com/user-attachments/assets/b542ce4f-1d51-43b8-8ecc-3dd21d97a0ed" />

Mediante la FFT se identificó un pico de interferencia aproximadamente en **35 Hz**.

A partir de este análisis se diseñó un filtro Butterworth pasa-bajas de:

- Frecuencia de corte: **25 Hz**
- Orden: **4**
- Filtrado: `sosfiltfilt`

La frecuencia de corte se seleccionó por debajo de la interferencia de 35 Hz, buscando reducir el ruido y conservar la mayor parte de la información fisiológica del ECG.

## 5. Validación del filtrado

Se compararon la señal contaminada y la señal recuperada tanto en el dominio temporal como en el frecuencial.

Los resultados obtenidos fueron:

- **MSE:** \(9.381*10^{-5}\)
- **RMSE:** \(0.00969\)
- **SNR antes del filtrado:** **5.10 dB**
- **SNR después del filtrado:** **28.39 dB**

El aumento considerable del SNR indica una mejora importante de la relación señal-ruido.

Además, la FFT mostró una reducción significativa del pico correspondiente a la interferencia de 35 Hz.

La morfología general del ECG se mantuvo, incluyendo los complejos QRS y las ondas P y T, y los intervalos R-R permanecieron sin desplazamientos apreciables.

## 6. Errores de diseño del filtro

También se evaluaron situaciones en las que el filtro está mal diseñado.

### Frecuencia de corte demasiado baja

Se utilizó una frecuencia de corte de **5 Hz**. Como consecuencia, el complejo QRS perdió su característica forma rápida y se observó más aplanado y ensanchado.

El MSE aumentó hasta:

\[
MSE=2.715*10^{-2}
\]

Esto demuestra que una frecuencia de corte demasiado baja puede eliminar información fisiológica relevante.

### Desplazamiento de fase

También se comparó el filtrado mediante `sosfilt` frente a `sosfiltfilt`.

El filtrado en un solo sentido puede producir un desplazamiento temporal de la señal debido a la respuesta de fase del filtro IIR. Esto puede afectar la ubicación temporal de los picos R y, por lo tanto, las mediciones de intervalos fisiológicos.

El uso de `sosfiltfilt` permite realizar un filtrado de fase cero, evitando este desplazamiento.

## 7. Transformada Z

La Transformada Z permitió analizar los filtros como sistemas discretos mediante su función de transferencia:

\[
H(z)=\frac{Y(z)}{X(z)}
\]

A través de la función de transferencia se pueden estudiar los **polos, ceros, estabilidad y respuesta en frecuencia**.

La relación con Fourier se obtiene evaluando la función de transferencia sobre el círculo unitario:

\[
z=e^{j\omega}
\]

Por ello:

**Transformada Z → análisis general de sistemas discretos**

**Transformada de Fourier → análisis frecuencial**

## Conclusiones

El laboratorio permitió comprobar que el diseño de un filtro para señales biomédicas debe basarse en un análisis previo de la señal y no en la eliminación indiscriminada de frecuencias.

La FFT permitió identificar las componentes frecuenciales y detectar la interferencia de **35 Hz**, a partir de la cual se seleccionó una frecuencia de corte de **25 Hz** para recuperar el ECG contaminado.

La comparación FIR-IIR mostró que ambos filtros pueden reducir componentes no deseadas, pero presentan diferencias en realimentación, orden, fase, estabilidad y costo computacional.

Finalmente, las métricas obtenidas mostraron una mejora significativa después del filtrado, aumentando el SNR de **5.10 dB a 28.39 dB**, mientras se conservó la morfología general del ECG. Por ello, la validación debe considerar simultáneamente el análisis temporal, frecuencial y cuantitativo para asegurar que el ruido sea reducido sin perder información fisiológica relevante.
