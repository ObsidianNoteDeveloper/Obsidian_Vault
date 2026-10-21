
### JavaFX

Es una biblioteca y plataforma gráfica para desarrollar interfaces y aplicaciones de escritorio con Java. Proporciona ventanas, controles, escenas, imágenes, animaciones y herramientas para gestionar la interacción del usuario.

### Maven

Maven es una herramienta de construcción y gestión de proyectos Java. Su función es automatizar tareas que, de otro modo, tendrías que realizar manualmente.

> [!Note]
> Sin Maven, tendrías que buscar las bibliotecas adecuadas, descargarlas, configurar las rutas y asegurarte de que sus versiones sean compatibles. Maven automatiza gran parte de ese trabajo.

### Herramientas principales

| Herramienta   | ¿Para qué sirve?                                              |
| ------------- | ------------------------------------------------------------- |
| JDK           | Proporciona Java, el compilador y herramientas de desarrollo. |
| JavaFX        | Proporciona las herramientas gráficas.                        |
| Maven         | Gestiona las dependencias y el proceso de construcción.       |
| IntelliJ IDEA | Es el entorno de desarrollo donde trabajas.                   |
| `pom.xml`     | Es el archivo en el que defines la configuración de Maven.    |
### Dependencia 

Biblioteca externa que el proyecto necesita para funcionar.

**Ejemplo de dependencia para utilizar JavaFX:** 
```Java
<dependencies>
    <dependency>
        <groupId>org.openjfx</groupId>
        <artifactId>javafx-controls</artifactId>
        <version>21.0.2</version>
    </dependency>
</dependencies>
```

En este ejemplo se incluye `javafx-controls`, que proporciona controles gráficos y también requiere componentes básicos de JavaFX.

### pom.xml

Este archivo es la parte más importante del proyecto **Maven**.
- Archivo de configuración central del proyecto.
- Normalmente se encuentra en la raíz, junto a la carpeta `src` .

En el `pom.xml` se pueden declarar las dependencias, la versión de Java, los complementos de construcción y otros parámetros del proyecto.

### Implementar Maven en IntelliJ IDEA

Crear un proyecto JavaFX seleccionando Maven como sistema de construcción es recomendable para empezar.

# Cómo iniciar un proyecto de JavaFX en IntelliJ IDEA (con Maven)

### Paso 1: Crear el proyecto en IntelliJ IDEA

> [!Note] Crear el proyecto
> Se puedes seleccionar JavaFX, Java, Maven y un JDK compatible. La versión del JDK debe ser compatible con la versión de JavaFX que se haya configurado.

1. Abre **IntelliJ IDEA** y selecciona **New Project**.
    
2. En el panel izquierdo, selecciona **JavaFX**.
    
3. Configura los parámetros iniciales:
    
    - **Name:** Nombre de tu proyecto.
        
    - **Language:** Java.
        
    - **Build System:** **Maven** (esencial para descargar las librerías automáticamente).
        
    - **JDK:** Selecciona un JDK moderno compatible (ej. **Java 17** o **Java 21**). Si no lo tienes, puedes descargarlo directamente desde el menú desplegable del IDE.
        
4. Haz clic en **Create**.

### Paso 2: Configurar la versión de Java en el `pom.xml`

> [!Note] Configurar el compilador
> No siempre se necesita modificar manualmente el `maven-compiler-plugin`. Si IntelliJ ya generó una configuración coherente, es preferible conservarla. Si se necesita fijar la versión, la propiedad `maven.compiler.release` es una opción clara y habitual.

Para evitar errores con los módulos de JavaFX, debes asegurarte de que Maven compile usando la misma versión de tu JDK.

1. Abre el archivo **`pom.xml`** en la raíz de tu proyecto.
    
2. Busca la sección del plugin del compilador (`maven-compiler-plugin`) casi al final del archivo.
    
3. Asegúrate de que las etiquetas `<source>` y `<target>` coincidan con la versión de tu JDK (por ejemplo, **21**):

XML

```XML
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.13.0</version>
                <configuration>
                    <source>21</source>
                    <target>21</target>
                </configuration>
            </plugin>
```

### Paso 3: Sincronizar Maven

> [!Note] Sincronizar Maven
> Cuando se cambian las dependencias o la configuración del `pom.xml`, se requiere recargar los proyectos Maven en IntelliJ. El IDE resolverá los cambios y descargará lo necesario.

Cada vez que crees un proyecto nuevo o modifiques el archivo `pom.xml`, debes indicarle a IntelliJ que descargue y aplique las dependencias:

1. Haz clic en el botón de **Reload All Maven Projects** (el ícono de las flechitas circulares, usualmente ubicado en la esquina superior derecha del archivo `pom.xml` o en la pestaña lateral de Maven).
    
2. Espera unos segundos a que la barra de progreso inferior termine de descargar las librerías de OpenJFX.

### Paso 4: Verificar la estructura básica

> [!Note] Estructura del proyecto
> La clase principal debe extender `Application`, pero FXML es opcional. Si se utiliza, el archivo debe estar en la ruta de recursos que espera tu código.

Asegúrate de que tu estructura de archivos principal esté lista:

1. Una clase principal (por ejemplo, `HelloApplication.java`) que extienda de `javafx.application.Application` e incluya tanto el método `start` como el método `main(String[] args)` con un `launch();`.
    
2. Tu archivo de interfaz visual correspondiente (`hello-view.fxml`) ubicado correctamente dentro de la carpeta de recursos (`src/main/resources/...`).

### Paso 5: ¡A ejecutar!

1. Ve a tu clase principal (`HelloApplication.java`).
    
2. Haz clic en el **botón verde de reproducción (Play)** que aparece al lado del método `main` o al margen izquierdo.
    
3. ¡Listo! Se abrirá la ventana de prueba inicial de JavaFX.

---

# Archivos básicos de JavaFX

### HelloApplication.java

Es la clase principal de la aplicación JavaFX. Normalmente extiende `Application`, configura la ventana y carga la interfaz gráfica.


### HelloController.java

Es el controlador de la interfaz FXML. Se encarga de gestionar las acciones de los botones y otros elementos visuales, según cómo esté configurado el proyecto.

### Launcher.java

Generalmente sirve para iniciar la aplicación mediante un método `main()`, delegando el arranque a `HelloApplication`. Esto es útil en proyectos JavaFX modulares.

---

# Estructura actual

<div style="text-align: center;">  
<img src="Pasted%20image%2020261020184942.png" width="500">  
</div>


### Estructura futura 

```
src/main/java/
└── com/example/vjprueba1/
    ├── HelloApplication.java
    ├── Launcher.java
    ├── controller/
    │   └── MenuController.java
    ├── game/
    │   ├── GameManager.java
    │   └── GameLoop.java
    ├── entities/
    │   ├── Player.java
    │   └── Enemy.java
    └── model/
        └── Score.java
```

