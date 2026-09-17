 # Informe 4  - Aplicación del BiTalino en ECG
## **Objetivos**
* Adquirir señales biomédicas de ECG en derivadas bipolares (DI, DII, DIII).
* Hacer una correcta configuración de BiTalino.
* Extraer la información de las señales ECG del software OpenSignals (r)evolution



## **Materiales y equipos** 

<div align="center">

|  **Modelo**  | **Descripción** | **Cantidad** |
|:------------:|:---------------:|:------------:|
| (R)EVOLUTION |   Kit BITalino  |       1      |
|       -      |      Laptop     |       1      |

</div>

## **Procedimiento**
## Preparación del sistema y colocación de los electrodos
Al incio el labortorio se preparó el sistema BITalino utilizando el sensor de electrocardiografía (ECG) y tres electrodos adhesivos de Ag/AgCl. El sensor ECG cuenta con dos cables de medición, correspondientes a IN+ e IN−, y un cable de referencia (REF). Para el montaje empleado, estos cables correspondieron al cable rojo (IN+), negro (IN−) y blanco (REF).
Los electrodos fueron colocados en zonas con baja actividad muscular específicamente sobre las regiones correspondientes a ambas clavículas y la cresta ilíaca izquierda, de esta forma disminuye la interferencia producida por la actividad muscular y los artefactos asociados al movimiento durante la adquisición del ECG.

Figura 1. Ubicación de los electrodos y configuración de las derivaciones I, II y III de Einthoven.

<img width="516" height="161" alt="image" src="https://github.com/user-attachments/assets/3d67087c-48a4-42e1-9230-96af131b9587" />

## Configuración de las derivaciones de Einthoven
Una vez colocados los tres electrodos en las posiciones corporales correspondientes, se configuró el sensor para realizar las adquisiciones mediante las tres derivaciones de Einthoven: DI, DII y DIII. Estas derivaciones permiten registrar la actividad eléctrica cardíaca desde diferentes orientaciones en el plano frontal, ya que cada una mide una diferencia de potencial entre dos puntos determinados del cuerpo.

Para obtener cada derivación, se modificó la conexión de los cables IN+, IN− y REF entre los tres electrodos . La configuración utilizada se presenta en la siguiente tabla:

Tabla 1. Configuración de los electrodos y conexiones de los cables para las derivaciones DI, DII y DIII.

| **Derivación** | **Electrodo positivo (IN+)** | **Electrodo negativo (IN−)** | **Electrodo de referencia (REF)** | **Diferencia de potencial registrada**         |
| -------------- | ---------------------------- | ---------------------------- | --------------------------------- | ---------------------------------------------- |
| **DI**         | Clavícula izquierda          | Clavícula derecha            | Cresta ilíaca izquierda           | Entre el brazo izquierdo y el brazo derecho    |
| **DII**        | Cresta ilíaca izquierda      | Clavícula derecha            | Clavícula izquierda               | Entre la pierna izquierda y el brazo derecho   |
| **DIII**       | Clavícula izquierda          | Cresta ilíaca izquierda      | Clavícula derecha                 | Entre la pierna izquierda y el brazo izquierdo |

## Adquisición de la lectura basal
Una vez realizada la configuración inicial del sistema, se inició la adquisición de la señal mediante el software OpenSignals (r)evolution. Primero se obtuvo una lectura basal durante aproximadamente 30 segundos, manteniendo al participante en reposo y con respiración normal. Durante esta etapa se procuró mantener el cuerpo estable para obtener una señal con el menor nivel posible de ruido y utilizarla como referencia para las condiciones posteriores.
La lectura basal se realizó para las tres derivaciones de Einthoven, registrándose sucesivamente DI, DII y DIII.

Figura 2. Adquisición de la señal ECG durante la lectura basal en reposo.

<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/c195a3d1-56e9-47b9-9d52-e5bda72462a2" />

## Adquisición durante hiperventilación
Posteriormente, se realizó la prueba de hiperventilación. Para esta etapa, el participante modificó voluntariamente su patrón respiratorio acelerando la inhalación, mantenimiento y exhalación, durante aproximadamente 30 segundos.

La señal electrocardiográfica se registró nuevamente mediante las derivaciones DI, DII y DIII. Entre las adquisiciones correspondientes a cada derivación se estableció un período de reposo de aproximadamente 1 minuto, con el propósito de permitir la recuperación del participante

Figura 3. Adquisición de la señal ECG durante la prueba de hiperventilación.

<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/3385b0fd-4ddd-4751-a6a0-6b3716fc2499" />

## Adquisición durante hipoventilación
En la prueba de hipoventilación el participante mantuvo la respiración durante el mayor tiempo posible y posteriormente realizó la exhalación indicada, tras lo cual se procedió a cuantificar el registro obtenido. Se las tres derivaciones de Einthoven teniendo 1 minuto y 30 segundos entre cada una de ellas 

Figura 4. Adquisición de la señal ECG durante la prueba de hipoventilación.

<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/dfdde800-0877-4147-b045-7a4e6b08309e" />

## Adquisición posterior a la actividad aeróbica
Finalmente, se realizó una actividad aeróbica durante aproximadamente 5 a 10 minutos, con el objetivo de generar una condición de esfuerzo físico. Al finalizar la actividad, se realizó rápidamente la adquisición de la señal electrocardiográfica para registrar la respuesta del organismo inmediatamente después del esfuerzo.
La señal se obtuvo nuevamente mediante las derivaciones DI, DII y DIII, estableciendo un intervalo aproximado de 30 segundos entre las adquisiciones de cada derivación.

Figura 5. Realización de la actividad aeróbica previa a la adquisición de la señal ECG.

<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/787af0b0-f284-480e-9a33-569898662675" />


## **Resultados**
### Fotos de conexión usada.


### Videos de las señales en cada actividad
|                 **Modelo**                 | **Video** |
|:------------------------------------------:|:---------:|
|                **Reposo**                |Insertar video aqui (borrar luego este texto)|
|            **Hiperventilación** |Insertar video aqui (borrar luego este texto)|
|                **Hipoventilación**                |Insertar video aqui (borrar luego este texto)|
|       **Actividad aeróbica**       |Insertar video aqui (borrar luego este texto)|


### Ploteo de la señal en OpenSignals
**Señal cruda:** 
  * Reposo
    
    En un intervalo de tiempo de 15 segundos:

    
  * Hiperventilación
    
    En un intervalo de tiempo de 15 segundos:
    
    <div align="center">
    </div> 
    
  * Hipoventilación
    
    En un intervalo de tiempo de 15 segundos:
    
    <div align="center">
    </div> 

  * Actividad aeróbica
    
    En un intervalo de tiempo de 15 segundos:
    
    <div align="center">
    </div> 

### Ploteo de la señal en Python

**Señal original y filtrada:**

  * Reposo
    
    En un intervalo de tiempo de 15 segundos:

    
  * Hiperventilación
    
    En un intervalo de tiempo de 15 segundos:
    
    <div align="center">
    </div> 
    
  * Hipoventilación
    
    En un intervalo de tiempo de 15 segundos:
    
    <div align="center">
    </div> 

  * Actividad aeróbica
    
    En un intervalo de tiempo de 15 segundos:
    
    <div align="center">
    </div> 


### Archivos

* [Programa de ploteo (Jupyter Notebook)]()

  
## Resumen y explicación de la señal


## Preguntas de la guía del Bitalino ECG

P1. ¿Cuáles son los tipos de fuentes de ruido más típicos que afectan al ECG?

P2. ¿Por qué el cambio en la posición de los sensores (derivaciones I-III) modifica las componentes de la señal de ECG? ¿Cómo cambian estas componentes?

P3. Describe si existen diferencias significativas en la señal al registrarla desde distintas ubicaciones del cuerpo (por ejemplo, muñeca / clavícula / pecho). ¿Cuál podría ser la causa? ¿Esperabas esos cambios en la señal? Guarda un segmento de señal de cada una para visualizar las diferencias.

P4. Es bien sabido que los sistemas cardíaco y respiratorio están profundamente interconectados. ¿Esperas que los diferentes tipos de respiración (por ejemplo, más rápida o más profunda) influyan en las señales de ECG? Muestra capturas de pantalla de señales de ECG en distintas circunstancias respiratorias y describe las variaciones, si las hay.

P5. En la Home-Guide #1 (guía anterior sobre EMG) viste que distintas cantidades de fuerza producidas en el músculo generaban señales con diferentes amplitudes. ¿Cómo influye el movimiento en tu señal de ECG?

P6. Según tu conocimiento, ¿cómo se pueden detectar la bradicardia y la taquicardia en la señal de ECG?

