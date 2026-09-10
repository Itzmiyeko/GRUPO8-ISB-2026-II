# Informe 3  - Aplicación del BiTalino en EMG
## **Objetivos**
* Adquirir señales biomédicas de EMG en diferentes músculos.
* Hacer una correcta configuración de BiTalino.
* Extraer la información de las señales EMG del software OpenSignals (r)evolution



## **Materiales y equipos** 

<div align="center">

|  **Modelo**  | **Descripción** | **Cantidad** |
|:------------:|:---------------:|:------------:|
| (R)EVOLUTION |   Kit BITalino  |       1      |
|       -      |      Laptop     |       1      |

</div>


## **RESULTADOS**

### **Conexión utilizada**

Para la adquisición de la señal EMG se empleó el sensor EMG de tres electrodos
del BITalino, conectado a la placa de adquisición como se muestra a continuación.

<img width="473" height="1024" alt="WhatsApp Image 2026-09-10 at 11 06 00 AM" src="https://github.com/user-attachments/assets/c426424b-fdc1-46b7-a1c6-b1388821d784" />

Posteriormente, los electrodos del sensor EMG fueron colocados sobre el
usuario de prueba para registrar la actividad eléctrica del bíceps braquial.
La ubicación de los electrodos se realizó siguiendo las recomendaciones
establecidas en la **Guía de Procedimiento de Electromiografía y Velocidad de
Conducción de Nervios Periféricos**, elaborada en 2020 por el **Instituto
Nacional de Salud del Niño San Borja** para el **Ministerio de Salud (MINSA)**.


### Video de señal

### Ploteo de la señal en OpenSignals
**1.Señales del biceps:** 
  * Reposo

  En resposo 1 se registró la señal EMG del bíceps braquial en condición de reposo,     manteniendo el músculo relajado durante la adquisición. 
<img width="473" height="1024" alt="WhatsApp Image 2026-09-10 at 11 06 00 AM" src="https://github.com/user-attachments/assets/353424cb-777e-47c2-a301-2da99d1ed41c" />

    
  * Movimiento Leve
En la prueba 2 se registró la señal del EMG del bíceps braquial durante una contracción leve, realizando un movimiento de baja intensidad durante la adquisición.
<img width="473" height="1024" alt="WhatsApp Image 2026-09-10 at 11 19 31 AM" src="https://github.com/user-attachments/assets/2e44d2a9-a74f-4f5e-ab85-e772035d0ccf" />

    
  * Movimiento Opuesto
En la prueba 3 se registró la señal del EMG del bíceps braquial durante una contracción en oposición, realizando un movimiento de mayor intensidad durante la adquisición
<img width="473" height="1024" alt="WhatsApp Image 2026-09-10 at 11 25 17 AM" src="https://github.com/user-attachments/assets/9a778683-b9f2-4155-9862-b4fd071888e9" />

A continuación, se presenta un video donde se muestra el movimiento realizado durante la adquisición de la señal EMG del bíceps braquial, desde el inicio hasta la finalización de la prueba.
https://github.com/user-attachments/assets/1e87e90e-cda8-46fa-80ed-fc97e57e164a




**2.Señales del musculo del pulgar:** 
  * Reposo
  A continuación, se presenta un video y una imagen correspondientes a la adquisición de la señal EMG del pulgar en condición de reposo, manteniendo el dedo relajado durante toda la prueba.
      
  * Movimiento Leve
A continuación, se presenta un video y una imagen correspondientes al movimiento leve realizado con el dedo pulgar durante la adquisición de la señal EMG.
    
  * Movimiento Opuesto
A continuación, se presenta un video y una imagen correspondientes al movimiento de oposición realizado con el dedo pulgar durante la adquisición de la señal EMG.

### Ploteo de la señal en Python

**1.Señales del biceps:**
  * Reposo
  
    <div align="center">
    <img width="989" height="299" alt="WhatsApp Image 2026-09-10 at 10 40 08 AM" src="https://github.com/user-attachments/assets/2e124cfa-4046-4599-ae7c-943f5538ca13" />
  
    </div>
    
  * Movimiento Leve
    <div align="center">
    <img width="988" height="886" alt="WhatsApp Image 2026-09-10 at 10 40 09 AM" src="https://github.com/user-attachments/assets/2a8392b9-5b4b-4750-b873-f133b878b83f" />
  
    </div>
    
  * Movimiento Opuesto
    <div align="center">
  <img width="989" height="886" alt="WhatsApp Image 2026-09-10 at 10 40 09 AM (2)" src="https://github.com/user-attachments/assets/cd9fba6a-ec08-4a08-ae8d-47d456e11618" />
    </div>

**2.Señales del musculo del pulgar:** 
  * Reposo
  
      
  * Movimiento Leve

    
  * Movimiento Opuesto

### Archivos
### Resumen y explicación de la señal
