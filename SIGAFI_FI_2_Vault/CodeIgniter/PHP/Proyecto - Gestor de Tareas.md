# Task Manager

Al finalizar:

- Entender la sintaxis de PHP.
- Trabajar con formularios.
- Conectar PHP con MySQL.
- Aplicar CRUD (Crear, Leer, Actualizar, Eliminar).
- Organizar código en archivos.
- Entender MVC antes de llegar a CodeIgniter.
- Migrar fácilmente el proyecto a CodeIgniter 4.

---

# Módulo 0 - Preparación del entorno

## Objetivos

Instalar herramientas y comprender cómo funciona PHP.

### Temas

- ¿Qué es PHP?
- Cliente vs Servidor
- HTTP básico
- Instalar:
    - XAMPP
    - PHP
    - MySQL
    - VS Code
- [[Estructura de un proyecto PHP]]

### Ejercicio

Crear:

```
<?phpecho "Hola Mundo";
```

---

# Módulo 1 - Fundamentos de PHP

## Objetivos

Aprender la sintaxis básica.

### Temas

### Variables

```
$nombre = "Juan";$edad = 20;
```

### Constantes

```
define("PI", 3.1416);
```

### Tipos de datos

- string
- int
- float
- bool
- array

### Operadores

```
$suma = 5 + 3;
```

### Concatenación

```
echo "Hola " . $nombre;
```

---

## Práctica

Crear una página:

```
perfil.php
```

que muestre:

```
Nombre
Edad
Carrera
```

utilizando variables.

---

# Módulo 2 - Estructuras de Control

## Temas

### if

```
if($edad >= 18){    echo "Mayor de edad";}
```

### switch

```
switch($rol){    case "admin":        echo "Administrador";        break;}
```

### while

```
while($contador <= 10){    echo $contador;}
```

### for

```
for($i=1;$i<=10;$i++){    echo $i;}
```

### foreach

```
foreach($usuarios as $usuario){    echo $usuario;}
```

---

## Práctica

Mostrar una lista de tareas usando arrays.

```
$tareas = [    "Estudiar PHP",    "Practicar SQL",    "Aprender MVC"];
```

---

# Módulo 3 - Funciones

## Temas

### Crear funciones

```
function saludar($nombre){    return "Hola $nombre";}
```

### Parámetros

### Return

### Scope

---

## Práctica

Crear funciones:

```
agregarTarea()eliminarTarea()listarTareas()
```

---

# Módulo 4 - Formularios

Aquí comienza el proyecto real.

## Temas

### GET

```
$_GET
```

### POST

```
$_POST
```

### Formularios HTML

```
<form method="POST"></form>
```

### Validación

```
if(empty($_POST['nombre']))
```

---

## Proyecto

Formulario para crear tareas.

```
Nueva tarea
```

- Título
- Descripción

Guardar temporalmente en arrays.

---

# Módulo 5 - Arreglos Avanzados

## Temas

### Arrays asociativos

```
$tarea = [    'id' => 1,    'titulo' => 'Aprender PHP'];
```

### Arrays multidimensionales

```
$tareas = [   [      'id'=>1,      'titulo'=>'PHP'   ]];
```

---

## Proyecto

Convertir tareas simples en:

```
[    'id',    'titulo',    'descripcion',    'estado']
```

---

# Módulo 6 - Programación Orientada a Objetos

Muy importante para CodeIgniter.

## Temas

### Clase

```
class Usuario {}
```

### Propiedades

```
private $nombre;
```

### Métodos

```
public function saludar(){}
```

### Constructor

```
public function __construct(){}
```

### Encapsulación

### Herencia

### Polimorfismo (básico)

---

## Práctica

Crear:

```
class Tarea
```

Con:

```
idtitulodescripcionestado
```

---

# Módulo 7 - MySQL con PHP

## Objetivos

Persistir información.

### Temas

### MySQL

### CRUD

### PDO

Conexión:

```
$pdo = new PDO(    "mysql:host=localhost;dbname=taskmanager",    "root",    "");
```

---

## Proyecto

Crear tabla:

```
CREATE TABLE tareas(    id INT AUTO_INCREMENT PRIMARY KEY,    titulo VARCHAR(100),    descripcion TEXT,    estado VARCHAR(20));
```

---

Implementar:

- Crear tarea
- Listar tareas

---

# Módulo 8 - CRUD Completo

## Proyecto

### Create

Agregar tarea.

### Read

Listar tareas.

### Update

Editar tarea.

### Delete

Eliminar tarea.

---

Al terminar tendrás:

```
Task Manager v1
```

funcionando completamente.

---

# Módulo 9 - Organización de Archivos

## Problema

Todo el código está mezclado.

---

### Separar

```
project/
│
├── index.php
├── config/
├── controllers/
├── models/
├── views/
├── database/
└── assets/
```

---

Crear:

### Modelo

```
TareaModel.php
```

### Vista

```
listar.php
```

### Controlador

```
TareaController.php
```

---

Aquí aprenderás MVC manualmente.

---

# Módulo 10 - Preparación para CodeIgniter

Ahora compararemos nuestro proyecto con la estructura real de CodeIgniter 4.

## Nuestro MVC

```
controllers/models/views/
```

## CodeIgniter

```
app/
├── Controllers
├── Models
├── Views
```

Verás que la lógica es prácticamente la misma.

---

# Proyecto Final

## Sistema de Gestión de Tareas

Características:

### Usuarios

- Login simple
- Logout

### Tareas

- Crear
- Editar
- Eliminar
- Listar

### Estados

- Pendiente
- En proceso
- Terminada

### Base de Datos

MySQL

### Arquitectura

MVC