
En esta primera clase vamos a estudiar la **modificación del DOM con JavaScript**

Conceptos que vamos abordar en esta clase:

- Selección de elementos
- Eventos
- Atributos HTML
- Condiciones 
- Modificación del contenido de un elemento

---

# ¿Qué es el DOM (Document Object Model)?

El navegador convierte el HTML en una estructura de objetos que JavaScript puede consultar y modificar.

Por ejemplo:

```HTML
<input id="entrada">
<button>1</button>
<button>2</button>
```

JavaScript puede acceder a esos elementos y cambiar su comportamiento o contenido.

Una idea fundamental:

> [!Note]
> **HTML define la estructura, CSS define la apariencia y JavaScript puede modificar la estructura y el comportamiento de la página.**

---

# Seleccionar elementos del DOM

Dos formas diferentes de buscar elementos son:

### 1. `getElementById()`

```JavaScript
const entrada = document.getElementById("entrada");
```

Conceptos:

- **`document`**: Es un objeto de JavaScript que representa el documento HTML completo. Permite acceder y modificar los elementos que forman parte de la página.
	
- **`getElementById()`**: Es un método de `document` que permite buscar y obtener un elemento HTML utilizando el valor de su atributo `id`. Por ejemplo, `document.getElementById("entrada")`.
	
- **`id` en HTML**: Es un identificador único que se asigna a un elemento HTML para poder localizarlo fácilmente desde CSS o JavaScript. Por ejemplo: `<input id="entrada">`.
	
- **Referencia a un elemento**: Es una variable que guarda el acceso a un elemento del HTML. Esto permite trabajar con él posteriormente sin tener que buscarlo nuevamente. Por ejemplo: `const entrada = document.getElementById("entrada");`.
	
- **`const`**: Es una palabra reservada de JavaScript utilizada para declarar una variable cuyo valor no puede ser reasignado después de su creación. Se utiliza frecuentemente para guardar referencias a elementos del DOM.



Ejemplo:

```HTML
<input id="entrada">
```

```JavaScript
const entrada = document.getElementById("entrada");
```

Aquí `entrada` **no contiene el texto del input**. Contiene una referencia al elemento HTML.

Esto es muy importante para principiantes.

---

### 2. `querySelectorAll()`

```JavaScript
const botones = document.querySelectorAll(".hijo2 button");
```

`querySelector()`

Busca un solo elemento utilizando un selector CSS.

```JavaScript
document.querySelector("#entrada");
```

`querySelectorAll()`

Busca todos los elementos que coincidan con el selector.

```JavaScript
document.querySelectorAll(".hijo2 button");
```

El selector:

```CSS
.hijo2 button
```

significa:

> "Todos los elementos `button` que estén dentro de un elemento con clase `.hijo2`."

Esto permite relacionar **CSS Selectors + JavaScript**.

---

## Colecciones en JavaScript

Cuando trabajamos con el **DOM**, es común que necesitemos seleccionar no solamente un elemento HTML, sino **varios elementos al mismo tiempo**. Por ejemplo, en nuestro teclado podemos tener varios botones y queremos que todos respondan a un evento `click`.

Para esto JavaScript proporciona diferentes tipos de **colecciones**, entre ellas `NodeList`.


### 1. ¿Qué es una colección?

Una **colección** es un conjunto de elementos que podemos almacenar y recorrer desde JavaScript.

Por ejemplo, imaginemos este HTML:

```HTML
<button>1</button>
<button>2</button>
<button>3</button>
<button>4</button>
```

Si queremos obtener todos los botones, no tendría sentido buscarlos uno por uno. Podemos seleccionarlos todos mediante:

```JavaScript
const botones = document.querySelectorAll("button");
```

Ahora `botones` contiene una colección:

```
botón 1
botón 2
botón 3
botón 4
```

Es decir, la variable `botones` **no representa un solo botón**, sino un conjunto de botones.

---

### 2. ¿Qué es una `NodeList`?

Una **NodeList** es un tipo de colección que puede contener varios nodos del DOM.

Cuando utilizamos:

```JavaScript
document.querySelectorAll()
```

el resultado normalmente es una `NodeList`.

Por ejemplo:

```
const botones = document.querySelectorAll(".hijo2 button");

Si tenemos:

<div class="hijo2">

    <button>1</button>

    <button>2</button>

    <button>3</button>

    <button>4</button>

</div>

`querySelectorAll()` encuentra todos los elementos que coinciden con:

.hijo2 button

Por lo tanto:

botones

contiene:

NodeList

 ├── button

 ├── button

 ├── button

 └── button

Podemos comprobarlo con:

console.log(botones);

El navegador mostrará algo parecido a:

NodeList(4) [button, button, button, button]

---

# 3. `querySelectorAll()`

`querySelectorAll()` permite seleccionar **todos los elementos HTML que coincidan con un selector CSS**.

Por ejemplo:

const botones = document.querySelectorAll("button");

Selecciona todos los `<button>`.

También podemos utilizar clases:

const botones = document.querySelectorAll(".boton");

O combinaciones:

const botones = document.querySelectorAll(".hijo2 button");

Esto significa:

> "Busca todos los elementos `button` que estén dentro de un elemento que tenga la clase `.hijo2`."

---

# 4. Una NodeList puede contener varios elementos

Es importante diferenciar entre estas dos situaciones:

### Un solo elemento

const entrada = document.getElementById("entrada");

Aquí `entrada` representa **un solo elemento**:

entrada

   ↓

<input>

En cambio:

const botones = document.querySelectorAll(".hijo2 button");

representa **varios elementos**:

botones

   ↓

NodeList

   ├── button

   ├── button

   ├── button

   └── button

Esta diferencia es fundamental para entender por qué necesitamos **recorrer una colección**.

---

# 5. ¿Por qué necesitamos recorrer la colección?

Supongamos que tenemos:

<button>1</button>

<button>2</button>

<button>3</button>

Y queremos que **cada botón** responda cuando el usuario haga clic.

Tenemos:

const botones = document.querySelectorAll("button");

Ahora JavaScript tiene tres elementos.

Pero si escribimos:

botones.addEventListener("click", ...);

no funcionará como esperamos.

¿Por qué?

Porque `addEventListener()` pertenece a **cada elemento individual**, mientras que `botones` es una colección.

Tenemos que hacer:

NodeList

   ↓

recorrer

   ↓

button 1 → agregar evento

button 2 → agregar evento

button 3 → agregar evento

---

# 6. Recorrer una NodeList con `forEach()`

Una de las formas más sencillas de recorrer una `NodeList` es utilizando `forEach()`.

const botones = document.querySelectorAll(".hijo2 button");

  

botones.forEach(boton => {

    console.log(boton);

});

Aquí ocurre lo siguiente:

botones

   ↓

forEach()

   ↓

┌─────────────┐

│ botón 1     │

│ botón 2     │

│ botón 3     │

│ botón 4     │

└─────────────┘

`forEach()` toma cada elemento de la colección y ejecuta el código para ese elemento.

La variable:

boton

representa **el botón actual que se está recorriendo**.

---

# 7. Entendiendo `boton` dentro de `forEach()`

Este código:

botones.forEach(boton => {

    console.log(boton);

});

puede entenderse conceptualmente como:

Para cada botón dentro de botones:

  

    toma ese botón

  

    ejecuta:

        console.log(boton)

Por ejemplo:

Primera vuelta:

boton → <button>1</button>

  

Segunda vuelta:

boton → <button>2</button>

  

Tercera vuelta:

boton → <button>3</button>

La variable `boton` va cambiando en cada iteración.

---

# 8. Aplicándolo a eventos

Aquí es donde la `NodeList` se vuelve especialmente útil.

Podemos hacer:

const botones = document.querySelectorAll(".hijo2 button");

  

botones.forEach(boton => {

  

    boton.addEventListener("click", () => {

  

        console.log("Hiciste clic");

  

    });

  

});

El proceso sería:

querySelectorAll()

        ↓

obtiene todos los botones

        ↓

     NodeList

        ↓

    forEach()

        ↓

 ┌──────┼──────┐

 ↓      ↓      ↓

Botón  Botón  Botón

 1      2      3

 ↓      ↓      ↓

evento evento evento

De esta manera, **cada botón recibe su propio evento `click`**.

---

# 9. Ejemplo con tu teclado

En el código que estás utilizando:

const botones = document.querySelectorAll(".hijo2 button");

JavaScript busca todos los botones que se encuentran dentro de `.hijo2`.

Después:

botones.forEach(boton => {

recorre la colección.

Y finalmente:

boton.addEventListener("click", () => {

agrega un evento individual a cada botón.

Por lo tanto, si tienes:

<div class="hijo2">

  

    <button data-valor="1">1</button>

    <button data-valor="2">2</button>

    <button data-valor="3">3</button>

  

</div>

JavaScript realiza conceptualmente:

NodeList

   │

   ├── botón 1 → agregar click

   ├── botón 2 → agregar click

   └── botón 3 → agregar click

---

# 10. `NodeList` tiene posiciones

Una `NodeList` también permite acceder a sus elementos mediante un **índice**.

Los índices comienzan en `0`.

Por ejemplo:

const botones = document.querySelectorAll("button");

Si tenemos cuatro botones:

Índice       Elemento

  

  0     →    botón 1

  1     →    botón 2

  2     →    botón 3

  3     →    botón 4

Podemos acceder al primero:

botones[0]

Al segundo:

botones[1]

Y al tercero:

botones[2]

Esto es similar a trabajar con arreglos.

---

# 11. Propiedad `length`

También podemos conocer cuántos elementos contiene una `NodeList` utilizando:

botones.length

Por ejemplo:

const botones = document.querySelectorAll("button");

  

console.log(botones.length);

Si existen cinco botones, obtendremos:

5

Esto resulta útil cuando queremos saber cuántos elementos fueron encontrados.

---

# 12. `NodeList` no es exactamente un Array

Aquí aparece un concepto importante.

Una `NodeList` **se parece a un arreglo**, porque podemos hacer:

botones[0]

y:

botones.length

Sin embargo, **NodeList y Array son tipos diferentes**.

Por ejemplo:

const botones = document.querySelectorAll("button");

  

console.log(Array.isArray(botones));

El resultado será:

false

Porque `botones` es una `NodeList`, no un `Array`.

Aun así, las `NodeList` tienen algunos métodos que permiten trabajar fácilmente con sus elementos, como:

forEach()

---

# 13. `NodeList` y `HTMLCollection`

Otra colección que podemos encontrar cuando trabajamos con el DOM es `HTMLCollection`.

Por ejemplo:

const botones = document.getElementsByTagName("button");

En este caso obtenemos una `HTMLCollection`.

Mientras que:

const botones = document.querySelectorAll("button");

normalmente devuelve una `NodeList`.

Podemos resumirlo así:

|Método|Resultado|
|---|---|
|`getElementById()`|Un elemento|
|`querySelector()`|Un elemento|
|`querySelectorAll()`|`NodeList`|
|`getElementsByClassName()`|`HTMLCollection`|
|`getElementsByTagName()`|`HTMLCollection`|

Para comenzar a trabajar con el DOM, `querySelectorAll()` + `NodeList` + `forEach()` es una combinación muy útil.

---

# 14. NodeList y el DOM

Es importante entender que la `NodeList` **no crea nuevos botones**.

Los botones ya existen en el HTML.

JavaScript simplemente obtiene referencias a ellos.

Por ejemplo:

<button>1</button>

<button>2</button>

<button>3</button>

Después:

const botones = document.querySelectorAll("button");

Podemos visualizarlo así:

HTML

│

├── <button>1</button>

├── <button>2</button>

└── <button>3</button>

        │

        │ querySelectorAll()

        ↓

     NodeList

        │

        ├── referencia → botón 1

        ├── referencia → botón 2

        └── referencia → botón 3

Esto conecta directamente con el concepto anterior de **referencia a un elemento**.

---

# 15. Idea fundamental para explicar en clase

Una forma sencilla de explicarlo sería:

> **Cuando JavaScript necesita trabajar con varios elementos del DOM, puede obtener una colección de ellos. `querySelectorAll()` devuelve normalmente una `NodeList`, que contiene todos los elementos que coinciden con el selector indicado. Como la colección contiene varios elementos, podemos recorrerla con `forEach()` para realizar una acción individual sobre cada elemento.**

Por ejemplo:

const botones = document.querySelectorAll(".hijo2 button");

  

botones.forEach(boton => {

    boton.addEventListener("click", () => {

        console.log("Botón presionado");

    });

});

La idea que deberían quedarse es:

querySelectorAll()

        ↓

   NodeList

        ↓

    forEach()

        ↓

cada elemento

        ↓

modificar / escuchar / consultar

**En resumen:** `document` nos permite acceder al DOM, `querySelectorAll()` encuentra varios elementos, `NodeList` representa la colección obtenida y `forEach()` permite recorrer esa colección para trabajar con cada elemento individualmente.

