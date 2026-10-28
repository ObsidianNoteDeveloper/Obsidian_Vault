
### JavaFX

Es una biblioteca y plataforma gráfica para desarrollar interfaces y aplicaciones de escritorio con Java. Proporciona ventanas, controles, escenas, imágenes, animaciones y herramientas para gestionar la interacción del usuario.
VJ
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

> [!Note] Crear el proyecto.
> Se puede seleccionar JavaFX, Java, Maven y un JDK compatible. La versión del JDK debe ser compatible con la versión de JavaFX que se haya configurado.

1. Abre **IntelliJ IDEA** y selecciona **New Project**.
    
2. En el panel izquierdo, selecciona **JavaFX**.
    
3. Configura los parámetros iniciales:
    
    - **Name:** Nombre de tu proyecto.
        
    - **Language:** Java.
        
    - **Build System:** **Maven** (esencial para descargar las librerías automáticamente).
        
    - **JDK:** Selecciona un JDK moderno compatible (ej. **Java 17** o **Java 21**). Si no lo tienes, puedes descargarlo directamente desde el menú desplegable del IDE.
        
4. Haz clic en **Create**.

### Paso 2: Configurar la versión de Java en el `pom.xml`

> [!Note] Configurar el compilador.
> No siempre se necesita modificar manualmente el `maven-compiler-plugin`. Si IntelliJ ya generó una configuración coherente, es preferible conservarla. Si se necesita fijar la versión, la propiedad `maven.compiler.release` es una opción clara y habitual.

Para evitar errores con los módulos de JavaFX, asegurarse de que Maven compile usando la misma versión del JDK previamente seleccionado.

1. Abrir el archivo **`pom.xml`** en la raíz de tu proyecto.
    
2. Buscar la sección del plugin del compilador (`maven-compiler-plugin`) casi al final del archivo.
    
3. Asegurarse de que las etiquetas `<source>` y `<target>` coincidan con la versión de tu JDK (por ejemplo, **21**):

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

> [!Note] Sincronizar Maven.
> Cuando se cambian las dependencias o la configuración del `pom.xml`, se requiere recargar los proyectos Maven en IntelliJ. El IDE resolverá los cambios y descargará lo necesario.

Cada vez que se crea un proyecto nuevo o se modifica el archivo `pom.xml`, indicar a IntelliJ que debe descargar y aplicar las dependencias:

1. Haz clic en el botón de **Reload All Maven Projects** (el ícono de las flechitas circulares, usualmente ubicado en la esquina superior derecha del archivo `pom.xml` o en la pestaña lateral de Maven).
    
2. Espera unos segundos a que la barra de progreso inferior termine de descargar las librerías de OpenJFX.

### Paso 4: Verificar la estructura básica

> [!Note] Estructura del proyecto
> La clase principal debe extender `Application`, pero FXML es opcional. Si se utiliza, el archivo debe estar en la ruta de recursos que espera tu código.

Verificar la estructura de archivos principal:

1. Una clase principal (por ejemplo, `HelloApplication.java`) que extienda de `javafx.application.Application` e incluya tanto el método `start` como el método `main(String[] args)` con un `launch();`.
    
2. Archivo de interfaz visual correspondiente (`hello-view.fxml`) ubicado correctamente dentro de la carpeta de recursos (`src/main/resources/...`).

### Paso 5: Ejecutar

1. Ir a la clase principal (`HelloApplication.java`).
    
2. Hacer clic en el **botón verde de reproducción (Play)** que aparece al lado del método `main` o al margen izquierdo.
    
3. Se abrirá la ventana de prueba inicial de JavaFX.

---

# Archivos básicos de JavaFX

### HelloApplication.java

Es la clase principal de la aplicación JavaFX. Normalmente extiende `Application`, configura la ventana y carga la interfaz gráfica.

```Java
package com.example.vjprueba1;  
  
import javafx.application.Application;  
import javafx.fxml.FXMLLoader;  
import javafx.scene.Scene;  
import javafx.stage.Stage;  
  
import java.io.IOException;  
  
public class HelloApplication extends Application {  
    @Override  
    public void start(Stage stage) throws IOException {  
        FXMLLoader fxmlLoader = new FXMLLoader(HelloApplication.class.getResource("hello-view.fxml"));  
        Scene scene = new Scene(fxmlLoader.load(), 320, 240);  
        stage.setTitle("Hello!");  
        stage.setScene(scene);  
        stage.show();  
    }  
}
```
- La anotación `@Override` indica que esta implementando el método heredado de `Application`.

##### Importaciones

Las siguientes importaciones (`import`) son las necesarias para construir una aplicación gráfica de escritorio utilizando **JavaFX** y un marco de trabajo (_framework_) moderno para el desarrollo de interfaces de usuario (_UI_). 

Clase base para crear aplicaciones JavaFx.
```Java
import javafx.application.Application;
```
- Para crear una interfaz gráfica en JavaFX, la clase principal debe extender (_extends_) de `Aplication`. Esta clase gestiona el inicio, la ejecución y el cierre de la aplicación de manera automática. 

Cargar y procesar una interfaz definida en un archivo FXML.
```Java
import javafx.fxml.FXMLLoader;
```
- Lee archivos basados en XML que definen el diseño visual de la interfaz de usuario de forma separada al código de programación.
- Toma un archivo `.fxml`, que contiene botones, etiquetas, campos de texto, etc, y lo carga en memoria para convertirlo en objetos de Java utilizables para la aplicación.

Representa la escena que contiene los elementos visuales de la interfaz.
```Java
import javafx.scene.Scene;
```
- La `Scene` es como el "lienzo" o la "obra de teatro". Contiene todos los componentes visuales de la interfaz (botones, paneles, texto) y se coloca dentro de una ventana principal.

Representa la ventana principal de la aplicación.
```Java
import javafx.stage.Stage;
```
- Es la ventana principal del sistema operativo (el marco con los botones de minimizar, maximizar y cerrar)
- JavaFX pasa una instancia de `Stage` al método `start()` para configurar el titulo, las dimensiones y mostrar la ventana en la pantalla.

Excepción que puede producirse al cargar el archivo FXML.
```Java
import java.io.IOException;
```
- `IOException`es una clase de error que Java utiliza para manejar problemas relacionados con la lectura o escritura de datos
- En JavaFX, cuando se usa `FXMLLoader` para cargar un archivo externo (`.fxml`), Java requiere manejar o declarar que podría ocurrir un error si el archivo no se encuentra o no se puede leer correctamente.

##### Método start()

El método `start()` es el método principal del ciclo de vida de una aplicación JavaFX, pero no es el método principal de entrada de un programa Java tradicional.

- La JVM busca este método para comenzar la ejecución de la aplicación.
- JavaFX invoca este método cuando el entorno gráfico está listo para iniciar la aplicación.

```Java
public void start(Stage stage) throws IOException {
	...
}
```

> [!Note]
> Cuando se ejecuta el programa de JavaFX (a través del método `launch()`), Java arranca el motor gráfico por debajo y busca automáticamente un método llamado `start` para saber cómo debe iniciar la interfaz gráfica.

> [!Note]
> La palabra `throws` (que se traduce como _"lanza"_ o _"puede arrojar"_) le avisa a Java que el código que está dentro del método `start` va a realizar una acción riesgosa: en este caso, **leer un archivo externo (el archivo FXML o recursos del sistema)**.

Este es el método automático que **arranca** la interfaz gráfica (`start`), recibiendo una ventana (`Stage`), y advierte que durante su inicio podría ocurrir un error al leer archivos (`throws IOException`).

##### Cargar la interfaz visual

```Java
FXMLLoader fxmlLoader = new FXMLLoader(HelloApplication.class.getResource("hello-view.fxml"));
```
- Crea un objeto `FXMLLoader` que busca y lee el archivo de diseño visual llamado `"hello-view.fxml"`.
- `HelloApplication.class.getResource(...)` le dice a Java: _"Busca este archivo FXML exactamente en la misma carpeta o ruta donde está ubicada esta clase principal"_. Este archivo FXML contiene los elementos visuales de tu pantalla (botones, textos, etc.).

##### Crear el "lienzo" (Scene)

```Java
Scene scene = new Scene(fxmlLoader.load(), 320, 240);
```
- Crea la **escena (`Scene`)** de JavaFX y define sus dimensiones iniciales.
- `fxmlLoader.load()` toma todo el diseño que leyó del archivo FXML anterior y lo convierte en componentes visuales reales de Java.
- Los números `320` y `240` indican el **ancho y el alto** (en píxeles) que tendrá la ventana al abrirse.

##### Título en la ventana

```Java
stage.setTitle("Prueba1");
```
- Toma la ventana principal (`stage`) que recibe como parámetro en el método `start` y le asigna el texto `"Prueba1"` para que aparezca en la parte superior del marco de la ventana.

##### Asignar la escena a la ventana

```Java
stage.setScene(scene);
```
- Coloca el "lienzo" dentro de la ventana.

##### Mostrar la ventana

```Java
stage.show;
```
- Por defecto, cuando JavaFX arranca, la ventana está oculta en la memoria. Esta instrucción final ordena al sistema operativo que dibuje la ventana y se la muestre al usuario.

### HelloController.java

Este programa es el controlador de la interfaz gráfica del proyecto. Su función es responder a una acción del usuario y modificar el texto que aparece en la ventana.

```Java
import javafx.fxml.FXML;  
import javafx.scene.control.Label;  
  
public class HelloController {  
    @FXML  
    private Label welcomeText;  
  
    @FXML  
    protected void onHelloButtonClick() {  
        welcomeText.setText("Mensaje generado por el archivo HelloController.java");  
    }  
}
```

##### Importaciones

```Java
import javafx.fxml.FXML;
```
- `FXML` es una anotación proporcionada por JavaFX que permite identificar elementos de una clase que deben estar disponibles para la integración con FXML.

```Java
import javafx.scene.control.Label;
```
- `Label` es una clase de JavaFX que representa un elemento visual para mostrar texto.
- `welcomeText` será la referencia a una etiqueta que ya está declarada en el archivo FXML.

##### Clase controladora

```Java
public class HelloController {
	...
}
```
- Este controlador no es la aplicación principal (_no extiende de `Application`_), es una clase encargada de gestionar interacciones de la interfaz

##### Atributo welcomeText

```Java
@FXML
private Label welcomeText;
```
- La anotación `@FXML` permite acceder al atributo durante la carga.
- `private` restringe el acceso directo al atributo desde otra clase.
-  `Label` es el tipo de dato de etiqueta visual JavaFX.
- Para que esto funcione, el archivo `hello-view.fxml` debe tener una etiqueta con el identificador adecuado.

##### Método onHelloButtonClick()

```Java
@FXML
protected void onHelloButtonClick() {
    welcomeText.setText("Welcome to JavaFX Application!");
}
```
- `@FXML` permite que el cargador FXML pueda asociar el método con la interfaz.
- El modificador `protected` permite el acceso desde el mismo paquete y desde las subclases, con las reglas propias de Java.
- El nombre de este método describe la acción que se ejecuta 

`welcomeText.setText(...)`
- Este método solo se ejecuta cuando algo lo invoca
	- La etiqueta inicial no muestra nada cuando se ejecuta el programa
	- Después de hacer click en el boton, se ejecuta el método y muestra "Mensaje generado por el archivo HelloController.java".

### Launcher.java

Generalmente sirve para iniciar la aplicación mediante un método `main()`, delegando el arranque a `HelloApplication`. Esto es útil en proyectos JavaFX modulares.

El archivo `Launcher.java` es el encargado de iniciar tu aplicación JavaFX, utiliza varios conceptos importantes de Java: las importaciones, las clases, los métodos, los parámetros y las llamadas a métodos estáticos.

```Java
import javafx.application.Application;  
  
public class Launcher {  
    public static void main(String[] args) {  
        Application.launch(HelloApplication.class, args);  
    }  
}
```

Este archivo no crea botones, no dibuja personajes y no configura la ventana. Su responsabilidad es poner en marcha JavaFX y señalar cuál es la clase que contiene la lógica inicial de la aplicación.

```Java
import javafx.application.Application;
```
- `application` es el paquete que contiene clases relacionadas con el ciclo de vida de las aplicaciones.

##### Clase Launcher

```Java
public class Launcher {
	...
}
```
- La clase se llama `Launcher`, porque significa aproximadamente «iniciador» o «lanzador».
- La clase es `public` para que pueda ser accesible desde otros paquetes, sujeto a las reglas de Java.

```Java
Application.launch(HelloApplication.class, args);
```
- Esta llamando al método estático `launch()` de la clase `Application`
- Su función es iniciar el entorno de ejecución de JavaFX y poner en marcha la aplicación indicada.

`HelloApplication.class`
- En Java, `.class` permite obtener el objeto que representa una clase.
- Se le indica a JavaFX qué clase debe utilizar como aplicación.

### hello-view.fxml

El archivo `hello-view.fxml` define la apariencia de la interfaz gráfica de la aplicación JavaFX. Indica qué elementos aparecen en la ventana, cómo se organizan y qué método se ejecuta al pulsar el botón.

```XML
<?xml version="1.0" encoding="UTF-8"?>  
  
<?import javafx.geometry.Insets?>  
<?import javafx.scene.control.Label?>  
<?import javafx.scene.layout.VBox?>  
  
<?import javafx.scene.control.Button?>  
<VBox alignment="CENTER" spacing="20.0" xmlns:fx="http://javafx.com/fxml"  
      fx:controller="com.example.vjprueba1.HelloController">  
    <padding>        <Insets bottom="20.0" left="20.0" right="20.0" top="20.0"/>  
    </padding>  
    <Label fx:id="welcomeText"/>  
    <Button text="Contenido del boton" onAction="#onHelloButtonClick"/>  
</VBox>
```

Contiene tres elementos principales:

- `VBox`: es el contenedor que organiza los elementos verticalmente, uno debajo del otro y centrados.
    
- `Label`: es una etiqueta donde se mostrará un texto. Su identificador `welcomeText` permite que `HelloController.java` acceda a ella y modifique su contenido.
    
- `Button`: es un botón que muestra el texto «Contenido del boton». Al pulsarlo, ejecuta el método `onHelloButtonClick()` del controlador.

Además, el archivo establece un espacio de 20 unidades entre los elementos y un margen interior de 20 unidades alrededor del contenido.



---

# Estructura actual

> [!Note] Nuevos archivos .java.
> Crear el archivo con extensión .java en el paquete correspondiente al proyecto.

<div style="text-align: center;">  
<img src="EstrucutraActual.png" width="500">  
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

