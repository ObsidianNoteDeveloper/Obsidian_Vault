# Índice

1. Introducción  
2. Objetivo del sistema  
3. Requisitos de uso  
4. Descripción de la interfaz 
5. Ejecución de juegos 
6. Funcionalidades principales
7. Consideraciones y solución de problemas
8. Créditos  
9. Conclusiones  

---

## **Arcade Zone**

<div style="text-align: center;">  
<img src="Pasted image 20260425153352.png" width="900">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 1</b>. Interfaz principal.
</div>

---

### **1. Introducción**

Arcade Zone es una plataforma web interactiva diseñada para ofrecer una experiencia de juego accesible y atractiva mediante la integración de videojuegos desarrollados en Scratch. El sitio presenta una interfaz inspirada en el estilo arcade retro, permitiendo a los usuarios explorar diferentes juegos y ejecutarlos directamente desde el navegador sin necesidad de instalaciones adicionales.

> Para acceder a la plataforma, el usuario debe dirigirse a la siguiente dirección web:  
> [https://arcade-zone-055.netlify.app/](https://arcade-zone-055.netlify.app/)

---

### **2. Objetivo del sistema**

El objetivo principal de Arcade Zone es proporcionar un entorno intuitivo que facilite la navegación entre distintos videojuegos y permita su ejecución de manera inmediata. La plataforma está orientada tanto a usuarios casuales como a estudiantes o desarrolladores que deseen visualizar proyectos interactivos de forma dinámica.

---

### **3. Requisitos de uso**

Para garantizar un funcionamiento adecuado del sistema, se recomienda utilizar un navegador web actualizado como Google Chrome, Mozilla Firefox o Microsoft Edge, así como contar con una conexión estable a internet. El sitio está optimizado para distintos tamaños de pantalla, aunque se sugiere una resolución mínima de 1280x720 para una mejor experiencia visual.

---

### **4. Descripción de la interfaz**

La interfaz del sistema se divide en varias secciones claramente diferenciadas. En la parte superior se encuentra el encabezado, el cual muestra el título “ARCADE ZONE” acompañado de un mensaje introductorio que invita al usuario a seleccionar un juego. Esta sección cumple una función informativa y estética, reforzando la temática retro del sitio.

<div style="text-align: center;">  
<img src="Pasted image 20260425153528.png" width="400">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 2</b>. Encabezado con el titulo de la pagina web.
</div>

En la zona central se ubica el carrusel de juegos, que constituye el elemento principal de interacción. En este carrusel se presentan diversas tarjetas, cada una correspondiente a un videojuego. Cada tarjeta incluye el nombre del juego, una imagen representativa y un indicador visual que sugiere la acción de jugar. Adicionalmente, se incorpora un enlace que permite acceder directamente al proyecto original en la plataforma Scratch.

<div style="text-align: center;">  
<img src="2026-04-25_15-39.png" width="600">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 3</b>. 1) Tarjeta señalada, 2) Botón decorativo, al dar clic sobre la tarjeta el juego se ejecuta, 3) Enlace para acceder al proyecto en la plataforma de Scratch.
</div>


El carrusel puede ser controlado mediante botones de navegación, los cuales permiten desplazarse entre los juegos disponibles. También se incluyen indicadores visuales en forma de puntos que facilitan la navegación directa hacia un juego específico.

<div style="text-align: center;">  
<img src="Pasted image 20260425155047.png" width="400">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 4</b>. Botones y puntos de navegación. 
</div>

---

### **5. Ejecución de juegos**

Al seleccionar una tarjeta dentro del carrusel, el sistema despliega una ventana modal superpuesta que contiene el videojuego seleccionado. Inicialmente, se muestra un indicador de carga con el mensaje “CARGANDO JUEGO...”, tras lo cual el contenido se renderiza dentro de un marco embebido (iframe).

<div style="text-align: center;">  
<img src="Pasted image 20260425155724.png" width="500">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 5</b>. Ventana modal superpuesta. 
</div>

Dentro de esta ventana, el usuario puede interactuar con el juego utilizando los controles definidos en cada proyecto. Asimismo, se dispone de opciones adicionales, como la posibilidad de activar el modo de pantalla completa y un botón para cerrar la ventana. El sistema también permite cerrar el modal mediante la tecla Escape, proporcionando una alternativa rápida de navegación.

<div style="text-align: center;">  
<img src="2026-04-25_16-02.png" width="600">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 6</b>. 1) Modo pantalla completa, 2) Botón para cerrar la ventana, 3) Controles predeterminados de Scratch (iniciar y detener el juego). 
</div>
---

### **6. Funcionalidades principales**

Arcade Zone integra diversas funcionalidades que enriquecen la experiencia del usuario. Entre ellas destacan la navegación mediante carrusel interactivo, la carga dinámica de contenido, la integración directa con juegos de Scratch y el soporte para visualización en pantalla completa. Además, el diseño es responsivo, lo que permite su correcta visualización en dispositivos móviles y de escritorio.

El sistema también incorpora elementos visuales avanzados, como animaciones, efectos de iluminación tipo neón y una estética inspirada en videojuegos clásicos, lo que contribuye a una experiencia inmersiva.

---

### **7. Consideraciones y solución de problemas**

En caso de que el sistema no funcione correctamente, se recomienda verificar la conexión a internet y asegurarse de que el navegador esté actualizado. Si un juego no se carga adecuadamente, puede solucionarse recargando la página. Algunas funciones, como la pantalla completa, pueden depender de la compatibilidad del navegador utilizado.

---

### **8. Créditos**

El desarrollo de la plataforma fue realizado por:

**Rojo Ramirez Luis Edgar | Redgnar055**

---

### **9. Conclusión**

Arcade Zone constituye una solución web eficiente para la visualización y ejecución de videojuegos interactivos en línea. Su diseño intuitivo y su enfoque en la experiencia del usuario permiten una navegación sencilla, mientras que su estética retro refuerza su identidad como plataforma de entretenimiento digital.



---
---
---

Los cambios son: renombrar los dos `index.html`, crear un `index.html` limpio que sirva de hub, y agregar la tarjeta de Math Quest al array `games` en `main.js`.

Se crearon 3 archivos, ejecutó un comando

Ahora el `main.js` actualizado con la nueva tarjeta de Math Quest y las rutas corregidas para que funcione desde `arcade-zone/arcade.html`:

Main.js — adds Math Quest card, fixes image paths for subfolder, same logic

Main.js — adds Math Quest card, fixes image paths for subfolder, same logic

Ahora copio todos los archivos JS y CSS de Math Quest que ya teníamos:

```
ZonaArcade/
├── index.html                  ← hub limpio, redirige a arcade.html
├── main.js                     ← carrusel con la nueva tarjeta Math Quest
├── styles.css                  ← (el tuyo, sin tocar)
├── img/                        ← (tus imágenes, sin tocar)
│
├── arcade-zone/
│   └── arcade.html             ← era index.html de ZonaArcade
│
└── math-quest/
    ├── math-quest.html         ← era index.html de Math Quest
    ├── css/style.css
    └── js/ (los 8 módulos)
```

