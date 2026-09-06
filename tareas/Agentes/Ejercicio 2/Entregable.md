# Ejercicio 2 — Descripción PEAS de agentes inteligentes

## Elaborado por: Arianna Rodríguez Rodas

## Contexto
En el capítulo 2 de Artificial Intelligence: A Modern Approach (Russell & Norvig), un agente se entiende mejor cuando se especifica su entorno de tarea. Una forma estándar de hacerlo es la descripción PEAS:

Letra	Significado	Pregunta guía

P	Performance (medida de desempeño)	¿Cómo se evalúa el éxito del agente?

E	Environment (entorno)	¿En qué mundo opera? ¿Quién más actúa ahí?

A	Actuators (actuadores)	¿Qué acciones puede ejecutar?

S	Sensors (sensores)	¿Qué información puede percibir?

Este ejercicio no requiere programar. Consiste en analizar distintos tipos de aplicaciones reales y describir cada una con el esquema PEAS.

## Objetivo
Para cada una de las 8 aplicaciones listadas abajo, redacta una descripción PEAS completa y coherente. Debes pensar como diseñador del agente: qué optimiza, dónde actúa, con qué puede mover o modificar el mundo, y qué puede observar.

## Aplicaciones a analizar
Describe PEAS para cada una de estas aplicaciones:

### Asistente virtual de voz (p. ej. Siri, Alexa o Google Assistant en un altavoz inteligente).

- **Performance:** Escuchar indicaciones en lenguaje natural para dar respuesta en lenguaje natural también, ejecutar acciones solicitadas que estén dentro de sus capacidades para agilizar las tareas del usuario.
- **Environment:** Espacio con sonido moderado, de preferencia con poco o nulo ruido, dispositivo con conexión a internet. Suele ser estocástico en las respuestas a preguntas que solicitan información. Suele ser determinista al solicitarle tareas concretas como encender/apagar la linterna del teléfono o reproducir una canción específica en Youtube Music. No es observable, solo podemos ver/escuchar el resultado. Las posibilidades de solicitudes son infinitas, todas las que se le ocurran, así que es continuo. 
- **Actuators:** Genera respuesta por texto/voz al hablarle e interactuar por medio de un dispositivo, generalmente una pantalla. Usa el altavoz para comunicarse generalmente y no usar el teléfono manualmente. Ejecuta la tarea indicada dentro de sus capacidades, por ejemplo: leer un mensaje de Whatsapp en voz alta y escuchar la respuesta del humano para transcribirla y enviarla por respuesta dentro del mismo Whatsapp. Agregar eventos al calendario, activar alarmas, abrir aplicaciones dentro del teléfono.
- **Sensors:** Micrófono, detecta la disponibilidad de internet para poder dar servicio por lo que un sensor es el dispositivo de red.

### Robot aspirador doméstico (p. ej. Roomba u otro robot que limpia pisos de un departamento).

- **Performance:** Aspirar pequeños y ligeros objetos del suelo, como el polvo, arena, pelo de mascota, para mantener limpio un espacio sin que un humano tenga que quitar el polvo.
- **Environment:** Una habitación pequeña o mediana que no esté saturada de cosas intermedias al paso, por ejemplo, una recámara o la sala de una casa. No puede ser un basurero ni una bodega que tenga objetos sobre todo el piso. Es parcialmente observable porque el espacio sobre el que trabaja es pequeño y aun así puede tener obstáculos. Es de tipo episódico porque cada vez que vuelve a realizar su función pasa por los mismos lugares de principio a fin y vuelve a empezar.
- **Actuators:** Motor y batería que le permite desplazarse, aspiradora, escobillas para barrer y llevar los objetos hacia la aspiradora, interruptor de encendido/apagado.
- **Sensors:** Sensor de proximidad, algunas más avanzadas cuentan con sensor que les ayuda a identificar si aún hay objetos o zonas por las que no pasaron en la habitación por lo que tienen cámara.

### Sistema de recomendación de streaming (p. ej. Netflix o Spotify que sugiere películas o canciones).

- **Performance:** Obtener recomendaciones de géneros similares basadas en las preferencias o en la información histórica de las reproducciones del usuario.
- **Environment:** Dispositivo con conexión a internet, una cuenta de usuario que haya configurado sus preferencias de música o series o que tenga historial de reproducciones. Es estocástico, ya que suele recomendar diversas pistas de canciones o series cada vez que se ejecuta, el propósito es recomendar algo nuevo. Aunque suele haber miles de opciones de recomendación es discreto, ya que las opciones son limitadas. 
- **Actuators:** Presentar al usuario los resultados de las recomendaciones después de ejecutar algoritmo de ML entrenado para tener como input una base de datos y dar como output un resultado de conjuntos de cosas similares.
- **Sensors:** Nuevo inicio de sesión del usuario, nuevas series o canciones agregadas, listas de reproducción, configuración de las preferencias, bases de datos.

### Vehículo autónomo en ciudad (conducción sin conductor en calles urbanas con tráfico y peatones).

- **Performance:** Conducción segura con poca interacción del humano para llegar a un destino.
- **Environment:** Ciudad con tráfico de automóviles de pequeñas o medianas dimensiones, con calles en buenas condiciones, espacios amplios para que los autos puedan transitar. Este es de ambiente parcialmente observable, necesita ver su alrededor y calcula mientras se va desplazando. Es secuencial porque cada decisión que toma le da un resultado que no puede cambiar y debe seguir avanzando.
- **Actuators:** Acelerador y freno para desplazarse o detenerse, volante/guía para redireccionar, toma de decisiones en tiempo real para poder esquivar, continuar o detenerse.
- **Sensors:** Sensor de proximidad de objetos, cámara de video para captar imágenes de lo que está a su alrededor, sensor de clima, GPS.

### Agente de trading algorítmico en bolsa (compra y venta automática de acciones en mercados financieros).

- **Performance:** Identificar operaciones de compra y venta que conlleven a una ganancia y realizar las transacciones de inmediato y oportunamente sin intervención humana.
- **Environment:** Dispositivo con internet estable de alto rendimiento, con buenas capacidades de cómputo para ejecutar los algoritmos de evaluación y obtener respuestas en tiempo real, con acceso a APIs de trading e información de los mercados financieros. Es estocástico porque la decisión siempre la tomará después de ejecutar el algoritmo y este puede emitir diversos resultados basados en los datos de entrada.
- **Actuators:** Comprar/vender acciones.
- **Sensors:** Identificador de nuevos eventos por medio de APIs o webhooks, señal positiva de su API para ejecutar compra o venta.

### Sistema de diagnóstico médico asistido por IA (apoya a un médico a interpretar síntomas e imágenes clínicas).

- **Performance:** Obtener un diagnóstico claro y acertado del paciente por medio de su información clínica para indicar un tratamiento adecuado.
- **Environment:** Dispositivo con internet que ejecute un sistema que lea e interprete documentos de tipo texto e imágenes, que pueda comparar con un archivo histórico de síntomas y tratamientos exitosos. Es parcialmente observable porque tiene algo de información, pero pueden hacer falta datos clínicos del paciente.
- **Actuators:** Dar una respuesta de tratamiento sugerido basado en datos históricos después de ejecutar el agente entrenado con información clínica de miles de pacientes.
- **Sensors:** Lector de texto, lector de imágenes, interfaz para interactuar con el médico.

### Dron de inspección de infraestructura (revisa grietas, corrosión o fugas en puentes, tuberías o líneas eléctricas).

- **Performance:** Identificar anomalías o alteraciones de infraestructura, tomar lectura, generar alerta y enviarla para su revisión.
- **Environment:** Espacio abierto y despejado para el correcto desplazamiento del dron, iluminación de buena a excelente para el correcto cotejo de objetos y comparación con las referencias, clima normal sin tormentas. Es parcialmente observable porque solo tiene un área visible enfrente para revisar.
- **Actuators:** Mapa para guiarse hacia la infraestructura de ida y vuelta, orientar la cámara hacia los objetos a observar, enviar la alerta necesaria en caso de hallazgos.
- **Sensors:** Proximidad, GPS, radar de conexión con el control, sensor de lluvia, de iluminación, cámara, batería.

### Agente jugador de ajedrez (programa que compite contra un humano u otro agente en partidas completas).

- **Performance:** Mantener una partida de ajedrez de principio a fin, cumpliendo con las reglas del juego, con objetivo de ganar la partida y obtener experiencia para jugar mejor las próximas partidas.
- **Environment:** Dispositivo donde se ejecuta el agente y una pantalla o dispositivo de salida de la respuesta de cada ejecución. Es observable porque tiene que ver todas las posiciones para calcular el próximo movimiento. Es secuencial, ya que cada movimiento genera una consecuencia positiva o negativa para su objetivo.
- **Actuators:** Mover la pieza en el tablero, indicar el fin de su turno, detener el reloj después de terminar su turno.
- **Sensors:** Detección del turno de mover, contador de tiempo restante de la partida, contador de movimientos para cumplir reglas, validador de movimiento para cada pieza.