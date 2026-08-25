
[[#Servidor]]


### Resultado del aprendizaje

Comprender qué es JavaScript y cómo se ejecuta en el navegador.

### Temas

- Historia de JavaScript
- ECMAScript
- Navegador y motor JavaScript
- Consola del navegador
- Vinculación con HTML
- Primer programa

### Proyecto

- “Hola Mundo” interactivo
- Mensaje dinámico en pantalla

---
---

## Resultado del aprendizaje

Al finalizar este módulo, el estudiante comprenderá qué es JavaScript, cómo funciona dentro del navegador y cuál es su papel en el desarrollo web moderno y en la creación de videojuegos interactivos.

---

# 1.1 ¿Qué es JavaScript?

JavaScript es un lenguaje de programación diseñado originalmente para agregar interactividad a las páginas web. Antes de su aparición, los sitios web eran documentos estáticos compuestos principalmente por texto e imágenes. Con JavaScript, las páginas comenzaron a reaccionar a las acciones del usuario, permitiendo botones interactivos, animaciones, formularios dinámicos, videojuegos y aplicaciones completas ejecutándose directamente en el navegador.

Actualmente, JavaScript es considerado uno de los lenguajes más importantes del mundo tecnológico. Su principal ventaja es que puede ejecutarse prácticamente en cualquier navegador moderno sin necesidad de instalar software adicional. Esto significa que un programa escrito en JavaScript puede funcionar en computadoras, teléfonos móviles y tabletas utilizando únicamente un navegador web.

JavaScript también es un lenguaje multipropósito. Aunque nació para el [[desarrollo web]], hoy se utiliza en [[servidores]], aplicaciones móviles, videojuegos, inteligencia artificial y automatización. Gracias a tecnologías modernas como [[Node.js]], JavaScript puede utilizarse tanto en el frontend como en el backend, convirtiéndose en un lenguaje FullStack.

En el desarrollo de videojuegos, JavaScript es ampliamente utilizado junto con la etiqueta `<canvas>` para crear gráficos, movimientos, colisiones y animaciones en tiempo real. Muchos juegos independientes y educativos funcionan completamente en el navegador utilizando este lenguaje.

---

# 1.2 Historia de JavaScript

JavaScript fue creado en 1995 por Brendan Eich mientras trabajaba en la empresa Netscape. El objetivo era desarrollar un lenguaje sencillo que permitiera agregar interacción a las páginas web de manera rápida.

Inicialmente, JavaScript fue desarrollado en apenas unos días y recibió diferentes nombres antes de adoptar su nombre actual. Aunque comparte parte de su sintaxis con el lenguaje Java, ambos son tecnologías diferentes. El nombre “JavaScript” fue principalmente una estrategia comercial debido a la popularidad de Java en aquella época.

Con el crecimiento de internet, JavaScript comenzó a expandirse rápidamente. Sin embargo, durante sus primeros años existieron diferencias entre navegadores, lo que provocaba que algunos programas funcionaran correctamente en ciertos navegadores y fallaran en otros.

Para resolver este problema se creó el estándar [[#1.3 ECMAScript|ECMAScript]], encargado de definir oficialmente cómo debe comportarse el lenguaje. Gracias a este estándar, JavaScript evolucionó hasta convertirse en una tecnología moderna y estable utilizada en millones de aplicaciones alrededor del mundo.

Actualmente, JavaScript es mantenido y actualizado constantemente, incorporando nuevas características que facilitan el desarrollo de software moderno.

---

# 1.3 ECMAScript

ECMAScript es el estándar oficial sobre el cual está basado JavaScript. Este estándar define las reglas, sintaxis y comportamientos que deben seguir los navegadores y motores de JavaScript.

Cuando se habla de versiones modernas como ES6, ES2020 o ES2023, realmente se está haciendo referencia a versiones del estándar ECMAScript. Cada nueva versión agrega mejoras al lenguaje, como nuevas estructuras, funciones modernas y herramientas que simplifican la programación.

Uno de los cambios más importantes ocurrió con ECMAScript 6 (ES6), lanzado en 2015. Esta versión introdujo características ampliamente utilizadas actualmente, entre ellas:

- `let` y `const`
- Funciones flecha
- Clases
- Módulos
- Template strings
- Promesas

Gracias a ECMAScript, JavaScript puede evolucionar de manera organizada y compatible entre distintos navegadores.

---

# 1.4 Navegador y motor JavaScript

Un navegador web es una aplicación capaz de interpretar páginas web. Entre los navegadores más populares se encuentran:

- Google Chrome
- Mozilla Firefox
- Microsoft Edge
- Safari

Dentro de cada navegador existe un componente llamado [[motor de JavaScript]]. Este motor es el encargado de leer, interpretar y ejecutar el código escrito por el programador.

Por ejemplo:

- Chrome utiliza el [[motor de JavaScript#motor V8|motor V8]].
- Firefox utiliza [[motor de JavaScript#SpiderMonkey|SpiderMonkey]].
- Safari utiliza [[motor de JavaScript#JavaScriptCore|JavaScriptCore]].

Cuando el navegador encuentra código JavaScript dentro de una página web, el motor lo procesa línea por línea y ejecuta las instrucciones correspondientes.

En videojuegos, este motor es el responsable de actualizar la posición de personajes, detectar colisiones, reproducir sonidos y ejecutar la lógica del juego en tiempo real.

---

# 1.5 La consola del navegador

La consola del navegador es una herramienta de desarrollo que permite ejecutar código JavaScript y observar resultados inmediatamente. Es uno de los entornos más importantes para aprender programación debido a que facilita experimentar y detectar errores.

La consola puede abrirse normalmente con la tecla:

```
F12
```

o utilizando:

```
Ctrl + Shift + I
```

Dentro de la consola es posible escribir instrucciones directamente. Por ejemplo:

```JavaScript
console.log("Hola Mundo");
```

La función `console.log()` permite mostrar información en pantalla dentro de la consola. Es ampliamente utilizada para depuración y aprendizaje.

Resultado:

```
Hola Mundo
```

La consola también permite:

- Detectar errores
- Probar funciones
- Revisar variables
- Monitorear programas
- Analizar comportamiento de videojuegos

En el desarrollo profesional, la consola es una herramienta esencial para diagnosticar problemas y verificar el funcionamiento del código.

---

# 1.6 Vinculación de JavaScript con HTML

JavaScript normalmente se utiliza junto con HTML y CSS. HTML define la estructura de la página, CSS controla la apariencia visual y JavaScript agrega comportamiento e interactividad.

Para conectar JavaScript con una página HTML se utiliza la etiqueta `<script>`.

Ejemplo:

```HTML
<!DOCTYPE html>
<html>
<head>
    <title>Mi primera página</title>
    </head>
    <body>
        <h1>Bienvenido</h1>    
        <script>
            console.log("JavaScript conectado");
        </script>
	</body>
</html>
```

En este ejemplo, el navegador interpreta primero el contenido HTML y posteriormente ejecuta el código JavaScript incluido dentro de la etiqueta `<script>`.

También es posible separar el código JavaScript en archivos independientes utilizando la extensión `.js`.

Ejemplo:

```HTML
<script src="script.js"></script>
```

Esto permite organizar mejor los proyectos y reutilizar código en aplicaciones grandes o videojuegos complejos.

## [[Servidor]]

[[Servidor#Servidor Local|Servidor Local]]

```Bash
python3 -m http.server 
```

---

# 1.7 Primer programa en JavaScript

Tradicionalmente, el primer programa en cualquier lenguaje consiste en mostrar el mensaje “Hola Mundo”.

Ejemplo:

```
console.log("Hola Mundo");
```

Aunque parece sencillo, este programa introduce conceptos fundamentales:

- Instrucciones
- Texto
- Funciones
- Ejecución del programa

También puede mostrarse información directamente dentro de la página web utilizando HTML.

Ejemplo:

```HTML
<!DOCTYPE html>
<html>
<body>
	<h1 id="titulo"></h1>
	<script>
		document.getElementById("titulo").textContent = "Hola Mundo";
	</script>
</body>
</html>
```

En este caso, JavaScript busca un elemento HTML mediante su identificador y modifica su contenido dinámicamente.

Esta interacción entre HTML y JavaScript será la base para construir:

- Interfaces FullStack
- Menús interactivos
- Videojuegos
- Paneles administrativos
- Aplicaciones web modernas

---

# Proyecto del módulo

# “Hola Mundo” interactivo

## Objetivo

Crear una página web sencilla donde JavaScript modifique dinámicamente el contenido mostrado en pantalla.

---

# Estructura del proyecto

## Archivo HTML

```HTML
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Hola Mundo Interactivo</title>
</head>
<body>
    <h1 id="mensaje">Mensaje original</h1>
    <button onclick="cambiarMensaje()">
        Cambiar mensaje    
    </button>
    <script src="script.js"></script>
</body>
</html>
```

El siguiente bloque combina HTML con JavaScript para crear un botón interactivo dentro de una página web:

```HTML
<button onclick="cambiarMensaje()">
    Cambiar mensaje    
</button>
```

**Visión general**

El objetivo de este bloque es:

> Crear un botón que ejecute una función de JavaScript cuando el usuario haga clic sobre él.

### 1. `<button>`

```
<button>
```

La etiqueta `<button>` es un elemento HTML utilizado para crear botones interactivos en una página web.

El navegador interpreta esta etiqueta y dibuja visualmente un botón que el usuario puede presionar con el mouse, el teclado o incluso mediante pantallas táctiles.

Un botón funciona como un disparador de acciones. Su propósito es permitir que el usuario interactúe con la aplicación.

### 2. `onclick`

```HTML
onclick
```

`onclick` es un atributo HTML relacionado con eventos.

**Un evento es una acción que ocurre dentro del navegador**. Algunos ejemplos son:

|Evento|Acción|
|---|---|
|`click`|El usuario hace clic|
|`keydown`|El usuario presiona una tecla|
|`mousemove`|El mouse se mueve|
|`submit`|Se envía un formulario|

El atributo `onclick` significa literalmente:

> “Cuando ocurra un clic”.

El navegador permanece esperando interacción del usuario. Cuando detecta un clic sobre el botón:

1. Captura el evento.
2. Ejecuta el código indicado en `onclick`.
3. Actualiza la página si es necesario.

### 3. `="cambiarMensaje()"`

```
="cambiarMensaje()"
```

Aquí se especifica qué acción debe ejecutarse cuando ocurre el clic.

La función indicada es:

``` JavaScript
cambiarMensaje()
```

Esto significa:

> “Ejecuta la función llamada `cambiarMensaje`”.

### Relación con el DOM

Cuando el botón se presiona:

1. El navegador detecta el evento.
2. JavaScript interactúa con el DOM.
3. El contenido HTML puede modificarse dinámicamente.

Esto es la base de toda la interactividad moderna.

---

## Archivo JavaScript

```JavaScript
function cambiarMensaje(){
    document.getElementById("mensaje").textContent = "Bienvenido a JavaScript";
}
```

La línea:

```JavaScript
document.getElementById("mensaje").textContent = "Bienvenido a JavaScript";
```

es una instrucción muy importante en JavaScript porque permite modificar **dinámicamente el contenido de una página web**. Esta línea conecta directamente el código JavaScript con un elemento HTML visible en el navegador. Aunque parece pequeña, internamente realiza varios procesos.

### 1. `document`

```JavaScript
document
```

La palabra `document` representa toda la página web cargada en el navegador. Técnicamente, hace referencia al [[DOM]] (Document Object Model), que es una representación estructurada del documento HTML.

El navegador convierte el HTML en una especie de árbol de objetos que JavaScript puede manipular. Por ejemplo, si existe este HTML:

```HTMl
<h1 id="mensaje">Hola</h1>
```

el navegador crea internamente un objeto correspondiente a ese elemento `<h1>`.

JavaScript utiliza `document` para acceder a los elementos de la página.

Puede imaginarse como:

- La página web completa
- El entorno HTML cargado
- La puerta de entrada al DOM

---

### 2. `getElementById("mensaje")`

```JavaScript
getElementById("mensaje")
```

Esta parte significa:

> “Busca un elemento HTML cuyo identificador sea `mensaje`”.

Por ejemplo:

```HTML
<h1 id="mensaje">Hola</h1>
```

Aquí el atributo:

```HTML
id="mensaje"
```

funciona como una etiqueta única o nombre exclusivo para identificar el elemento.

### 3. `.textContent`

```JavaScript
.textContent
```

`textContent` es una propiedad del elemento HTML.

Esta propiedad controla el texto contenido dentro del elemento.

Por ejemplo:

```HTML
<h1 id="mensaje">Hola</h1>
```

El contenido textual es:

```
Hola
```

Entonces:

```JavaScript
elemento.textContent
```

permite:

- Leer el texto
- Cambiar el texto

### 4. El operador `=`

```JavaScript
=
```

El signo `=` es el operador de asignación.

Su función es almacenar un valor dentro de una variable o propiedad.

En este caso:

```
.textContent = "Bienvenido a JavaScript"
```

significa:

> “Reemplaza el texto actual por el nuevo texto”.

---

# Explicación del proyecto

El programa contiene un título y un botón. Cuando el usuario presiona el botón, JavaScript ejecuta la función `cambiarMensaje()`.

La función localiza el elemento HTML mediante su identificador (`mensaje`) y cambia el texto mostrado en pantalla. Este proceso demuestra cómo JavaScript puede modificar dinámicamente el contenido de una página web en tiempo real.

Este mismo principio es utilizado en:

- Interfaces FullStack
- Menús de videojuegos
- Sistemas de puntuación
- Inventarios
- HUDs
- Aplicaciones interactivas

---

# Actividad práctica

Realiza las siguientes modificaciones al proyecto:

## 1. Cambia el color del texto utilizando JavaScript.

Para cambiar el color de un texto utilizando JavaScript, se puede modificar la propiedad `style.color` de un elemento HTML. JavaScript primero localiza el elemento dentro de la página y después cambia dinámicamente su color en tiempo real.

### HTML

```HTML
<!DOCTYPE html>
<html lang="es">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Hola Mundo Interactivo</title>
</head>
<body>

	<h1 id="mensaje">Mensaje Original</h1>
	<button onclick="cambiarMensaje(), cambiarColor()">
		Cambiar mensaje y color
	</button>
	<script src="script1.js"></script>
	
</body>
</html>
```

### JavaScript

```JavaScript
function cambiarMensaje(){

	document.getElementById("mensaje").textContent = "Bienvenido a JavaScript";
	document.getElementById("mensaje").style.color = "blue";

}
```

La línea:

```JavaScript
document.getElementById("mensaje").style.color ="red";
```

#### `.style`

Permite acceder a los estilos CSS del elemento.

#### `.color`

Representa específicamente el color del texto.

#### Usar colores HEX

También pueden utilizarse códigos HEX:

```JavaScript
document.getElementById("mensaje").style.color ="#00FF00";
```

#### Usar RGB

```JavaScript
document.getElementById("mensaje").style.color ="rgb(255,0,0)";
```


## 2. Agrega un segundo botón para restaurar el mensaje original.

Para restaurar el mensaje original, se puede agregar un segundo botón que ejecute otra función de JavaScript. Esta nueva función devolverá el texto y el color iniciales del elemento HTML.

La idea general es la siguiente:

- El primer botón cambia el mensaje.
- El segundo botón restaura el estado original.

**Extra:** cuando presionas un botón, él mismo se oculta (`display: none`) y revela el otro (`display: inline-block`). Así siempre verás solo uno a la vez.
### HTML

```HTML

<body>

	<h1 id="mensaje">Mensaje Original</h1>
	
	<button id="btn1" onclick="cambiarMensaje()">
		Cambiar mensaje y color
	</button>
	
	<button id="btn2" onclick="restaurarMensaje()" style="display:none;">
		Restaurar mensaje
	</button>
	
	<script src="script1.js"></script>

</body>
```

### JavaScript

```JavaScript
function cambiarMensaje(){
	document.getElementById("mensaje").textContent = "Bienvenido a JavaScript";
	document.getElementById("mensaje").style.color = "blue";
	
	document.getElementById("btn1").style.display = "none";
	document.getElementById("btn2").style.display = "inline-block";
}

function restaurarMensaje(){
	document.getElementById("mensaje").textContent = "Mensaje original";
	document.getElementById("mensaje").style.color = "black";
	
	document.getElementById("btn2").style.display = "none";
	document.getElementById("btn1").style.display = "inline-block";
}
```

### CSS

```CSS
body {
	font-family: Arial, sans-serif;
	display: flex;
	flex-direction: column;
	align-items: center;
	padding: 40px;
	background-color: #f5f5f5;
}

h1 {
	color: black;
	margin-bottom: 20px;
}

button {
	margin: 5px;
	padding: 10px 20px;
	font-size: 16px;
	cursor: pointer;
	border: 1px solid #ccc;
	border-radius: 6px;
	background-color: white;
}

button:hover {
	background-color: #e0e0e0;
}
```

## 3. Muestra mensajes diferentes cada vez que se presione el botón.

### JavaScript

```JavaScript
function cambiarMensaje(){
	const mensajes = [
		"Bienvenido a JavaScript",
		"JavaScript es increíble",
		"Sigue practicando",
		"Ya casi eres un experto"
	];
	
	const colores = [
		"red",
		"blue",
		"green",
		"purple"
	];
	
	let numeroM = Math.floor(Math.random() * mensajes.length);
	let numeroC = Math.floor(Math.random() * colores.length);
	
	document.getElementById("mensaje").textContent = mensajes[numeroM];
	document.getElementById("mensaje").style.color = colores[numeroC];
	
	document.getElementById("btn1").style.display = "none";
	document.getElementById("btn2").style.display = "inline-block";
}
```

La línea:

```JavaScript
let numeroM = Math.floor(Math.random() * mensajes.length);
```

se utiliza para generar un número aleatorio que servirá como índice para seleccionar un elemento dentro del arreglo `mensajes`. Esta instrucción es muy común en JavaScript y aparece constantemente en videojuegos, aplicaciones interactivas y sistemas dinámicos.

La línea genera aleatoriamente uno de estos números:

```
0, 1, 2 o 3
```

#### `let numeroM`

```
let numeroM
```

`let` se utiliza para declarar una variable, y almacenará el número aleatorio generado.

#### `mensajes.length`

```
mensajes.length
```

La propiedad `.length` devuelve la cantidad de elementos que existen dentro del arreglo. Produce:

```
4
```

porque el arreglo contiene cuatro mensajes.

#### `Math.random()`

```
Math.random()
```

`Math.random()` genera un número decimal aleatorio entre:

```
0 y 1
```

pero sin incluir el 1.

Ejemplos posibles:

```
0.12
0.87
0.45
0.003
```

Cada vez que se ejecuta, el valor cambia.

#### `Math.random() * mensajes.length`

```
Math.random() * mensajes.length
```

Aquí el número aleatorio se multiplica por el tamaño del arreglo.

Como:

```
mensajes.length
```

vale:

```
4
```

el resultado será un decimal entre:

```
0 y 4
```

Ejemplos posibles:

|Random|Resultado|
|---|---|
|0.25|1.0|
|0.50|2.0|
|0.75|3.0|
|0.10|0.4|
#### `Math.floor()`

```
Math.floor()
```

`Math.floor()` elimina la parte decimal y redondea hacia abajo.

Ejemplos:

|Número|Resultado|
|---|---|
|3.9|3|
|2.1|2|
|0.8|0|


---

# Conclusión

JavaScript es el lenguaje que aporta dinamismo e interactividad al desarrollo web moderno. En este módulo se estudiaron sus orígenes, el funcionamiento dentro del navegador y la manera en que interactúa con HTML. También se introdujeron herramientas fundamentales como la consola del navegador y la manipulación básica del contenido de una página web.

Estos conocimientos representan la base para construir aplicaciones FullStack y videojuegos interactivos, ya que prácticamente toda experiencia moderna en la web depende del uso de JavaScript.