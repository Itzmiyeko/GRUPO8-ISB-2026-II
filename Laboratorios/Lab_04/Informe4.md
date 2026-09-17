# Informe 3  - Aplicación del BiTalino en ECG
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

## **Resultados**
### Fotos de conexión usada (Electrodos-cuerpo, BITalino-cables).


### Video de señal en reposo



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

P5. En la Guía para el hogar #1 (guía anterior sobre EMG) viste que distintas cantidades de fuerza producidas en el músculo generaban señales con diferentes amplitudes. ¿Cómo influye el movimiento en tu señal de ECG?

P6. Según tu conocimiento, ¿cómo se pueden detectar la bradicardia y la taquicardia en la señal de ECG?

