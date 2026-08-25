
## Índice

[[#Descripción del Módulo]]
[[#Tema 1. Variables y estados del juego]]
	[[#1.1 Concepto de variable]]
	[[#1.2 Puntaje]]
	[[#1.3 Vida]]
	[[#1.4 Tiempo]]
	
[[#Tema 2. Decisiones dentro del juego]]
	[[#2.1 Condicionales]]
	[[#2.2 Estados de ganar]]
	[[#2.3 Estados de perder]]
	
[[#Tema 3. Movimiento y repetición]]
	[[#3.1 Eventos de teclado]]
	[[#3.2 Bucles]]
	[[#3.3 Interacción con objetos]]


---

## Descripción del Módulo

El **Módulo 1: Fundamentos para Creadores de Videojuegos** introduce a las y los estudiantes en los principios esenciales de la programación aplicada al desarrollo de juegos interactivos mediante Scratch. A lo largo del módulo, se construye una base sólida comenzando con el **movimiento y la repetición**, donde se aprende a dar vida a los personajes mediante eventos de teclado, bucles y la interacción con objetos. Posteriormente, se incorporan las **variables y estados del juego**, permitiendo gestionar elementos clave como el puntaje, la vida y el tiempo, los cuales aportan estructura y seguimiento al progreso del jugador. Finalmente, se abordan las **decisiones dentro del juego** mediante el uso de condicionales, lo que posibilita crear escenarios donde el jugador puede ganar o perder según sus acciones. En conjunto, este módulo sienta las bases para comprender cómo funcionan los videojuegos a nivel lógico y prepara al estudiante para desarrollar proyectos más complejos e interactivos.

El taller tiene una duración total de 24 horas, distribuidas en 12 sesiones de 2 horas + 2 horas de evaluación y cierre.

---

# Tema 1. Variables y estados del juego 

En el desarrollo de videojuegos, uno de los elementos más importantes para crear experiencias interactivas es el uso de **variables**. Las variables permiten almacenar información que puede cambiar durante el juego, como el puntaje del jugador, la cantidad de vidas o el tiempo restante. Gracias a ellas, el juego puede “recordar” lo que está ocurriendo y reaccionar de manera dinámica a las acciones del usuario.

---

## 1.1 Concepto de variable 

Una **variable** es un espacio en la memoria donde se guarda un valor que puede cambiar a lo largo del programa. En Scratch, las variables son fundamentales para controlar el estado del juego.

Para crear una variable en Scratch:

1. Ir a la categoría **“Variables”** .
2. Hacer clic en **“Crear una variable”**.
3. Asignar un nombre (por ejemplo: _puntaje_, _vida_, _tiempo_).
4. Elegir si será para todos los objetos o solo para uno.



<div style="text-align: center;">
  <img src="Diagrama sin título-Página-3.drawio.png" width="500">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 1</b>. Crear variable . I) Seleccionar categoria. II) Crear una variable. III) Configurar la nueva variable. IV) Mostrar la variable en el escenario.
</div>

Una vez creada, aparecerán bloques como:

- `fijar [variable] a ( )` → asigna un valor inicial.
- `cambiar [variable] por ( )` → modifica el valor.
- `mostrar variable” / “ocultar variable` → controla su visualización.

<div style="text-align: center;">
  <img src="Pasted image 20260418155758.png" width="300">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 2</b>. Bloques para manipular las variables.
</div>

Estas herramientas permiten actualizar constantemente la información durante el juego.

---

## 1.2 Puntaje

El **puntaje** representa la cantidad de logros o recompensas obtenidas por el jugador. Es una de las variables más comunes en videojuegos, ya que motiva al usuario a mejorar su desempeño.

Ejemplo en Scratch:

- Crear la variable **puntaje**.
- Al iniciar el juego:
    - Usar el bloque: **“al presionar bandera verde”**
    - Luego: **“fijar puntaje a 0”**
- Cada vez que el jugador logre un objetivo (por ejemplo, tocar un objeto):
    - Usar: **“cambiar puntaje por 1”**

<div style="text-align: center;">
  <img src="Pasted image 20260418161530.png" width="400">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 3</b>. Esto permite que el puntaje aumente conforme se presiona la tecla "espacio".
</div>

---

## 1.3 Vida

La variable **vida** indica cuántas oportunidades tiene el jugador antes de perder el juego. Es útil para introducir dificultad y generar retos.

Ejemplo en Scratch:

- Crear la variable **vida**.
- Al iniciar:
    - **“fijar vida a 3”**
- Cuando el jugador comete un error (por ejemplo, toca un enemigo):
    - **“cambiar vida por -1”**

Para agregar lógica al juego:

- Usar un bloque de la categoría **Control** (color naranja claro):
    - **“si <vida = 0> entonces”**
        - Mostrar mensaje de “Game Over”
        - Detener el juego con **“detener todo”**

<div style="text-align: center;">
  <img src="Pasted image 20260418163228.png" width="300">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 4</b>. Con el uso de una condicional simple se puede reducir el valor de la variable.
</div>

Esto permite controlar el final del juego.

---

## 1.4 Tiempo

El **tiempo** se utiliza para limitar la duración del juego o generar presión en el jugador. Puede funcionar como una cuenta regresiva.

Ejemplo en Scratch:

- Crear la variable **tiempo**.
- Al iniciar:
    - **“fijar tiempo a 30”** (por ejemplo, 30 segundos)
- Usar un bucle:
    - **“por siempre”** o **“repetir hasta que”**
    - Dentro:
        - **“esperar 1 segundos”**
        - **“cambiar tiempo por -1”**

<div style="text-align: center;">
  <img src="Pasted image 20260418165036.png" width="400">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 5</b>. Simulación de un temporizador.
</div>

Para finalizar el juego:

- **“si <tiempo = 0> entonces”**
    - Terminar el juego o mostrar resultados.

---

## Actividades propuestas

---

> [!note] Actividad 1: Mi primera variable
> **Duración:** 15 minutos  
> **Objetivo:** Comprender el uso básico de variables en Scratch.  
>  
> **Desarrollo:**  
> El estudiante creará una variable llamada `contador`. Al presionar la bandera verde, deberá iniciar en 0. Luego, al presionar una tecla (por ejemplo, espacio), el valor aumentará en 1 y cuando el contador llegue a 10 se deberá manda un mensaje.  
>  
> **Ejemplo:**  
> - “al presionar bandera verde” → fijar contador a 0  
> - “al presionar tecla espacio” → cambiar contador por 1

---

> [!tip] Actividad 2: Sistema de puntaje
> **Duración:** 20 minutos  
> **Objetivo:** Implementar un sistema de puntaje básico.  
>  
> **Desarrollo:**  
> Crear un objeto que, al ser tocado por el personaje, aumente el puntaje. El objeto puede desaparecer y reaparecer en otra posición.  
>  
> **Ejemplo:**  
> - “si toca personaje” → cambiar puntaje por 1  
> - “ir a posición aleatoria”

---

> [!warning] Actividad 3: Control de vidas
> **Duración:** 20 minutos  
> **Objetivo:** Implementar mecánica de vidas en un juego.  
>  
> **Desarrollo:**  
> El personaje perderá una vida cada vez que toque un obstáculo. Cuando las vidas lleguen a 0, el juego termina.  
>  
> **Ejemplo:**  
> - “si toca enemigo” → cambiar vida por -1  
> - “si vida = 0” → detener todo

---

> [!success] Actividad 4: Cuenta regresiva
> **Duración:** 25 minutos  
> **Objetivo:** Aplicar una variable de tiempo en el juego.  
>  
> **Desarrollo:**  
> Crear un temporizador que inicie en 10 o 20 segundos y disminuya cada segundo hasta llegar a 0.  
>  
> **Ejemplo:**  
> - “esperar 1 segundo”  
> - “cambiar tiempo por -1”  
> - “si tiempo = 0” → mostrar mensaje final

---
---
# Tema 2. Decisiones dentro del juego

En los videojuegos, no todo ocurre de manera lineal; las acciones del jugador generan diferentes resultados. Para lograr esto, se utilizan las **decisiones**, que permiten que el juego responda de forma inteligente a lo que está sucediendo. Estas decisiones se implementan mediante **condicionales**, estructuras que evalúan una situación y ejecutan acciones dependiendo de si se cumple o no una condición.

Las decisiones son clave para construir mecánicas como ganar, perder, evitar obstáculos, desbloquear niveles o reaccionar a eventos dentro del juego. En herramientas como Scratch, estas estructuras son visuales y fáciles de usar, lo que facilita comprender la lógica detrás del comportamiento de un videojuego.

---

## 2.1 Condicionales

Las **condicionales** permiten ejecutar instrucciones solo si se cumple una condición específica. En Scratch, se encuentran en la categoría **“Control”** (color naranja claro).

Los bloques principales son:

- **“si <condición> entonces”**
- **“si <condición> entonces / si no”**

Para construir la condición, se utilizan bloques de:

- **“Operadores”** (color verde) → comparaciones como `=`, `<`, `>`
- **“Sensores”** (color azul claro) → detectar contacto, teclas, etc.

<div style="text-align: center;">
  <img src="2026-04-28_17-14.png" width="500">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 6</b>. 1) Uso de condición simple y operadores de comparación, cuando la variable puntos es igual a 5 la condición se vuelve verdadera y ejecuta el bloque en el interior de esta condicional. 2) Uso de una condicional doble y sensores, se usa un bucle infinito "por siempre" para que la condicional se repita hasta que la condición se cumpla, cuando el "Sprite" toca el borde la condicional devuelve "True" y se ejecuta el bloque "detener todo". 
</div>

Ejemplo en Scratch:

- Si el personaje toca un objeto:
    - Bloque: **“si \<tocando objeto> entonces”**
        - Ejecutar una acción (sumar puntos, cambiar disfraz, etc.)

Esto permite que el juego reaccione a eventos específicos en tiempo real.

---

## 2.2 Estados de ganar

Un **estado de ganar** ocurre cuando el jugador cumple un objetivo dentro del juego. Este puede depender del puntaje, el tiempo, la recolección de objetos o llegar a una meta.

Ejemplo en Scratch:

- Si el puntaje alcanza un valor específico:
    - **“si <puntaje = 10> entonces”**
        - Mostrar mensaje: “¡Ganaste!”
        - Usar bloque de **Apariencia** (color morado): **“decir ¡Ganaste! por 2 segundos”**
        - Detener el juego con **“detener todo”**

<div style="text-align: center;">
  <img src="Pasted image 20260428175225.png" width="500">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 7</b>. Implementación del estado "Ganar". 
</div>


También se puede usar:

- **“enviar mensaje”** (categoría **Eventos**, color amarillo) para coordinar varios objetos al ganar.

<div style="text-align: center;">
  <img src="Pasted image 20260428181849.png" width="600">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 8</b>. Implementación del estado "Ganar". Cuando se cumple la condición para ganar, se manda un mensaje (Evento) y los "Sprite" que reciben el mensaje reaccionan al evento. 
</div>

Esto permite crear finales claros y satisfactorios para el jugador.

---

## 2.3 Estados de perder 

Un **estado de perder** se activa cuando el jugador falla en cumplir las condiciones del juego, como quedarse sin vidas, perder todo el tiempo o cometer errores críticos.

Ejemplo en Scratch:

- Si la variable vida llega a 0:
    - **“si <vida = 0> entonces”**
        - Mostrar mensaje: “Game Over”
        - Detener el juego

También se pueden usar condiciones como:

- **“si <tiempo = 0> entonces”**
- **“si \<tocando enemigo> entonces”**

<div style="text-align: center;">
  <img src="Pasted image 20260428183557.png" width="600">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 9</b>. Implementación del estado "Perder". Cuando se cumple la condición para perder, se manda un mensaje (Evento) y por medio de "Cambiar fondo" ubicado en la sección de apariencia, cuando se recibe el mensaje de "Perdió" cambia el escenario. 
</div>


Esto introduce dificultad y desafío, haciendo el juego más interesante.

---

## Actividades propuestas

---

> [!note] Actividad 1: Uso de condicionales
> **Duración:** 15 minutos  
> **Objetivo:** Comprender el uso de estructuras condicionales en Scratch.  
>  
> **Desarrollo:**  
> El estudiante programará un objeto que reaccione cuando el personaje principal lo toque.  
>  
> **Ejemplo:**  
> - “si \<tocando personaje> entonces” → decir “¡Hola!” por 2 segundos  

---

> [!tip] Actividad 2: Condición de victoria
> **Duración:** 20 minutos  
> **Objetivo:** Implementar un estado de ganar en un juego.  
>  
> **Desarrollo:**  
> El jugador deberá alcanzar cierto puntaje (por ejemplo, 5 puntos) para ganar.  
>  
> **Ejemplo:**  
> - “si <puntaje = 5> entonces”  
>   - decir “¡Ganaste!”  
>   - detener todo  

---

> [!warning] Actividad 3: Condición de derrota
> **Duración:** 20 minutos  
> **Objetivo:** Implementar un estado de perder en un juego.  
>  
> **Desarrollo:**  
> El jugador perderá cuando su variable vida llegue a 0.  
>  
> **Ejemplo:**  
> - “si <vida = 0> entonces”  
>   - decir “Game Over”  
>   - detener todo  

---

> [!success] Actividad 4: Decisiones combinadas
> **Duración:** 25 minutos  
> **Objetivo:** Aplicar múltiples condicionales en un mismo juego.  
>  
> **Desarrollo:**  
> El juego debe tener una condición de ganar (puntaje) y una de perder (vidas o tiempo).  
>  
> **Ejemplo:**  
> - “si <puntaje = 10> entonces” → ganar  
> - “si <vida = 0> entonces” → perder  


---
---

# Tema 3. Movimiento y repetición

> [!danger] Propuesta
>
> Iniciar con este tema antes de "Variables y estados del juego" y "Decisiones dentro del juego".
>
> Empezar con **movimiento y repetición** es más efectivo porque constituye la parte más visual, intuitiva y motivadora del aprendizaje en programación de videojuegos. Cuando una persona inicia, necesita ver resultados inmediatos, como que un personaje se mueva, responda a teclas o que ocurran acciones de manera continua; esto se logra fácilmente utilizando los bloques de **Movimiento** (color azul) y los bloques de **Control** como “por siempre” o “repetir” en Scratch. Sin estos elementos, el juego no tiene dinamismo ni vida. En cambio, si se comienza directamente con variables como puntaje, vidas o tiempo sin que exista movimiento o interacción, el aprendizaje se vuelve abstracto, ya que el estudiante no comprende para qué sirven estos elementos, qué los afecta o qué está ocurriendo dentro del juego, lo que puede generar confusión desde las primeras etapas.

El movimiento es uno de los elementos fundamentales en cualquier videojuego, ya que permite dar vida a los personajes y crear interacción con el entorno. En Scratch, el movimiento se logra mediante bloques simples que controlan la posición y dirección de los objetos (sprites). Sin embargo, para que estas acciones ocurran de manera continua o en respuesta al usuario, es necesario utilizar **eventos** y **estructuras de repetición (bucles)**.

==La combinación de movimiento y repetición permite construir mecánicas básicas como desplazamiento del personaje, seguimiento de objetos, animaciones y comportamientos automáticos==. Estos conceptos son la base sobre la cual se construyen posteriormente elementos más complejos como puntajes, vidas y decisiones dentro del juego.

---

## 3.1 Eventos de teclado

Los **eventos de teclado** permiten que el usuario controle el comportamiento de un personaje mediante la interacción con el teclado. En Scratch, estos bloques se encuentran en la categoría **“Eventos”** (color amarillo).

El bloque más utilizado es:

- **“al presionar tecla [ ]”**

Este bloque ejecuta acciones cuando el usuario presiona una tecla específica, como las flechas de dirección o la barra espaciadora.

Ejemplo en Scratch:

- Para mover un personaje hacia la derecha:
    - **“al presionar tecla flecha derecha”**
        - **“cambiar x por 10”** (bloque de Movimiento, color azul)
- Para moverlo hacia la izquierda:
    - **“al presionar tecla flecha izquierda”**
        - **“cambiar x por -10”**


<div style="text-align: center;">
  <img src="Pasted image 20260502145032.png" width="400">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 10</b>. Implementación para un movimiento lateral.
</div>

También se pueden usar:

- **“cambiar y por ( )”** → movimiento vertical
- **“apuntar en dirección ( )”** → cambiar orientación

<div style="text-align: center;">
  <img src="Pasted image 20260502145101.png" width="400">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 11</b>. Implementación para un movimiento vertical. 
</div>

Esto permite crear controles básicos de un personaje dentro del juego.

---

## 3.2 Bucles

Los **bucles** permiten repetir acciones múltiples veces o de forma continua. Son esenciales para mantener el juego en ejecución constante. En Scratch, se encuentran en la categoría **“Control”** (color naranja claro).

Los bloques principales son:

- **“por siempre”** → repite indefinidamente
- **“repetir ( )”** → repite un número específico de veces
- **“repetir hasta que < >”** → se ejecuta hasta que se cumpla una condición

Ejemplo en Scratch:

- Para hacer que un objeto se mueva constantemente:
    - **“al presionar bandera verde”**
        - **“por siempre”**
            - **“mover 2 pasos”**
- Para crear una animación:
    - **“siguiente disfraz”**
    - **“esperar 0.3 segundos”**

<div style="text-align: center;">
  <img src="Pasted image 20260502150844.png" width="400">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 12</b>. Ejemplo de dos secuencias en ejecución simultanea, se desplaza mientras hace cambios de disfraz.  
</div>

Los bucles son fundamentales para crear comportamiento continuo en los videojuegos, como enemigos en movimiento o animaciones.

---

## 3.3 Interacción con objetos

La interacción con objetos permite que los elementos del juego reaccionen entre sí, como cuando un personaje toca un objeto o un enemigo. Esto se logra combinando sensores, movimiento y bucles.

En Scratch, se utilizan bloques de la categoría **“Sensores”** (color azul claro), como:

- **“tocando \[objeto]”**
- **“tocando color [ ]”**

Ejemplo en Scratch:

- Detectar colisión con un objeto:
    - **“por siempre”**
        - **“si \<tocando objeto> entonces”**
            - Ejecutar acción (sumar puntos, cambiar posición, etc.)

Ejemplo práctico:

- Cuando el personaje toca una objeto:
    - Cambia de dirección
    - Se mueve de forma horizontal 

<div style="text-align: center;">
  <img src="Pasted image 20260502151938.png" width="500">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 13</b>. Se retomo el ejemplo de la imagen 12 para implementar una interacción con dos objetos 
</div>

Esto permite crear mecánicas básicas como recolección de objetos, obstáculos y colisiones.

---

## Actividades propuestas

---

> [!note] Actividad 1: Movimiento con teclado
> **Duración:** 15 minutos  
> **Objetivo:** Controlar un personaje mediante el teclado.  
>  
> **Desarrollo:**  
> El estudiante programará un sprite para moverse en cuatro direcciones usando las teclas de flecha.  
>  
> **Ejemplo:**  
> - “al presionar tecla flecha derecha” → cambiar x por 10  
> - “al presionar tecla flecha izquierda” → cambiar x por -10  
> - “al presionar tecla flecha arriba” → cambiar y por 10  
> - “al presionar tecla flecha abajo” → cambiar y por -10  

---

> [!tip] Actividad 2: Movimiento continuo
> **Duración:** 20 minutos  
> **Objetivo:** Aplicar bucles para generar movimiento automático.  
>  
> **Desarrollo:**  
> Crear un objeto que se mueva constantemente por la pantalla.  
>  
> **Ejemplo:**  
> - “al presionar bandera verde”  
>   - “por siempre”  
>     - “mover 5 pasos”  

---

> [!warning] Actividad 3: Interacción con objetos
> **Duración:** 20 minutos  
> **Objetivo:** Detectar colisiones entre objetos.  
>  
> **Desarrollo:**  
> Programar una interacción donde el personaje reaccione al tocar otro objeto.  
>  
> **Ejemplo:**  
> - “por siempre”  
>   - “si \<tocando objeto> entonces”  
>     - decir “¡Me tocaste!”  

---

> [!success] Actividad 4: Mini juego básico
> **Duración:** 25 minutos  
> **Objetivo:** Integrar movimiento, repetición e interacción.  
>  
> **Desarrollo:**  
> Crear un juego donde el personaje se mueva y deba tocar un objeto que aparece en diferentes posiciones.  
>  
> **Ejemplo:**  
> - Movimiento con teclado  
> - “si \<tocando objeto> entonces” → ir a posición aleatoria  

---
---

# Integración de proyecto 

# Evaluación y cierre


