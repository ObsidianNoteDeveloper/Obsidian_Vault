
Cuando trabajes con frameworks como Laravel o CodeIgniter, prácticamente todo estará basado en funciones y métodos, por lo que dominar este tema es indispensable.


# ¿Qué es una función?

Una función es un conjunto de instrucciones agrupadas bajo un nombre.

Ejemplo simple:

```PHP
<?php

function saludar()
{
    echo "Hola Mundo";
}

saludar();

?>
```

Salida:

```
Hola Mundo
```

La función no se ejecuta al ser creada.

Solo se ejecuta cuando la llamamos:

```
saludar();
```


## Función con parámetros 

```PHP
function saludar($nombre)
{
    echo "Hola $nombre";
}

saludar("Juan");
saludar("Ana");
```

Salida:

```
Hola Juan
Hola Ana
```

El parámetro cambia el comportamiento de la función.


## Parámetros obligatorios

```PHP
function crearUsuario($nombre, $correo)
{
    echo "Usuario: $nombre";
}

crearUsuario("Juan", "juan@gmail.com");
```


## Parámetros con valor por defecto

Permiten que un parámetro sea opcional.

```PHP
function saludar($nombre = "Invitado")
{
    echo "Hola $nombre";
}

saludar();
saludar("Carlos");
```


## Parámetros tipados

PHP moderno permite indicar qué tipo de dato debe recibir una función.

```PHP
function sumar(int $a, int $b)
{
    return $a + $b;
}

echo sumar(10, 5);
```


## Varios tipos de datos

```PHP
<?php

function registrarUsuario(
	string $nombre,
	int $edad,
	bool $activo
){
	echo "$nombre - $edad";
}

registrarUsuario("Juan", 25, true);

?>
```


## Return

El return es probablemente el concepto más importante de este módulo.

Muchos principiantes confunden: `echo` con `return`


### Echo

Muestra información.

```PHP
function sumar($a, $b)
{
    echo $a + $b;
}

sumar(5, 3);
```

Salida:

```
8
```

Pero no devuelve nada.

---

### Return

Devuelve un valor.

```PHP
function sumar($a, $b)
{
    return $a + $b;
}

$resultado = sumar(5, 3);

echo $resultado;
```

Salida:

```
8
```
