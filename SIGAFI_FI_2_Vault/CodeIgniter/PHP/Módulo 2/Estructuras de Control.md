
Las estructuras de control son uno de los pilares fundamentales de cualquier lenguaje de programación. Permiten que un programa tome decisiones, repita acciones y procese colecciones de datos de manera eficiente. Sin ellas, un programa ejecutaría las instrucciones de forma lineal sin posibilidad de reaccionar ante diferentes situaciones.

En PHP, las estructuras de control más utilizadas son:

- `if`
- `switch`
- `while`
- `for`
- `foreach`

Dominar estas estructuras es esencial para desarrollar aplicaciones web dinámicas, sistemas de autenticación, procesamiento de formularios, validación de datos y acceso a bases de datos.

---
---

## 1. Sentencia if

La estructura `if` permite ejecutar un bloque de código únicamente cuando una condición es verdadera.

### Sintaxis básica

```PHP
if($edad >= 18){
    echo "Mayor de edad";
}
```

#### Ejemplo

```PHP
<?php

$edad = 20;
if($edad >= 18){
    echo "Puede ingresar";
}
?>
```

Salida:

```
Puede ingresar
```

### if - else

Cuando necesitamos ejecutar una acción si la condición es verdadera y otra diferente si es falsa.

```PHP
<?php

$edad = 16;
if($edad >= 18){
    echo "Mayor de edad";
}else{
    echo "Menor de edad";
}
?>
```

Salida:

```
Menor de edad
```

## if - elseif - else

Permite evaluar múltiples condiciones.

```PHP
<?php

$calificacion = 85;
if($calificacion >= 90){
    echo "Excelente";
}
elseif($calificacion >= 80){
    echo "Muy bien";
}
elseif($calificacion >= 70){
    echo "Aprobado";
}
else{
    echo "Reprobado";
}
?>
```

Salida:

```
Muy bien
```

### Uso de operadores lógicos

PHP permite combinar condiciones mediante:

| Operador | Significado |
| -------- | ----------- |
| &&       | AND         |
| \|\|     | OR          |
| !        | NOT         |

### Ejemplo

```PHP
<?php

$usuario = "admin";
$password = "1234";
if($usuario == "admin" && $password == "1234"){
    echo "Acceso concedido";
}
?>
```

### Ejemplo nivel medio

Validación de acceso a una plataforma.

```PHP
<?php

$rol = "editor";
$activo = true;

if($activo && ($rol == "admin" || $rol == "editor")){
    echo "Puede acceder al panel";
}else{
    echo "Acceso denegado";
}
?>
```

---
---

## 2. Sentencia switch

Cuando existen muchas comparaciones contra una misma variable, `switch` suele ser más legible que varios `if`.

### Sintaxis básica

```PHP
switch($rol){
    case "admin":        
	    echo "Administrador";       
	    break;
}
```

### Ejemplo completo

```PHP
<?php

$rol = "editor";

switch($rol){
    case "admin":
        echo "Acceso total";        
        break;    
    case "editor":
        echo "Puede editar contenido";        
        break;
    case "usuario":
        echo "Puede visualizar contenido";        
        break;    
    default:        
	    echo "Rol no reconocido";
}
?>
```

### Agrupar casos

```PHP
<?php

$dia = "sabado";

switch($dia){
    case "sabado":    
    case "domingo":        
	    echo "Fin de semana";        
		break;    
	default:
        echo "Día laboral";
}
?>
```

### Ejemplo nivel medio

Menú de sistema.

```PHP
<?php

$opcion = 3;

switch($opcion){
    case 1:
        echo "Crear usuario";        
        break;    
    case 2:
        echo "Editar usuario";        
        break;    
    case 3:
        echo "Eliminar usuario";        
        break;    
    case 4:        
	    echo "Consultar usuarios";        
	    break;    
	default:        
		echo "Opción inválida";
}
?>
```

---
---

## 3. Ciclo while

El ciclo `while` ejecuta un bloque de código mientras la condición sea verdadera.

### Sintaxis básica

```PHP
while($contador <= 10){
    echo $contador;
}
```

### Ejemplo correcto

```PHP
<?php

$contador = 1;

while($contador <= 5){
    echo $contador . "<br>";    
    $contador++;
}
?>
```

Salida:

```
1
2
3
4
5
```

### Uso práctico

Procesar registros hasta alcanzar un límite.

```PHP
<?php

$pagina = 1;

while($pagina <= 3){
    echo "Procesando página $pagina <br>";    
    $pagina++;
}
?>
```

### Ejemplo nivel medio

Simulación de intentos de inicio de sesión.

```PHP
<?php

$intentos = 1;

while($intentos <= 3){
    echo "Intento número $intentos <br>";    
    $intentos++;
}
echo "Cuenta bloqueada";
?>
```

---
---

## 4. Ciclo for

Es ideal cuando conocemos cuántas veces debe repetirse una acción.

### Sintaxis

```PHP
for($i=1; $i<=10; $i++){
    echo $i;
}
```

### Componentes

```PHP
for(inicialización; condición; incremento)
```

### Recorrido descendente

```PHP
<?php

for($i=10; $i>=1; $i--){
    echo $i . "<br>";
}
?>
```

### Tabla de multiplicar

```PHP
<?php

$numero = 7;

for($i=1; $i<=10; $i++){
    echo "$numero x $i = " . ($numero * $i) . "<br>";
}
?>
```

### Ejemplo nivel medio

Generar usuarios ficticios.

```PHP
<?php

for($i=1; $i<=20; $i++){
    echo "usuario$i@gmail.com <br>";
}
?>
```

---
---

## 5. Ciclo foreach

Es la estructura más utilizada para recorrer arrays y resultados de consultas SQL.

### Sintaxis básica

```PHP
foreach($usuarios as $usuario){
    echo $usuario;
}
```

### Ejemplo simple

```PHP
<?php

$usuarios = [
    "Juan",    
    "Ana",    
    "Pedro"
];

foreach($usuarios as $usuario){
    echo $usuario . "<br>";
}
?>
```

### Obtener índice y valor

```PHP
<?php

$usuarios = [
    "Juan",    
    "Ana",    
    "Pedro"
];

foreach($usuarios as $indice => $usuario){
    echo "$indice => $usuario <br>";
}
?>
```

Salida:

```
0 => Juan
1 => Ana
2 => Pedro
```

### Recorrer arrays asociativos

Muy común en aplicaciones web.

```PHP
<?php

$usuario = [
    "nombre" => "Carlos",    
    "email" => "carlos@gmail.com",    
    "rol" => "admin"
];

foreach($usuario as $clave => $valor){
    echo "$clave : $valor <br>";
}
?>
```

### Ejemplo nivel medio

Procesar productos de una tienda.

```PHP
<?php

$productos = [
    [        
	    "nombre" => "Laptop",        
	    "precio" => 15000    
	],
    [        
	    "nombre" => "Monitor",        
	    "precio" => 4500   
	],
    [        
	    "nombre" => "Teclado",        
	    "precio" => 900    
	]
];

foreach($productos as $producto){
    echo "Producto: " . $producto["nombre"];
    echo " | Precio: $" . $producto["precio"];
    echo "<br>";
}
?>
```

# Comparación entre ciclos

| Ciclo   | Cuándo usarlo                                 |
| ------- | --------------------------------------------- |
| while   | No conocemos el número exacto de repeticiones |
| for     | Conocemos el número exacto de repeticiones    |
| foreach | Recorrer arrays o colecciones                 |

---
---

## Práctica Guiada

### Mostrar lista de tareas

Código base:

```PHP
<?php

$tareas = [
    "Estudiar PHP",    
    "Practicar SQL",    
    "Aprender MVC"
];

foreach($tareas as $tarea){
    echo $tarea . "<br>";
}
?>
```

Salida:

```
Estudiar PHP
Practicar SQL
Aprender MVC
```

### Práctica Nivel Medio

 Mostrar tareas numeradas.

```PHP
<?php

$tareas = [    
	"Estudiar PHP",    
	"Practicar SQL",    
	"Aprender MVC",    
	"Crear proyecto en Flask",    
	"Aprender MySQL"
];

foreach($tareas as $indice => $tarea){
    echo ($indice + 1) . ". " . $tarea . "<br>";
}
?>
```

Salida:

```
1. Estudiar PHP
2. Practicar SQL
3. Aprender MVC
4. Crear proyecto en Flask
5. Aprender MySQL
```

---

### Ejercicio Integrador

Este ejercicio combina `if`, `foreach` y arrays asociativos.

```PHP
<?php

$usuarios = [
    [
        "nombre" => "Carlos",        
        "edad" => 25    
    ],    
    [        
	    "nombre" => "Ana",        
	    "edad" => 17    
	],
	[   
		"nombre" => "Pedro",        
		"edad" => 30    
	]
];

foreach($usuarios as $usuario){
    if($usuario["edad"] >= 18){
        echo $usuario["nombre"] . " es mayor de edad <br>";    
    }else{
        echo $usuario["nombre"] . " es menor de edad <br>";    
	}
}
?>
```

Este tipo de lógica es prácticamente la misma que usarás más adelante cuando obtengas datos desde una base de datos MySQL y los muestres en aplicaciones desarrolladas con PHP, Laravel o CodeIgniter. El dominio de `if`, `switch`, `while`, `for` y `foreach` es fundamental antes de avanzar hacia funciones, programación orientada a objetos, formularios web y frameworks MVC.
