
**Nombre del juego:**  BallsTwo
**Autor:**  Rojo Ramirez Luis Edgar

## **Descripción del Juego:**  

Este es un juego multijugador para dos participantes en el que cada jugador controla una barra vertical ubicada en los extremos opuestos del campo. El objetivo principal es evitar que el balón atraviese su lado, manteniéndolo en juego el mayor tiempo posible mediante rebotes estratégicos.

Cada jugador cuenta con cinco vidas, las cuales se reducen cada vez que el balón toca su respectivo borde del escenario. El jugador rojo controla su movimiento con las teclas **Q** (subir) y **A** (bajar), mientras que el jugador azul utiliza las teclas **P** (subir) y **L** (bajar).

El balón inicia en el centro con una velocidad base, la cual aumenta progresivamente en tres ocasiones durante la partida, incrementando la dificultad. Además, cada vez que colisiona con algún objeto, su dirección cambia de manera aleatoria, generando trayectorias impredecibles. Al entrar en contacto con los bordes superior e inferior, el balón rebota automáticamente.

La partida finaliza cuando uno de los jugadores pierde todas sus vidas, siendo declarado perdedor, mientras que el oponente resulta ganador.

---

## **Lógica interna del juego**

El juego está basado en un modelo de ejecución por eventos y ciclos continuos. Al presionar la bandera verde, se inicializan todas las variables necesarias para la partida, incluyendo las vidas de ambos jugadores y la posición inicial del balón.

El balón comienza en el centro del escenario con una dirección y velocidad inicial definidas. Su movimiento se controla mediante un ciclo infinito, en el cual avanza constantemente y evalúa colisiones en cada iteración.

El sistema de colisiones verifica si el balón entra en contacto con las barras de los jugadores o con los bordes superior e inferior. En caso de colisión con una barra, el balón invierte su dirección horizontal y modifica su ángulo de forma aleatoria, generando trayectorias impredecibles. Si colisiona con los bordes superior o inferior, invierte su dirección vertical para simular un rebote.

Adicionalmente, el sistema detecta si el balón toca el borde izquierdo o derecho del escenario. Cuando esto ocurre, se reduce en una unidad la vida del jugador correspondiente y el balón se reinicia en el centro del campo.

El incremento de dificultad se implementa mediante un temporizador o contador interno que aumenta progresivamente la velocidad del balón en tres etapas distintas durante la partida.

El movimiento de los jugadores se gestiona mediante eventos de teclado. Cada barra responde continuamente a la presión de teclas específicas, actualizando su posición vertical dentro de los límites del escenario.

El juego finaliza cuando una de las variables de vida llega a cero. En ese momento, se detienen todos los ciclos activos y se muestra el resultado de la partida.

---

## **Soccer Ball** 

El sprite **Soccer Ball**, así como los demás sprite estan compuestos por múltiples **scripts** orientados a eventos. Cada script se activa mediante un estímulo específico, como el inicio del juego, la recepción de mensajes o interacciones dentro del entorno.

El sprite **Soccer Ball** controla la lógica principal del juego relacionada con el movimiento del balón y la gestión de las vidas de los jugadores. Al iniciar (bandera verde), el balón se oculta temporalmente, se inicializan las variables de vidas de ambos jugadores en 5 y se establecen sus coordenadas iniciales. A partir de ahí, entra en un ciclo infinito donde constantemente actualiza su posición y evalúa su ubicación en el eje X. Si el balón sobrepasa el límite izquierdo (x < -224), se interpreta como un punto en contra del jugador rojo, reduciendo su vida en una unidad; de forma similar, si sobrepasa el límite derecho (x > 224), se reduce la vida del jugador azul. Después de cada actualización, el sistema verifica si alguna de las vidas ha llegado a cero o es menor, lo que indica el final de la partida. En ese caso, el balón se oculta, se envía un mensaje declarando al ganador correspondiente (según quién conserve vidas) y se detiene completamente la ejecución del juego.

#### Diagrama de flujo

<div style="text-align: center;">  
<img src="BallsTwo1A.drawio.png" width="400">  
</div>
<div style="text-align: center; color: #555555;">
<b>Diagrama de Flujo 1.A</b></div>

#### Diagrama de bloques

<div style="text-align: center;">  
<img src="Pasted image 20260426100430.png" width="400">  
</div>
<div style="text-align: center; color: #555555;">
<b>Diagrama de Bloques 1.A</b></div>

El siguiente script del sprite **Soccer Ball** controla el movimiento dinámico del balón, las colisiones con los jugadores y el incremento progresivo de la dificultad durante la partida. El flujo inicia cuando el sprite recibe el mensaje `mensaje1`, momento en el que se inicializan variables importantes como la velocidad inicial del balón (`moverBalon = 10`), la dirección horizontal (`direccion = 90`), la trayectoria aleatoria y el cronómetro. Posteriormente, el sistema entra en un ciclo continuo donde verifica constantemente las colisiones con los jugadores. Cuando el balón toca al sprite del jugador rojo, se ajusta la dirección hacia la derecha (`direccion = 90`) y se genera aleatoriamente una trayectoria entre dos posibles valores, permitiendo modificar el ángulo del rebote en ±30 grados y creando trayectorias impredecibles. De forma similar, cuando el balón colisiona con el jugador azul, la dirección cambia hacia la izquierda (`direccion = -90`) y nuevamente se aplica una variación aleatoria en el ángulo de rebote. Además, el script implementa un sistema de aumento progresivo de dificultad mediante el cronómetro del juego; en determinados intervalos de tiempo (10–13, 20–23 y 30–33 segundos), la velocidad del balón aumenta, haciendo que el juego sea cada vez más rápido y desafiante para ambos jugadores.
#### Diagrama de flujo

<div style="text-align: center;">  
<img src="BallsTwo-Soccer Ball_2.drawio.png" width="400">  
</div>
<div style="text-align: center; color: #555555;">
<b>Diagrama de Flujo 2.A</b></div>

#### Diagrama de bloques

<div style="text-align: center;">  
<img src="Pasted image 20260507183104.png" width="400">  
</div>
<div style="text-align: center; color: #555555;">
<b>Diagrama de Bloques 2.A</b></div>

---

## **Rojo1**

El sprite **Rojo1** controla la barra del jugador rojo y gestiona tanto su movimiento vertical como las interacciones físicas con el balón. Cuando recibe el mensaje `mensaje1`, el sprite se posiciona en las coordenadas iniciales del lado izquierdo del escenario (`x = -224`, `y = 0`). Posteriormente, entra en un ciclo continuo donde verifica constantemente diferentes eventos y condiciones. En primer lugar, detecta si la barra toca alguno de los bordes superior o inferior del escenario; en caso de colisión, ejecuta un rebote para impedir que el jugador salga de los límites del campo. Después, el sistema monitorea las teclas de control del jugador: al presionar la tecla **Q**, la barra se desplaza hacia arriba aumentando su coordenada vertical en 15 unidades, mientras que al presionar la tecla **A**, se desplaza hacia abajo disminuyendo dicha coordenada. Finalmente, el script verifica constantemente si existe contacto con el sprite **Soccer Ball**; cuando ocurre una colisión, se reproduce el sonido `Basket`, proporcionando retroalimentación auditiva al impacto entre la barra y el balón.

#### Diagrama de flujo

<div style="text-align: center;">  
<img src="BallsTwo-Rojo1.drawio.png" width="400">  
</div>
<div style="text-align: center; color: #555555;">
<b>Diagrama de Flujo 3.A</b></div>

#### Diagrama de bloques

<div style="text-align: center;">  
<img src="Pasted image 20260508145825.png" width="400">  
</div>
<div style="text-align: center; color: #555555;">
<b>Diagrama de Bloques 3.A</b></div>

---

## **Azul1**

El sprite **Azul1** administra la barra correspondiente al jugador azul, incluyendo su posicionamiento inicial, movimiento vertical y detección de colisiones con el balón. Al recibir el mensaje `mensaje1`, la barra se coloca en el lado derecho del escenario en las coordenadas (`x = 224`, `y = 0`). A continuación, el sprite entra en un ciclo infinito donde supervisa continuamente múltiples condiciones del juego. Primero, detecta si la barra entra en contacto con los bordes del escenario y, en caso afirmativo, ejecuta una acción de rebote para mantenerla dentro de los límites permitidos. Después, controla el movimiento del jugador mediante eventos de teclado: la tecla **P** desplaza la barra hacia arriba incrementando la coordenada `y` en 15 unidades, mientras que la tecla **L** la mueve hacia abajo reduciendo dicha coordenada. Además, el script verifica constantemente las colisiones con el sprite **Soccer Ball**; cuando ocurre un impacto, se reproduce el sonido `Basket`, generando una respuesta sonora que indica la interacción entre el balón y la barra del jugador azul.

#### Diagrama de flujo

<div style="text-align: center;">  
<img src="BallsTwo-Azul1.drawio.png" width="400">  
</div>
<div style="text-align: center; color: #555555;">
<b>Diagrama de Flujo 4.A</b></div>

#### Diagrama de bloques

<div style="text-align: center;">  
<img src="Pasted image 20260508150652.png" width="400">  
</div>
<div style="text-align: center; color: #555555;">
<b>Diagrama de Bloques 4.A</b></div>


---





---

