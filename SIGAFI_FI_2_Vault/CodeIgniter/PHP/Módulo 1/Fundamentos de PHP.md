PHP (Hypertext Preprocessor) es un lenguaje de programación orientado principalmente al desarrollo web del lado del servidor. Cuando un usuario accede a una página PHP, el servidor ejecuta el código y genera HTML que posteriormente es enviado al navegador. Antes de aprender frameworks como CodeIgniter o Laravel, es fundamental dominar los conceptos básicos del lenguaje, ya que todos los frameworks se construyen sobre ellos.

---

## 1. Variables

Las variables son espacios de memoria utilizados para almacenar información que puede cambiar durante la ejecución del programa.

En PHP todas las variables comienzan con el símbolo `$`.

```PHP
$nombre = "Juan";
$edad = 20;
```

En este ejemplo:

- `$nombre` almacena una cadena de texto.
- `$edad` almacena un número entero.

PHP es un lenguaje de tipado dinámico, lo que significa que no es necesario declarar el tipo de dato.

```PHP
$variable = "Hola";
$variable = 10;
$variable = true;
```

La misma variable puede almacenar diferentes tipos de datos durante la ejecución.

### Reglas para nombrar variables

Correcto:

```PHP
$nombre
$nombreCompleto
$_usuario
$edad2
```

Incorrecto:

```PHP
$2edad
$mi variable
$nombre-completo
```

### Interpolación de variables

PHP permite insertar variables directamente dentro de cadenas utilizando comillas dobles.

```PHP
$nombre = "Juan";
echo "Hola $nombre";
```

Resultado:

```
Hola Juan
```

Con comillas simples no funciona:

```PHP
echo 'Hola $nombre';
```

Resultado:

```
Hola $nombre
```

### Variables avanzadas

#### Variables variables

Permiten crear nombres de variables dinámicamente.

```PHP
$campo = "nombre";
$$campo = "Carlos";
echo $nombre;
```

Resultado:

```
Carlos
```

Aunque existen, rara vez se utilizan en aplicaciones modernas.

---
---

## 2. Constantes

Una constante almacena un valor que no puede modificarse después de ser definido.

### Definir constantes

```PHP
define("PI", 3.1416);
```

Uso:

```PHP
echo PI;
```

Resultado:

```
3.1416
```

### Constantes con const

Forma moderna:

```PHP
const IVA = 0.16;
echo IVA;
```

## Ejemplo práctico

```PHP
const DESCUENTO = 0.20;
$precio = 1000;
$total = $precio - ($precio * DESCUENTO);
echo $total;
```

Resultado:

```
800
```

---
---

## 3. Tipos de datos

PHP soporta múltiples tipos de datos.

### String

Representa texto.

```PHP
$nombre = "Juan";
$mensaje = "Bienvenido al sistema";
```

Ejemplo:

```PHP
$nombre = "Carlos";
echo "Hola $nombre";
```

Resultado:

```
Hola Carlos
```

### Integer

Representa números enteros.

```PHP
$edad = 25;
$cantidad = 100;
```

Ejemplo:

```PHP
$productos = 15;
$clientes = 20;
$total = $productos + $clientes;
echo $total;
```

Resultado:

```
35
```

### Float

Representa números decimales.

```PHP
$precio = 199.99;
$temperatura = 36.5;
```

Ejemplo:

```PHP
$radio = 5;
$area = 3.1416 * ($radio * $radio);
echo $area;
```

Resultado:

```
78.54
```

### Boolean

Representa verdadero o falso.

```PHP
$activo = true;
$eliminado = false;
```

Ejemplo:

```PHP
$esAdmin = true;
echo $esAdmin;
```

Resultado:

```
1
```

## Array

Permite almacenar múltiples valores.

```PHP
$colores = ["Rojo", "Verde", "Azul"];
```

Acceso:

```PHP
echo $colores[0];
```

Resultado:

```
Rojo
```

### Arrays asociativos

Muy utilizados en aplicaciones web.

```PHP
$usuario = [    
	"nombre" => "Juan",
    "edad" => 20,
    "correo" => "juan@gmail.com"
];
```

Acceso:

```PHP
echo $usuario["correo"];
```

Resultado:

```
juan@gmail.com
```

---

Un **array asociativo** es un arreglo donde cada elemento tiene un nombre (clave o key) en lugar de una posición numérica.

En un `array` normal (Array indexado) PHP asigna automáticamente índices numéricos:

```PHP
$usuario[0] = "Juan";  
$usuario[1] = 20;  
$usuario[2] = "juan@gmail.com";
```

En un **array asociativo** los índices tienen nombre:

```PHP
echo $usuario["correo"];
```

Un array asociativo se parece mucho a una ficha de información.

#### Agregar nuevos datos

```PHP
$usuario["telefono"] = "555-1234";
```

Resultado:

```PHP
[    
	"nombre" => "Juan",    
	"edad" => 20,    
	"correo" => "juan@gmail.com",    
	"telefono" => "555-1234"]      // Nuevo elemento 
```

#### Eliminar elementos

```PHP
unset($usuario["correo"]);
```

#### Recorrer un array asociativo

Con `foreach`.

```PHP
foreach($usuario as $clave => $valor)
{    
	echo $clave . ": " . $valor . "<br>";
}
```

Resultado:

```
nombre: Juan
edad: 20
correo: juan@gmail.com
```


### Visualizar en un servidor local

Con el comando: 

```BASH
php -S localhost:8000
```

```BASH
redgnar055@redgnar055-Latitude-E7470:~/Proyectos/php-curso$ php -S localhost:8000
[Mon Jun 15 11:08:35 2026] PHP 8.3.6 Development Server (http://localhost:8000) started
```

Acceder directamente al archivo:

```BASH
http://localhost:8000/hola.php
```


---
### Arrays multidimensionales

Muy comunes cuando se trabaja con bases de datos.

```PHP
$usuarios = [
    [
        "nombre" => "Juan",
        "edad" => 20
    ],
    [
        "nombre" => "Ana",
        "edad" => 22
    ]
];

echo $usuarios[1]["nombre"];
```

Resultado:

```
Ana
```

---

Un array multidimensional es un arreglo que contiene otros arreglos.

Visualmente:

```
Array
 ├── Array
 ├── Array
 └── Array
```

#### Ejemplo básico

```PHP
$usuarios = [    
	[        
		"nombre" => "Juan",        
		"edad" => 20    
	],    
	[        
		"nombre" => "Ana",        
		"edad" => 22    
	]
];
```

Observa la estructura:

```
$usuarios
│
├── Usuario 0
│   ├── nombre = Juan
│   └── edad = 20
│
└── Usuario 1
    ├── nombre = Ana
    └── edad = 22
```

#### Acceso a los datos

Primer usuario:

```PHP
echo $usuarios[0]["nombre"];
```

Resultado:

```
Juan
```

---
#### Obtener el tipo de dato

```PHP
$edad = 20;
echo gettype($edad);
```

Resultado:

```
integer
```

#### Conversión de tipos

```PHP
$numero = "100";
$total = (int)$numero + 50;
echo $total;
```

Resultado:

```
150
```

---
---

## 4. Operadores

Los operadores permiten realizar operaciones sobre variables.

### Operadores aritméticos

```PHP
$suma = 10 + 5;
$resta = 10 - 5;
$multiplicacion = 10 * 5;
$division = 10 / 5;
$modulo = 10 % 3;
```

Ejemplo:

```PHP
$precio = 1000;
$iva = 160;
$total = $precio + $iva;
echo $total;
```

Resultado:

```
1160
```

### Operadores de asignación

```PHP
$x = 10;

$x += 5;
$x -= 3;
$x *= 2;
$x /= 4;
```

Ejemplo:

```PHP
$saldo = 1000;
$saldo += 500;
echo $saldo;
```

Resultado:

```
1500
```

### Operadores de comparación

```PHP
10 == "10"
10 === "10"
10 != 5
10 > 5
10 < 5
```

Ejemplo:

```PHP
$edad = 18;
var_dump($edad >= 18);
```

Resultado:

```
bool(true)
```

---

`var_dump()` es una función de PHP utilizada para **inspeccionar variables**. Muestra:

- El tipo de dato.
- El valor almacenado.
- En arreglos y objetos, también muestra su estructura.

Es una de las herramientas más usadas para depurar (debuggear) programas.

---
### Diferencia entre == y ===

```PHP
var_dump(10 == "10");
```

Resultado:

```
true
```

```PHP
var_dump(10 === "10");
```

Resultado:

```
false
```

`===` compara valor y tipo de dato.

En aplicaciones reales se recomienda utilizar siempre `===`.

**Regla práctica para recordar**

- `==` → **"¿Tienen el mismo valor?"**
- `===` → **"¿Tienen el mismo valor y el mismo tipo?"**

### Operadores lógicos

```PHP
&&
||
!
```

Ejemplo:

```PHP
$usuarioActivo = true;
$esAdmin = true;

if ($usuarioActivo && $esAdmin) {
    echo "Acceso permitido";
}
```

---
---

## 5. Concatenación

La concatenación permite unir cadenas.

```PHP
$nombre = "Juan";
echo "Hola " . $nombre;
```

Resultado:

```
Hola Juan
```

### Concatenación múltiple

```PHP
$nombre = "Juan";
$apellido = "Pérez";

echo $nombre . " " . $apellido;
```

Resultado:

```
Juan Pérez
```

### Concatenación con variables numéricas

```PHP
$producto = "Laptop";
$precio = 15000;

echo "Producto: " . $producto . " Precio: $" . $precio;
```

Resultado:

```
Producto: Laptop Precio: $15000
```

### Operador .=

Permite agregar contenido a una cadena existente.

```PHP
$mensaje = "Hola";
$mensaje .= " Juan";
$mensaje .= " Bienvenido";

echo $mensaje;
```

Resultado:

```
Hola Juan Bienvenido
```


---
---

## Ejemplos Integradores (Nivel Medio-Avanzado)

---

### Ejemplo 1: Perfil de estudiante

```PHP
<?php

$nombre = "Carlos";
$edad = 21;
$carrera = "Ingeniería en Computación";
$promedio = 9.2;
$becado = true;

echo "<h2>Perfil del Estudiante</h2>";

echo "Nombre: " . $nombre . "<br>";
echo "Edad: " . $edad . "<br>";
echo "Carrera: " . $carrera . "<br>";
echo "Promedio: " . $promedio . "<br>";
echo "Becado: " . ($becado ? "Sí" : "No");
```

La línea:

```PHP
echo "Becado: " . ($becado ? "Sí" : "No");
```

Usa el **operador ternario**

Con el comando: 

```BASH
php -S localhost:8000
```

Acceder directamente al archivo:

```BASH
http://localhost:8000/perfilEstudiante.php
```


---

### Ejemplo 2: Sistema de ventas

```PHP
<?php
const IVA = 0.16;

$producto = "Laptop";
$precio = 15000;
$cantidad = 2;

$subtotal = $precio * $cantidad;
$impuesto = $subtotal * IVA;
$total = $subtotal + $impuesto;

echo "<h2>Ticket de Compra</h2>";
echo "Producto: $producto <br>";
echo "Cantidad: $cantidad <br>";
echo "Subtotal: $$subtotal <br>";
echo "IVA: $$impuesto <br>";
echo "Total: $$total";
```

---

### Ejemplo 3: Gestión de usuario

```PHP
<?php
$usuario = [
    "nombre" => "Juan",    
    "correo" => "juan@gmail.com",    
    "rol" => "Administrador",    
    "activo" => true
];

echo "<h2>Datos del Usuario</h2>";
echo "Nombre: " . $usuario["nombre"] . "<br>";
echo "Correo: " . $usuario["correo"] . "<br>";
echo "Rol: " . $usuario["rol"] . "<br>";
echo "Estado: " .
(    
	$usuario["activo"]    
	? "Activo"    
	: "Inactivo"
);
```

Este tipo de estructura es muy similar a los registros que posteriormente obtendrás desde MySQL.

