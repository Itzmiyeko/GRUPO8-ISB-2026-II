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

## **Resultados**
### Fotos de conexión usada (Electrodos-cuerpo, BITalino-cables).


### Video de señal
1. Video de la señal del biceps
   

https://github.com/user-attachments/assets/388064dc-3f96-470d-be18-31ba369073b5

2. Video de la señal del pulgar
   

https://github.com/user-attachments/assets/47313070-4606-488b-8ca7-22d7f4bfdfad



https://github.com/user-attachments/assets/e2eb4bf3-17f6-4228-84bb-cafdc206dc85



### Ploteo de la señal en OpenSignals
**1.Señales del biceps:** 
  * Reposo
    
    En un intervalo de tiempo de 10 segundos:
    
    <div align="center">
    <img width="1832" height="152" alt="rep1" src="https://github.com/user-attachments/assets/b9c1d1f8-153d-4145-a8b0-c5402e308f3d" />
    </div> 
    
  * Movimiento Leve
    
    En un intervalo de tiempo de 10 segundos:
    
    <div align="center">
    <img width="1917" height="121" alt="leve1_brazo" src="https://github.com/user-attachments/assets/974262ce-05aa-4b3c-8306-c3d092e3341f" />  
    </div> 
    
  * Movimiento Opuesto
    
    En un intervalo de tiempo de 20 segundos:
    
    <div align="center">
<img width="1896" height="125" alt="Opo1_brazo" src="https://github.com/user-attachments/assets/dfac770f-07f0-463f-aa3a-0ca9626eef40" />
    </div> 


**2.Señales del musculo del pulgar:** 
  * Reposo
    
    En un intervalo de tiempo de 10 segundos:
    
    <div align="center">
   <img width="1916" height="136" alt="rep2" src="https://github.com/user-attachments/assets/e4156017-9b23-4127-b988-2509b2c9c0f4" />

  
    </div> 
      
  * Movimiento Leve
        
    En un intervalo de tiempo de 10 segundos:
    
    <div align="center">
   <img width="1892" height="137" alt="leve_pulgar" src="https://github.com/user-attachments/assets/5fdc1f78-b272-4972-90c0-0ec78bedfabd" />

  
    </div> 
    
  * Movimiento Opuesto
        
    En un intervalo de tiempo de 10 segundos:
    
    <div align="center">
   <img width="1917" height="137" alt="opo_pulgar" src="https://github.com/user-attachments/assets/bb4e1f7c-9451-4af8-8b61-b903b62e4dc2" />

  
    </div> 

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
- Resumen y explicación de las señales del biceps:
Resumen: Las señales EMG presentan diferencias claras entre las tres condiciones evaluadas. En reposo, la señal mantiene una amplitud baja y relativamente estable alrededor de 0 mV, con pequeñas oscilaciones atribuibles a actividad muscular basal y/o ruido de adquisición. Durante el movimiento leve se observa un incremento transitorio de la amplitud, alcanzando valores mayores que en reposo. Las tres repeticiones presentan un comportamiento general similar, aunque varían en el momento y amplitud de la activación máxima. Finalmente, durante el movimiento con fuerza contraria se observa una activación muscular considerablemente mayor y más prolongada, con amplitudes que superan ampliamente las registradas en las otras condiciones.
Explicación: El incremento de la amplitud de la señal EMG puede asociarse con un aumento de la activación muscular requerido para realizar la tarea. Por ello, la señal presenta menor amplitud en reposo, una activación intermedia durante el movimiento leve y una activación mucho mayor durante el movimiento contra resistencia. Las diferencias observadas entre las tres repeticiones de cada condición pueden deberse a variaciones en la ejecución del movimiento, el nivel de contracción y/o factores propios de la adquisición de la señal EMG.
