
**Estructura del taller RUTA 1: JavaScript → Desarrollo de Videojuegos Educativos Web *Módulo 1* (20 horas - 10 sesiones de 2 horas)**

### Índice

Descripción del Módulo 

[[#Tema 1. Arquitectura de un videojuego web]]
	[[#1.1 Componentes del videojuego]]
	[[#1.2 Archivo del videojuego]]
	[[#1.3 Escena inicial]]
	[[#1.4 Vinculación de lógica]]

[[#Tema 2. Primeros elementos interactivos del juego]]
	2.1 Interacción básica
	2.2 Mensajes dinámicos
	2.3 Depuración 

---
---

**(8 horas - 4 sesiones de 2 horas)**
# Tema 1. Arquitectura de un videojuego web

La arquitectura de un videojuego web representa la forma en que se organizan y conectan todos los elementos que permiten que un juego funcione dentro de un navegador. En el desarrollo de videojuegos con JavaScript, comprender esta estructura es fundamental, ya que un juego no solo consiste en dibujar personajes en pantalla, sino en coordinar sistemas como la lógica del juego, las entradas del jugador, las colisiones, el renderizado gráfico, el sonido y la administración de recursos. Generalmente, un videojuego web se construye utilizando HTML para definir la estructura de la página, CSS para controlar la apariencia visual y JavaScript para programar toda la lógica interactiva. Además, muchos juegos modernos utilizan el elemento `<canvas>` para dibujar gráficos en tiempo real y crear animaciones fluidas. Aprender la arquitectura de un videojuego permite desarrollar proyectos más organizados, escalables y fáciles de mantener, algo especialmente importante cuando los juegos comienzan a crecer en complejidad con múltiples enemigos, niveles, físicas y sistemas de puntuación.

---

## 1.1 Componentes del videojuego

Un videojuego web está compuesto por varios elementos que trabajan en conjunto para crear una experiencia interactiva dentro del navegador. Cuando un jugador abre un videojuego web, el navegador interpreta archivos HTML, CSS y JavaScript para construir el entorno del juego como ya se mencionó anteriormente. JavaScript administra toda la lógica del videojuego, incluyendo movimiento, colisiones, puntajes, enemigos y eventos del teclado o mouse.

Uno de los componentes más importantes en los videojuegos web es el área de renderizado gráfico. En muchos proyectos modernos se utiliza la etiqueta `<canvas>`, la cual funciona como una superficie de dibujo donde JavaScript puede pintar personajes, escenarios, efectos visuales y animaciones cuadro por cuadro. Este proceso ocurre constantemente mediante un **ciclo de actualización llamado _game loop_**, el cual permite que el juego responda en tiempo real a las acciones del jugador.

Otro componente esencial es el sistema de entrada del usuario. Este sistema detecta acciones como presionar teclas, mover el mouse o tocar la pantalla en dispositivos móviles. Gracias a esto, el jugador puede controlar personajes, disparar, saltar o interactuar con objetos dentro del videojuego. JavaScript escucha estos [[#eventos]] y ejecuta acciones específicas dependiendo de la lógica programada.

Los videojuegos también necesitan un sistema de lógica interna. Este componente administra reglas como la pérdida de vidas, el aumento de puntuación, la aparición de enemigos o la detección de colisiones. Por ejemplo, cuando un personaje toca un obstáculo, el sistema puede restar vida o terminar la partida.

Además, muchos videojuegos incluyen componentes multimedia como sonidos, música, animaciones y efectos visuales. Estos elementos ayudan a mejorar la experiencia del jugador y hacen que el juego sea más dinámico e inmersivo. Todo esto es procesado por el navegador utilizando los recursos del sistema del usuario.

Comprender cómo interactúan estos componentes permite desarrollar videojuegos más organizados y eficientes. En proyectos grandes, cada componente suele dividirse en módulos o archivos independientes para facilitar el mantenimiento y la escalabilidad del videojuego.

---

## 1.2 Archivo del videojuego

Todo videojuego web necesita una estructura organizada de archivos para funcionar correctamente. Aunque un proyecto pequeño puede contener pocas líneas de código, los videojuegos suelen crecer rápidamente al agregar personajes, enemigos, sonidos, niveles, animaciones y sistemas de puntuación. Por esta razón, es importante aprender desde el inicio cómo separar y organizar los archivos del proyecto.

En el desarrollo de videojuegos web, los archivos principales suelen dividirse según su función. El archivo HTML representa la estructura principal del videojuego y actúa como el punto de entrada que el navegador carga primero. Dentro de este archivo normalmente se coloca el elemento `<canvas>`, que funcionará como la pantalla del videojuego.

Por otro lado, los archivos CSS controlan la apariencia visual de la página. Aunque muchos videojuegos dibujan sus gráficos directamente en el canvas, CSS sigue siendo importante para configurar colores de fondo, márgenes, menús, pantallas de inicio y elementos de interfaz como botones o marcadores.

El componente más importante suele ser el archivo JavaScript. Aquí se programa toda la lógica del videojuego: movimiento de personajes, controles, físicas, colisiones, enemigos, animaciones y reglas del juego. En proyectos más avanzados, el código JavaScript puede dividirse en múltiples archivos especializados, por ejemplo:

- `player.js` para el jugador.
- `enemy.js` para enemigos.
- `controls.js` para controles.
- `game.js` para el ciclo principal del juego.

Además de los archivos principales, los videojuegos utilizan carpetas para organizar recursos multimedia como imágenes, sonidos y tipografías. Una estructura ordenada facilita el mantenimiento del proyecto y permite trabajar de manera más profesional.

Un ejemplo básico de estructura podría verse así:

```
mi_juego/
├── index.html
├── style.css
├── game.js
│
├── sprites/
│   ├── jugador.png
│   └── enemigo.png
│
├── sounds/
│   ├── salto.wav
│   └── musica.mp3
│
└── fonts/
```

**Explicación**
La estructura organiza los recursos según su tipo.
- `sprites/` guarda imágenes.
- `sounds/` almacena audio.
- `fonts/` contiene tipografías personalizadas.

Esta separación facilita el desarrollo y mantenimiento del videojuego.

Esta organización ayuda a localizar rápidamente cada componente del videojuego y evita mezclar recursos con código.

---

## 1.3 Escena inicial

La escena inicial es el primer entorno visual que aparece cuando un videojuego comienza. En los videojuegos web, esta escena funciona como la base donde posteriormente se colocarán personajes, enemigos, plataformas, fondos, interfaces y animaciones. Construir correctamente esta estructura es uno de los primeros pasos del desarrollo, ya que define el espacio donde ocurrirá toda la acción del juego.

En un videojuego desarrollado con JavaScript, la escena inicial generalmente se crea utilizando el elemento `<canvas>` de HTML. Este elemento actúa como una superficie de dibujo donde el programador puede representar gráficos, mover objetos y actualizar imágenes continuamente mediante código. El navegador interpreta el canvas como un área independiente dentro de la página web, permitiendo construir videojuegos interactivos directamente en el navegador sin necesidad de software externo.

La escena inicial también ayuda a establecer aspectos importantes del videojuego como la resolución, el tamaño de la ventana, los colores principales y la distribución visual del espacio de juego. Algunos videojuegos utilizan una escena fija, mientras que otros generan escenarios dinámicos o mapas más grandes que se desplazan conforme avanza el jugador.

Otro aspecto importante es el contenedor visual del videojuego. En muchos proyectos, el canvas se coloca dentro de un contenedor HTML que permite centrar el juego, agregar interfaces gráficas o adaptar el tamaño a diferentes dispositivos. CSS cumple un papel importante en esta etapa porque permite modificar colores, márgenes, fondos y alineaciones para mejorar la presentación visual del proyecto.

La escena inicial también representa el primer contacto entre el jugador y el videojuego. Por esta razón, muchos desarrolladores utilizan esta pantalla para mostrar títulos, instrucciones básicas o una pequeña introducción antes de iniciar la partida. Aunque en esta etapa el proyecto sea sencillo, la construcción correcta de la escena inicial servirá como base para todos los sistemas posteriores del videojuego.

---

## 1.4 Vinculación de lógica

En un videojuego web, la lógica y la interfaz trabajan de manera conjunta para crear una experiencia interactiva. La interfaz representa todo lo que el jugador puede observar en pantalla, como personajes, botones, fondos, menús y barras de vida. La lógica, por otro lado, corresponde al conjunto de instrucciones programadas en JavaScript que controlan el comportamiento del videojuego. Vincular ambos elementos significa lograr que las acciones internas del programa produzcan cambios visibles dentro del juego.

Cuando el jugador presiona una tecla, hace clic o interactúa con algún objeto, el navegador genera eventos que JavaScript puede detectar. A partir de estos eventos, la lógica del videojuego modifica variables internas y actualiza la interfaz gráfica. Por ejemplo, si el jugador presiona la flecha derecha, el sistema cambia la posición del personaje y posteriormente redibuja el objeto en una nueva ubicación dentro del canvas.

La vinculación de lógica también permite que el videojuego responda dinámicamente a diferentes situaciones. Un enemigo puede aparecer cuando el jugador alcanza cierta puntuación, una barra de vida puede disminuir después de una colisión o un mensaje puede mostrarse al finalizar la partida. Todo esto ocurre gracias a la conexión constante entre el estado interno del juego y los elementos visuales que aparecen en pantalla.

En videojuegos modernos, este proceso ocurre continuamente mediante un ciclo de actualización conocido como _[[#game loop]]_. Este ciclo ejecuta repetidamente la lógica del juego, actualiza variables y vuelve a renderizar la escena gráfica varias veces por segundo. Gracias a esto, el jugador percibe movimientos fluidos y respuestas inmediatas a sus acciones.

Comprender cómo conectar la lógica con la interfaz es fundamental porque representa la base de toda interacción dentro de un videojuego. Sin esta conexión, los elementos visuales permanecerían estáticos y el juego no podría responder a las acciones del usuario.

---

> [!success] Sintaxis del lenguaje

### Ejemplo de sintaxis de HTML para videojuegos

HTML se utiliza para crear la estructura principal del videojuego web.

```HTML
<!DOCTYPE html>
<html lang="es">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Mi Videojuego</title>
	<link rel="stylesheet" href="style.css">
</head>

<body>
	<div id="contenedorJuego">
		<canvas id="gameCanvas"></canvas>
	</div>
	<script src="game.js"></script>
</body>
</html>
```

El código presentado corresponde a la estructura básica de una página web creada con HTML. En el desarrollo de videojuegos para navegador, **este archivo funciona como el punto de partida del proyecto**, ya que define los elementos que aparecerán en pantalla y conecta otros recursos importantes, como los estilos visuales y la lógica del juego programada en JavaScript. HTML actúa como el esqueleto del videojuego: organiza las secciones, crea contenedores y establece la base sobre la cual trabajarán las demás tecnologías.

En las lineas:
```HTML
<!DOCTYPE html>
<html lang="es">
```

`<!DOCTYPE html>`, indica al navegador que el documento utiliza la versión moderna de HTML, conocida como HTML5. Esta declaración es importante porque permite que el navegador interprete correctamente las etiquetas y características actuales del lenguaje. Gracias a ello, herramientas modernas para videojuegos, como el elemento `<canvas>`, funcionan de manera adecuada.

Y la etiqueta `<html lang="es">` marca el inicio del documento HTML completo. El atributo `lang="es"` especifica que el contenido de la página está escrito en español. Esto ayuda a los navegadores, motores de búsqueda y tecnologías de accesibilidad a interpretar correctamente el idioma utilizado dentro del sitio.

Dentro del documento aparece la sección `<head>`:

```HTML
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Mi Videojuego</title>
	<link rel="stylesheet" href="style.css">
</head>
```

Contiene información interna sobre la página. Esta parte no muestra contenido visual directamente al usuario, pero es fundamental para configurar el funcionamiento del sitio. En proyectos de videojuegos, aquí se suelen definir configuraciones generales, enlaces a archivos externos y datos necesarios para que el navegador prepare correctamente la aplicación.

La línea `<meta charset="UTF-8">` establece el tipo de codificación de caracteres que utilizará la página. UTF-8 permite mostrar correctamente letras, símbolos y caracteres especiales, incluyendo acentos y signos propios del español. Sin esta configuración, algunos textos podrían mostrarse con errores visuales o caracteres extraños.

Posteriormente aparece `<meta name="viewport" content="width=device-width, initial-scale=1.0">`. Esta instrucción es especialmente importante en el desarrollo moderno porque adapta la página a diferentes tamaños de pantalla, como computadoras, tabletas y teléfonos móviles. En videojuegos web, esto ayuda a que la interfaz pueda visualizarse correctamente en distintos dispositivos.

La etiqueta `<title>Mi Videojuego</title>` define el nombre que aparecerá en la pestaña del navegador. Aunque parece un detalle pequeño, representa la identidad inicial del proyecto. Cuando un jugador abre el juego en su navegador, este título sirve para reconocer la aplicación entre otras pestaas abiertas.

Después se encuentra `<link rel="stylesheet" href="style.css">`. Esta línea conecta un archivo CSS externo llamado `style.css`. CSS es el lenguaje encargado de la apariencia visual de la página. En un videojuego, este archivo puede controlar colores, tamaños, posiciones de elementos, fondos, animaciones de interfaz y estilos generales del entorno visual. HTML crea la estructura, mientras que CSS le da presentación y diseño.

La sección `<body>`:

```HTML
<body>
	<div id="contenedorJuego">
		<canvas id="gameCanvas"></canvas>
	</div>
	<script src="game.js"></script>
</body>
```

Contiene todo el contenido visible de la página. Todo lo que el jugador podrá observar dentro del navegador se coloca dentro de esta parte. En proyectos de videojuegos, el `<body>` suele incluir el área de juego, menús, botones, indicadores de vida, puntaje y otros elementos interactivos.

Dentro del cuerpo aparece un `<div id="contenedorJuego">`. Un `<div>` funciona como un contenedor genérico que agrupa elementos relacionados. En este caso, el contenedor sirve para organizar el área principal del videojuego. El atributo `id="contenedorJuego"` le da un identificador único, permitiendo que CSS y JavaScript puedan localizar este elemento para modificarlo o aplicarle estilos específicos.

En el interior del contenedor se encuentra `<canvas id="gameCanvas"></canvas>`. El elemento `<canvas>` es una de las herramientas más importantes para crear videojuegos en HTML5. Funciona como una superficie de dibujo sobre la cual JavaScript puede generar gráficos, personajes, escenarios, animaciones y efectos visuales en tiempo real. A diferencia de otros elementos HTML tradicionales, el `<canvas>` comienza vacío; será el código JavaScript quien dibuje cada objeto del juego fotograma por fotograma.

Finalmente aparece `<script src="game.js"></script>`. Esta línea conecta un archivo JavaScript externo llamado `game.js`. Mientras HTML construye la estructura y CSS diseña la apariencia, JavaScript aporta la lógica y el comportamiento del videojuego. En este archivo normalmente se programa el movimiento de personajes, las colisiones, el sistema de puntaje, la detección de teclas y el game loop principal.

En conjunto, este código representa la base mínima de un videojuego web moderno. **HTML organiza la estructura general, CSS mejora la presentación visual y JavaScript convierte la página en una experiencia interactiva**. La combinación de estas tres tecnologías constituye el núcleo del desarrollo de videojuegos en navegador.

### Ejemplo de sintaxis de CSS para videojuegos

CSS controla la apariencia visual del juego.

```CSS
* {
	box-sizing: border-box;
	margin: 0;
	padding: 0;
}

body {
	margin: 0;
	background: #111;
	overflow: hidden;
}

#contenedorJuego {
	display: flex;
	justify-content: center;
	align-items: center;
	height: 100vh;
}

canvas {
	display: block;
	background: black;
	border: 4px solid white;
}
```

El código presentado pertenece al lenguaje CSS, utilizado para definir la apariencia visual de una página web. En el desarrollo de videojuegos para navegador, CSS cumple una función fundamental porque controla cómo se muestran los elementos en pantalla, cómo se posicionan y qué aspecto tendrá la interfaz del juego. Mientras HTML crea la estructura básica del proyecto, CSS transforma esa estructura en una experiencia visual organizada y atractiva.

La primera parte del código utiliza el selector universal `*`:

```CSS
* {
	box-sizing: border-box;
	margin: 0;
	padding: 0;
}
```

Este selector aplica reglas a absolutamente todos los elementos de la página. Dentro de este bloque aparecen tres propiedades importantes: `box-sizing`, `margin` y `padding`. Estas configuraciones suelen colocarse al inicio de muchos proyectos porque ayudan a mantener un comportamiento visual consistente en todos los navegadores.

La propiedad `box-sizing: border-box` modifica la forma en que el navegador calcula el tamaño de los elementos. Normalmente, el ancho y el alto de un elemento no incluyen bordes ni espacios internos, lo que puede provocar resultados inesperados al diseñar interfaces. Con `border-box`, el tamaño total del elemento incluye tanto el borde como el relleno interno, facilitando el control del diseño. En videojuegos web esto resulta útil para mantener alineados los contenedores, paneles y áreas de juego.

Las propiedades `margin: 0` y `padding: 0` eliminan los espacios externos e internos predeterminados que los navegadores agregan automáticamente a muchos elementos HTML. Sin esta limpieza inicial, podrían aparecer márgenes inesperados alrededor de la página o separaciones no deseadas entre componentes del juego. Este proceso suele conocerse como “**_reinicio de estilos_**” y ayuda a trabajar desde una base visual más controlada.

Posteriormente aparece el selector `body`:

```CSS
body {
	margin: 0;
	background: #111;
	overflow: hidden;
}
```

Representa el cuerpo completo de la página web. Todo el contenido visible del videojuego se encuentra dentro de esta sección. La propiedad `margin: 0` elimina nuevamente cualquier espacio externo alrededor del cuerpo de la página, permitiendo que el juego ocupe toda la ventana del navegador sin bordes blancos alrededor.

La línea `background: #111` establece un color de fondo oscuro para toda la página. El valor `#111` corresponde a un tono casi negro. Los videojuegos suelen utilizar fondos oscuros porque ayudan a resaltar los elementos gráficos del juego, como personajes, efectos o interfaces. Además, este tipo de color crea una sensación visual más cinematográfica y reduce distracciones fuera del área principal del juego.

La propiedad `overflow: hidden` controla lo que ocurre cuando algún elemento excede el tamaño visible de la pantalla. Con el valor `hidden`, cualquier contenido que sobresalga queda oculto y no aparecen barras de desplazamiento. En videojuegos esto es importante porque evita que el jugador pueda mover accidentalmente la página mientras juega, manteniendo la experiencia enfocada únicamente en el área interactiva.

Después aparece el selector `#contenedorJuego`:

```CSS
#contenedorJuego {
	display: flex;
	justify-content: center;
	align-items: center;
	height: 100vh;
}
```

El símbolo `#` indica que se está seleccionando un elemento mediante su [[#identificador]] único, en este caso el contenedor principal del videojuego. Este contenedor se utiliza para organizar y posicionar el área de juego dentro de la ventana del navegador.

La propiedad `display: flex` activa el sistema Flexbox, una herramienta moderna de CSS diseñada para alinear y distribuir elementos de manera flexible. Flexbox es muy utilizado en interfaces de videojuegos porque simplifica el centrado y acomodo de componentes visuales.

Las propiedades `justify-content: center` y `align-items: center` trabajan juntas para centrar el contenido tanto horizontal como verticalmente. Gracias a estas instrucciones, el elemento `<canvas>` aparece exactamente en el centro de la pantalla. Este tipo de alineación es común en videojuegos porque dirige la atención del jugador hacia el área principal de acción.

La línea `height: 100vh` indica que el contenedor ocupará el 100% de la altura visible de la ventana del navegador. La unidad `vh` significa “viewport height”, es decir, altura de la ventana visible. Esto permite que el contenedor cubra toda la pantalla disponible, independientemente del tamaño del monitor o dispositivo.

Finalmente aparece el selector `canvas`:

```CSS
canvas {
	display: block;
	background: black;
	border: 4px solid white;
}
```

Aplica estilos directamente al área donde se dibuja el videojuego. La propiedad `display: block` convierte el elemento en un bloque visual independiente. Esto evita pequeños espacios automáticos que algunos navegadores agregan alrededor de elementos gráficos.

La línea `background: black` establece un fondo negro dentro del área del juego. Aunque el cuerpo de la página ya posee un fondo oscuro, aquí se define específicamente el color del área de dibujo del videojuego. Esto permite diferenciar claramente el espacio jugable del resto de la interfaz.

Por último, `border: 4px solid white` crea un borde blanco de cuatro píxeles alrededor del canvas. Este borde ayuda a delimitar visualmente el área del videojuego, funcionando como un marco que separa el espacio interactivo del fondo general de la página. En muchos juegos clásicos, este tipo de borde también aporta una estética retro o arcade.

En conjunto, este código CSS prepara el entorno visual básico para un videojuego en navegador. El diseño centra el área de juego, elimina espacios innecesarios y crea una apariencia limpia y enfocada en la experiencia interactiva. Aunque el código es pequeño, contiene conceptos fundamentales que sirven como base para construir interfaces de videojuegos más complejas y profesionales.


### Ejemplo de sintaxis de JavaScript para videojuegos

JavaScript controla toda la lógica interactiva.

```JavaScript
// ── SETUP ────────────────────────────────────────────
const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");
canvas.width = 800;
canvas.height = 400;

// ── ESTADO ───────────────────────────────────────────
let x = 100;
const velocidad = 5;
const teclas = {};

// ── EVENTOS ──────────────────────────────────────────
document.addEventListener("keydown", (e) => { teclas[e.key] = true; });
document.addEventListener("keyup", (e) => { teclas[e.key] = false; });

// ── LOOP PRINCIPAL ────────────────────────────────────
function actualizar() {
	if (teclas["ArrowRight"] && x + 50 < canvas.width) x += velocidad; 
	if (teclas["ArrowLeft"] && x > 0) x -= velocidad;

	ctx.clearRect(0, 0, canvas.width, canvas.height);

	ctx.fillStyle = "white";
	ctx.font = "bold 28px 'Courier New'";
	ctx.fillText("MI VIDEOJUEGO", 240, 50);

	ctx.fillStyle = "red";
	ctx.fillRect(680, 170, 80, 50);

	ctx.fillStyle = "#4af";
	ctx.fillRect(x, 170, 50, 50);

	requestAnimationFrame(actualizar);
}

actualizar();
```

El código presentado corresponde a la base lógica de un videojuego desarrollado con JavaScript y el elemento `<canvas>` de HTML5. En un proyecto de videojuegos para navegador, JavaScript es el lenguaje encargado de controlar el comportamiento interactivo del juego: movimiento, animaciones, detección de teclas, actualización de objetos y renderizado de gráficos. Este programa crea un escenario simple donde un jugador puede desplazarse horizontalmente mientras el sistema redibuja constantemente la pantalla para simular movimiento en tiempo real.

La primera sección del código está identificada como “SETUP”:

```JavaScript
const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");
canvas.width = 800;
canvas.height = 400;
```

Esta etapa representa la preparación inicial del entorno gráfico del videojuego. La línea `const canvas = document.getElementById("gameCanvas");` obtiene el elemento `<canvas>` desde el documento HTML. El método `getElementById()` busca un elemento utilizando su identificador único. En este caso, JavaScript localiza el área de dibujo donde se mostrará el videojuego.

Posteriormente aparece `const ctx = canvas.getContext("2d");`. Esta línea obtiene el contexto de dibujo en dos dimensiones del canvas. El contexto funciona como un conjunto de herramientas gráficas que permite dibujar formas, texto, imágenes y animaciones dentro del área del juego. Sin este contexto, el canvas sería simplemente una superficie vacía sin capacidad de renderizar gráficos.

Las líneas `canvas.width = 800;` y `canvas.height = 400;` establecen el tamaño interno del área de juego. El canvas tendrá 800 píxeles de ancho y 400 píxeles de alto. En videojuegos, definir correctamente estas dimensiones es importante porque determina el espacio donde se moverán los personajes y objetos interactivos.

La siguiente sección se llama “ESTADO”:

```JavaScript
let x = 100;
const velocidad = 5;
const teclas = {};
```

En programación de videojuegos, el estado representa toda la información que cambia durante la ejecución del juego. Aquí se guardan posiciones, velocidades, puntajes, vidas y otros datos dinámicos.

La variable `let x = 100;` almacena la posición horizontal del jugador. El valor inicial de 100 significa que el personaje comenzará dibujado a 100 píxeles desde el borde izquierdo de la pantalla. La palabra `let` indica que el valor puede modificarse posteriormente durante el juego.

Después aparece `const velocidad = 5;`. Esta constante define la rapidez con la que el jugador se moverá cada vez que se presione una tecla de dirección. El uso de `const` indica que este valor permanecerá fijo durante toda la ejecución.

La línea `const teclas = {};` crea un [[#objeto]] vacío utilizado para registrar las teclas presionadas. Este objeto funciona como una pequeña memoria temporal del teclado. Cuando el jugador presiona una tecla, el programa guarda el estado correspondiente dentro de este objeto. Gracias a esto, el sistema puede **detectar múltiples teclas activas y mantener movimientos fluidos**.

La sección “EVENTOS”:

```JavaScript
document.addEventListener("keydown", (e) => { teclas[e.key] = true; });
document.addEventListener("keyup", (e) => { teclas[e.key] = false; });
```

Introduce uno de los conceptos más importantes de JavaScript: la programación basada en eventos. Un evento ocurre cuando el usuario interactúa con el sistema, por ejemplo, al presionar una tecla o mover el mouse.

La instrucción `document.addEventListener("keydown", (e) => { teclas[e.key] = true; });` agrega un detector de eventos al documento. El evento `"keydown"` se activa cuando una tecla es presionada. El parámetro `e` representa el evento generado y contiene información sobre la tecla utilizada. La expresión `teclas[e.key] = true` guarda el valor verdadero dentro del objeto `teclas`, indicando que esa tecla está siendo presionada.

De manera similar, `document.addEventListener("keyup", (e) => { teclas[e.key] = false; });` detecta cuando una tecla deja de presionarse. En ese momento, el programa cambia el estado de la tecla a falso. Este sistema permite controlar movimientos continuos en lugar de movimientos únicos y rígidos.

La función `actualizar()`:

```JavaScript
actualizar();
```

Contiene toda la lógica del videojuego. Dentro de ella se encuentran las instrucciones que revisan las teclas presionadas y modifican la posición del jugador.

`actualizar();` se encuentra en la última línea, inicia el loop principal por primera vez. A partir de ese momento, el juego comienza a actualizarse continuamente.

La sección más importante del programa corresponde al “LOOP PRINCIPAL”:

```JavaScript
function actualizar() {
	if (teclas["ArrowRight"] && x + 50 < canvas.width) x += velocidad; 
	if (teclas["ArrowLeft"] && x > 0) x -= velocidad;

	ctx.clearRect(0, 0, canvas.width, canvas.height);

	ctx.fillStyle = "white";
	ctx.font = "bold 28px 'Courier New'";
	ctx.fillText("MI VIDEOJUEGO", 260, 50);

	ctx.fillStyle = "red";
	ctx.fillRect(680, 170, 80, 50);

	ctx.fillStyle = "#4af";
	ctx.fillRect(x, 170, 50, 50);

	requestAnimationFrame(actualizar);
}

```

En videojuegos, un loop o bucle principal es una función que se ejecuta repetidamente muchas veces por segundo. Su función es actualizar el estado del juego y redibujar la pantalla constantemente para crear la ilusión de movimiento.

La línea `if (teclas["ArrowRight"] && x + 50 < canvas.width)` verifica si la flecha derecha está presionada y si el jugador todavía no ha llegado al borde derecho de la pantalla. La condición `x + 50 < canvas.width` toma en cuenta el tamaño del personaje, evitando que salga parcialmente del canvas.

Si la condición se cumple, se ejecuta `x += velocidad;`, lo que incrementa la posición horizontal del jugador. Esto produce el movimiento hacia la derecha.

La siguiente condición realiza el mismo proceso para la flecha izquierda. `if (teclas["ArrowLeft"] && x > 0)` verifica que el personaje no atraviese el borde izquierdo del canvas. Si la condición es válida, la posición disminuye mediante `x -= velocidad;`.

Posteriormente aparece `ctx.clearRect(0, 0, canvas.width, canvas.height);`. Esta instrucción limpia completamente el canvas antes de volver a dibujar la escena. En videojuegos, este proceso es esencial porque cada fotograma reemplaza al anterior. Si no se limpiara la pantalla, los objetos dejarían rastros visuales mientras se mueven.

Después del borrado, el programa comienza a renderizar nuevamente todos los elementos visibles. La línea `ctx.fillStyle = "white";` define el color blanco como color de dibujo actual. Luego `ctx.font = "bold 28px 'Courier New'";` configura la fuente y tamaño del texto.

La instrucción `ctx.fillText("MI VIDEOJUEGO", 240, 50);` dibuja el título del juego en la pantalla. Debido a que el canvas se limpia constantemente, _el texto debe redibujarse dentro del loop principal_ en cada [[#fotograma]].

Más adelante se dibuja el enemigo utilizando `ctx.fillStyle = "red";` y `ctx.fillRect(680, 170, 80, 50);`. La función `fillRect()` crea un rectángulo sólido utilizando coordenadas y dimensiones específicas. En este caso, el enemigo aparece como un bloque rojo estático.

Posteriormente se dibuja el jugador utilizando un color azul claro mediante `ctx.fillStyle = "#4af";`. La línea `ctx.fillRect(x, 170, 50, 50);` crea el rectángulo del personaje usando la posición almacenada en la variable `x`. Gracias a esto, el personaje cambia de lugar cuando la variable se modifica.

Finalmente aparece `requestAnimationFrame(actualizar);`. Esta función le pide al navegador ejecutar nuevamente la función `actualizar()` en el siguiente fotograma disponible. Este mecanismo crea el ciclo continuo que mantiene vivo al videojuego. En lugar de ejecutar el código una sola vez, el navegador lo repite constantemente, generando movimiento y animación fluida.

En conjunto, este programa representa una estructura clásica de desarrollo de videojuegos en JavaScript. Incluye preparación gráfica, manejo de estado, detección de entrada del jugador y un loop principal de renderizado. Aunque el ejemplo es sencillo, contiene los fundamentos esenciales sobre los cuales se construyen videojuegos mucho más complejos.

<div style="text-align: center;">
  <img src="Pasted image 20260527163508.png" width="500">
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 1</b>. Vista de la ejecución del programa "MI VIDEOJUEGO"
</div>



> [!success] Fin de la sintaxis del lenguaje


---
---

**(6 horas - 3 sesiones de 2 horas)**
# Tema 2. Primeros elementos interactivos del juego

En el desarrollo de videojuegos, la interacción es el elemento que transforma una simple animación en una experiencia jugable. Hasta este punto, el estudiante ya conoce la estructura básica de una página y algunos conceptos iniciales de programación; ahora comenzará a crear sistemas que reaccionen a las acciones del jugador. En este tema se introducen elementos fundamentales como botones, mensajes dinámicos y herramientas de depuración. Estos componentes son esenciales porque permiten controlar el flujo del juego, comunicar información al usuario y detectar errores durante el desarrollo. Comprender estos principios es importante no solo para videojuegos simples, sino también para proyectos más avanzados donde la interacción constante entre jugador y sistema define toda la experiencia.

## 2.1 Interacción básica 


## 2.2 Mensajes dinámicos


## 2.3 Depuración 


---
---

**(2 horas - 1 sesión de 2 horas)**
# Integración


---

**(2 horas - 1 sesión de 2 horas)**
# Práctica


---

**(2 horas - 1 sesión de 2 horas)**
# Evaluación





---
---


> [!quote] Glosario

### Glosario

#### Atributo

Un atributo es una característica o propiedad que pertenece a un objeto. En programación de videojuegos, los atributos permiten almacenar información relacionada con un elemento del juego, como la posición de un personaje, su velocidad, color o cantidad de vidas. En JavaScript, los atributos se acceden usando la notación de punto, por ejemplo: `jugador.vida`.

#### Comparación estricta

La comparación estricta es una operación que verifica si dos valores son exactamente iguales tanto en contenido como en tipo de dato. En JavaScript se utiliza el operador `===`. Esto es importante en videojuegos para evitar errores lógicos, por ejemplo al detectar teclas, estados del juego o colisiones.

Ejemplo:

```javascript
if (vidas === 0) {
    console.log("Game Over");
}
```

#### eventos

Los eventos son acciones que ocurren dentro del navegador o del videojuego y que el programa puede detectar y responder. Algunos ejemplos son presionar una tecla, mover el mouse, hacer clic o cargar una página. En videojuegos, los eventos permiten controlar personajes, disparar acciones o interactuar con el entorno.

Ejemplo:

```javascript
document.addEventListener("keydown", moverJugador);
```

#### fotograma

Un fotograma es cada imagen individual que se muestra en pantalla durante una animación o videojuego. Cuando muchos fotogramas se reproducen rápidamente, se genera la ilusión de movimiento. La velocidad de un videojuego suele medirse en FPS (_Frames Per Second_ o fotogramas por segundo).

#### Función anónima

Una función anónima es una función que no tiene nombre. Se utiliza frecuentemente como respuesta rápida a eventos o para ejecutar tareas específicas dentro del código. En videojuegos, es común usar funciones anónimas para manejar controles, temporizadores y animaciones.

Ejemplo:

```javascript
document.addEventListener("click", function() {
    console.log("Disparo");
});
```

#### game loop

El _game loop_ o “bucle principal del juego” es la estructura que mantiene funcionando un videojuego constantemente mientras está activo. Este ciclo normalmente actualiza la lógica del juego, procesa entradas del jugador y renderiza gráficos muchas veces por segundo.

Un _game loop_ básico realiza tres tareas:

1. Actualizar datos del juego.
    
2. Dibujar los elementos en pantalla.
    
3. Repetir el proceso continuamente.

#### identificador

Un identificador es el nombre que se le asigna a elementos del programa como variables, funciones, objetos o constantes. Los identificadores ayudan a reconocer y utilizar datos dentro del código.

Ejemplo:

```javascript
let puntuacion = 100;
```

Aquí `puntuacion` es el identificador.

#### Método

Un método es una función que pertenece a un objeto. Los métodos permiten que un objeto realice acciones o comporte cierta lógica. En videojuegos, un personaje puede tener métodos para moverse, atacar o saltar.

Ejemplo:

```javascript
jugador.saltar();
```

#### objeto

Un objeto es una estructura que agrupa datos y comportamientos relacionados. Los objetos son fundamentales en JavaScript y en el desarrollo de videojuegos, ya que permiten representar elementos del juego como personajes, enemigos, proyectiles o escenarios.

Ejemplo:

```javascript
let jugador = {
    nombre: "Heroe",
    vida: 100
};
```

#### Píxeles

Los píxeles son las unidades más pequeñas que forman una imagen digital en pantalla. En videojuegos, las posiciones, tamaños y movimientos de los elementos suelen medirse en píxeles.

Ejemplo:

```javascript
x = 150;
y = 300;
```

Esto puede representar la posición de un personaje en la pantalla.

#### Renderizado

El renderizado es el proceso mediante el cual el navegador o motor gráfico dibuja los elementos visuales del videojuego en pantalla. Durante el renderizado se muestran personajes, fondos, efectos y animaciones.

#### Variable

Una variable es un espacio de memoria utilizado para almacenar información que puede cambiar durante la ejecución del programa. En videojuegos, las variables se usan para guardar datos como puntos, tiempo, vidas, posiciones y estados.

Ejemplo:

```javascript
let vidas = 3;
```



