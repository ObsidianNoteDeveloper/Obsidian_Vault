
---

# 1. Uso profesional del IDE

---

## Instalación de IntelliJ IDEA

> [!warning] Intalación de **IntelliJ IDEA**
>
> Generar la documentación para la instalación guiada del IDE que se usara a lo largo de la Ruta

---

## Nuevo Proyecto en Java

### Creación de un proyecto nuevo

Si es tu primer proyecto:
1. En la pantalla inicial le damos click en "New Project"

Si no es tu primer proyecto:
![[2026-04-28_14-43.png]]
1. 
2. En el panel izquierdo selecciona **Java** 
3. En la parte derecha selecciona el **JDK más estable hasta el momento (versión 17 o 21)**
	* Si no aparece dar click en "Download JDK"  
4. Configurar el proyecto 
	* Name: `nombre del proyecto`
	* Location: se puede dejar la ruta por defecto
	* Build system: `Intellij` 
5. Click en `Create` 
![[Pasted image 20260405145959.png]]
<div style="text-align: center; color: #555555;">
Img 1. Ejemplo de configuración para un proyecto nuevo
</div>

### Creación de una nueva Clase

1. Una vez abierto el proyecto:
	* En el panel izquierdo (Project) expandir la carpeta `src`
2. Dar click derecho sobre `src`: New → Java Class
3. Nombre: HolaMundo
4. Presionar `Enter`
![[Pasted image 20260405152928.png]]
<div style="text-align: center; color: #555555;">
  Img 2. Creación de una clase en java (HolaMundo.java)
</div>

5. Dentro del archivo que se creo (HolaMundo.java)
	* Escribir el ejemplo clásico del "Hola Mundo"
```Java
public class HolaMundo {
    public static void main(String[] args) {
        System.out.println("Hola mundo");
    }
}
```
6. Ejecución del programa
	* Opción 1:
		Click en el botón verde a un lado del `HolaMundo`
	* Opción 2: 
		Click derecho en el archivo → **Run 'HolaMundo.main()'**

---

# 1.1 Creación de Proyecto de JavaFX

---

# 1.1.1 Configuración del JDK

> [!warning] Instalación y configuración en Windows
>
> Instalar y configurar JavaFx 21 en el sistema operativo Windows

## Instalación y configuración de JavaFX 21 con JDK 17 en SO Linux (Debian)

### 1. Requisitos previos

Antes de iniciar el proceso de instalación, es necesario contar con los siguientes elementos:

- Sistema operativo basado en Linux (preferentemente Debian o derivado)
- Entorno de desarrollo integrado (IDE) como IntelliJ IDEA
- Java Development Kit (JDK) versión 17

El uso de JDK 17 se recomienda debido a que es una versión **LTS (Long-Term Support)**, lo que garantiza estabilidad y soporte extendido. Además, JavaFX 21 es compatible con versiones modernas de Java, asegurando interoperabilidad entre herramientas (Oracle, 2023).

### 2. Instalación de JDK 17

El comando `apt update` actualiza el índice de paquetes del sistema, asegurando la instalación de versiones recientes. Posteriormente, `apt install` permite instalar el JDK desde repositorios oficiales, garantizando integridad y seguridad del software (Debian Project, 2024).

Para verificar si Java está instalado en el sistema, se ejecuta:

```Bash
java -version
```

Si no se encuentra instalado, se procede con:

```Bash
sudo apt update    
sudo apt install openjdk-17-jdk
```

### 3. Descarga de JavaFX 21

La descarga desde fuentes oficiales como OpenJFX asegura que el software no ha sido alterado. JavaFX se distribuye de manera independiente del JDK desde Java 11, por lo que su instalación manual es necesaria (OpenJFX, 2023).

El SDK de JavaFX debe descargarse desde el sitio oficial:  [https://jdk.java.net/javafx21/](https://jdk.java.net/javafx21/)

Archivo recomendado:

	`openjfx-21.0.2_linux-x64_bin-sdk.tar.gz`

### 4. Instalación de JavaFX

#### 4.1 Crear directorio

El directorio `/opt` está destinado en sistemas Linux para la instalación de software adicional o de terceros. Esto permite mantener una estructura organizada y separada del sistema base (Linux Foundation, 2022).

```Bash
sudo mkdir -p /opt/javafx
```

#### 4.2 Extraer el SDK

El uso del comando `tar` permite descomprimir archivos en formato `.tar.gz`. La opción `-C` especifica el destino, asegurando que los archivos se ubiquen en una ruta accesible para futuras configuraciones (Shotts, 2019).

```Bash
sudo tar -xvzf ~/Descargas/openjfx-21.0.2_linux-x64_bin-sdk.tar.gz -C /opt/javafx
```

#### 4.3 Verificar instalación

Verificar la existencia del directorio garantiza que la extracción fue exitosa y que los archivos están disponibles para ser utilizados por el IDE.

```Bash
ls /opt/javafx
```

### 5. Configuración en IntelliJ IDEA

#### 5.1 Crear proyecto

Crear un proyecto con el JDK correcto es esencial para evitar incompatibilidades entre versiones. IntelliJ utiliza el SDK configurado para compilar y ejecutar el código (JetBrains, 2024).

- File → New Project
- Seleccionar Java
- Elegir JDK 17

#### 5.2 Agregar JavaFX

La carpeta `lib` contiene los archivos `.jar` necesarios para que el compilador reconozca las clases de JavaFX. Si se agrega una ruta incorrecta, el sistema no podrá resolver dependencias, generando errores como _“package javafx.application does not exist”_.

Ir a: `File → Project Structure → Libraries`

#####  Agregar librería:

- Click en `+ → Java` 
- Seleccionar: `/opt/javafx/javafx-sdk-21.0.2/lib` 

### 6. Configuración de ejecución (VM Options)

JavaFX utiliza el sistema de módulos introducido en Java 9. La opción `--module-path` define dónde se encuentran los módulos, mientras que `--add-modules` especifica cuáles se cargarán en tiempo de ejecución (Oracle, 2023).

Ir a: `Run → Edit Configurations`

#### Agregar configuración:

- Tipo: Application
- Main class: tu clase principal

#### Activar VM Options:

- Click en **Modify options**
- Activar **Add VM options**

#### Agregar:

```Bash
--module-path /opt/javafx/javafx-sdk-21.0.2/lib --add-modules javafx.controls,javafx.fxml
```

### 7. Primer programa en JavaFX

La clase extiende `Application`, que es el punto de entrada de JavaFX. El método `start()` se ejecuta automáticamente al iniciar la aplicación y permite construir la interfaz gráfica. El uso de `Scene` y `Stage` responde al modelo de contenedores de JavaFX (OpenJFX, 2023).

Crear clase:

```Java
import javafx.application.Application;  
import javafx.scene.Scene;  
import javafx.scene.control.Label;  
import javafx.stage.Stage;  
  
public class HolaMundoJavaFX extends Application {  
  
    @Override  
    public void start(Stage stage) {  
        Label label = new Label("Hola Mundo desde JavaFX");  
        Scene scene = new Scene(label, 400, 300);  
  
        stage.setTitle("Mi primera app JavaFX");  
        stage.setScene(scene);  
        stage.show();  
    }  
  
    public static void main(String[] args) {  
        launch();  
    }  
}
```

## 8. Ejecutar programa

La ejecución desde el IDE permite integrar la configuración del entorno, incluyendo VM Options, librerías y JDK. Esto asegura que el programa se ejecute con todas las dependencias correctamente resueltas.

- Seleccionar configuración creada
- Click en **Run**



# Referencias

- Debian Project. (2024). _Debian Administrator’s Handbook_. [https://www.debian.org](https://www.debian.org)
- JetBrains. (2024). _IntelliJ IDEA Documentation_. [https://www.jetbrains.com/help/idea/](https://www.jetbrains.com/help/idea/)
- Linux Foundation. (2022). _Filesystem Hierarchy Standard_. [https://refspecs.linuxfoundation.org](https://refspecs.linuxfoundation.org)
- OpenJFX. (2023). _JavaFX Documentation_. [https://openjfx.io](https://openjfx.io)
- Oracle. (2023). _Java Platform, Standard Edition Documentation_. [https://docs.oracle.com](https://docs.oracle.com)
- Shotts, W. E. (2019). _The Linux Command Line_. No Starch Press