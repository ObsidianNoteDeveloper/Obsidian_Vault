### Resultado del aprendizaje

Manipular información dentro de programas.

### Temas

- `let`
- `const`
- Tipos primitivos
- Strings
- Numbers
- Booleans
- Null y Undefined
- Conversión de tipos

### Proyecto FullStack

- Calculadora simple

### Proyecto Videojuegos

- Sistema de vida y puntaje

---
---

## Resultado del aprendizaje

Al finalizar este módulo, el estudiante será capaz de almacenar, modificar y manipular información dentro de programas JavaScript mediante el uso de variables y diferentes tipos de datos. También comprenderá cómo convertir datos entre distintos formatos y aplicará estos conocimientos en el desarrollo de aplicaciones web y videojuegos.

---

## Introducción

Todo programa necesita almacenar información para poder funcionar. Cuando un usuario escribe su nombre, cuando una calculadora realiza operaciones matemáticas o cuando un videojuego registra la cantidad de vidas y puntos de un jugador, se utilizan variables y tipos de datos.

Las variables permiten guardar información temporalmente dentro de la memoria del programa. Por otro lado, los tipos de datos determinan qué clase de información puede almacenarse y cómo puede ser utilizada.

En JavaScript, comprender el manejo de variables es uno de los primeros pasos para desarrollar aplicaciones dinámicas e interactivas.

---

## 1. Variables con `let`

Una variable es un espacio de memoria que almacena un valor. Dicho valor puede cambiar durante la ejecución del programa.

La palabra clave `let` se utiliza para declarar variables cuyo contenido puede modificarse posteriormente.

### Sintaxis

```JavaScript
let nombreVariable = valor;
```

#### Ejemplo

```JavaScript
let nombre = "Carlos";
let edad = 20;

console.log(nombre);
console.log(edad);
```

#### Resultado

```
Carlos
20
```

En este ejemplo se crean dos variables. La primera almacena un texto y la segunda almacena un número.


### Modificando variables

Una de las principales características de `let` es que permite cambiar el valor almacenado.

#### Ejemplo

```JavaScript
let puntos = 0;
console.log(puntos);

puntos = 100;
console.log(puntos);
```

#### Resultado

```
0
100
```

La variable comienza con el valor cero y posteriormente se actualiza a cien.

### Aplicación en videojuegos

Los videojuegos utilizan constantemente variables para almacenar información dinámica.

#### Ejemplo

```JavaScript
let vidas = 3;
let monedas = 0;
vidas = vidas - 1;
monedas = monedas + 10;
console.log("Vidas:", vidas);
console.log("Monedas:", monedas);
```

#### Resultado

```
Vidas: 2
Monedas: 10
```

Cada vez que el jugador recibe daño o recoge objetos, estas variables cambian.

---

## 2. Variables con `const`

Existen situaciones donde ciertos valores no deben modificarse durante la ejecución del programa. Para estos casos se utiliza la palabra clave `const`.

Una constante almacena un valor fijo que no puede ser reasignado posteriormente.

### Sintaxis

```JavaScript
const nombreConstante = valor;
```

#### Ejemplo

```JavaScript
const PI = 3.1416;
console.log(PI);
```

#### Resultado

```
3.1416
```

### Error al modificar una constante

```JavaScript
const PI = 3.1416;
PI = 5;
```

#### Resultado:

```
TypeError: Assignment to constant variable.
```

JavaScript genera un error porque las constantes no pueden cambiar.

### Aplicación en videojuegos

En un videojuego es común utilizar constantes para almacenar configuraciones generales.

```JavaScript
const VELOCIDAD_MAXIMA = 10;
const VIDAS_INICIALES = 3;
```

Estos valores sirven como referencia durante todo el desarrollo.

---

## 3. Tipos Primitivos

Los tipos primitivos representan los valores más básicos que JavaScript puede almacenar.

Los principales son:

|Tipo|Ejemplo|
|---|---|
|String|"Hola"|
|Number|25|
|Boolean|true|
|Undefined|undefined|
|Null|null|

### Identificando tipos

JavaScript proporciona el operador `typeof`.

#### Ejemplo

```JavaScript
console.log(typeof "Hola");
console.log(typeof 50);
console.log(typeof true);
```

> [!question]
`typeof` es un operador porque forma parte de la sintaxis del lenguaje y no se invoca como una función.

#### Resultado

```
string
number
boolean
```

Esto permite verificar el tipo de dato almacenado en una variable.

---

## 4. Strings

Los strings son cadenas de texto utilizadas para almacenar palabras, frases o caracteres.

Pueden escribirse utilizando comillas simples, dobles o invertidas.

#### Ejemplos

```JavaScript
let nombre = "Ana";
let ciudad = 'México';
```

### Concatenación

La concatenación consiste en unir textos.

#### Ejemplo

```JavaScript
let nombre = "Ana";
let saludo = "Hola " + nombre;
console.log(saludo);
```

#### Resultado

```
Hola Ana
```

---

### Plantillas Literales

Las plantillas literales permiten insertar variables dentro de cadenas de texto utilizando acentos graves.

#### Ejemplo

```JavaScript
let jugador = "Mario";
let puntos = 500;

console.log(`El jugador ${jugador} tiene ${puntos} puntos.`);
```

#### Resultado

```
El jugador Mario tiene 500 puntos.
```

---

### Aplicación en videojuegos

```JavaScript
let nombreJugador = "Link";
let nivel = 4;

console.log(`Jugador: ${nombreJugador}`);
console.log(`Nivel actual: ${nivel}`);
```

Estas técnicas son útiles para mostrar información en pantalla.

---

## 5. Numbers

Los números permiten realizar operaciones matemáticas.

JavaScript utiliza un único tipo numérico para enteros y decimales.

#### Ejemplos

```JavaScript
let edad = 18;
let precio = 199.99;
```

---

### Operadores aritméticos

|Operador|Función|
|---|---|
|+|Suma|
|-|Resta|
|*|Multiplicación|
|/|División|
|%|Módulo|
|**|Potencia|

#### Ejemplo

```JavaScript
let a = 10;
let b = 5;

console.log(a + b);
console.log(a - b);
console.log(a * b);
console.log(a / b);
```

#### Resultado

```
15
5
50
2
```

---

### Aplicación en videojuegos

```JavaScript
let experiencia = 0;

experiencia += 50;
experiencia += 100;

console.log(experiencia);
```

#### Resultado

```
150
```

La experiencia del jugador aumenta conforme realiza acciones.

---

## 6. Booleans

Los valores booleanos representan únicamente dos estados:

```JavaScript
true
false
```

Son fundamentales para la toma de decisiones.

#### Ejemplo

```JavaScript
let juegoActivo = true;

console.log(juegoActivo);
```

---

### Comparaciones

```JavaScript
console.log(10 > 5);
console.log(10 < 5);
```

#### Resultado

```
true
false
```

---

### Aplicación en videojuegos

```JavaScript
let tieneLlave = true;

console.log(tieneLlave);
```

Este valor puede utilizarse para decidir si un jugador puede abrir una puerta.

---

## 7. Null y Undefined

Estos valores representan ausencia de información, pero tienen significados diferentes.

---

### Undefined

Una variable declarada sin valor tiene el valor `undefined`.

#### Ejemplo

```JavaScript
let personaje;

console.log(personaje);
```

#### Resultado

```
undefined
```

---

### Null

`null` representa un valor vacío asignado intencionalmente.

#### Ejemplo

```JavaScript
let enemigo = null;

console.log(enemigo);
```

#### Resultado

```
null
```

---

### Diferencias

```JavaScript
let a;
let b = null;

console.log(a);
console.log(b);
```

Resultado:

```
undefined
null
```

---

### Aplicación en videojuegos

```JavaScript
let jefeFinal = null;
```

Esto puede indicar que el jefe aún no ha aparecido en la partida.

---

## 8. Conversión de Tipos

En muchas ocasiones es necesario transformar datos de un tipo a otro.

Por ejemplo, los formularios HTML suelen devolver texto aunque el usuario escriba números.

---

### Convertir String a Number

#### Ejemplo

```JavaScript
let edad = "20";

console.log(Number(edad));
```

#### Resultado

```
20
```

---

### Convertir Number a String

#### Ejemplo

```JavaScript
let puntuacion = 100;

console.log(String(puntuacion));
```

#### Resultado

```
"100"
```

---

### Convertir a Boolean

#### Ejemplo

```JavaScript
console.log(Boolean(1));
console.log(Boolean(0));
```

#### Resultado

```
true
false
```

---

### Problema común

```JavaScript
let numero1 = "10";
let numero2 = "5";

console.log(numero1 + numero2);
```

#### Resultado:

```
105
```

JavaScript concatena cadenas de texto en lugar de realizar una suma.

#### Solución

```JavaScript
let numero1 = Number("10");
let numero2 = Number("5");

console.log(numero1 + numero2);
```

#### Resultado:

```
15
```

---

# Proyecto FullStack: Calculadora Simple

### Objetivo

Crear una calculadora web capaz de sumar dos números introducidos por el usuario.

---

#### HTML

```HTML
<h1>Calculadora</h1>

<input type="number" id="numero1">
<input type="number" id="numero2">

<button onclick="sumar()">
    Sumar
</button>

<p id="resultado"></p>
```

---

#### JavaScript

```JavaScript
function sumar() {

    let numero1 =
        Number(document.getElementById("numero1").value);

    let numero2 =
        Number(document.getElementById("numero2").value);

    let resultado = numero1 + numero2;

    document.getElementById("resultado").textContent =
        "Resultado: " + resultado;
}
```

---

##### Conceptos aplicados

- Variables con `let`
- Tipo Number
- Conversión de tipos
- Manipulación del DOM
- Operaciones matemáticas

---

# Proyecto Videojuegos: Sistema de Vida y Puntaje

### Objetivo

Simular el sistema básico de estadísticas de un personaje.

---

#### Código

```JavaScript
let vidas = 3;
let puntaje = 0;

function recibirDanio() {

    vidas--;

    console.log(
        `Vidas restantes: ${vidas}`
    );
}

function ganarPuntos() {

    puntaje += 100;

    console.log(
        `Puntaje actual: ${puntaje}`
    );
}
```

---

#### Pruebas

```JavaScript
ganarPuntos();
ganarPuntos();

recibirDanio();
```

#### Resultado

```
Puntaje actual: 100
Puntaje actual: 200
Vidas restantes: 2
```