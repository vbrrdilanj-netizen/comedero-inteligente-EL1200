Comedero Inteligente para Gatos

Curso: EL-1200 Introducción a la Electrónica
Institución: Instituto Tecnológico de Costa Rica
Periodo: II semestre 2026
Profesor: William Marín Moreno
Integrantes: Dilan Vargas B.

Descripción del proyecto

El Comedero Inteligente para Gatos es un proyecto que busca representar el funcionamiento de un sistema automático de alimentación mediante el uso de un ESP32, un sensor PIR, un servomotor y un LED.
Su función principal consiste en detectar movimiento frente al comedero y activar un mecanismo que permite dispensar alimento. Además, cuenta con una condición programada para evitar que se sirva comida varias veces mientras el gato permanezca frente al sensor.
El proyecto se desarrolla en Wokwi, una plataforma que permite simular las conexiones y comprobar el funcionamiento de los componentes sin necesidad de contar con ellos físicamente.

Funcionamiento

El sistema inicia en modo de espera, con el servomotor en una posición de 40° y el LED apagado.
Cuando el sensor PIR detecta movimiento, envía una señal al ESP32. Este procesa la información y activa el servomotor, que gira hasta los 140° para representar la apertura del dispensador. Al mismo tiempo, el LED se enciende para indicar que se está sirviendo el alimento.Después de 1,5 segundos, el servomotor regresa a su posición inicial de 40° y el LED se apaga.
Para evitar que el comedero dispense alimento de forma repetida, el programa utiliza una variable booleana llamada dispensado. Esta permite registrar si ya se realizó una dispensación. Mientras el sensor continúe activado, el sistema no vuelve a servir alimento.
Cuando el sensor deja de detectar movimiento, la variable se reinicia y el comedero queda preparado para una nueva activación.

Materiales utilizados

Para desarrollar la simulación se utilizan los siguientes componentes:
* 1 placa ESP32.
* 1 sensor de movimiento PIR.
* 1 servomotor.
* 1 LED rojo.
* 1 resistencia de 220 Ω.
* Cables de conexión.
* Plataforma Wokwi.

Conexiones del circuito

Los componentes se conectan al ESP32 de la siguiente manera:
Componente	Conexión al ESP32
Sensor PIR (OUT)	GPIO 2
Servomotor (PWM)	GPIO 13
LED con resistencia de 220 Ω	GPIO 5
Alimentación positiva	3V3
Tierra	GND

El sensor PIR funciona como entrada, ya que permite detectar movimiento. Por otra parte, el servomotor y el LED funcionan como salidas, debido a que responden a las instrucciones del ESP32.

Diagrama de conexiones
Simulación en Wokwi
El proyecto se realiza en Wokwi, donde se puede observar el circuito y comprobar la respuesta de sus componentes.
Para ejecutar la simulación, se debe abrir el proyecto y seleccionar la opción Start Simulation. Después, se activa el sensor PIR mediante la opción Simulate Motion.
Durante la prueba, el Monitor Serial muestra mensajes que indican cuándo se detecta movimiento, cuándo se completa la dispensación y cuándo el sistema queda preparado para una nueva activación.

Enlace del proyecto: https://wokwi.com/projects/480359969703759873

Código del proyecto
El código se encuentra en la carpeta firmware/, que contiene los siguientes archivos:
* sketch.ino: contiene las instrucciones que controlan el funcionamiento del comedero.
* diagram.json: guarda los componentes y las conexiones realizadas en Wokwi.
* libraries.txt: indica la biblioteca utilizada para controlar el servomotor.
Para el movimiento del servomotor se utiliza la biblioteca ESP32Servo, que permite establecer las posiciones de apertura y cierre.

Evidencia del funcionamiento

La simulación permite comprobar la detección de movimiento, la activación del LED y la secuencia programada para el servomotor.
También permite verificar los mensajes del Monitor Serial y la condición que evita una nueva dispensación mientras el sensor permanece activado.

Posibles mejoras

Aunque el proyecto representa el funcionamiento básico de un comedero automático, se podrían incorporar otras funciones para mejorar su uso.
Una posible mejora sería agregar un sensor que permita conocer la cantidad de alimento disponible en el recipiente. También se podría implementar una función de horarios para establecer momentos específicos de alimentación.
Otra opción sería aprovechar la conectividad Wi-Fi del ESP32 para enviar notificaciones cuando se active el dispensador.
Estas mejoras permitirían ampliar las funciones del sistema y acercarlo al funcionamiento de un comedero automático real.
