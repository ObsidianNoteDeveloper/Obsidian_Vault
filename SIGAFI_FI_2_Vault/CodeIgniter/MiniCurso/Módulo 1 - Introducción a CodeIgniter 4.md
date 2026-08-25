
## Objetivos

Al finalizar este módulo serás capaz de:

- Comprender qué es un framework y por qué se utiliza en el desarrollo profesional.
- Entender la arquitectura **MVC (Model-View-Controller)**.
- Conocer la estructura de carpetas de un proyecto en CodeIgniter 4.
- Comprender el flujo completo de una petición HTTP dentro del framework.
- Crear y ejecutar tu primer proyecto con CodeIgniter 4.

---

# ¿Qué es un Framework?

Cuando un desarrollador comienza a aprender PHP normalmente escribe todo el código en un solo archivo.

Por ejemplo:

```PHP
<?php

$conexion = new mysqli("localhost", "root", "", "empresa");

$resultado = $conexion->query("SELECT * FROM empleados");

while($fila = $resultado->fetch_assoc()){
    echo $fila["nombre"];
}
```

Este código funciona, pero conforme el proyecto crece aparecen muchos problemas:

- Código desordenado.
- Archivos enormes.
- Difícil mantenimiento.
- Mucha repetición de código.
- Poco seguro.
- Muy complicado trabajar en equipo.

Para solucionar estos problemas surgieron los **Frameworks**.

Un **Framework** es un conjunto de herramientas, librerías y reglas que proporcionan una estructura organizada para desarrollar aplicaciones.

En lugar de comenzar un proyecto desde cero, el framework ya incluye:

- Manejo de rutas.
- Seguridad.
- Conexión a base de datos.
- Sistema de plantillas.
- Validaciones.
- Manejo de sesiones.
- Carga automática de clases.
- Organización del proyecto.

En otras palabras:

> Un framework es una base sobre la cual construyes tu aplicación.

---

## Analogía

Imagina que construir una aplicación es como construir una casa.

### Sin Framework

Debes fabricar:

- ladrillos
- ventanas
- puertas
- tuberías
- electricidad
- techo

Todo desde cero.

---

### Con Framework

Ya tienes una casa con:

- paredes
- instalaciones eléctricas
- tuberías
- puertas
- ventanas

Tú solamente agregas lo que hace diferente a tu proyecto.

---

## Ventajas de utilizar un Framework

### Organización

Cada archivo tiene un lugar específico.

No existe el clásico proyecto con cientos de archivos PHP mezclados.

---

### Reutilización

Mucho código ya viene desarrollado.

Por ejemplo:

En lugar de escribir esto:

```PHP
session_start();

if(!isset($_SESSION["usuario"])){
    header("Location: login.php");
}
```

CodeIgniter posee clases especializadas para trabajar con sesiones.

---

### Seguridad

El framework ya protege contra muchos ataques.

Por ejemplo:

- SQL Injection
- Cross Site Scripting (XSS)
- CSRF
- Validación de datos
- Escape de caracteres

---

### Productividad

Muchas tareas comunes ya están implementadas.

Crear un CRUD completo puede tomar minutos.

---

### Escalabilidad

Es posible desarrollar proyectos grandes sin perder organización.

---

### Trabajo en equipo

Todos los desarrolladores conocen la misma estructura.

Eso facilita muchísimo el mantenimiento.

---

# ¿Por qué aprender CodeIgniter 4?

CodeIgniter es uno de los frameworks más ligeros del ecosistema PHP.

Sus principales ventajas son:

- Muy rápido.
- Fácil de aprender.
- Excelente documentación.
- Poco consumo de memoria.
- Arquitectura limpia.
- Muy utilizado para sistemas administrativos.
- Ideal para aprender MVC.

---

## Comparación con PHP puro

PHP puro

```
Todo mezclado

HTML
CSS
PHP
SQL
```

CodeIgniter

```
Controlador
↓
Modelo
↓
Base de Datos
↓
Vista
↓
Usuario
```

Cada componente tiene una responsabilidad específica.

---

# Arquitectura MVC

MVC significa:

**Model – View – Controller**

Es el patrón de arquitectura utilizado por CodeIgniter.

Su objetivo es separar responsabilidades.

---

## ¿Qué problema resuelve MVC?

Supongamos un sistema escolar.

Sin MVC:

```
index.php

Conexión BD
Consultas SQL
HTML
CSS
Validaciones
Sesiones
Lógica

Todo mezclado
```

Después de varios meses el archivo puede tener miles de líneas.

Modificar algo se vuelve complicado.

---

Con MVC:

```
Controlador
↓
Modelo
↓
Base de Datos
↓
Modelo
↓
Controlador
↓
Vista
↓
Usuario
```

Cada archivo hace solamente una tarea.

---

# Componentes del MVC

## Modelo (Model)

El Modelo es el encargado de trabajar con la base de datos.

No genera HTML.

No imprime información.

Su única responsabilidad es obtener y modificar datos.

Ejemplo:

```PHP
<?php

namespace App\Models;

use CodeIgniter\Model;

class UsuarioModel extends Model
{
    protected $table = 'usuarios';
    protected $primaryKey = 'id';
    protected $allowedFields = [
        'nombre',
        'correo'
    ];
}
```

El modelo sabe cómo acceder a la tabla.

---

Ejemplo de uso

```PHP
$modelo = new UsuarioModel();

$usuarios = $modelo->findAll();
```

No existe HTML.

Sólo obtiene información.

---

## Vista (View)

La Vista únicamente muestra información.

No realiza consultas SQL.

No contiene lógica complicada.

Ejemplo:

```PHP
<h1>Lista de usuarios</h1>
<ul>
<?php foreach($usuarios as $usuario): ?>
    <li><?= esc($usuario["nombre"]) ?></li>
<?php endforeach; ?>
</ul>
```

La vista solamente recibe datos y los presenta.

---

## Controlador (Controller)

Es el intermediario entre el usuario y la aplicación. 
- Recibe la petición. 
- Obtiene información del Modelo.
- Envía los datos a la Vista.

Ejemplo:

```PHP
<?php

namespace App\Controllers;
use App\Models\UsuarioModel;

class Usuarios extends BaseController
{
    public function index()
    {
        $modelo = new UsuarioModel();
        $datos["usuarios"] = $modelo->findAll();
        return view("usuarios/index", $datos);
    }
}
```

Observa que:
- El controlador **no hace consultas SQL directamente**.
- Tampoco genera HTML.
- Simplemente coordina todo.

---

# Flujo MVC

```
Usuario

↓

Controlador

↓

Modelo

↓

Base de Datos

↓

Modelo

↓

Controlador

↓

Vista

↓

Navegador
```

Cada componente tiene una responsabilidad clara.

---

# Estructura de carpetas

Una instalación típica de CodeIgniter 4 tiene la siguiente organización:

```
mi_proyecto/
├── app/
├── public/
├── writable/
├── tests/
├── vendor/
├── env
├── composer.json
└── spark
```

A continuación se describen las carpetas más importantes.

---

## app/

Es la carpeta más importante del proyecto.

Aquí desarrollarás prácticamente toda tu aplicación.

Contiene:

```
app/

Controllers/
Models/
Views/
Config/
Filters/
Helpers/
Libraries/
Database/
Language/
```

---

## Controllers/

Contiene los controladores.

Ejemplo:

```
Home.php
Usuarios.php
Productos.php
Login.php
```

Cada controlador responde a una o varias rutas.

---

## Models/

Aquí se encuentran los modelos.

Ejemplo:

```
UsuarioModel.php

ProductoModel.php

ClienteModel.php
```

Todos acceden a la base de datos.

---

## Views/

Aquí vive la interfaz.

Ejemplo:

```
inicio.php

usuarios.php

login.php

dashboard.php
```

Generalmente contienen:

- HTML
- Bootstrap
- CSS
- un poco de PHP

---

## Config/

Contiene toda la configuración del proyecto.

Por ejemplo:

```
App.php

Database.php

Routes.php

Filters.php
```

---

### Database.php

Configura la conexión con MySQL.

Ejemplo:

```
public array $default = [

'hostname' => 'localhost',

'username' => 'root',

'password' => '',

'database' => 'empresa',

'DBDriver' => 'MySQLi'

];
```

---

### Routes.php

Aquí se registran las rutas.

Ejemplo:

```
$routes->get('/', 'Home::index');

$routes->get('/usuarios', 'Usuarios::index');

$routes->post('/usuarios/guardar', 'Usuarios::guardar');
```

---

## public/

Es la única carpeta accesible desde el navegador.

Contiene:

```
index.php

css/

js/

images/
```

Todo inicia desde **public/index.php**, que es el _Front Controller_ de la aplicación.

---

## writable/

Aquí CodeIgniter guarda información generada durante la ejecución:

- logs
- caché
- sesiones
- archivos temporales
- archivos subidos (si así se configura)

Normalmente no se modifica manualmente.

---

## vendor/

Esta carpeta es creada automáticamente por Composer.

Aquí viven todas las dependencias del proyecto, incluyendo el propio framework.

Nunca se recomienda modificar su contenido.

---

## composer.json

Describe las dependencias del proyecto y permite instalar o actualizar paquetes con Composer.

---

## spark

Es una herramienta de línea de comandos incluida en CodeIgniter 4.

Permite ejecutar tareas como:

```
php spark serve
```

Inicia un servidor local.

---

```
php spark make:controller Usuarios
```

Crea un controlador.

---

```
php spark make:model UsuarioModel
```

Genera un modelo.

---

```
php spark migrate
```

Ejecuta migraciones de la base de datos.

---

# Flujo de una petición

Uno de los aspectos más importantes para dominar CodeIgniter es entender qué sucede cuando un usuario escribe una URL en su navegador.

Supongamos que el usuario visita:

```
http://localhost:8080/usuarios
```

El recorrido interno es el siguiente:

1. **El navegador** envía una petición HTTP al servidor.
2. La petición entra por **`public/index.php`**, que es el punto de entrada único de la aplicación.
3. CodeIgniter carga la configuración, inicializa los servicios y consulta el archivo de rutas (`app/Config/Routes.php`).
4. Si existe una ruta para `/usuarios`, el framework identifica el controlador y el método que debe ejecutar.
5. El **Controlador** recibe la petición y procesa la lógica necesaria.
6. Si requiere datos, el controlador llama al **Modelo**.
7. El **Modelo** realiza las consultas a la base de datos y devuelve los resultados.
8. El controlador prepara la información y la envía a una **Vista**.
9. La vista genera el HTML final.
10. El servidor responde al navegador, que renderiza la página al usuario.

El flujo puede representarse de la siguiente manera:

```
Usuario
   │
   ▼
Navegador
   │
   ▼
public/index.php
   │
   ▼
Routes.php
   │
   ▼
Controlador
   │
   ▼
Modelo
   │
   ▼
Base de Datos
   │
   ▼
Modelo
   │
   ▼
Controlador
   │
   ▼
Vista
   │
   ▼
HTML
   │
   ▼
Navegador
```

Comprender este ciclo es fundamental, ya que todas las solicitudes (consultas, registros, actualizaciones o eliminaciones) siguen esta misma lógica.

---

# Primer proyecto

Después de instalar CodeIgniter con Composer, puedes crear un nuevo proyecto con:

```
composer create-project codeigniter4/appstarter mi_primer_proyecto
```

Ingresa al directorio del proyecto:

```
cd mi_primer_proyecto
```

Inicia el servidor de desarrollo:

```
php spark serve
```

Si todo está correcto, verás un mensaje similar a:

```
CodeIgniter development server started on http://localhost:8080
```

Abre esa dirección en tu navegador y aparecerá la página de bienvenida de CodeIgniter.

---

## Crear un controlador

Desde la terminal:

```
php spark make:controller Bienvenida
```

Se generará el archivo:

```
app/
└── Controllers/
    └── Bienvenida.php
```

Edita el controlador:

```
<?php

namespace App\Controllers;

class Bienvenida extends BaseController
{
    public function index()
    {
        return "¡Hola desde mi primer controlador!";
    }
}
```

---

## Registrar una ruta

En `app/Config/Routes.php` agrega:

```
$routes->get('/bienvenida', 'Bienvenida::index');
```

Ahora, al visitar:

```
http://localhost:8080/bienvenida
```

el navegador mostrará:

```
¡Hola desde mi primer controlador!
```

---

## Crear una vista

Crea el archivo `app/Views/inicio.php`:

```
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Mi primer proyecto</title>
</head>
<body>

    <h1>Bienvenido a CodeIgniter 4</h1>

    <p>Mi primera vista utilizando el patrón MVC.</p>

</body>
</html>
```

Actualiza el controlador para devolver la vista:

```
<?php

namespace App\Controllers;

class Bienvenida extends BaseController
{
    public function index()
    {
        return view('inicio');
    }
}
```

Al acceder nuevamente a `http://localhost:8080/bienvenida`, el controlador cargará la vista y el navegador mostrará el contenido HTML generado.

---

# Buenas prácticas desde el inicio

A medida que desarrolles proyectos con CodeIgniter 4, procura seguir estas recomendaciones:

- Mantén la lógica de negocio en los modelos o servicios, no en las vistas.
- Utiliza los controladores para coordinar el flujo de la aplicación, evitando que acumulen demasiada lógica.
- Escapa los datos que se muestran al usuario utilizando `esc()` para prevenir vulnerabilidades XSS.
- Organiza las vistas en carpetas por módulo (`usuarios`, `productos`, `ventas`, etc.).
- Aprovecha Composer y el comando `spark` para generar componentes y administrar el proyecto.
- Comprende el ciclo completo de una petición antes de profundizar en características más avanzadas del framework.

---

# Resumen del módulo

En este primer módulo aprendiste que **CodeIgniter 4** es un framework que proporciona una estructura sólida para desarrollar aplicaciones PHP de manera profesional. Comprendiste cómo el patrón **MVC** divide las responsabilidades entre modelos, vistas y controladores, facilitando el mantenimiento y la escalabilidad del código.

También conociste la estructura de carpetas del proyecto, el recorrido que sigue una petición HTTP desde el navegador hasta la respuesta final y los pasos para crear un primer proyecto funcional. Estos conceptos constituyen la base sobre la que se construirán todos los módulos posteriores, donde comenzarás a desarrollar aplicaciones completas utilizando rutas, controladores, vistas, modelos y bases de datos.