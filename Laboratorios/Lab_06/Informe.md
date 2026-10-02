# Introducción
La electroencefalografía (EEG) es una técnica que nos permite registrar la actividad eléctrica del cerebro mediante sensores colocados sobre la cabeza. Esta actividad eléctrica se manifiesta en forma de ondas cerebrales que cambian según nuestro estado de ánimo, nivel de alerta o lo que estemos haciendo en ese momento:
 - Ondas delta (0–4 Hz): Aparecen principalmente durante el sueño profundo.   
 - Ondas theta (4–8 Hz): Se relacionan con momentos de somnolencia o cuando realizamos           pruebas   de memoria y concentración.   
 - Ondas alfa (8–12 Hz): Predominan cuando estamos relajados, con los ojos cerrados, y           disminuyen en cuanto nos ponemos a pensar o abrimos los ojos.
 - Ondas beta (12–25 Hz): Están presentes cuando tenemos la mente activa, concentrada o          resolviendo problemas.   
 - Ondas gamma (>25 Hz): Se vinculan con procesos mentales de alta exigencia y                 concentración     intensa.
   
<img width="857" height="523" alt="image" src="https://github.com/user-attachments/assets/37b4ec69-86d2-4cac-91ff-9d84019847dc" />

Para este estudio, se decidió colocar los electrodos específicamente en el lóbulo frontal (en la zona de la frente). Las razones principales para elegir esta área son dos: primero, porque el lóbulo frontal se encarga de funciones clave como la planificación, la concentración, la toma de decisiones y el pensamiento activo; y segundo, por una razón práctica fundamental de medición: al estar ubicados en la frente, la piel está libre de cabello, lo que permite que los sensores hagan un contacto directo y limpio con la piel, evitando las interferencias que el pelo suele causar en las señales eléctricas.

<img width="552" height="291" alt="image" src="https://github.com/user-attachments/assets/980edba3-5828-4c28-84b6-4afb8ba286d3" />

# Ubicación de los electrodos:
La colocación de los electrodos se distribuye de la siguiente manera sobre el sujeto de prueba:
- Electrodo activo principal: Se coloca en la parte frontal izquierda de la frente.
- Electrodo de referencia/comparación: Se ubica en la parte frontal derecha de la frente      para contrastar la señal.
- Electrodo de referencia física (REF): Se coloca en la zona ósea detrás de la oreja. Esta área sin actividad cerebral directa sirve como punto de apoyo neutral para estabilizar la lectura y reducir ruidos eléctricos externos.
  
  <img width="729" height="398" alt="image" src="https://github.com/user-attachments/assets/b3bab594-b5c8-499e-8151-7f73ad273c36" />

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

### Preguntas complejas y marco de reflexión:
Manteniendo al participante con un auricular puesto en un solo oído, se procedió a susurrarle un total de 7  preguntas de alta complejidad analítica. No se le solicitó una respuesta inmediata; por el contrario, se estableció un marco de reflexión de aproximadamente 20 a 30 segundos por pregunta para obligar al cerebro a un proceso de concentración profunda y resolución de problemas (estimulando la actividad en las ondas beta y theta).
a. ¿Cuáles son las frecuencias significativas para las adquisiciones de EEG? ¿Son las mismas en todas las áreas del cerebro?
Las principales bandas de frecuencia del EEG son:
Delta: 0–4 Hz → sueño profundo.
Theta: 4–8 Hz → somnolencia, memoria y algunos procesos de aprendizaje.
Alpha: 8–12 Hz → relajación y reposo, especialmente con los ojos cerrados.
Beta: 12–25 Hz → actividad mental, concentración y resolución de problemas.
Gamma: >25 Hz → procesos cognitivos de alta demanda y concentración intensa.
No necesariamente son iguales en todas las áreas del cerebro. La actividad EEG depende de la región cerebral y de la función que se esté realizando. Por ejemplo, la actividad frontal está relacionada con planificación, concentración, toma de decisiones y pensamiento activo, mientras que otras regiones tienen funciones diferentes.

b. ¿Qué tipo de filtro es esencial al trabajar con señales de EEG? ¿Por qué necesitamos aplicar este tipo de filtro?
Para EEG normalmente se utiliza un filtro pasa banda (band-pass filter) para conservar el rango de frecuencias de interés y eliminar componentes que están fuera de ese rango. Además, puede utilizarse un filtro notch para reducir la interferencia eléctrica de la red, típicamente alrededor de 50 Hz en Perú.
¿Por qué? Porque la señal EEG tiene amplitudes muy pequeñas y puede contaminarse fácilmente con: ruido eléctrico de la red, movimiento,actividad muscular,interferencias externas,componentes de frecuencia que no corresponden al EEG que queremos analizar.

c. ¿Puedes influir en la señal de EEG mediante tus pensamientos? ¿Qué acción puedes realizar para activar una banda de frecuencia de tu elección? ¿Pudiste visualizar el cambio en la señal?
Sí, los estados mentales y las actividades cognitivas pueden modificar la actividad EEG.
Según el experimento que realizamos, una de las formas más claras de provocar un cambio fue:
Cerrar los ojos , ya que al cerrar los ojos, se espera un incremento de la actividad alpha (8–12 Hz), porque esta banda está asociada con relajación y reposo.
también se resolvió preguntas complejas: la reflexión y resolución de problemas durante 20–30 segundos implican mayor concentración y actividad cognitiva, por lo que pueden observarse cambios principalmente en las bandas beta y gamma.


d. Muestra una captura de pantalla de una parte relevante de los datos de EEG dentro del experimento propuesto. ¿Esta señal corresponde a lo que esperabas? ¿Por qué?

e. ¿Existe alguna diferencia en la señal entre las dos ubicaciones, FP1 y FP2?
Sí, puede existir una diferencia entre FP1 y FP2, aunque ambos están ubicados en la región frontal.
Según el sistema 10–20:
FP1: región frontal izquierda.
FP2: región frontal derecha.
Aunque ambos registran actividad frontal, las señales pueden presentar diferencias debido a la actividad cerebral de cada hemisferio, a la posición exacta de los electrodos y a artefactos.
Además, en su experimento la actividad frontal es particularmente relevante porque está relacionada con planificación, concentración, toma de decisiones y pensamiento activo.

f. ¿Qué frecuencias se supone que deben cambiar en las tareas realizadas? ¿Puedes observar los cambios específicos en la señal RAW (señal sin procesar)? Describe lo que observas.
Apertura y cierre de ojos:
La frecuencia que esperamos que cambie principalmente es:
Alpha -> 8-12 Hz
Con los ojos cerrados, debería aumentar la actividad alpha.
Beta-> 12-25 Hz 
y potencialmente:
Gamma->25 Hz
porque están relacionadas con actividad mental, concentración y resolución de problemas.

Música:
La música relajante puede favorecer estados de relajación asociados con alpha, mientras que una música más estimulante puede producir cambios en la actividad asociada con alerta y concentración.
¿Y en RAW?
No necesariamente puedes identificar visualmente una banda específica solamente mirando la señal RAW.
Por ejemplo, alpha está entre 8–12 Hz, pero la señal RAW contiene una combinación de diferentes componentes. Para identificar claramente qué banda cambió es mucho mejor analizar el espectro de frecuencia o aplicar filtros.

g. Según tu conocimiento, ¿la amplitud del EEG es equivalente al nivel de concentración que has aplicado?
No directamente. A mayor amplitud no necesariamente tiene que ser mayor concentración. La amplitud del EEG depende de muchos factores y no representa por sí sola el nivel de concentración .
Por ejemplo, diferentes estados fisiológicos pueden producir cambios en la amplitud, y también pueden aparecer cambios debido a:
* Movimiento
* Parpadeo
* Actividad muscular
* Posición de electrodos
* Ruido
* Sincronización neuronal

Estímulo musical comparativo (Opcional):
Como fase complementaria, se expuso al evaluado a escuchar fragmentos musicales de contraste (aproximadamente entre 1 a 1 minuto y medio por género), comparando el impacto neurofisiológico de música relajante de tipo Lo-Fi frente a música más intensa o estridente.
