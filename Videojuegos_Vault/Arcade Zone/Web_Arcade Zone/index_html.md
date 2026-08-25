
HTML (HyperText Markup Language) es el lenguaje de marcado que permite estructurar el contenido de una página web. A diferencia de un lenguaje de programación, HTML no realiza cálculos ni toma decisiones; su función es describir qué elementos existen en una página y cuál es el significado de cada uno. Gracias a HTML, un navegador sabe qué texto corresponde a un título, qué parte representa un menú, dónde comienza una sección, cuál es un botón o qué archivo de JavaScript debe ejecutar.

---

## La estructura básica de un documento HTML

Todo documento HTML comienza con una estructura estándar que prácticamente todas las páginas web utilizan.

```HTML
<!DOCTYPE html>

<html lang="es">
```

La primera línea:

```HTML
<!DOCTYPE html>
```

no es realmente una etiqueta HTML. Se conoce como una **declaración de tipo de documento** (_Document Type Declaration_). Su función es indicar al navegador que el documento fue escrito utilizando la versión moderna de HTML, conocida simplemente como **HTML5**.

En versiones antiguas existían diferentes tipos de documentos, pero actualmente prácticamente todos los sitios web utilizan esta declaración.

Después aparece la etiqueta:

```HTML
<html lang="es">
```

La etiqueta `<html>` representa el elemento raíz del documento. Todo el contenido de la página debe encontrarse dentro de ella.

Aquí aparece un atributo muy importante:

```HTML
lang="es"
```

El atributo **lang** indica el idioma principal del documento.

En este caso:

- `es` significa Español.
- `en` significaría Inglés.
- `fr` Francés.
- `ja` Japonés.

Aunque el navegador puede mostrar la página sin este atributo, es una buena práctica incluirlo porque mejora la accesibilidad, ayuda a los lectores de pantalla y permite que los motores de búsqueda comprendan el idioma del sitio.

---

## Las dos grandes partes de una página HTML

Todo documento HTML posee dos grandes secciones: `<head>` y `<body>`

Estas dos etiquetas cumplen funciones completamente distintas.

Podemos imaginarlas como un libro.

El `<head>` sería toda la información administrativa del libro: el título, el autor, el idioma y otros datos que el lector normalmente no ve.

El `<body>` sería el contenido del libro, es decir, todo aquello que realmente observa el usuario.

---

## La sección `<head>`

El código contiene el siguiente bloque:

```HTML
<head>
```

Todo lo que se encuentra aquí sirve para configurar la página antes de que el navegador la muestre. Dentro encontramos varias etiquetas importantes.

### `<meta charset="UTF-8">`

```HTML
<meta charset="UTF-8" />
```

La etiqueta `<meta>` proporciona información adicional sobre la página. En este caso se utiliza el atributo: `charset="UTF-8`.

UTF-8 es un sistema de codificación de caracteres.

Gracias a él pueden mostrarse correctamente símbolos como:

```HTML
á é í ó ú ñ ¿ ¡ € ✓ 🕹️
```

Si esta línea no existiera, algunos caracteres especiales podrían aparecer como símbolos extraños.

### `<meta name="viewport">`

Después aparece:

```HTML
<meta name="viewport"
      content="width=device-width, initial-scale=1.0" />
```

Esta línea es fundamental para que la página sea adaptable a teléfonos y tabletas.

El atributo: `width=device-width`
Le indica al navegador que utilice el ancho real del dispositivo.

Mientras que: `initial-scale=1.0`
Establece el nivel inicial de zoom.

### La etiqueta `<title>`

```HTML
<title>Arcade Zone</title>
```

Esta etiqueta define el nombre que aparecerá en la pestaña del navegador. También es el título que normalmente utilizan los buscadores cuando muestran un sitio web. Es importante notar que el contenido del `<title>` no aparece dentro de la página.

---

## Vinculando recursos externos

Uno de los principios más importantes del desarrollo web consiste en separar responsabilidades.

-  HTML contiene la estructura.
-  CSS contiene el diseño.
-  JavaScript contiene el comportamiento.

Para lograr esa separación se utilizan enlaces hacia archivos externos.

### La etiqueta `<link>`

En este ejemplo aparecen dos.

La primera:

```HTML
<link
href="https://fonts.googleapis.com/..."
rel="stylesheet">
```

descarga tipografías desde Google Fonts.

La segunda:

```HTML
<link rel="stylesheet"
href="styles.css">
```

carga la hoja de estilos del proyecto. La etiqueta `<link>` no genera contenido visible. Simplemente le dice al navegador:
	_"Antes de mostrar la página, también carga este archivo."_

El atributo más importante es:

```HTML
rel="stylesheet"
```

que indica que el archivo enlazado corresponde a una hoja de estilos CSS.

---

## La sección `<body>`

Todo lo que aparece dentro del `<body>` será visible para el usuario.

En esta página encontramos cuatro grandes bloques:

- Encabezado.
- Carrusel.
- Ventana modal.
- Pie de página.

Cada uno utiliza etiquetas semánticas diferentes.

---

## Las etiquetas semánticas

HTML5 introdujo las llamadas **etiquetas semánticas**.

Antes era común construir toda una página utilizando únicamente: `<div>`

Sin embargo, esto hacía difícil comprender qué representaba cada sección. Actualmente existen etiquetas con significado propio.

Por ejemplo:

```HTML
<header>
<section>
<footer>
```

Estas etiquetas ayudan tanto a los desarrolladores como a los motores de búsqueda.

---

## El encabezado (`<header>`)

```HTML
<header>
    <h1>ARCADE ZONE</h1>    
    <p>
        Elige tu juego y presiona play    
    </p>
</header>
```

La etiqueta `<header>` representa la cabecera principal de la página. Dentro encontramos dos elementos. El primero:

```HTML
<h1>
```

es el encabezado de mayor importancia.

Los encabezados van desde: `<h1>` hasta `<h6>`
donde:
- `<h1>` representa el título principal.
- `<h2>` los subtítulos principales.
- `<h3>` las subsecciones.
- `<h4>` hasta `<h6>` representan niveles de menor jerarquía.

Después aparece:

```HTML
<p>
```

La etiqueta `<p>` significa **paragraph**. Representa un párrafo de texto. Es una de las etiquetas más utilizadas de todo HTML.

---

## La sección principal (`<section>`)

Después aparece:

```HTML
<section class="carousel-section">
```

La etiqueta `<section>` representa un bloque temático dentro del documento. No tiene apariencia propia. Su utilidad consiste en agrupar contenido relacionado. ==En este caso agrupa todo el carrusel de videojuegos==.

---

## El uso de `<div>`

Dentro de la sección encontramos varios elementos:

```HTML
<div>
```

La etiqueta `<div>` significa **division**. Es el contenedor genérico por excelencia. No tiene significado semántico. Su única función consiste en agrupar otros elementos para organizarlos o aplicarles estilos mediante CSS y manipularlos desde JavaScript.

En este ejemplo existen varios `<div>` porque el carrusel necesita una estructura jerárquica. Cada uno representa una capa diferente.

Por ejemplo:

```HTML
<div class="carousel-track-wrapper">
```

envuelve toda el área del carrusel.

Luego:

```HTML
<div class="carousel-track"id="track">
```

representa la pista donde JavaScript insertará dinámicamente las tarjetas de los juegos.

---

## Los atributos `class` e `id`

Este ejemplo utiliza constantemente: `class=""` e `id=""`. Aunque parecen similares, cumplen funciones diferentes.

Una **clase** puede repetirse muchas veces.

```HTML
class="ctrl-btn"
```

permite aplicar el mismo estilo a varios botones.

En cambio, un **id** debe ser único.

```HTML
id="track"
```

identifica un único elemento dentro de toda la página. JavaScript utiliza estos identificadores para localizar elementos específicos mediante funciones como:

```JavaScript
document.getElementById("track")
```

---

## Los botones

El carrusel posee:

```HTML
<button>
```

La etiqueta `<button>` crea un botón interactivo. Aquí existen dos botones. Uno retrocede: (`←`) y otro avanza: (`→`)

El contenido: `&#8592` es una entidad HTML. Representa una flecha hacia la izquierda. Mientras que `&#8594` corresponde a una flecha hacia la derecha.

---

## La importancia de `aria-label`

Cada botón posee:

```
aria-label="anterior"
```

o

```
aria-label="siguiente"
```

Los atributos que comienzan con `aria-` pertenecen al estándar **Accessible Rich Internet Applications (ARIA)** y mejoran la accesibilidad de la página. Permiten que tecnologías de asistencia, como los lectores de pantalla, describan correctamente elementos cuyo contenido visual por sí solo no resulta suficiente.

En este caso, el botón únicamente muestra una flecha. Un lector de pantalla no sabría si esa flecha significa avanzar, retroceder o realizar otra acción. Gracias a `aria-label`, el lector puede anunciar "anterior" o "siguiente", facilitando la navegación para personas con discapacidad visual.
