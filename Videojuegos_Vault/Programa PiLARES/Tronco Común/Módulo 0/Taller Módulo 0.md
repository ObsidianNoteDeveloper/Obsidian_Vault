# Alfabetización Digital y Lógica Básica (20 horas - 10 sesiones de 2 horas)

Plataformas gratuitas: 
- Papel y lápiz 
- Draw.io 
- Google Docs 

### Objetivo del módulo 

Desarrollar pensamiento lógico y comprensión básica del funcionamiento tecnológico necesario para entender cómo operan los videojuegos. 

# Tema 1. Fundamentos tecnológicos para videojuegos

El desarrollo de videojuegos requiere comprender una serie de conceptos tecnológicos fundamentales antes de comenzar a utilizar herramientas de programación o motores de desarrollo. Un videojuego no funciona únicamente gracias al código que escribe un desarrollador, sino mediante la interacción de diferentes elementos de hardware, software, dispositivos de entrada, sistemas de procesamiento y medios de salida. Comprender estos elementos permite que el estudiante identifique qué sucede técnicamente cuando una persona interactúa con un videojuego y cómo dicha interacción se transforma en una respuesta visible o audible.

En este tema se estudiarán los fundamentos tecnológicos que permiten comprender el funcionamiento general de un videojuego. Primero se analizará la diferencia entre hardware y software; posteriormente se estudiará el modelo de entrada, proceso y salida, que permite representar de manera sencilla la interacción entre el usuario y el sistema. Después se establecerá la diferencia entre un programa y un videojuego y se identificarán las principales plataformas en las que pueden ejecutarse. Finalmente, se introducirá el concepto de ciclo de juego o _Game Loop_, elemento fundamental para comprender cómo un videojuego permanece activo y responde continuamente a las acciones del jugador.

---

## 1.1 Hardware y software

### Hardware

El **hardware** comprende todos los componentes físicos de un sistema informático, es decir, aquellos elementos que pueden ser observados y manipulados físicamente. En el contexto de los videojuegos, el hardware proporciona los recursos necesarios para ejecutar el programa, recibir las acciones del jugador, procesar información y producir una respuesta.

Entre los componentes más importantes se encuentra el **procesador o CPU**, encargado de ejecutar instrucciones y realizar operaciones necesarias para el funcionamiento del programa. La **memoria RAM** permite almacenar temporalmente información que está siendo utilizada por el sistema y los programas en ejecución. La **GPU o tarjeta gráfica** se especializa en el procesamiento y generación de imágenes, por lo que desempeña un papel especialmente importante en videojuegos que requieren representar gráficos complejos.

También forman parte del hardware los dispositivos utilizados para interactuar con el videojuego. El teclado, el mouse, el control de una consola, la pantalla táctil, el micrófono y algunos sensores son ejemplos de dispositivos que permiten introducir información al sistema. Por otro lado, el monitor, los altavoces, los audífonos y los dispositivos de vibración permiten presentar al jugador las respuestas generadas por el videojuego.

Por ejemplo, cuando un jugador presiona una tecla para mover a un personaje, el teclado representa un componente físico que detecta la acción. El sistema recibe dicha información, la procesa mediante el software y finalmente utiliza otros componentes físicos, como la GPU y el monitor, para mostrar el movimiento del personaje.

### Software

El **software** está constituido por los programas, instrucciones y datos que indican al hardware qué debe hacer. A diferencia del hardware, el software no es un objeto físico que pueda manipularse directamente. El sistema operativo, los controladores, las aplicaciones y los videojuegos son ejemplos de software.

En un videojuego, el software contiene las instrucciones que determinan las reglas y comportamientos del juego. Por ejemplo, puede establecer que al presionar una determinada tecla el personaje debe desplazarse hacia la derecha, que un enemigo debe perseguir al jugador o que una determinada cantidad de puntos debe producir una recompensa.

También existen herramientas de software utilizadas para crear videojuegos. Los motores como Godot, Unity o Unreal Engine proporcionan diferentes sistemas que permiten construir escenarios, personajes, físicas, sonidos, interfaces y comportamientos sin tener que desarrollar todos estos elementos desde cero.

Por lo tanto, hardware y software trabajan conjuntamente. El hardware proporciona los recursos físicos y el software proporciona las instrucciones que utilizan dichos recursos. Un videojuego necesita ambos elementos para funcionar correctamente.

### Actividad 1.1. Identificación de hardware y software

**Instrucciones:** Clasificar los siguientes elementos como **hardware** o **software**:

1. Teclado.
2. Godot.
3. Monitor.
4. Sistema operativo.
5. Control de videojuegos.
6. GPU.
7. Videojuego.
8. Memoria RAM.

**Resolución:**

|Elemento|Clasificación|Justificación|
|---|---|---|
|Teclado|Hardware|Es un dispositivo físico utilizado para introducir información.|
|Godot|Software|Es una herramienta informática utilizada para desarrollar videojuegos.|
|Monitor|Hardware|Es un dispositivo físico que muestra información visual.|
|Sistema operativo|Software|Es un conjunto de programas que administra los recursos del equipo.|
|Control de videojuegos|Hardware|Es un dispositivo físico utilizado para introducir acciones del jugador.|
|GPU|Hardware|Es un componente físico encargado principalmente del procesamiento gráfico.|
|Videojuego|Software|Está compuesto por instrucciones, datos y recursos digitales que son ejecutados por el sistema.|
|Memoria RAM|Hardware|Es un componente físico utilizado para almacenar temporalmente información en ejecución.|

**Conclusión de la actividad:** La principal diferencia consiste en que el hardware corresponde a los componentes físicos del sistema, mientras que el software corresponde a los programas e instrucciones que utilizan dichos componentes.

---

## 1.2 Modelo de entrada, proceso y salida

Una forma sencilla de comprender la interacción entre una persona y un sistema informático es mediante el modelo de **entrada, proceso y salida**. Este modelo representa una secuencia básica en la que el sistema recibe información, la procesa y genera una respuesta.

La **entrada** corresponde a la información que recibe el sistema. En un videojuego, puede ser una tecla presionada, un movimiento del mouse, una pulsación sobre una pantalla táctil, el movimiento de un control o cualquier otra acción realizada por el jugador. La entrada representa, por lo tanto, la interacción inicial del usuario con el videojuego.

El **proceso** consiste en las operaciones que realiza el sistema para interpretar la entrada y determinar qué debe suceder. En esta etapa interviene principalmente el software del videojuego, que contiene las reglas y condiciones que determinan el comportamiento del sistema. Por ejemplo, si el jugador presiona la tecla correspondiente a saltar, el videojuego puede comprobar si el personaje está en el suelo y, si se cumple la condición, modificar su movimiento vertical.

La **salida** corresponde al resultado producido por el sistema después del procesamiento. En un videojuego, esta salida puede ser visual, sonora o incluso física. El personaje puede desplazarse en la pantalla, reproducirse un sonido, cambiar el marcador, aparecer un mensaje o producirse una vibración en el control.

Puede representarse de la siguiente manera:

**Entrada → Proceso → Salida**

Por ejemplo:

**Presionar tecla → El juego interpreta la tecla → El personaje se mueve**

Es importante comprender que este modelo no ocurre solamente una vez. En un videojuego, las entradas y los procesos se producen continuamente mientras el juego está activo, generando nuevas salidas de manera constante.

### Actividad 1.2. De una tecla a una acción

**Situación:** En un videojuego de plataformas, el jugador presiona la tecla **Espacio** para hacer saltar al personaje.

**Instrucciones:** Identificar la entrada, el proceso y la salida.

**Resolución:**

**Entrada:** El jugador presiona la tecla Espacio del teclado.

**Proceso:** El videojuego detecta que la tecla Espacio fue presionada y ejecuta la instrucción correspondiente al salto. El programa modifica el movimiento vertical del personaje y aplica las reglas físicas establecidas.

**Salida:** El personaje se eleva visualmente en la pantalla y, si el videojuego lo contempla, puede reproducirse un efecto de sonido.

El proceso completo puede representarse así:

**Jugador presiona Espacio → El juego detecta la tecla → Se ejecuta la acción de salto → El personaje aparece saltando**

**Conclusión de la actividad:** Una acción dentro de un videojuego no ocurre de manera aislada. Existe una relación entre la acción realizada por el usuario, el procesamiento de dicha información y la respuesta producida por el sistema.

---

## 1.3 Diferencia entre programa y videojuego

Un **programa informático** es un conjunto de instrucciones diseñadas para realizar determinadas tareas. Existen programas destinados a escribir documentos, reproducir música, editar imágenes, realizar cálculos, navegar por Internet o administrar información, entre muchas otras funciones.

Un **videojuego también es un programa**, porque está compuesto por instrucciones y datos que son ejecutados por un sistema informático. Sin embargo, posee características particulares que permiten diferenciarlo de otros tipos de programas.

Una característica fundamental de un videojuego es la existencia de una **interacción significativa con el usuario** dentro de un sistema de reglas. El jugador realiza acciones y el videojuego responde a ellas. Además, normalmente existe un objetivo, un desafío, una condición de progreso o algún tipo de sistema que determina las consecuencias de las acciones realizadas.

Por ejemplo, una calculadora es un programa porque recibe datos, realiza operaciones y presenta resultados. Sin embargo, no está diseñada principalmente como una experiencia interactiva basada en reglas, desafíos y objetivos propios de un videojuego.

En cambio, un videojuego de matemáticas puede solicitar al jugador resolver una operación antes de permitirle avanzar. Aunque también procesa información matemática, incorpora elementos como reglas, objetivos, retroalimentación, desafíos y participación activa del jugador.

Por lo tanto, puede afirmarse que **todo videojuego es un programa, pero no todo programa es un videojuego**.

### Actividad 1.3. ¿Programa o videojuego?

**Instrucciones:** Clasificar los siguientes ejemplos y explicar brevemente la decisión:

1. Calculadora.
2. Procesador de textos.
3. Videojuego de carreras.
4. Aplicación que enseña matemáticas mediante desafíos.
5. Reproductor de música.

**Resolución:**

1. **Calculadora: programa.** Su función principal es realizar operaciones matemáticas y proporcionar resultados.
2. **Procesador de textos: programa.** Está diseñado principalmente para crear y editar documentos.
3. **Videojuego de carreras: videojuego y programa.** Es un programa que utiliza reglas, objetivos, interacción y desafíos propios de una experiencia de juego.
4. **Aplicación que enseña matemáticas mediante desafíos: puede considerarse videojuego educativo.** Además de proporcionar contenido educativo, utiliza interacción, reglas, objetivos y desafíos para alcanzar un propósito de aprendizaje.
5. **Reproductor de música: programa.** Su propósito principal es reproducir archivos o contenidos de audio.

**Conclusión de la actividad:** El criterio no consiste únicamente en determinar si existe interacción. Muchos programas son interactivos. Lo que distingue al videojuego es la combinación de interacción con elementos como reglas, objetivos, desafíos, retroalimentación y una experiencia estructurada de juego.

---

## 1.4 Plataformas: PC, consola, móvil y web

Una **plataforma** es el entorno tecnológico sobre el cual puede ejecutarse un videojuego. Cada plataforma posee características particulares relacionadas con el hardware, el sistema operativo, los dispositivos de entrada, la distribución del software y las capacidades técnicas disponibles.

La **PC** es una de las plataformas más flexibles para videojuegos. Puede utilizar diferentes sistemas operativos, componentes de hardware y dispositivos de entrada. Un mismo videojuego para PC puede utilizar teclado y mouse, controles, pantallas táctiles u otros periféricos. Además, la computadora es una plataforma ampliamente utilizada para aprender programación y desarrollo de videojuegos debido a la disponibilidad de herramientas de desarrollo.

Las **consolas** son dispositivos diseñados específicamente para ejecutar videojuegos y ofrecer experiencias de entretenimiento. Normalmente utilizan hardware y sistemas operativos controlados por el fabricante. El control o mando representa uno de los principales dispositivos de entrada y los videojuegos suelen distribuirse mediante tiendas digitales o medios físicos.

Los **dispositivos móviles**, como teléfonos inteligentes y tabletas, utilizan principalmente pantallas táctiles como mecanismo de interacción, aunque también pueden conectarse controles y otros dispositivos. Esta plataforma permite desarrollar videojuegos que aprovechan características como sensores de movimiento, cámara, micrófono, conectividad inalámbrica y pantalla táctil.

La **web** permite ejecutar videojuegos mediante un navegador. En este caso, el usuario normalmente no necesita instalar un programa tradicional en su equipo, ya que el contenido puede cargarse desde un servidor y ejecutarse mediante tecnologías web. HTML, CSS y JavaScript constituyen algunas de las tecnologías fundamentales utilizadas para crear experiencias interactivas en este entorno.

Un mismo concepto de videojuego puede adaptarse a varias plataformas, pero esto no significa necesariamente que el desarrollo sea idéntico. Cada plataforma puede requerir diferentes controles, resoluciones, métodos de distribución y consideraciones técnicas.

### Actividad 1.4. Clasificación por plataforma

**Instrucciones:** Clasificar cada situación según la plataforma más adecuada.

1. Un videojuego que se controla principalmente mediante teclado y mouse.
2. Un juego que utiliza una pantalla táctil para seleccionar objetos.
3. Un videojuego diseñado para ejecutarse mediante un navegador.
4. Un juego pensado para utilizar un control conectado a una consola.

**Resolución:**

1. **PC:** El teclado y el mouse son dispositivos de entrada habituales en esta plataforma.
2. **Móvil:** La pantalla táctil es uno de los principales mecanismos de interacción de teléfonos y tabletas.
3. **Web:** El videojuego se ejecuta mediante un navegador utilizando tecnologías web.
4. **Consola:** El videojuego está diseñado para ejecutarse en un sistema de consola y utilizar su control.

**Conclusión de la actividad:** La plataforma determina parte de las condiciones en las que funcionará el videojuego. Por esta razón, un desarrollador debe considerar desde las primeras etapas dónde se ejecutará su proyecto y qué dispositivos utilizará el jugador.

---

## 1.6 Ciclo de juego (Game Loop)

Un videojuego no puede limitarse a ejecutar una instrucción una sola vez. Mientras el jugador está jugando, el sistema debe recibir continuamente información, actualizar el estado del juego y mostrar los resultados. Para comprender este comportamiento se utiliza el concepto de **Game Loop o ciclo de juego**.

El _Game Loop_ es un proceso que se repite continuamente mientras el videojuego permanece activo. Aunque su implementación puede variar dependiendo del motor o tecnología utilizada, conceptualmente puede representarse mediante tres etapas principales: **recibir entradas, actualizar el estado del juego y generar la salida visual o sonora**.

El ciclo puede representarse de manera simplificada de la siguiente forma:

**Entrada → Actualización → Renderizado → Repetición**

En la primera etapa, el videojuego comprueba las acciones realizadas por el jugador. Puede detectar si se presionó una tecla, se movió el mouse, se pulsó la pantalla o se desplazó un control.

Posteriormente, el sistema **actualiza el estado del juego**. En esta etapa se aplican las reglas correspondientes a las entradas y también se procesan otros elementos que suceden automáticamente. Por ejemplo, puede actualizarse la posición de un personaje, el movimiento de un enemigo, la cantidad de vidas, el tiempo restante o la posición de un objeto.

Después se realiza el **renderizado**, que consiste en representar visualmente el estado actualizado del juego. El sistema genera la imagen que será presentada en la pantalla. También pueden actualizarse elementos de sonido, interfaz y otros sistemas de salida.

Una vez completado el proceso, el ciclo vuelve a comenzar. Esta repetición ocurre muchas veces por segundo, permitiendo que el jugador perciba movimiento y respuestas prácticamente continuas.

Por ejemplo, si un personaje está caminando hacia la derecha, el videojuego puede realizar continuamente un proceso semejante al siguiente:

**Detectar entrada → Actualizar posición → Dibujar personaje → Detectar nueva entrada → Actualizar posición → Dibujar personaje → Repetir**

Gracias a este ciclo, el videojuego puede responder constantemente a las acciones del jugador y mantener actualizados los diferentes elementos que forman parte de la experiencia.

### Actividad 1.6. Simulación de un Game Loop

**Situación:** Un jugador controla un personaje que puede desplazarse hacia la derecha utilizando la tecla **D**.

**Instrucciones:** Representar tres ciclos consecutivos del videojuego suponiendo que el jugador mantiene presionada la tecla D.

**Resolución:**

**Ciclo 1**

- **Entrada:** Se detecta la tecla D.

- **Actualización:** La posición horizontal del personaje aumenta.

- **Salida:** El personaje aparece ligeramente desplazado hacia la derecha.

**Ciclo 2**

- **Entrada:** La tecla D continúa presionada.

- **Actualización:** La posición horizontal vuelve a aumentar.

- **Salida:** El personaje aparece nuevamente desplazado hacia la derecha.

**Ciclo 3**

- **Entrada:** La tecla D continúa presionada.

- **Actualización:** La posición del personaje vuelve a modificarse.

- **Salida:** El personaje continúa avanzando hacia la derecha.

El proceso simplificado sería:

**Detectar D → Mover personaje → Mostrar resultado**

**Detectar D → Mover personaje → Mostrar resultado**

**Detectar D → Mover personaje → Mostrar resultado**

**Conclusión de la actividad:** El movimiento continuo no significa que el videojuego "mueva" al personaje de una sola vez. El sistema actualiza repetidamente su estado y vuelve a representar el resultado. La repetición de este proceso constituye una parte fundamental del funcionamiento de un videojuego.

---

## Actividad integradora

#### Representación del proceso completo de interacción en un videojuego

La actividad integradora tiene como propósito relacionar los conceptos estudiados durante el tema. El estudiante deberá representar mediante un diagrama qué ocurre desde que el jugador realiza una acción hasta que observa la respuesta en pantalla.

Para realizar la actividad se propone utilizar como ejemplo un videojuego de plataformas en el que el jugador presiona la tecla **Espacio** para hacer saltar al personaje.

El diagrama deberá incluir los siguientes elementos:

**1. Jugador:** El jugador realiza una acción utilizando un dispositivo de entrada.

**2. Hardware de entrada:** El teclado detecta que la tecla Espacio fue presionada.

**3. Software del videojuego:** El programa recibe la información y determina qué acción corresponde a esa entrada.

**4. Procesamiento:** El videojuego actualiza el estado del personaje aplicando las reglas correspondientes al salto.

**5. Hardware de procesamiento y salida:** El procesador y la GPU participan en la actualización y representación de la escena.

**6. Pantalla:** El monitor presenta visualmente el nuevo estado del videojuego.

**7. Game Loop:** El proceso continúa y el videojuego vuelve a recibir nuevas entradas y actualizar su estado.

### Resolución de la actividad integradora

Un posible diagrama completo sería:
<div style="text-align: center;">  
<img src="Pasted%20image%2020260911153729.png" width="900">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 1</b>. Ejemplo gráfico de un Game Loop.
</div>

Este diagrama permite integrar los principales conceptos estudiados. El teclado representa un componente de **hardware**; el videojuego representa un tipo de **software**; la acción del jugador constituye una **entrada**; las reglas y operaciones realizadas por el programa constituyen el **proceso**; la imagen presentada en pantalla representa la **salida**; y la repetición de estos pasos forma parte del **Game Loop**.

### Producto esperado

Al finalizar la actividad, el estudiante deberá ser capaz de elaborar un diagrama similar utilizando otro ejemplo de interacción. Puede seleccionar acciones como caminar, disparar, recoger un objeto, atacar a un enemigo o seleccionar una opción del menú.

El diagrama deberá identificar claramente:

**Jugador → Entrada → Procesamiento → Actualización → Salida → Repetición mediante Game Loop**

### Cierre del tema

Los conceptos estudiados permiten establecer una primera representación técnica del funcionamiento de un videojuego. El hardware proporciona los componentes físicos necesarios para ejecutar el sistema y recibir las acciones del jugador, mientras que el software contiene las instrucciones que determinan el comportamiento del videojuego. La interacción puede comprenderse mediante el modelo de entrada, proceso y salida, mientras que el concepto de _Game Loop_ permite explicar cómo estas acciones se repiten continuamente durante una partida.

A partir de esta base, el estudiante puede comenzar a comprender que desarrollar un videojuego no consiste únicamente en crear imágenes o programar personajes. Implica diseñar un sistema en el que diferentes componentes tecnológicos trabajan conjuntamente para recibir información, procesarla, actualizar un estado y producir una respuesta. Esta comprensión será fundamental para abordar posteriormente conceptos como lógica de programación, variables, eventos, estructuras de control, física, programación orientada a objetos y utilización de motores de videojuegos.

---

# Tema 2. Pensamiento lógico aplicado al juego

El pensamiento lógico constituye una de las habilidades fundamentales para el desarrollo de videojuegos, debido a que permite analizar un problema, dividirlo en acciones y establecer las reglas que determinan cómo debe comportarse un sistema. Antes de escribir código, un desarrollador necesita ser capaz de describir qué debe suceder, en qué orden debe suceder, bajo qué circunstancias debe ejecutarse una acción y cuáles acciones deben repetirse.

En un videojuego, prácticamente todos los comportamientos pueden describirse mediante estructuras lógicas. El personaje puede comenzar una partida, desplazarse, recoger objetos, recibir daño, perder vidas, alcanzar una meta o reiniciar el nivel. Cada uno de estos comportamientos requiere organizar acciones, tomar decisiones y repetir determinados procesos. Por esta razón, el pensamiento lógico no debe entenderse únicamente como una herramienta relacionada con la programación, sino como una forma de analizar y diseñar el comportamiento de un videojuego.

En este tema se estudiarán tres elementos fundamentales del pensamiento lógico: **secuencias, condiciones y repetición**. Posteriormente, estos elementos serán combinados para construir una lógica de juego completa que permita diseñar, en papel, el funcionamiento de un pequeño videojuego.

---

## 2.1 Secuencias

Una **secuencia** es un conjunto de acciones organizadas en un orden determinado. En pensamiento lógico, el orden es importante porque una acción puede depender de que otra haya ocurrido previamente. Por ejemplo, para iniciar una partida primero es necesario seleccionar una opción del menú; posteriormente se carga el nivel y finalmente comienza el juego.

En el desarrollo de videojuegos, las secuencias permiten describir el comportamiento de los personajes, los eventos de una partida, las instrucciones de un nivel y las acciones que debe realizar el jugador. Una secuencia puede ser muy sencilla, como presionar una tecla y posteriormente mover un personaje, o puede estar formada por numerosas acciones relacionadas entre sí.

Por ejemplo, imaginemos un videojuego en el que el jugador debe abrir una puerta. Una secuencia lógica podría ser:

**Acercarse a la puerta → encontrar la llave → recoger la llave → regresar a la puerta → abrir la puerta → entrar en la siguiente zona.**

El orden de estas acciones es importante. Si el jugador intenta abrir la puerta antes de obtener la llave, el comportamiento del videojuego tendría que contemplar esa situación mediante una condición, concepto que será estudiado posteriormente.

Las secuencias también permiten dividir problemas complejos en pasos pequeños y ordenados. Esta capacidad es especialmente importante durante el desarrollo, ya que permite que una idea general como "crear un videojuego de plataformas" pueda dividirse en acciones concretas como iniciar el nivel, controlar al personaje, detectar colisiones, recoger objetos, actualizar vidas y comprobar si se alcanzó la meta.

Una secuencia puede representarse mediante una lista de instrucciones:

```
1. Iniciar el juego.
2. Mostrar al personaje.
3. Permitir el movimiento.
4. Buscar la llave.
5. Recoger la llave.
6. Llegar a la puerta.
7. Abrir la puerta.
8. Completar el nivel.
```

Esta representación todavía no constituye código, pero permite expresar de manera clara la lógica que posteriormente podría convertirse en instrucciones de programación.

### Actividad 2.1. Ordenar las acciones de un videojuego

**Situación:** El jugador debe completar un pequeño nivel en el que tiene que recoger una moneda y llegar a una meta.

Las acciones se encuentran desordenadas:

- Llegar a la meta.
- Iniciar el nivel.
- Recoger la moneda.
- Mover al personaje hacia la moneda.
- Mostrar el nivel.

**Instrucciones:** Organizar las acciones en el orden lógico en el que deberían ejecutarse.

### Resolución

La secuencia correcta es:

```
1. Iniciar el nivel.
2. Mostrar el nivel.
3. Mover al personaje hacia la moneda.
4. Recoger la moneda.
5. Llegar a la meta.
```

La primera acción debe ser iniciar el nivel porque las demás acciones necesitan que el nivel esté disponible. Después se muestra el escenario y se permite al jugador controlar al personaje. Una vez que el personaje llega hasta la moneda, puede recogerla y posteriormente dirigirse hacia la meta.

**Conclusión de la actividad:** Las secuencias permiten organizar un conjunto de acciones de manera lógica. Cuando el orden de las acciones es incorrecto, el comportamiento del videojuego puede producir resultados inesperados. Por ello, aprender a ordenar instrucciones constituye una de las primeras habilidades necesarias para posteriormente construir algoritmos y programas.

---

## 2.2 Condiciones

Una **condición** permite que un sistema tome una decisión dependiendo de si determinada situación se cumple o no. En términos sencillos, una condición responde a preguntas como: **¿el jugador tiene una llave?, ¿el personaje tiene vidas?, ¿el enemigo fue derrotado?, ¿el tiempo terminó?, ¿el jugador llegó a la meta?**

Las condiciones pueden expresarse mediante una estructura lógica conocida comúnmente como **si-entonces**. La estructura básica puede representarse de la siguiente manera:

```
SI ocurre una situación
ENTONCES realizar una acción
```

Por ejemplo:

```
SI el jugador tiene la llave
ENTONCES abrir la puerta.
```

Si el jugador no tiene la llave, la acción de abrir la puerta no debe ejecutarse. El videojuego necesita tomar una decisión dependiendo del estado actual de la partida.

También pueden utilizarse condiciones alternativas:

```
SI el jugador tiene vidas
    continuar jugando
SI NO
    mostrar pantalla de Game Over
```

Las condiciones permiten, por lo tanto, que un videojuego responda de diferentes maneras ante diferentes situaciones. Sin ellas, el sistema tendría que ejecutar siempre las mismas acciones independientemente de lo que ocurra durante la partida.

En un videojuego educativo, por ejemplo, una condición puede utilizarse para comprobar una respuesta:

```
SI la respuesta es correcta
    sumar puntos
SI NO
    mostrar "Respuesta incorrecta"
```

Esta estructura demuestra que las condiciones no solamente se utilizan para controlar personajes o enemigos. También permiten crear reglas, sistemas de puntuación, niveles de dificultad, menús, diálogos, recompensas y múltiples comportamientos dentro de un videojuego.

Una condición puede basarse en diferentes tipos de información. Puede comprobar una comparación numérica, la existencia de un objeto, el estado de un personaje o una acción realizada por el jugador. Lo importante es que exista una situación que pueda evaluarse y que dicha evaluación determine qué ocurre posteriormente.

### Actividad 2.2. Crear reglas de decisión

**Situación:** En un videojuego de plataformas, el personaje tiene **3 vidas**. Cuando recibe daño pierde una vida. Si sus vidas llegan a cero, debe terminar la partida.

**Instrucciones:** Construir las reglas utilizando estructuras de tipo "si-entonces".

### Resolución

Una posible solución es:

```
SI el personaje recibe daño
ENTONCES perder una vida.

SI las vidas son mayores que 0
ENTONCES continuar jugando.

SI las vidas son iguales a 0
ENTONCES mostrar "Game Over".
```

También puede representarse como una secuencia de decisiones:

<div style="text-align: center;">  
<img src="Pasted%20image%2020260911184912.png" width="400">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 2</b>. Diagrama de una condición.
</div>


La condición permite que el videojuego tome una decisión diferente dependiendo del estado de las vidas del personaje.

**Conclusión de la actividad:** Las condiciones permiten construir comportamientos dinámicos. El videojuego no responde siempre de la misma manera, sino que evalúa la situación actual y determina qué acción corresponde realizar.

---

## 2.3 Repetición

La **repetición** consiste en ejecutar una acción o conjunto de acciones más de una vez. En los videojuegos, esta estructura es especialmente importante porque muchos comportamientos ocurren de manera continua o periódica.

Un personaje puede caminar durante varios segundos, un enemigo puede patrullar una zona, una animación puede reproducirse varias veces, una serie de enemigos puede aparecer uno después de otro o el videojuego puede comprobar continuamente si el jugador ha recibido daño.

La repetición permite evitar la necesidad de describir manualmente cada ejecución de una acción. Por ejemplo, si queremos que un enemigo avance cinco pasos, conceptualmente podemos escribir:

```
Repetir 5 veces:
    avanzar un paso.
```

En lugar de:

```
Avanzar.
Avanzar.
Avanzar.
Avanzar.
Avanzar.
```

Existen diferentes formas de establecer una repetición. Puede repetirse una acción un número determinado de veces o puede repetirse mientras se cumpla una condición.

Por ejemplo:

```
REPETIR 10 VECES
    mover enemigo.
```

También:

```
MIENTRAS el juego esté activo
    actualizar el juego.
```

En el segundo caso, no se establece una cantidad específica de repeticiones. La acción continúa mientras se mantenga determinada condición.

La repetición está estrechamente relacionada con el funcionamiento de los videojuegos porque permite actualizar constantemente el estado del juego. El concepto de **Game Loop** estudiado en el tema anterior constituye precisamente un ejemplo de un proceso que se repite continuamente mientras la partida está activa.

Las repeticiones también pueden utilizarse para representar patrones. Por ejemplo, un juego podría hacer que una plataforma se mueva hacia la derecha y posteriormente hacia la izquierda:

```
Repetir:
    mover a la derecha
    mover a la izquierda
```

Este patrón puede producir un comportamiento continuo.

### Actividad 2.3. Identificar una repetición

**Situación:** En un videojuego aparecen cinco monedas consecutivas. El jugador debe recogerlas una por una.

**Instrucciones:** Expresar mediante una estructura de repetición el comportamiento necesario para recoger las monedas.

### Resolución

Una forma de representar la lógica es:

```
REPETIR 5 VECES:
    avanzar hacia la siguiente moneda
    recoger la moneda
```

También podría representarse de manera visual:

```
Buscar moneda
     ↓
Recoger moneda
     ↓
¿Quedan monedas?
   ↓          ↓
  Sí          No
  ↓            ↓
Repetir      Continuar
```

En este caso, la repetición permite representar cinco veces el mismo comportamiento sin tener que escribir cinco instrucciones independientes.

**Conclusión de la actividad:** La repetición permite representar comportamientos que ocurren varias veces. Es fundamental para construir patrones y comportamientos continuos, y posteriormente será una herramienta esencial dentro de la programación.

