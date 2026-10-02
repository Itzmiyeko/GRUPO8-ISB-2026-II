# Introducción
La electroencefalografía (EEG) es una técnica que nos permite registrar la actividad eléctrica del cerebro mediante sensores colocados sobre la cabeza. Esta actividad eléctrica se manifiesta en forma de ondas cerebrales que cambian según nuestro estado de ánimo, nivel de alerta o lo que estemos haciendo en ese momento:
 - Ondas delta (0–4 Hz): Aparecen principalmente durante el sueño profundo.   
 - Ondas theta (4–8 Hz): Se relacionan con momentos de somnolencia o cuando realizamos           pruebas   de memoria y concentración.   
 - Ondas alfa (8–12 Hz): Predominan cuando estamos relajados, con los ojos cerrados, y           disminuyen en cuanto nos ponemos a pensar o abrimos los ojos.
 - Ondas beta (12–25 Hz): Están presentes cuando tenemos la mente activa, concentrada o          resolviendo problemas.   
 - Ondas gamma (>25 Hz): Se vinculan con procesos mentales de alta exigencia y                 concentración     intensa.

Figura 1: Principales lóbulos cerebrales y sus funciones asociadas

<img width="857" height="523" alt="image" src="https://github.com/user-attachments/assets/37b4ec69-86d2-4cac-91ff-9d84019847dc" />

Para este estudio, se decidió colocar los electrodos específicamente en el lóbulo frontal (en la zona de la frente). Las razones principales para elegir esta área son dos: primero, porque el lóbulo frontal se encarga de funciones clave como la planificación, la concentración, la toma de decisiones y el pensamiento activo; y segundo, por una razón práctica fundamental de medición: al estar ubicados en la frente, la piel está libre de cabello, lo que permite que los sensores hagan un contacto directo y limpio con la piel, evitando las interferencias que el pelo suele causar en las señales eléctricas.

Figura 2: Clasificación de las ondas cerebrales según su frecuencia (Gamma, Beta, Alpha, Theta y Delta), rangos en Hz y tipos de tareas o estudios asociados.

<img width="552" height="291" alt="image" src="https://github.com/user-attachments/assets/980edba3-5828-4c28-84b6-4afb8ba286d3" />

# Ubicación de los electrodos:
La colocación de los electrodos se distribuye de la siguiente manera sobre el sujeto de prueba:
- Electrodo activo principal: Se coloca en la parte frontal izquierda de la frente.
- Electrodo de referencia/comparación: Se ubica en la parte frontal derecha de la frente      para contrastar la señal.
- Electrodo de referencia física (REF): Se coloca en la zona ósea detrás de la oreja. Esta área sin actividad cerebral directa sirve como punto de apoyo neutral para estabilizar la lectura y reducir ruidos eléctricos externos.

  <img width="729" height="398" alt="image" src="https://github.com/user-attachments/assets/b3bab594-b5c8-499e-8151-7f73ad273c36" />

  
  Figura 3: Esquema de posicionamiento de los electrodos BITalino en la región frontal ($F_{P1}$, $F_{P2}$) y el electrodo de referencia (REF) colocado en el lóbulo de la oreja.

# Materiales e instrumentos
- Kit BITalino (Core BT): Plataforma biomédica inalámbrica empleada para la adquisición de la señal electroencefalográfica (EEG).
- Batería de 3.7V: Fuente de alimentación portátil para el funcionamiento del kit BITalino.
- Sensor de EEG y cable de referencia (1-lead electrode cable): Sensor especializado para     la captura de la actividad cerebral y cable auxiliar para el electrodo de referencia.
- Electrodos de superficie descartables: Dispositivos adhesivos que se conectan a los pines   del sensor para captar la actividad eléctrica de manera no invasiva.
- Software OpenSignals (r)evolution: Herramienta oficial utilizada para la configuración,     adquisición y visualización en tiempo real de las señales.
- Laptop: Equipo de cómputo utilizado para ejecutar el software de registro y análisis de     datos.

# Metodología y Procedimiento Experimental
Para llevar a cabo el registro de la actividad electroencefalográfica (EEG), el estudio contempló la participación de dos evaluados bajo condiciones experimentales controladas. El protocolo consistió en someter a ambos participantes a una misma secuencia de estímulos y estados de reposo para posteriormente comparar la respuesta de sus ondas cerebrales ante distintas cargas cognitivas y sensoriales.

La dinámica experimental se estructuró en cuatro etapas secuenciales:

Lectura basal (Reposo inicial):
Se solicitó al evaluado permanecer en un estado de tranquilidad inicial, intentando anular o minimizar la mayor cantidad de estímulos externos posibles (evitando ruidos y movimientos innecesarios) durante un intervalo aproximado de 1 a 2 minutos. Esta fase permite registrar la actividad cerebral de referencia de cada participante en condiciones de relajación base.

<img width="1200" height="1600" alt="image" src="https://github.com/user-attachments/assets/26aacb11-4229-4c19-bf7a-d4a0302b2569" />


Ciclos de apertura y cierre de ojos:
Se le dio la indicación al evaluado de realizar 5 repeticiones alternadas de apertura y cierre de ojos. Cada transición se mantuvo por un lapso de 5 segundos, manteniendo la vista fija en un punto específico de referencia durante los momentos de apertura. Esta prueba clásica busca evidenciar la modulación de las ondas alfa, las cuales suelen incrementarse notablemente al cerrar los ojos y bloquear el estímulo visual.
Manteniendo al participante con un auricular puesto en un solo oído, se procedió a susurrarle un total de 7  preguntas de alta complejidad analítica. No se le solicitó una respuesta inmediata; por el contrario, se estableció un marco de reflexión de aproximadamente 20 a 30 segundos por pregunta para obligar al cerebro a un proceso de concentración profunda y resolución de problemas (estimulando la actividad en las ondas beta y theta).

Estímulo musical comparativo (Opcional):
Como fase complementaria, se expuso al evaluado a escuchar fragmentos musicales de contraste (aproximadamente entre 1 a 1 minuto y medio por género), comparando el impacto neurofisiológico de música relajante de tipo Lo-Fi frente a música más intensa o estridente.

# Resultados
## Ploteo en la señal de Python de la participante 1

### 1. Lectura Basal

![Emma basal](figuras_Emma_Vivi/Emma_Basal.png)

### 2. Apertura y cierre de ojos

![Emma abre y cierra](figuras_Emma_Vivi/Emma_Abre_y_cierra.png)

### 3. Preguntas complejas

![Emma preguntas complejas](figuras_Emma_Vivi/Emma_Preguntas_complejas.png)

### 4.1. Música suave

![Emma música tranquila](figuras_Emma_Vivi/Emma_Música_tranquila.png)

### 4.2. Música fuerte

![Emma música ruidosa](figuras_Emma_Vivi/Emma_Música_ruidosa.png)

## Ploteo en la señal de Python de la participante 2

### 1. Lectura Basal

![Vivi basal](figuras_Emma_Vivi/Vivi_Basal.png)

### 2. Apertura y cierre de ojos

![Vivi abre y cierra](figuras_Emma_Vivi/Vivi_Abre_y_cierra.png)

### 3. Preguntas complejas

![Vivi preguntas complejas](figuras_Emma_Vivi/Vivi_Preguntas_complejas.png)

### 4.1. Música suave

![Vivi música tranquila](figuras_Emma_Vivi/Vivi_Música_tranquila.png)

### 4.2. Música fuerte

![Vivi música ruidosa](figuras_Emma_Vivi/Vivi_Música_ruidosa.png)

## Comparación de las dos participantes en Python

### 1. Lectura Basal

![Comparación basal Emma y Vivi](figuras_Emma_Vivi/Comparacion_Emma_Vivi_Basal.png)

### 2. Apertura y cierre de ojos

![Comparación abre y cierra Emma y Vivi](figuras_Emma_Vivi/Comparacion_Emma_Vivi_Abre_y_cierra.png)

### 3. Preguntas complejas

![Comparación preguntas complejas Emma y Vivi](figuras_Emma_Vivi/Comparacion_Emma_Vivi_Preguntas_complejas.png)

### 4.1. Música suave

![Comparación música tranquila Emma y Vivi](figuras_Emma_Vivi/Comparacion_Emma_Vivi_Música_tranquila.png)

### 4.2. Música fuerte

![Comparación música ruidosa Emma y Vivi](figuras_Emma_Vivi/Comparacion_Emma_Vivi_Música_ruidosa.png)

## Ploteo en la señal en OpenSignals de la participante 1
### 1. Lectura Basal

![Emma basal OpenSignals](figuras_Emma_Vivi/emma_basal_1_opensignal.jpeg)


### 2. Apertura y cierre de ojos

![Emma abre/cierra OpenSignals](figuras_Emma_Vivi/emma_abreycierra_2_opensignal.jpeg)

### 3. Preguntas complejas

![Emma preguntas OpenSignals](figuras_Emma_Vivi/emma_preguntas_3_opensignal.jpeg)

### 4.1. Música suave

![Emma música suave OpenSignals](figuras_Emma_Vivi/emma_musica_suave_4.1_opensignal.jpeg)

### 4.2. Música fuerte

![Emma música fuerte OpenSignals](figuras_Emma_Vivi/emma_musica_fuerte_4.2_opensignal.jpeg)

## Ploteo en la señal en OpenSignals de la participante 2
### 1. Lectura Basal

![vivi basal OpenSignals](figuras_Emma_Vivi/vivi_basal_1_opensignal.jpeg)

### 2. Apertura y cierre de ojos

![vivi abre/cierra OpenSignals](figuras_Emma_Vivi/vivi_abreycierra_2_opensignal.jpeg)

### 3. Preguntas complejas

![vivi preguntas OpenSignals](figuras_Emma_Vivi/vivi_preguntas_3_opensignal.jpeg)

### 4.1. Música suave

![vivi música suave OpenSignals](figuras_Emma_Vivi/emma_musica_suave_4.1_opensignal.jpeg)

### 4.2. Música fuerte

![vivi música fuerte OpenSignals](figuras_Emma_Vivi/vivi_musica_fuerte_4.2_opensignal.jpeg)


# Resumen y explicación
Las señales EEG fueron extraídas del módulo BiTalino, los cuales posteriormente de su adquisición, se analizo en Python. Como primer paso se extrae la señal cruda en valores de μV. Posteriormente se crea funciones de filtros para que la señal EEG se pueda observar de manera más nitida las señales y para eliminar también el ruido y las interferencias que contaminan, permitiendo obtener un trazo limpio y fácil de interpretar.

Los filtros que se emplearon fueron los siguientes:

Filtro pasa-altos (0.5 Hz) — para eliminar el baseline wander (deriva de la línea base), causado por la respiración, el movimiento de electrodos y el sudor.
Filtro pasa-bajos (50 Hz) — para eliminar ruido de alta frecuencia, principalmente interferencia muscular (EMG) captada por los mismos electrodos.
Filtro notch (rechazo de banda) de 60 Hz — para eliminar la interferencia de la red eléctrica con un factor de calidad de 30, para que ancho de banda de atenuación sea corta (2 Hz).

Como se puede observar en el archivo analisis_bitalino_EEG_frecuencia, en la gráfica densidad espectral de potencia existe un artefacto que existe entre 0.5 a 2 Hz, por lo que no consideraremos ese pico, ya que es dato espurio.

**- Lectura Basal**
  Se observa en ambas compañeras (Emma y Viviana) una dominancia pronunciada de la banda Delta (0.5-4 Hz), que como mencionamos antes se trata de un posible artefacto, seguida de una caída progresiva y sostenida hacia las bandas de mayor frecuencia, sin picos secundarios de relevancia en Theta, Alfa o Beta.
  En el caso de nuestra compañera Emma, la onda que tiene más predominancia entre **Theta y Alfa**, que podria estar correctamente interpretado ya que se trata de un estado de relajación. Caso contrario, nuestra compañera Viviana presenta una mayor predominancia en Delta, que puede ser producto a un error en la colocación de la tierra o producto de un parpadeo reflejo bajo el antifaz, dado que los electrodos frontales (FP1/FP2) son particularmente sensibles a este tipo de contaminación.
<img width="989" height="490" alt="emmac6_basal" src="https://github.com/user-attachments/assets/66b9ce33-3462-4c66-ba8c-85b4458e0c91" />
<img width="989" height="490" alt="vivic6_basal" src="https://github.com/user-attachments/assets/00aeb285-5328-40a8-8d1d-adfb1354944f" />


**- Apertura y cierre de los ojos**
En la condición de apertura y cierre de ojos, ejecutada mediante cinco repeticiones del ciclo con un intervalo de cinco segundos entre cierre y apertura, y con indicación explícita de fijar la mirada en un punto fijo durante las fases de ojos abiertos, se observa nuevamente una dominancia de la banda Delta en ambas sujetas (0.8 µV²/Hz en Vivi, hasta 19 µV²/Hz en Emma), sin que se distinga un pico diferenciado y sostenido específicamente dentro de la banda Alfa (8 a 12 Hz) que seria indicativo del fenómeno de bloqueo alfa (alpha blocking) característico de esta dinámica. Esta ausencia de un pico Alfa claro es atribuible, en primer lugar, al hecho de que el espectro de Welch promedia la totalidad de la ventana de registro, mezclando las fases de ojos cerrados (donde se esperaría el incremento de Alfa) con las fases de ojos abiertos con fijación visual, diluyendo así cualquier incremento transitorio de esta banda. En segundo lugar, el propio acto de parpadeo y cierre palpebral repetido —que constituye el evento central de esta dinámica— introduce artefactos de amplitud considerable en el rango de baja frecuencia, los cuales probablemente enmascaran el efecto Alfa, más sutil en comparación. Se recomienda, para análisis futuros, segmentar la señal en los cinco ciclos individuales de apertura/cierre y calcular el espectro de cada fase de forma independiente, a fin de aislar con mayor precisión el efecto esperado.

<img width="989" height="490" alt="acc2_emma" src="https://github.com/user-attachments/assets/e7de55ba-421b-4b86-a552-159b857610c1" />

<img width="989" height="490" alt="acc6_vivi" src="https://github.com/user-attachments/assets/6d879bc7-048c-4905-b269-f4f7548f0ae2" />

**- Preguntas**
En la condición de susurro de preguntas, que contempla la formulación de cinco preguntas complejas sin exigir respuesta inmediata y con un margen de reflexión de 20 a 30 segundos por pregunta, se observan resultados divergentes entre ambas sujetas. En el registro de Viviana en el FP1 (Canal 6) , el espectro exhibe un pico secundario moderado pero identificable alrededor de 19-20 Hz, dentro de la **banda Beta**, que se eleva por encima de la tendencia decreciente general del espectro; este hallazgo es consistente con el estado de procesamiento cognitivo y reflexión interna que caracteriza la mayor parte de la ventana de registro de esta condición. En el registro de Emma en el FP2 (Canal 2), al excluir la banda Delta del análisis, por corresponder esta al artefacto de baja frecuencia ya identificado,  la potencia se concentra de forma predominante en las frecuencias de onda entre **Beta y Gamma** igualmente, sin que se identifique un pico puntual y diferenciado que sobresalga claramente de esta tendencia decreciente. Aunque este cerca de la onda esperada, lo que se esperaba es que haya una predominancia en la onda Gamma ya que se trata de tareas de alto procesamiento cognitivo.

<img width="989" height="490" alt="preguntasc6_vivi" src="https://github.com/user-attachments/assets/c886894b-c6b0-4b49-98cb-96100fd0c1f8" />

<img width="989" height="490" alt="preg_emma" src="https://github.com/user-attachments/assets/20bf6297-e235-4246-b9a7-8ca80167838e" />

**- Musica**

Tabla 1: Actividad cerebral en respuesta a diferentes tipos de música en señal EEG Vivi
| Característica          | Música tranquila | Música fuerte | Interpretación                                         |
| ----------------------- | :---------------: | :------------: | ------------------------------------------------------ |
| Delta                   |            ~0.41 |         ~0.36 | Menor proporción de bajas frecuencias en música fuerte |
| Theta                   |            ~0.14 |         ~0.17 | Ligero incremento en música fuerte                     |
| Alfa                    |            ~0.08 |         ~0.08 | Cambio pequeño                                         |
| Beta                    |            ~0.14 |         ~0.15 | Incremento moderado                                    |
| Gamma                   |            ~0.04 |         ~0.06 | Incremento relativamente marcado                       |
| 20–30 Hz                |            Menor |         Mayor | Mayor potencia durante música fuerte                   |
| 30–45 Hz                |             Baja |         Mayor | Posible aumento de activación y/o EMG                  |
| Cambio respecto a basal |         Moderado |         Mayor | Música fuerte produce mayor desviación del basal       |

![Análisis por Espectro Potencias, Ganancias y Frecuencias](frecuencia_vivi.png)

En base principalmente en la tabla anterior, se puede observar que la música fuerte tiende a aumentar la actividad en las bandas de frecuencia más altas (Beta y Gamma), mientras que la música tranquila mantiene una mayor proporción de bajas frecuencias (Delta). Esto sugiere que la música fuerte podría estar asociada con un estado de mayor activación o alerta, mientras que la música tranquila podría favorecer un estado más relajado.

Cabe recalcar que se consideró principalmente lo muestreado en las señales EEG Vivi y no las señales EEG Emma debido a una presencia predominante de saturación en lo medido en este último. Por ende, los resultados pueden variar dependiendo de la persona y del contexto en el que se escuche la música: volumen, tempo, ritmo y timbre. Además, es importante tener en cuenta que la interpretación de los datos de EEG puede ser compleja y requiere un análisis más profundo para comprender completamente los efectos de la música en la actividad cerebral. En este caso, un montaje de los electrodos, teniendo la referencia en el gonion (hueso mandibular) hace importante considerar la actividad de los músculos faciales y mandibulares cercanos, ya que podrían influir en las señales registradas (contaminación electromiográfica), especialmente en las bandas de frecuencia más altas. Por lo tanto, se recomienda realizar estudios adicionales con un mayor número de participantes y condiciones controladas para obtener conclusiones más robustas sobre cómo diferentes tipos de música afectan la actividad cerebral medida por EEG.

### Preguntas complejas y marco de reflexión:
a. ¿Cuáles son las frecuencias significativas para las adquisiciones de EEG? ¿Son las mismas en todas las áreas del cerebro?
Las principales bandas de frecuencia del EEG son:
Delta: 0–4 Hz → sueño profundo.
Theta: 4–8 Hz → somnolencia, memoria y algunos procesos de aprendizaje.
Alpha: 8–12 Hz → relajación y reposo, especialmente con los ojos cerrados.
Beta: 12–25 Hz → actividad mental, concentración y resolución de problemas.
Gamma: >25 Hz → procesos cognitivos de alta demanda y concentración intensa.
No necesariamente son iguales en todas las áreas del cerebro. La actividad EEG depende de la región cerebral y de la función que se esté realizando. Por ejemplo, la actividad frontal está relacionada con planificación, concentración, toma de decisiones y pensamiento activo, mientras que otras regiones tienen funciones diferentes.

b. ¿Qué tipo de filtro es esencial al trabajar con señales de EEG? ¿Por qué necesitamos aplicar este tipo de filtro?
Para EEG se utiliza principalmente un filtro pasa banda (band-pass filter) para conservar el rango de frecuencias de interés y reducir componentes de baja y alta frecuencia que no corresponden a la señal EEG de interés. El filtrado es necesario porque la señal EEG tiene amplitudes muy pequeñas y puede contaminarse fácilmente con ruido eléctrico, movimiento, actividad muscular y otros artefactos. También puede utilizarse un filtro notch para reducir la interferencia de la red eléctrica cuando sea necesario.

c. ¿Puedes influir en la señal de EEG mediante tus pensamientos? ¿Qué acción puedes realizar para activar una banda de frecuencia de tu elección? ¿Pudiste visualizar el cambio en la señal?
Sí, los estados mentales y las actividades cognitivas pueden modificar la actividad EEG.
Según el experimento que realizamos, una de las formas más claras de provocar un cambio fue:
Cerrar los ojos , ya que al cerrar los ojos, se espera un incremento de la actividad alpha (8–12 Hz), porque esta banda está asociada con relajación y reposo.
también se resolvió preguntas complejas: la reflexión y resolución de problemas durante 20–30 segundos implican mayor concentración y actividad cognitiva, por lo que pueden observarse cambios principalmente en las bandas beta y gamma.


d. Muestra una captura de pantalla de una parte relevante de los datos de EEG dentro del experimento propuesto. ¿Esta señal corresponde a lo que esperabas? ¿Por qué?
La señal EEG corresponde parcialmente con lo esperado. Durante la tarea de apertura y cierre de ojos se observan cambios en la amplitud y en la forma de la señal EEG. En particular, se espera que cerrar los ojos aumente la actividad alfa (8–12 Hz), asociada con un estado de relajación. Sin embargo, el aumento de la actividad alfa no puede confirmarse directamente solo a partir de esta señal en el dominio del tiempo; sería necesario realizar un análisis en frecuencia. Solo a partir de esta señal en el dominio del tiempo; sería necesario realizar un análisis en frecuencia.
<img width="970" height="736" alt="e9758bdb-f587-414c-870d-a882e7695ccc" src="https://github.com/user-attachments/assets/9c4c5677-0895-44be-858d-8ca06ca0cfe6" />

e. ¿Existe alguna diferencia en la señal entre las dos ubicaciones, FP1 y FP2?
Puede existir una diferencia entre las señales registradas en FP1 y FP2, aunque ambas ubicaciones se encuentran en la región frontal. Según el sistema internacional 10–20, FP1 corresponde a la región frontal izquierda y FP2 a la región frontal derecha. Las señales pueden presentar diferencias debido a la actividad cerebral de cada hemisferio, la posición de los electrodos y la presencia de artefactos. Sin embargo, para confirmar una diferencia específica entre FP1 y FP2 es necesario comparar directamente las señales registradas en ambas ubicaciones.

f. ¿Qué frecuencias se supone que deben cambiar en las tareas realizadas? ¿Puedes observar los cambios específicos en la señal RAW (señal sin procesar)? Describe lo que observas.
En la tarea de apertura y cierre de ojos, se espera principalmente un cambio en la banda alpha (8–12 Hz). Al cerrar los ojos, se espera un incremento de la actividad alpha, asociada con un estado de relajación.
Durante la resolución de preguntas complejas, se esperan cambios principalmente en las bandas beta (12–25 Hz) y gamma (>25 Hz), relacionadas con la actividad mental, concentración y resolución de problemas.
En la tarea musical, la música relajante puede estar asociada con un estado de relajación y actividad alpha, mientras que una música más estimulante puede generar cambios relacionados con alerta y concentración.
Sin embargo, estas bandas no pueden identificarse de manera específica solamente observando la señal RAW en el dominio del tiempo, ya que esta contiene una combinación de diferentes frecuencias. Para determinar qué bandas cambiaron, es necesario realizar un análisis en frecuencia, por ejemplo mediante un espectro de potencia.


g. Según tu conocimiento, ¿la amplitud del EEG es equivalente al nivel de concentración que has aplicado?
No directamente. Una mayor amplitud del EEG no necesariamente significa un mayor nivel de concentración. La amplitud de la señal puede verse afectada por diferentes factores, como la actividad cerebral, la sincronización neuronal, los movimientos, los parpadeos, la actividad muscular, la posición de los electrodos y el ruido. Por ello, el nivel de concentración no debe evaluarse únicamente a partir de la amplitud del EEG, sino también considerando los cambios en las diferentes bandas de frecuencia.


