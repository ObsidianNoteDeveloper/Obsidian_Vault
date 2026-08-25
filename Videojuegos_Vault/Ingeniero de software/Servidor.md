
# Servidor Local

Un servidor local es un programa que permite compartir archivos o aplicaciones dentro de la propia computadora del usuario, simulando el funcionamiento de un servidor web real. Cuando se desarrolla una página web o una aplicación, muchas veces no basta con abrir un archivo HTML directamente desde una carpeta, ya que ciertas funciones modernas de JavaScript requieren ejecutarse mediante el protocolo HTTP, igual que ocurre en internet. Un servidor local crea precisamente ese entorno web dentro de la máquina del desarrollador, permitiendo que el navegador acceda a los archivos como si provinieran de un sitio web real.

El funcionamiento de un servidor local se basa en el modelo cliente-servidor. En este modelo, el navegador actúa como cliente y solicita recursos, mientras que el servidor responde enviando archivos como HTML, CSS, JavaScript, imágenes o audio. Cuando el usuario escribe una dirección como:

```
http://localhost:8000
```

el navegador envía una petición al servidor local, y este responde mostrando los archivos almacenados en la carpeta compartida. El término `localhost` hace referencia a la propia computadora del usuario, es decir, el servidor y el cliente están funcionando en la misma máquina.

El comando:

```
python3 -m http.server
```

utiliza el lenguaje Python para iniciar rápidamente un servidor web local. La parte `python3` ejecuta Python versión 3, mientras que la opción `-m` indica que se ejecutará un módulo interno de Python. En este caso, el módulo utilizado es `http.server`, el cual crea automáticamente un servidor HTTP sencillo sin necesidad de instalar software adicional.

Cuando el comando se ejecuta dentro de una carpeta, Python comparte todos los archivos contenidos en ese directorio. Después de iniciarlo, normalmente aparece un mensaje similar a:

```
Serving HTTP on 0.0.0.0 port 8000
```

Esto significa que el servidor está activo y escuchando peticiones en el puerto 8000. Un puerto puede entenderse como una puerta de comunicación utilizada por programas y servicios de red.

Para acceder al contenido, el usuario abre el navegador y escribe:

```
http://localhost:8000
```

Entonces el navegador mostrará los archivos disponibles dentro de la carpeta actual.

Este tipo de servidor local es muy utilizado en desarrollo web y videojuegos porque permite:

- Probar páginas web correctamente.
- Ejecutar proyectos JavaScript modernos.
- Cargar archivos JSON.
- Trabajar con Canvas y videojuegos.
- Simular un entorno real de internet.
- Evitar restricciones de seguridad del navegador.
- Compartir temporalmente proyectos dentro de una red local.

Por ejemplo, muchos videojuegos desarrollados con JavaScript necesitan cargar imágenes, sonidos o archivos externos mediante rutas HTTP. Si el proyecto se abre directamente desde un archivo local (`file://`), el navegador puede bloquear ciertos recursos por motivos de seguridad. Al utilizar un servidor local, el proyecto funciona igual que una aplicación web real.

En proyectos FullStack, los servidores locales también permiten probar APIs, bases de datos y sistemas backend antes de publicar una aplicación en internet. Aunque `python3 -m http.server` es un servidor sencillo y orientado al desarrollo básico, representa una excelente herramienta para principiantes debido a su facilidad de uso y porque viene incluida de manera predeterminada en Python.