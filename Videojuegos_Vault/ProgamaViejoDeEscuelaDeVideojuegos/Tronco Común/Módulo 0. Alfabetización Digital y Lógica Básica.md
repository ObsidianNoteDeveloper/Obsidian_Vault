
## Contenido 

[[#Descripción del Módulo]]
[[#Tema 1. Fundamentos tecnológicos para videojuegos]]
	[[#1.1 Hardware y Software]]
	[[#1.2 Modelo de entrada, proceso y salida]]
	[[#1.3 Diferencia entre programa y videojuego]]
	[[#1.4 Plataformas (PC, consola, móvil, web)]]
	[[#1.5 Ciclo de Juego]]
	[[#Actividad Integradora]]
[[#Tema 2. Pensamiento lógico aplicado al juego]]
	[[#2.1 Secuencias]]
	[[#2.2 Condiciones]]
	[[#2.3 Repetición]]
[[#Proyecto final]]


---

## Descripción del Módulo
El **Módulo 0** introduce a las y los participantes en las bases esenciales para el desarrollo de videojuegos, combinando conocimientos tecnológicos y habilidades de pensamiento lógico. En el **Tema 1: Fundamentos tecnológicos para videojuegos**, se abordan conceptos clave como hardware y software, el modelo de entrada–proceso–salida, las plataformas de desarrollo y el ciclo de juego, permitiendo comprender cómo funcionan los sistemas interactivos. Por su parte, el **Tema 2: Pensamiento lógico aplicado al juego** se enfoca en el desarrollo de habilidades como la secuenciación, la toma de decisiones mediante condiciones y la repetición de procesos, integrando estos elementos para construir la lógica básica de un videojuego. En conjunto, este módulo sienta las bases necesarias para que los participantes comprendan cómo se estructuran y funcionan los videojuegos, preparándolos para avanzar hacia etapas más complejas de programación y desarrollo.

El taller tiene una duración total de 20 horas, distribuidas en 10 sesiones de 2 horas.

---

# Tema 1. Fundamentos tecnológicos para videojuegos

---

## 1.1 Hardware y Software

El **software** es un elemento fundamental en el desarrollo y funcionamiento de los videojuegos, ya que representa la parte intangible que permite que estos cobren vida en distintos dispositivos como computadoras, consolas o teléfonos móviles. Está compuesto por un conjunto de programas, aplicaciones y datos que contienen las instrucciones necesarias para que el hardware ejecute acciones específicas dentro del juego, como mover personajes, reproducir sonidos o mostrar gráficos en pantalla. Sin el software, un videojuego no podría existir, ya que es el encargado de definir la lógica, las reglas y la experiencia del usuario.

En el contexto de los videojuegos, el software puede entenderse a través de diferentes tipos. Por un lado, el **software de sistema**, como los sistemas operativos, permite que el dispositivo funcione correctamente y sirva de base para ejecutar los juegos. Por otro lado, el **software de programación** incluye las herramientas que utilizan los desarrolladores para crear videojuegos, como motores gráficos y entornos de desarrollo. Finalmente, el **software de aplicación** es donde se encuentran los videojuegos en sí, diseñados para entretener e interactuar con el jugador mediante mecánicas, narrativas y retos específicos.

La relación entre software y hardware es clave dentro de la experiencia de juego. Mientras el hardware se encarga de los componentes físicos, como controles, pantallas o tarjetas gráficas, el software interpreta las acciones del jugador y las transforma en respuestas dentro del videojuego. Por ejemplo, cuando un jugador presiona un botón para saltar, el hardware detecta la entrada, pero es el software el que procesa esa información y genera la animación correspondiente en pantalla. Esta interacción constante permite que los videojuegos sean dinámicos e interactivos.

Además, dentro del desarrollo de videojuegos también es relevante el concepto de **software libre**, el cual permite a los desarrolladores acceder, modificar y distribuir el código de los programas. Esto fomenta la creatividad, el aprendizaje colaborativo y la innovación dentro de la industria, ya que facilita que más personas puedan experimentar y crear sus propios videojuegos sin tantas restricciones.

Concepto.de. (s.f.). _Software_. Recuperado de [https://concepto.de/software/](https://concepto.de/software/)

---
## Actividades propuestas

> [!info] Actividad 1: Clasificación rápida (Hardware vs Software)  
> **Duración:** 10–15 min  
> **Objetivo:** Identificar conceptos básicos
> 
> **Instrucciones:**  
> Presenta elementos relacionados con videojuegos y pide que los clasifiquen.
> 
> **Desarrollo:**
> 
> - Control de PlayStation (_Hardware_)
> - Fortnite (_Software_)
> - Monitor (_Hardware_)
> - Windows (_Software_)
> - Teclado (_Hardware_)
> - Unity (_Software_)

---

> [!tip] Actividad 2: Análisis de videojuego  
> **Duración:** 15 min  
> **Objetivo:** Analizar un videojuego
> 
> **Instrucciones:**  
> Pide que piensen en un videojuego que conozcan (ej. Minecraft, Free Fire).
> 
> **Desarrollo (preguntas guía):**
> 
> - ¿Qué partes son hardware?
> - ¿Qué partes son software?
> - ¿Qué pasa si falla uno de los dos?

---

> [!success] Actividad 3: Verdadero o falso  
> **Duración:** 10 min  
> **Objetivo:** Reforzar conocimientos
> 
> **Instrucciones:**  
> Preguntar al grupo conceptos vistos durante la sesión.
> 
> **Desarrollo:**
> 
> - “El software se puede tocar” (_Falso_)
> - “Un videojuego es software” (_Verdadero_)
> - “El hardware funciona sin software” (_Falso_)
> - “Unity es una herramienta de programación” (_Verdadero_)

---

> [!important] Actividad 4: Analogía creativa  
> **Duración:** 10–15 min  
> **Objetivo:** Comprensión profunda
> 
> **Instrucciones:**  
> Pide que comparen hardware y software con algo cotidiano.
> 
> **Desarrollo:**
> 
> - Cuerpo (hardware) y mente (software)
> - Auto (hardware) y conductor (software)
> 
> **Cierre:**  
> Cada participante explica su analogía al grupo.

---
---

## 1.2 Modelo de entrada, proceso y salida 

El **modelo de entrada, proceso y salida (EPS)** es un concepto fundamental para comprender cómo funcionan los sistemas tecnológicos, incluidos los videojuegos. Este modelo describe de manera sencilla cómo una acción realizada por el usuario se transforma en una respuesta dentro del sistema. En el contexto de los videojuegos, permite entender cómo las interacciones del jugador se convierten en acciones visibles en pantalla, lo que constituye la base de la experiencia de juego.

La **entrada (input)** corresponde a las acciones que realiza el jugador mediante dispositivos como el teclado, el mouse o un control. Por ejemplo, presionar una tecla para mover un personaje o hacer clic para disparar. Estas acciones son captadas por el hardware y enviadas al sistema para su interpretación. La entrada representa el punto de inicio de toda interacción dentro de un videojuego.

El **proceso** es la etapa en la que el software del videojuego interpreta la entrada recibida y toma decisiones basadas en sus reglas internas. Aquí intervienen elementos como la lógica del juego, las mecánicas y las condiciones programadas por los desarrolladores. Por ejemplo, al presionar la tecla de salto, el sistema verifica si el personaje puede saltar (si está en el suelo, si tiene energía, etc.) y determina qué acción ejecutar. Este proceso ocurre en milisegundos, pero es esencial para que el juego funcione correctamente.

La **salida (output)** es el resultado visible o perceptible de ese proceso. En los videojuegos, se manifiesta a través de cambios en la pantalla, sonidos o vibraciones en el control. Siguiendo el ejemplo anterior, la salida sería la animación del personaje saltando, acompañada posiblemente de un efecto de sonido. Esta respuesta cierra el ciclo de interacción y permite al jugador percibir el efecto de sus acciones.

Comprender este modelo permite a las y los participantes visualizar cómo se genera una acción dentro de un videojuego a partir de una interacción simple. Una forma efectiva de aprenderlo es mediante la **simulación de acciones**, por ejemplo: _tecla presionada → el sistema procesa la acción → el personaje se mueve_. Este flujo puede representarse mediante esquemas o diagramas sencillos que muestren claramente cada etapa del proceso, facilitando la comprensión del funcionamiento interno de los videojuegos y sentando las bases para el aprendizaje de la programación.

<div style="text-align: center;">  
<img src="figura1.png" width="700">  
</div>
<div style="text-align: center; color: #555555;">
<b>Figura 1</b>. Ejemplo del modelo EPS en videojuegos: una entrada del usuario es procesada por el sistema y produce una acción visible.
</div>

---
## Actividades propuestas

> [!info] Actividad 1: Identificando el modelo EPS  
> **Duración:** 10–15 min  
> **Objetivo:** Reconocer los elementos de entrada, proceso y salida en situaciones simples de videojuegos.  
> **Desarrollo:**  
> Presenta ejemplos de acciones dentro de un videojuego y pide a los participantes que identifiquen cada parte del modelo EPS.
> 
> Ejemplos:
> 
> - Presionar tecla "W" → El sistema interpreta movimiento → Personaje avanza
> - Clic del mouse → El juego detecta disparo → Se muestra animación
> 
> Los participantes deben separar cada ejemplo en: Entrada / Proceso / Salida.

---

> [!tip] Actividad 2: Completa el modelo EPS  
> **Duración:** 15 min  
> **Objetivo:** Comprender la relación entre los elementos del modelo EPS.  
> **Desarrollo:**  
> Proporciona modelos incompletos y pide a los participantes que los completen.
> 
> Ejemplos:
> 
> - Entrada: Presionar tecla "espacio" → Proceso: ______ → Salida: Personaje salta
> - Entrada: ______ → Proceso: Detecta colisión → Salida: Personaje pierde vida
> 
> Los estudiantes deben llenar los espacios faltantes correctamente.

---

> [!success] Actividad 3: Crear tu propio modelo EPS  
> **Duración:** 15–20 min  
> **Objetivo:** Aplicar el modelo EPS en situaciones creadas por el estudiante.  
> **Desarrollo:**  
> Pide a los participantes que inventen una acción dentro de un videojuego y la representen usando el modelo EPS.
> 
> Deben escribir:
> 
> - Entrada
> - Proceso
> - Salida
> 
> Finalmente, comparten su ejemplo con el grupo.

---

> [!important] Actividad 4: Representación en esquema EPS  
> **Duración:** 20 min  
> **Objetivo:** Visualizar el modelo EPS mediante esquemas simples.  
> **Desarrollo:**  
> Los participantes dibujan un esquema con tres bloques:
> 
> [Entrada] → [Proceso] → [Salida]
> 
> Luego lo aplican a un videojuego conocido.
> 
> Ejemplo:  
> [Presionar botón A] → [El juego valida acción] → [Personaje ataca]

---

> [!warning] Actividad 5: Detectando errores en el modelo EPS  
> **Duración:** 10–15 min  
> **Objetivo:** Identificar errores en la lógica del modelo EPS.  
> **Desarrollo:**  
> Presenta modelos EPS incorrectos y pide a los participantes corregirlos.
> 
> Ejemplo incorrecto:
> 
> - Entrada: Personaje salta
> - Proceso: Presionar tecla
> - Salida: Detecta acción
> 
> Los participantes deben reorganizar correctamente el modelo.

---
---

## 1.3 Diferencia entre programa y videojuego 

El **programa** es un conjunto de instrucciones diseñadas para realizar una tarea específica dentro de un sistema informático, como procesar datos, editar documentos o ejecutar cálculos. En cambio, un **videojuego** es un tipo particular de programa que, además de cumplir funciones técnicas, está diseñado para ofrecer **interacción, entretenimiento y una experiencia dinámica al usuario**. A diferencia de otros programas tradicionales, los videojuegos incorporan elementos como reglas, objetivos, retroalimentación inmediata, gráficos, sonido y, en muchos casos, narrativa, lo que los convierte en sistemas interactivos más complejos.

Una de las principales diferencias entre un programa convencional y un videojuego radica en la **interactividad constante**. Mientras que un programa como un procesador de texto responde a acciones específicas del usuario de manera funcional, un videojuego mantiene un ciclo continuo de interacción (entrada–proceso–salida), donde cada acción del jugador genera una respuesta inmediata que afecta el estado del juego. Además, los videojuegos suelen incluir mecánicas como niveles, puntuaciones, desafíos y recompensas, lo que los diferencia claramente de otros tipos de software orientados a tareas productivas.

## 1.4 Plataformas (PC, consola, móvil, web)

Los videojuegos pueden desarrollarse y ejecutarse en diversas **plataformas**, lo que influye directamente en su diseño, rendimiento y forma de interacción. Entre las principales plataformas se encuentran la **PC (computadora personal)**, que ofrece mayor flexibilidad y potencia; las **consolas** (como PlayStation o Xbox), diseñadas específicamente para jugar con controles dedicados; los **dispositivos móviles**, que permiten experiencias accesibles y portátiles mediante pantallas táctiles; y la **web**, donde los juegos se ejecutan directamente en el navegador sin necesidad de instalación. Cada plataforma presenta características particulares que los desarrolladores deben considerar al momento de crear un videojuego.

---

## Actividades propuestas

> [!info] Actividad 1: ¿Programa o videojuego?  
> **Duración:** 15 min  
> **Objetivo:** Diferenciar entre un programa y un videojuego según su propósito e interacción.  
> **Desarrollo:**  
> Presenta una lista de aplicaciones y pide a los participantes que las clasifiquen como “programa” o “videojuego”.  
> Luego deben justificar su respuesta considerando aspectos como interacción, objetivo y uso.
> 
> **Ejemplo:**
> 
> - Microsoft Word → Programa
> - Minecraft → Videojuego
> - Calculadora → Programa
> - Free Fire → Videojuego

---

> [!tip] Actividad 2: Comparación práctica  
> **Duración:** 15–20 min  
> **Objetivo:** Analizar las diferencias entre programas y videojuegos en estructura e interacción.  
> **Desarrollo:**  
> Divide al grupo en equipos y asigna un programa y un videojuego.  
> Deben comparar ambos considerando:
> 
> - Propósito
> - Tipo de interacción
> - Respuesta del sistema
> 
> Finalmente, comparten sus conclusiones.
> 
> **Ejemplo:**  
> Programa: Excel  
> Videojuego: Fortnite  
> → Excel sirve para cálculos; Fortnite para entretenimiento interactivo en tiempo real.

---

> [!success] Actividad 3: Clasificación por plataformas  
> **Duración:** 15 min  
> **Objetivo:** Reconocer las diferentes plataformas donde se desarrollan videojuegos.  
> **Desarrollo:**  
> Proporciona una lista de videojuegos y pide que los clasifiquen según su plataforma: PC, consola, móvil, web o multiplataforma.
> 
> **Ejemplo:**
> 
> - League of Legends → PC
> - Call of Duty → Consola
> - Clash Royale → Móvil
> - Juego en navegador (ej. .io) → Web

---

> [!important] Actividad 4: Diseña tu videojuego según la plataforma  
> **Duración:** 20 min  
> **Objetivo:** Comprender cómo la plataforma influye en el diseño del videojuego.  
> **Desarrollo:**  
> En equipos, los participantes eligen una plataforma (PC, consola, móvil o web) y diseñan un videojuego simple considerando:
> 
> - Tipo de control (teclado, control, pantalla táctil)
> - Estilo de juego
> - Experiencia del usuario
> 
> Al final, presentan su idea al grupo.
> 
> **Ejemplo:**  
> Plataforma: Móvil  
> → Juego tipo puzzle con controles táctiles simples.

---

> [!warning] Actividad 5: Detecta la plataforma  
> **Duración:** 10–15 min  
> **Objetivo:** Identificar características de cada plataforma de videojuegos.  
> **Desarrollo:**  
> Describe un videojuego sin mencionar la plataforma y pide a los participantes que adivinen dónde se juega.
> 
> **Ejemplo:**  
> “Juego con pantalla táctil, partidas cortas y uso con una sola mano”  
> → Respuesta: Móvil

---
---

## 1.5 Ciclo de Juego 

El **ciclo de juego** o _game loop_ es el proceso continuo que permite que un videojuego funcione de manera dinámica e interactiva. Consiste en una serie de pasos que se repiten constantemente mientras el juego está en ejecución, permitiendo que el sistema reciba las acciones del jugador, las procese y genere una respuesta en tiempo real. Este ciclo es esencial, ya que sin él el videojuego no podría actualizar su estado ni responder a las decisiones del usuario.

De manera general, el ciclo de juego sigue una estructura repetitiva: primero se **capturan las entradas del jugador** (como presionar teclas o mover un control), luego se **procesa la lógica del juego** (movimiento de personajes, detección de colisiones, reglas), y finalmente se **actualiza la salida** (gráficos, sonidos o animaciones en pantalla). Este proceso ocurre múltiples veces por segundo, lo que genera la sensación de fluidez y continuidad en el videojuego.

Comprender el ciclo de juego permite a las y los participantes visualizar cómo un videojuego está en constante ejecución, respondiendo a cada acción del usuario de forma inmediata. A través de la representación mediante diagramas y simulaciones paso a paso, es posible entender que el videojuego no es una secuencia estática, sino un sistema que se actualiza continuamente, formando un bucle que mantiene la experiencia interactiva activa en todo momento.

---

## Diagramas

Un **diagrama** es una representación visual que muestra de forma clara y organizada cómo funcionan o se relacionan los elementos de un sistema. Utiliza símbolos, formas, flechas y conexiones para explicar procesos, estructuras o ideas que, de otra manera, serían más difíciles de entender solo con texto. En el contexto tecnológico, los diagramas ayudan a simplificar conceptos complejos y permiten visualizar cómo fluye la información dentro de un sistema.

En la creación de videojuegos, los diagramas son especialmente importantes porque permiten **planificar, diseñar y comunicar** cómo funcionará el juego antes de programarlo. Por ejemplo, mediante diagramas es posible representar cómo responde el juego a las acciones del jugador, cómo se organizan sus componentes o cómo evoluciona el comportamiento de un personaje. Esto facilita que los desarrolladores comprendan la lógica del sistema y reduzcan errores durante el desarrollo.

Además, los diagramas ayudan a estructurar elementos clave como el **modelo de entrada–proceso–salida**, el **ciclo de juego (game loop)** y las **mecánicas del juego**. Gracias a ellos, se puede visualizar de manera sencilla cómo una acción del usuario se transforma en una respuesta dentro del videojuego, lo cual es fundamental para diseñar experiencias interactivas coherentes y funcionales.

#### Diagrama 1. Simple y universal

        ┌───────────────┐
        │    Entrada    │
        │(Input jugador)│
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │    Proceso    │
        │ (Lógica del   │
        │    juego)     │
        └───────┬───────┘
                │
                ▼
        ┌───────────────┐
        │    Salida     │
        │ (Gráficos,    │
        │ sonidos, etc.)│
        └───────┬───────┘
                │
                ▼
        Se repite continuamente

#### Diagrama de flujo

<div style="text-align: center;">
  <img src="Pasted image 20260414174846.png" width="300">
</div>
<div style="text-align: center; color: #555555;">
<b>Figura 2</b>. Ejemplo de Diagrama de flujo, simulación de juego en estado activo, representación de una tecla.
</div>

#### Diagrama profesional en Mermaid

<div style="text-align: center;">
  <img src="mermaid-diagram.png" width="250">
</div>
<div style="text-align: center; color: #555555;">
<b>Figura 3</b>. Mermaid es una herramienta que permite crear diagramas y gráficos usando texto
</div>


---

## Actividades propuestas

---

> [!info] Actividad 1: Identificando el ciclo de juego  
> **Duración:** 10–15 min  
> **Objetivo:** Reconocer las etapas del ciclo de juego (entrada, proceso y salida).  
> **Desarrollo:**  
> Presenta una acción dentro de un videojuego y pide a los participantes que identifiquen qué ocurre en cada etapa del ciclo.
> 
> **Ejemplo:**  
> Entrada: Presionar tecla "espacio"  
> Proceso: El juego detecta que el personaje puede saltar  
> Salida: El personaje realiza la animación de salto

---

> [!tip] Actividad 2: Simulación del Game Loop  
> **Duración:** 15–20 min  
> **Objetivo:** Comprender el funcionamiento continuo del ciclo de juego.  
> **Desarrollo:**  
> Selecciona tres participantes para representar:
> 
> - Entrada (jugador)
> - Proceso (sistema)
> - Salida (pantalla)
> 
> Repite varias acciones para simular el ciclo continuo del videojuego.
> 
> **Ejemplo:**  
> Jugador: “Mover derecha”  
> Sistema: “Procesa movimiento”  
> Pantalla: “Personaje se mueve”  
> (Repetir varias veces para simular el bucle)

---

> [!success] Actividad 3: Construyendo el ciclo  
> **Duración:** 15–20 min  
> **Objetivo:** Representar el ciclo de juego como un proceso repetitivo.  
> **Desarrollo:**  
> Los participantes dibujan un ciclo (bucle) con flechas que conecten:  
> Entrada → Proceso → Salida → (regresa a Entrada)
> 
> Luego agregan un ejemplo propio.
> 
> **Ejemplo:**  
> Entrada: Presionar botón  
> → Proceso: Detecta acción  
> → Salida: Disparo  
> → Regresa al inicio

---

> [!important] Actividad 4: Detecta el ciclo en un videojuego  
> **Duración:** 15 min  
> **Objetivo:** Identificar el ciclo de juego en ejemplos reales.  
> **Desarrollo:**  
> Pide a los participantes que piensen en un videojuego y describan cómo se repite el ciclo constantemente.
> 
> **Ejemplo:**  
> Juego: Minecraft  
> Entrada: Mover personaje  
> Proceso: El mundo se actualiza  
> Salida: Movimiento en pantalla  
> → El ciclo se repite continuamente

---

> [!warning] Actividad 5: Ordena el ciclo  
> **Duración:** 10–15 min  
> **Objetivo:** Comprender la secuencia correcta del ciclo de juego.  
> **Desarrollo:**  
> Proporciona pasos desordenados del ciclo y pide organizarlos correctamente.
> 
> **Ejemplo:**
> 
> - Mostrar animación
> - Presionar tecla
> - Procesar acción
> 
> Orden correcto:  
> Presionar tecla → Procesar acción → Mostrar animación

---
---

## Actividad Integradora

> [!important] Actividad Integradora: Construyendo el diagrama de un videojuego  
> **Duración:** 25–30 min  
> **Objetivo:**  
> Representar el proceso completo de interacción en un videojuego mediante un diagrama, integrando los conceptos de Entrada–Proceso–Salida y el ciclo de juego.
> 
> **Desarrollo:**  
> El docente guía a las y los participantes en la elaboración de un diagrama que represente cómo funciona un videojuego desde que el jugador realiza una acción hasta que el sistema genera una respuesta.
> 
> **Pasos:**
> 
> 1. Elegir una acción dentro de un videojuego (ej. saltar, moverse, disparar).
> 2. Identificar:
>     - **Entrada:** acción del jugador (tecla, clic, control)
>     - **Proceso:** interpretación del sistema (reglas del juego)
>     - **Salida:** resultado en pantalla (animación, sonido, efecto)
> 3. Dibujar un diagrama que conecte estos elementos con flechas.
> 4. Convertir el diagrama en un **ciclo (bucle)** agregando la repetición del proceso.
> 5. El docente acompaña y retroalimenta durante la actividad.
> 
> **Herramientas sugeridas:**
> 
> - Papel y lápiz
> - Pizarrón
> - Herramientas digitales (draw.io, PowerPoint, Obsidian con Mermaid)
> 
> **Ejemplo:**  
> Entrada: Presionar tecla “espacio”  
> → Proceso: El sistema detecta salto  
> → Salida: El personaje salta  
> → El ciclo se repite continuamente
> 
> **Cierre:**  
> Cada participante o equipo explica su diagrama al grupo, destacando cómo se representa la interacción dentro del videojuego.

---
---

# Tema 2. Pensamiento lógico aplicado al juego
---

## 2.1 Secuencias

El **pensamiento lógico** es una habilidad fundamental en el desarrollo de videojuegos, ya que permite organizar ideas, tomar decisiones y estructurar acciones de manera ordenada. Dentro de este contexto, las **secuencias** representan uno de los conceptos más básicos e importantes, ya que consisten en ejecutar una serie de pasos en un orden específico para lograr un objetivo determinado.

En los videojuegos, las secuencias están presentes en prácticamente todas las acciones. Por ejemplo, para que un personaje realice un movimiento, el sistema debe seguir un orden lógico: recibir la entrada del jugador, procesar la acción y mostrar el resultado en pantalla. Si este orden se altera, el videojuego no funcionaría correctamente. Por ello, comprender las secuencias permite a las y los participantes entender cómo se construyen las mecánicas básicas de un juego.

La resolución de ejercicios de ordenamiento de acciones ayuda a desarrollar esta habilidad, ya que implica analizar situaciones y organizar correctamente los pasos necesarios para alcanzar un resultado. A través de estas actividades, los participantes fortalecen su capacidad de razonamiento, anticipación y estructuración lógica, sentando las bases para conceptos más avanzados como condicionales y ciclos en programación.

---

## Actividades propuestas

---

> [!info] Actividad 1: Ordena la secuencia  
> **Duración:** 10–15 min  
> **Objetivo:** Identificar el orden correcto de acciones en un proceso.  
> **Desarrollo:**  
> Proporciona una lista de acciones desordenadas relacionadas con un videojuego y pide a los participantes que las organicen correctamente.
> 
> **Ejemplo:**
> 
> - Mostrar animación
> - Presionar tecla
> - Procesar acción
> 
> Orden correcto:  
> Presionar tecla → Procesar acción → Mostrar animación

---

> [!tip] Actividad 2: Construye la secuencia  
> **Duración:** 15 min  
> **Objetivo:** Crear secuencias lógicas a partir de una acción del juego.  
> **Desarrollo:**  
> Pide a los participantes que elijan una acción de un videojuego y construyan la secuencia completa de pasos necesarios para ejecutarla.
> 
> **Ejemplo:**  
> Acción: Disparar  
> Secuencia:
> 
> 1. Presionar botón
> 2. Detectar entrada
> 3. Ejecutar acción
> 4. Mostrar disparo en pantalla

---

> [!success] Actividad 3: Secuencia incorrecta  
> **Duración:** 10–15 min  
> **Objetivo:** Detectar errores en el orden lógico de acciones.  
> **Desarrollo:**  
> Presenta secuencias con errores y pide a los participantes corregirlas.
> 
> **Ejemplo:**  
> Secuencia incorrecta:
> 
> 1. Mostrar animación
> 2. Presionar tecla
> 3. Procesar acción
> 
> Corrección:
> 
> 4. Presionar tecla
> 5. Procesar acción
> 6. Mostrar animación

---

> [!important] Actividad 4: Secuencia del mundo real  
> **Duración:** 15–20 min  
> **Objetivo:** Relacionar secuencias con situaciones cotidianas y videojuegos.  
> **Desarrollo:**  
> Pide a los participantes que describan una actividad cotidiana en forma de secuencia y luego la comparen con una acción en un videojuego.
> 
> **Ejemplo:**  
> Vida real:
> 
> 1. Encender consola
> 2. Abrir juego
> 3. Presionar “jugar”
> 
> Videojuego:
> 
> 4. Presionar botón
> 5. Detectar acción
> 6. Iniciar partida

---

> [!warning] Actividad 5: Secuencia visual  
> **Duración:** 15 min  
> **Objetivo:** Representar secuencias mediante esquemas o diagramas.  
> **Desarrollo:**  
> Los participantes dibujan una secuencia usando flechas o diagramas simples para representar el orden de acciones en un videojuego.
> 
> **Ejemplo:**  
> [Presionar tecla] → [Procesar acción] → [Mostrar resultado]

---
---

## 2.2 Condiciones

El **pensamiento lógico** en el desarrollo de videojuegos no solo implica ordenar acciones, sino también tomar decisiones. En este sentido, las **condiciones** permiten que el sistema evalúe una situación y determine qué acción ejecutar en función de un criterio específico. Estas decisiones se expresan comúnmente mediante estructuras del tipo **“si–entonces” (if–then)**, las cuales son fundamentales en la programación y en la lógica de los videojuegos.

En un videojuego, las condiciones están presentes en todo momento. Por ejemplo, si un personaje tiene suficiente energía, entonces puede correr; si colisiona con un enemigo, entonces pierde vida; si alcanza cierta puntuación, entonces avanza de nivel. Este tipo de estructuras permiten que el juego sea dinámico e interactivo, ya que responde de manera diferente dependiendo de las acciones del jugador y del estado del sistema.

La resolución de situaciones tipo “si–entonces” ayuda a las y los participantes a desarrollar habilidades de análisis y toma de decisiones. Al enfrentarse a distintos escenarios de juego, deben identificar condiciones, prever resultados y comprender cómo cambian las reglas según el contexto. Este tipo de pensamiento es clave para avanzar hacia la programación, donde las decisiones lógicas son esenciales para controlar el comportamiento de un sistema.

---

## Actividades propuestas

---

> [!info] Actividad 1: Completa la condición  
> **Duración:** 10–15 min  
> **Objetivo:** Comprender la estructura básica “si–entonces”.  
> **Desarrollo:**  
> Presenta enunciados incompletos y pide a los participantes que los completen con lógica correcta.
> 
> **Ejemplo:**
> 
> - Si el jugador presiona “espacio”, entonces ______
> - Si la vida llega a 0, entonces ______
> 
> Posibles respuestas:
> 
> - El personaje salta
> - El juego termina

---

> [!tip] Actividad 2: Crea tus propias condiciones  
> **Duración:** 15 min  
> **Objetivo:** Aplicar condiciones en situaciones de videojuego.  
> **Desarrollo:**  
> Pide a los participantes que inventen al menos tres situaciones tipo “si–entonces” dentro de un videojuego.
> 
> **Ejemplo:**
> 
> - Si el personaje recoge una moneda, entonces suma puntos
> - Si toca un enemigo, entonces pierde vida

---

> [!success] Actividad 3: Detecta la condición  
> **Duración:** 10–15 min  
> **Objetivo:** Identificar condiciones dentro de un escenario de juego.  
> **Desarrollo:**  
> Describe situaciones de un videojuego y pide a los participantes que identifiquen la condición y el resultado.
> 
> **Ejemplo:**  
> Situación: El personaje abre una puerta solo si tiene una llave
> 
> Respuesta:
> 
> - Condición: Tener llave
> - Resultado: La puerta se abre

---

> [!important] Actividad 4: Decisiones en cadena  
> **Duración:** 15–20 min  
> **Objetivo:** Comprender múltiples condiciones en secuencia.  
> **Desarrollo:**  
> Pide a los participantes que construyan una serie de decisiones encadenadas dentro de un videojuego.
> 
> **Ejemplo:**
> 
> - Si tiene llave → abre puerta
> - Si no tiene llave → busca llave
> - Si encuentra llave → regresa a la puerta

---

> [!warning] Actividad 5: Corrige la condición  
> **Duración:** 10–15 min  
> **Objetivo:** Identificar errores en estructuras condicionales.  
> **Desarrollo:**  
> Presenta condiciones incorrectas y pide a los participantes corregirlas.
> 
> **Ejemplo:**  
> Incorrecto:
> 
> - Si el personaje pierde toda la vida, entonces sigue jugando
> 
> Corrección:
> 
> - Si el personaje pierde toda la vida, entonces el juego termina

---
---

## 2.3 Repetición 

La **repetición** es un concepto clave dentro del pensamiento lógico y del desarrollo de videojuegos, ya que permite ejecutar una misma acción varias veces de manera continua o hasta que se cumpla una condición. En programación, este concepto se conoce como **ciclo o bucle**, y es fundamental para automatizar procesos y hacer que los sistemas funcionen de forma eficiente.

En los videojuegos, la repetición está presente constantemente. Por ejemplo, el movimiento continuo de un personaje, la aparición repetida de enemigos o la actualización constante del entorno forman parte de ciclos que se ejecutan varias veces por segundo. Esto está directamente relacionado con el **ciclo de juego (game loop)**, donde el sistema repite de forma continua las etapas de entrada, proceso y salida para mantener la interacción activa.

Los ejercicios de patrones repetitivos permiten a las y los participantes comprender cómo funcionan estos ciclos. A través de la simulación de acciones repetidas, es posible identificar secuencias que se repiten y entender bajo qué condiciones continúan o se detienen. Este tipo de actividades fortalece la capacidad de reconocer patrones, optimizar procesos y desarrollar una lógica estructurada, lo cual es esencial para avanzar hacia la programación de videojuegos.

---

## Actividades propuestas

---

> [!info] Actividad 1: Identifica el patrón  
> **Duración:** 10–15 min  
> **Objetivo:** Reconocer patrones repetitivos en acciones de videojuegos.  
> **Desarrollo:**  
> Presenta secuencias de acciones y pide a los participantes identificar cuál es el patrón que se repite.
> 
> **Ejemplo:**
> 
> - Mover → Disparar → Mover → Disparar → Mover → Disparar
> 
> Patrón: Mover → Disparar

---

> [!tip] Actividad 2: Simulación de repetición  
> **Duración:** 15–20 min  
> **Objetivo:** Comprender cómo funciona un ciclo mediante repetición de acciones.  
> **Desarrollo:**  
> Selecciona participantes para simular acciones repetitivas dentro de un videojuego (por ejemplo, caminar o atacar).  
> Repetirán la misma acción varias veces para representar un ciclo.
> 
> **Ejemplo:**  
> Acción: Caminar  
> → Paso → Paso → Paso → Paso (repetición continua)

---

> [!success] Actividad 3: Completa la repetición  
> **Duración:** 10–15 min  
> **Objetivo:** Comprender la lógica de continuidad en un patrón.  
> **Desarrollo:**  
> Proporciona secuencias incompletas y pide a los participantes que las continúen siguiendo el patrón lógico.
> 
> **Ejemplo:**
> 
> - Saltar → Disparar → Saltar → Disparar → ______
> 
> Respuesta: Saltar → Disparar

---

> [!important] Actividad 4: Crea tu propio ciclo  
> **Duración:** 15–20 min  
> **Objetivo:** Diseñar un ciclo repetitivo aplicado a un videojuego.  
> **Desarrollo:**  
> Pide a los participantes que creen una secuencia repetitiva que represente una acción dentro de un juego.
> 
> **Ejemplo:**
> 
> - Enemigo aparece → Se mueve → Desaparece → Enemigo aparece → …

---

> [!warning] Actividad 5: ¿Cuándo se detiene?  
> **Duración:** 10–15 min  
> **Objetivo:** Comprender que los ciclos pueden depender de una condición para detenerse.  
> **Desarrollo:**  
> Presenta ciclos y pide a los participantes identificar en qué momento deberían detenerse.
> 
> **Ejemplo:**
> 
> - Disparar continuamente → ¿Cuándo se detiene?
> 
> Respuesta: Cuando se acaba la munición o el jugador deja de presionar el botón

---
---

## Integración de secuencias , condiciones y repetición

La integración de **secuencias, condiciones y repetición** constituye la base del pensamiento lógico aplicado al desarrollo de videojuegos. Estos tres elementos no funcionan de manera aislada, sino que se combinan para construir sistemas interactivos capaces de responder a las acciones del jugador de forma coherente y dinámica. Las **secuencias** permiten establecer el orden de las acciones, las **condiciones** introducen la toma de decisiones y la **repetición** posibilita la ejecución continua de procesos dentro del juego.

En un videojuego, esta integración se observa constantemente. Por ejemplo, una acción simple como mover un personaje implica una secuencia (detectar entrada → procesar movimiento → mostrar resultado), una condición (si el personaje puede moverse, entonces avanza) y una repetición (el movimiento se mantiene mientras el jugador presione la tecla). De esta manera, el juego logra comportarse como un sistema dinámico que se adapta a diferentes situaciones y decisiones del usuario.

El desarrollo guiado de ejercicios integradores permite a las y los participantes aplicar estos conceptos de forma práctica, construyendo la lógica completa de un videojuego a partir de escenarios sencillos. A través de estas actividades, se fomenta la capacidad de analizar problemas, estructurar soluciones y comprender cómo interactúan los diferentes componentes de un sistema. Este enfoque no solo refuerza el aprendizaje, sino que también prepara a los participantes para avanzar hacia la programación, donde estos conceptos se implementan mediante estructuras de control más formales.

En conjunto, la integración de secuencias, condiciones y repetición representa un paso clave en la formación del pensamiento computacional, ya que permite entender cómo se diseñan y controlan los comportamientos dentro de un videojuego. Este conocimiento facilita la transición de la teoría a la práctica, sentando las bases para el desarrollo de aplicaciones más complejas y sistemas interactivos completos.

---

## Actividades propuestas

---

> [!important] Actividad 1: Construyendo la lógica completa  
> **Duración:** 20–25 min  
> **Objetivo:** Integrar secuencias, condiciones y repetición en una acción de videojuego.  
> **Desarrollo:**  
> Pide a los participantes que seleccionen una acción de un videojuego (moverse, saltar, disparar) y describan:
> 
> - La **secuencia** de pasos
> - Una **condición** que afecte la acción
> - Una **repetición** que mantenga el comportamiento
> 
> Finalmente, organizan todo en un flujo lógico.
> 
> **Ejemplo:**
> 
> - Secuencia: Presionar tecla → Detectar acción → Mover personaje
> - Condición: Si hay obstáculo → No avanzar
> - Repetición: Mientras se presione la tecla → Seguir moviéndose

---

> [!info] Actividad 2: Completa la lógica del juego  
> **Duración:** 15–20 min  
> **Objetivo:** Identificar y completar elementos faltantes en una lógica de videojuego.  
> **Desarrollo:**  
> Proporciona estructuras incompletas donde falten secuencias, condiciones o repeticiones.  
> Los participantes deben completarlas correctamente.
> 
> **Ejemplo:**
> 
> - Secuencia: Presionar botón → ______ → Mostrar disparo
> - Condición: Si no hay munición → ______
> - Repetición: Mientras el botón esté presionado → ______
> 
> Respuestas posibles:
> 
> - Procesar acción
> - No dispara
> - Disparar continuamente

---

> [!tip] Actividad 3: Simulación de videojuego  
> **Duración:** 20 min  
> **Objetivo:** Comprender la interacción de los tres elementos mediante simulación.  
> **Desarrollo:**  
> Divide a los participantes en roles:
> 
> - Entrada (jugador)
> - Lógica (proceso con condiciones)
> - Salida (pantalla)
> 
> Simulan varias acciones incorporando decisiones y repeticiones.
> 
> **Ejemplo:**
> 
> - Jugador: “Disparar”
> - Lógica: Si hay balas → dispara / si no → no hace nada
> - Salida: Animación de disparo
> - Repetición: Se repite mientras el jugador presione el botón

---

> [!success] Actividad 4: Diseña tu mini videojuego lógico  
> **Duración:** 25–30 min  
> **Objetivo:** Aplicar la lógica completa en el diseño de un juego simple.  
> **Desarrollo:**  
> En equipos, diseñan un mini videojuego describiendo:
> 
> - Secuencia principal
> - Condiciones del juego
> - Acciones repetitivas
> 
> Presentan su propuesta al grupo.
> 
> **Ejemplo:**  
> Juego: Esquivar obstáculos
> 
> - Secuencia: Mover → Detectar obstáculo → Reaccionar
> - Condición: Si toca obstáculo → pierde
> - Repetición: Obstáculos aparecen constantemente

---

> [!warning] Actividad 5: Detecta errores en la lógica  
> **Duración:** 15 min  
> **Objetivo:** Identificar inconsistencias en la lógica de un videojuego.  
> **Desarrollo:**  
> Presenta un flujo lógico con errores y pide a los participantes corregirlo considerando secuencia, condición y repetición.
> 
> **Ejemplo:**  
> Incorrecto:
> 
> - Mostrar animación → Presionar tecla → Procesar acción
> - Si pierde toda la vida → sigue jugando
> 
> Corrección:
> 
> - Presionar tecla → Procesar acción → Mostrar animación
> - Si pierde toda la vida → termina el juego

---
---

# Proyecto final
## Actividad integradora

 - Preguntar si se tiene un proyecto final o proponer uno 