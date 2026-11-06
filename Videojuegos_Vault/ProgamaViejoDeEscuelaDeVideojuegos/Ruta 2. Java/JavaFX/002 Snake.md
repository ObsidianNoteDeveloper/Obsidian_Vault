
[MÓDULO 1](#MÓDULO%201)
[Introducción a la Programación y al Desarrollo de Videojuegos](#Introducción%20a%20la%20Programación%20y%20al%20Desarrollo%20de%20Videojuegos)
	[Unidad 1. ¿Qué es un videojuego?](#Unidad%201.%20¿Qué%20es%20un%20videojuego?)
	[Unidad 2. Introducción a Java](#Unidad%202.%20Introducción%20a%20Java)
	[Unidad 3. Introducción a la POO](#Unidad%203.%20Introducción%20a%20la%20POO)
	[Unidad 4. Modelado del videojuego](#Unidad%204.%20Modelado%20del%20videojuego)






# Curso: Desarrollo de Videojuegos en Java con JavaFX

> [!Note]
> "Aprender Java desarrollando un videojuego real desde cero."

El juego Snake se enfoca en aprender:

- Fundamentos de programación.
- Programación Orientada a Objetos.
- Arquitectura de software.
- Motores de videojuegos.
- JavaFX.
- Buenas prácticas de desarrollo.

Elementos principales:

1. El tablero de juego.
2. La serpiente y su movimiento.
3. La detección de colisiones y comida.

### Arquitectura inicial

```
com.snake.vj001_snake
│
├── engine
│   └── GameLoop
│
├── model
│   ├── Food
│   ├── Position
│   ├── Snake
│   └── Direction
│
├── ui
│   └── GameView
│
├── config
│   └── GameConfig
│
├── SnakeGame
└── Launcher
```

- **Model** → estado del juego.
- **Engine** → lógica y actualización.
- **UI** → renderizado.
- **Config** → constantes.
- **SnakeGame** → arranque de JavaFX.

---

- Módulo 1: Introducción a la Programación y al Desarrollo de Videojuegos
	- Unidad 1 - Qué es un videojuego
		- Definición de videojuego
		- Componente de un videojuego
		- Entrada
		- Procesamiento
		- Salida
		- Ciclo de Juego (Game Loop)
	- Unidad 2 - Introducción a Java
		- JVM
		- JDK
		- JRE
		- Compilación
		- Clase
		- Método
		- main()
		- Variables
		- Tipos de datos
		- Operadores
	- Unidad 3 - Introducción a la POO
		- Qué es un objeto
		- Qué es una clase
		- Encapsulamiento
		- Abstracción
		- Herencia 
		- Polimorfismo
	- Unidad 4 - Modelado del videojuego
		- Qué objetos existen en el juego Snake
			- Snake
			- Food
			- Position
		- Clase Position
			- Atributos
			- Constructor
			- Getters
			- Encapsulamiento
		- Clase Direction
			- Primer enum
		- Clase Food
			- Composición básica
		- Clase GameConfig
			- Introducción a constantes

- Módulo 2: Programación Orientada a Objetos Aplicada a Videojuegos
	- Unidad 1 - Profundización en POO
		- Encapsulamiento 
			- private
			- public
		- Abstracción
			- posición
			- dirección
			- cuerpo
	- Unidad 2 - Colecciones en Java
		- ArrayList
		- LinkedList
	- Unidad 3 - Diseño del modelo Snake
		- Clase Snake
			- Composición
			- Objetos dentro de objetos
			- Métodos de negocio
	- Unidad 4 - Introducción a la Arquitectura del Proyecto
		- Modulación de Proyectos
			- mantenimiento
			- escalabilidad
			- Código acoplado
		- Introducción a la arquitectura 
			- Model
			- Engine
			- UI
			- Config

- Módulo 3: Fundamentos de Desarrollo de Videojuegos con JavaFX
	- Unidad 1 - Introducción a JavaFX
		- Stage
		- Scene
		- Canvas
		- GraphicsContext
	- Unidad 2 - Arquitectura de un videojuego
		- Input
		- Update
		- Render
	- Unidad 3 - El Game Loop
		- No espera acciones
		- Se actualiza continuamente
	- Unidad 4 - El motor del videojuego
		- Implementación de:
			- Timeline
			- KeyFrame
		- Abstracción
		- Encapsulamiento
		- Clase GameView
			- render()
			- drawSnake()
			- drawFood()
		- Clase SnakeGame
			- Stage
			- Scene
			- Eventos de teclado
		- Clase Launcher

- Módulo 4: Desarrollo Completo del Videojuego Snake
	- Unidad 1 - Diseño del Motor del Juego
		- Clase GameLoop
	- Unidad 2 - Detección de Colisiones
		- Paredes
		- Cuerpo propio
		- Comida
	- Unidad 3 - POO Avanzada
		- Encapsulamiento
		- Abstracción
		- Herencia
		- Polimorfismo
	- Unidad 4 - Integración del videojuego
		- GameLoop
			- Crecimiento
			- Puntuación
			- Colisiones
			- Game Over
	- Unidad 5 - Refactorización y Mejores Prácticas
		- SOLID (introducción)
		- Separación de responsabilidades
		- Organización por capas 
		- Arquitectura del videojuego

#### Mejoras recomendadas

Una vez funcione la versión básica, puedes añadir:

- Puntuación.
- Pantalla de inicio.
- Reiniciar pulsando una tecla.
- Niveles de velocidad.
- Obstáculos.
- Efectos de sonido (`AudioClip`).
- Texturas e imágenes para la serpiente y la comida.
- Guardado de récords.

---
---

# MÓDULO 1

# Introducción a la Programación y al Desarrollo de Videojuegos

### Objetivo

Comprender qué es un videojuego, cómo funciona internamente y aprender los fundamentos de Java para construir las primeras clases del proyecto.

---

## Unidad 1. ¿Qué es un videojuego?

#### Temas

- Definición de videojuego.
- Componentes de un videojuego.
- Entrada.
- Procesamiento.
- Salida.
- Ciclo de juego (Game Loop).

### Videojuego 

Un videojuego es un sistema interactivo digital diseñado para proporcionar experiencias lúdicas mediante la participación activa del usuario dentro de un entorno virtual regido por reglas, objetivos y mecanismos de retroalimentación. Desde la perspectiva de los videojuegos, integra elementos como narrativas, desafíos, personajes, escenarios y sistemas de puntuación que permiten la interacción continua entre el jugador y el mundo de juego. En el contexto del desarrollo de software, un videojuego puede entenderse como una aplicación informática compleja que combina programación, diseño de interfaces, gráficos, audio, bases de datos y algoritmos para ofrecer una experiencia interactiva en tiempo real.

### Componentes de un videojuego

Los componentes de un videojuego son los elementos que conforman su estructura funcional y permiten su ejecución e interacción. Entre ellos se encuentran los gráficos, el audio, las mecánicas de juego, la narrativa, la interfaz de usuario, los sistemas de físicas, la inteligencia artificial y los dispositivos de entrada y salida. Desde la ingeniería de software, estos componentes suelen organizarse en módulos o subsistemas especializados que colaboran entre sí para garantizar la correcta operación del producto, facilitando aspectos como la mantenibilidad, escalabilidad y reutilización del código.

### Entrada

La entrada es el conjunto de datos o acciones que el sistema recibe desde fuentes externas para ser procesadas. En un videojuego, la entrada corresponde principalmente a las acciones realizadas por el jugador mediante dispositivos como teclado, ratón, mandos de control, pantallas táctiles o sensores de movimiento. Desde el punto de vista del desarrollo de software, el subsistema de entrada se encarga de capturar, interpretar y traducir estas señales en eventos comprensibles por el programa para que puedan influir en el comportamiento del sistema.

### Procesamiento

El procesamiento es la etapa en la que el sistema analiza y transforma los datos de entrada para generar una respuesta adecuada. En los videojuegos, este proceso incluye el cálculo de movimientos, detección de colisiones, aplicación de reglas del juego, simulación física, toma de decisiones de la inteligencia artificial y actualización del estado del entorno virtual. En términos de desarrollo de software, el procesamiento representa la ejecución de algoritmos y lógica de negocio que permiten convertir los datos recibidos en resultados coherentes y funcionales.

### Salida

La salida es la información que el sistema genera y presenta al usuario después de realizar el procesamiento correspondiente. En un videojuego, la salida se manifiesta a través de imágenes, animaciones, efectos visuales, sonidos, vibraciones o cualquier otra forma de retroalimentación que permita al jugador percibir los resultados de sus acciones. Desde la perspectiva del desarrollo de software, la salida constituye la representación de los resultados obtenidos por el programa mediante interfaces gráficas, reportes, notificaciones o dispositivos especializados.

### Ciclo de juego (Game Loop)

El ciclo de juego o _Game Loop_ es la estructura fundamental que controla la ejecución continua de un videojuego mientras este se encuentra en funcionamiento. Su operación consiste, de forma repetitiva, en capturar las entradas del usuario, procesar la lógica del juego, actualizar el estado de los objetos y generar las salidas visuales y sonoras correspondientes. Desde el desarrollo de software, el _Game Loop_ actúa como un ciclo de ejecución en tiempo real que garantiza la sincronización entre los distintos subsistemas del videojuego, permitiendo una experiencia fluida, responsiva y consistente para el jugador.

### El clásico juego de Snake

_Snake_ es un videojuego de género arcade cuya mecánica principal consiste en controlar una serpiente que se desplaza continuamente por un área delimitada mientras consume alimentos distribuidos en el escenario. Cada vez que la serpiente consume un objeto, su longitud aumenta, incrementando la dificultad del juego debido a la reducción progresiva del espacio disponible para maniobrar. El objetivo consiste en obtener la mayor puntuación posible evitando colisionar con los límites del escenario o con el propio cuerpo de la serpiente. Debido a la simplicidad de sus reglas y a su carácter altamente interactivo

> [!Note]
> _Snake_ es considerado uno de los ejemplos clásicos para el estudio de la lógica de videojuegos y la programación orientada a eventos.

El origen de _Snake_ se remonta al videojuego **Blockade**. Sin embargo, la versión que popularizó mundialmente el concepto fue la incluida en los teléfonos móviles **Nokia**, especialmente a partir del modelo **Nokia 6110** lanzado en 1997. Gracias a su presencia preinstalada en millones de dispositivos móviles, _Snake_ se convirtió en uno de los videojuegos más jugados de la década de 1990 y principios de los años 2000, siendo reconocido como un referente histórico en la evolución de los videojuegos para dispositivos portátiles.

> [!Note]
> **Blockade** es un clásico videojuego de arcade lanzado por **Gremlin** en **1976**. En este juego, dos jugadores controlan una flecha que deja un rastro detrás de sí, evitando chocar con paredes o el propio rastro del oponente. El objetivo es evitar que el rastro del oponente toque la pantalla, lo que resulta en una victoria para el jugador que logre hacerlo primero. El juego se juega en un entorno de blanco y negro y utiliza cuatro botones de dirección para el movimiento. Además, Blockade es considerado el precursor del género de videojuegos de serpientes, influyendo en otros juegos como **Snake**.

### Actividad

> [!success] 
> Identificar los componentes en Snake.

Desde una perspectiva de análisis y desarrollo de software, el juego _Snake_ puede descomponerse en varios componentes funcionales que permiten identificar las reglas de negocio necesarias para su implementación en Java. El primer componente es la **serpiente (Snake)**, que representa la entidad principal del juego. Esta entidad posee atributos como posición, longitud, dirección de movimiento y velocidad. La regla de negocio asociada establece que la serpiente debe avanzar continuamente en una dirección determinada y que cada segmento del cuerpo debe seguir la posición ocupada previamente por el segmento anterior.

> [!info]
> En **Ingeniería de Software**, una **regla de negocio** es una restricción, política, condición o comportamiento que define cómo debe operar un sistema para cumplir los objetivos de una organización, proceso o dominio específico. 
> - Estas reglas representan el conocimiento del negocio y establecen qué acciones están permitidas, prohibidas o son obligatorias dentro de una aplicación. 
> - Durante el análisis y diseño del software, las reglas de negocio se identifican y documentan para que posteriormente sean implementadas mediante algoritmos, validaciones y estructuras de programación.

Un segundo componente es el **alimento (Food)**, elemento encargado de provocar el crecimiento de la serpiente. La regla de negocio correspondiente indica que el alimento debe aparecer en una posición aleatoria válida dentro del tablero y no puede coincidir con ninguna celda ocupada por la serpiente. Cuando ocurre una colisión entre la cabeza de la serpiente y el alimento, este desaparece, se genera uno nuevo en otra ubicación y la puntuación se incrementa.

El **tablero de juego (Game Board)** constituye otro componente fundamental. Este define los límites espaciales dentro de los cuales se desarrolla la partida. Desde el punto de vista de las reglas de negocio, el tablero debe controlar las coordenadas válidas para el movimiento de la serpiente y verificar si se producen colisiones contra los bordes del escenario, condición que generalmente provoca la finalización del juego.

La **entrada del usuario (Input System)** representa el mecanismo mediante el cual el jugador interactúa con el sistema. En una implementación en Java, este componente suele capturar eventos provenientes del teclado. La regla principal establece que el jugador puede modificar la dirección de desplazamiento de la serpiente, pero no puede seleccionar la dirección opuesta inmediata a la actual, ya que esto supondría una colisión instantánea consigo misma.

El **sistema de colisiones (Collision System)** constituye un componente encargado de evaluar continuamente el estado de la partida. Sus reglas de negocio determinan si la cabeza de la serpiente entra en contacto con los bordes del tablero, con su propio cuerpo o con un alimento. Dependiendo del tipo de colisión detectada, el sistema ejecuta acciones específicas como finalizar la partida, incrementar la puntuación o aumentar la longitud de la serpiente.

Otro componente relevante es el **sistema de puntuación (Score System)**, responsable de registrar el desempeño del jugador. La regla de negocio establece que la puntuación aumenta cada vez que la serpiente consume un alimento y puede utilizarse para mostrar récords, niveles de dificultad o estadísticas de la partida.

Finalmente, el **ciclo de juego (Game Loop)** coordina la ejecución de todos los componentes anteriores. En una implementación en Java, este ciclo ejecuta repetidamente las operaciones de lectura de entrada, actualización de la posición de la serpiente, detección de colisiones, actualización de la puntuación y renderizado de los elementos gráficos. Esta estructura garantiza que el videojuego funcione de manera continua y consistente, manteniendo la sincronización entre las acciones del jugador y las respuestas del sistema.

En términos de modelado orientado a objetos, una implementación de _Snake_ en Java podría abstraerse mediante clases como **Snake**, **Food**, **Board**, **Game**, **ScoreManager** e **InputHandler**, donde cada una encapsula responsabilidades específicas y colabora para materializar las reglas de negocio que definen el comportamiento completo del videojuego.

---

## Unidad 2. Introducción a Java

#### Temas

- JVM.
- JDK.
- JRE.
- Compilación.
- Clase.
- Método.
- main().
- Variables.
- Tipos de datos.
- Operadores.
- Condicionales
- Bucles 

### JVM (Java Virtual Machine)

La **Java Virtual Machine (JVM)** es el componente responsable de ejecutar los programas escritos en Java. Su función principal consiste en interpretar y ejecutar el código compilado conocido como _bytecode_, permitiendo que una aplicación pueda ejecutarse en diferentes sistemas operativos sin necesidad de ser modificada. En el del desarrollo de videojuegos, la JVM actúa como la plataforma de ejecución que permite que el juego funcione de manera uniforme en distintos entornos. Por ejemplo, un videojuego desarrollado en Java puede ejecutarse tanto en Windows como en Linux siempre que exista una JVM instalada. Esta característica se conoce como _Write Once, Run Anywhere_ (escribir una vez, ejecutar en cualquier lugar).

### JDK (Java Development Kit)

El **Java Development Kit (JDK)** es el conjunto de herramientas necesarias para desarrollar aplicaciones en Java. Incluye el compilador, bibliotecas estándar, herramientas de depuración y la JVM. Desde la perspectiva del desarrollo de videojuegos, el JDK proporciona todos los recursos necesarios para crear, compilar y probar programas que posteriormente se convertirán en componentes de un videojuego, como menús, personajes, sistemas de colisión o motores de juegos sencillos.

### JRE (Java Runtime Environment)

El **Java Runtime Environment (JRE)** es el entorno de ejecución encargado de permitir que una aplicación Java funcione correctamente. Está compuesto principalmente por la JVM y las bibliotecas necesarias para ejecutar programas, pero no incluye herramientas de desarrollo. En el ámbito de los videojuegos, el JRE permite que los jugadores ejecuten el videojuego sin necesidad de instalar todas las herramientas de programación utilizadas por los desarrolladores.

### Compilación

La **compilación** es el proceso mediante el cual el código fuente escrito por el programador se transforma en bytecode que puede ser interpretado por la JVM. En el desarrollo de videojuegos, la compilación permite convertir la lógica del juego, escrita en archivos `.java`, en instrucciones ejecutables. Cada vez que se modifica el comportamiento de un personaje, una mecánica o una interfaz, es necesario compilar nuevamente el proyecto.

### Estructura básica de un programa en Java

```Java
import java.util.*;  
  
public class ClasePrincipal {  
    public static void main(String[] args) {   
    }  
}
```

##### Importar clases y herramientas de Java

`import java.util.*;`

- `import`: permite utilizar clases de otros paquetes sin tener que escribir su nombre completo.
- `java.util`: es un paquete que contiene herramientas útiles, como listas, colecciones, generadores de números aleatorios y otras utilidades.
- `*`: indica que se pueden utilizar las clases accesibles de ese paquete sin importarlas individualmente.

##### Clase

Una **clase** es una plantilla o molde que define las características y comportamientos de un objeto. Constituye uno de los conceptos fundamentales de la Programación Orientada a Objetos. En los videojuegos, las clases permiten modelar entidades como jugadores, enemigos, proyectiles, escenarios o elementos coleccionables. Cada objeto creado a partir de una clase hereda sus atributos y comportamientos.

- `public`: indica que la clase puede ser accesible desde otros lugares del programa, siempre que se cumplan las reglas de acceso de Java.
- `class`: es la palabra reservada para declarar una clase.
- `ClasePrincipal`: es el nombre que le damos a la clase.

**Ejemplo de una Clase en Java**
```Java
public class Jugador {
    String nombre;
    int vidas;
}
```

##### Las llaves `{ }`

Delimitar un bloque de código.

Las llaves indican dónde comienza y dónde termina una clase, un método o una estructura de control.

##### Método

Un **método** es un bloque de código que realiza una tarea específica dentro de una clase. Los métodos permiten organizar y reutilizar funcionalidades del programa. En el desarrollo de videojuegos, es común crear métodos para mover personajes, calcular colisiones, actualizar puntuaciones o reproducir sonidos.

###### Declarar el método principal del programa

`public static void main(String[] args)`

Este método es el punto de entrada convencional de una aplicación Java ejecutada directamente desde la JVM.

|Elemento|Función|
|---|---|
|`public`|Permite que el entorno de ejecución acceda al método.|
|`static`|Permite ejecutar el método sin crear previamente un objeto de `ClasePrincipal`.|
|`void`|Indica que el método no devuelve ningún valor.|
|`main`|Es el nombre del método de entrada.|
|`String[] args`|Recibe los argumentos de texto que se proporcionen al ejecutar el programa.|

##### main()

El método **main()** constituye el punto de entrada de una aplicación Java. Cuando se ejecuta un programa, la JVM busca este método para comenzar la ejecución del código. En un videojuego, el método _main()_ suele encargarse de inicializar recursos, crear ventanas y poner en marcha el ciclo principal del juego.

**Ejemplo de una Método en Java**
```Java
public class Jugador {
    void mover() {
        System.out.println("El jugador se mueve.");
    }
}
```

### Variables

Las **variables** son espacios de memoria utilizados para almacenar información que puede cambiar durante la ejecución del programa. En los videojuegos, las variables se utilizan para representar puntuaciones, posiciones, vidas, velocidades, energía o cualquier dato necesario para el funcionamiento del juego.

### Tipos de datos

Los **tipos de datos** determinan la naturaleza de la información que una variable puede almacenar. Java proporciona diversos tipos de datos que permiten representar números, caracteres, textos y valores lógicos. En los videojuegos, la selección adecuada del tipo de dato contribuye a _optimizar el uso de memoria y mejorar el rendimiento_ de la aplicación.

```Java
int puntos = 100;          // Entero
double velocidad = 2.5;   // Decimal
char direccion = 'D';     // Carácter
boolean vivo = true;      // Verdadero/Falso
String nombre = "Snake";  // Cadena de texto
```

##### Imprimir variables en Java

En Java puedes imprimir el valor de una variable utilizando `System.out.println()`. Este método muestra el contenido y agrega un salto de línea al final.

```Java
public class ClasePrincipal {
    public static void main(String[] args) {

        int puntos = 100;
        System.out.println(puntos);
    }
}
```

Para mostrar información más clara, se puede concatenar texto y variables utilizando el operador `+`.

```Java
System.out.println("Puntos: " + puntos);
```

##### var

`var` permite que Java deduzca automáticamente el tipo de dato de una variable a partir del valor con el que se inicializa.

```Java
var velocidad = 2.5;     // double
var direccion = 'D';     // char
var vivo = true;         // boolean
var nombre = "Snake";    // String
```

- Su principal ventaja es que permite escribir menos código cuando el tipo resulta evidente. 
- Es especialmente útil con tipos de datos largos o expresiones cuyo tipo es fácil de deducir.

##### Scanner

`Scanner` es una clase de Java que permite leer datos introducidos por el usuario, por ejemplo, desde la consola.

Para utilizarla, debes importar la clase:

```Java
import java.util.Scanner;
```

Después, creas un objeto `Scanner` asociado a la entrada estándar `System.in`:

```Java
Scanner entrada = new Scanner(System.in);
```

- `Scanner`: la clase que permite leer datos.
- `entrada`: el nombre de la variable que guarda la referencia al objeto.
- `new Scanner(...)`: crea el objeto.
- `System.in`: representa la entrada estándar, normalmente el teclado en la consola.

`Scanner` ofrece diferentes métodos para leer valores de distintos tipos. No siempre se necesita convertir manualmente el dato, se puedes utilizar directamente el método apropiado.

| **Tipo de dato**          | **Método**         | **Ejemplo de entrada** |
| ------------------------- | ------------------ | ---------------------- |
| `String` (palabra)        | `next()`           | `Snake`                |
| `String` (línea completa) | `nextLine()`       | `Mi primer videojuego` |
| `int`                     | `nextInt()`        | `100`                  |
| `double`                  | `nextDouble()`     | `2.5`                  |
| `float`                   | `nextFloat()`      | `2.5`                  |
| `long`                    | `nextLong()`       | `100000`               |
| `boolean`                 | `nextBoolean()`    | `true`                 |
| `char`                    | `next().charAt(0)` | `D`                    |
> [!warning]
> Los métodos numéricos esperan que la entrada tenga un formato válido. Por ejemplo, si se solicita un `int` y el usuario escribe `hola`, se producirá una excepción `InputMismatchException`.

**Ejemplo práctico: registrar los datos de un jugador**
```Java
import java.util.Scanner;

public class ClasePrincipal {

    public static void main(String[] args) {

        Scanner entrada = new Scanner(System.in);

        System.out.print("Nombre del jugador: ");
        String nombre = entrada.nextLine();

        System.out.print("Puntos iniciales: ");
        int puntos = entrada.nextInt();

        System.out.print("Velocidad del jugador: ");
        double velocidad = entrada.nextDouble();

        System.out.print("¿Está vivo? (true/false): ");
        boolean vivo = entrada.nextBoolean();

        System.out.print("Dirección inicial (D/I): ");
        char direccion = entrada.next().charAt(0);

        System.out.println("\n--- Datos del jugador ---");
        System.out.println("Nombre: " + nombre);
        System.out.println("Puntos: " + puntos);
        System.out.println("Velocidad: " + velocidad);
        System.out.println("¿Está vivo?: " + vivo);
        System.out.println("Dirección: " + direccion);

        entrada.close();
    }
}
```

El método `close()` se utiliza para cerrar un recurso que ya no se necesita y liberar los recursos asociados.

- `entrada.close()` cierra el objeto `Scanner` y, al estar asociado a `System.in`, también cierra la entrada estándar de la consola.

> [!important]
> `Scanner` puede presentar problemas al combinar `nextInt()` con `nextLine()`. Los métodos como `nextInt()` dejan pendiente el salto de línea que se produce al pulsar Enter. Si necesitas leer una línea después, normalmente debes consumir ese salto de línea con un `entrada.nextLine()` adicional.
> ```Java
>   
System.out.print("Nombre del jugador: ");  
String nombre = entrada.nextLine();  
  >
System.out.print("Puntos iniciales: ");  
int puntos = entrada.nextInt();  
entrada.nextLine();  
  >
System.out.print("Habilidad del jugador: ");  
String habilidad = entrada.nextLine();
> ```

##### Leer como `String` y convertir a un tipo específico

En ocasiones se recibe todo como texto y se requiere un tipo de dato en especial. Para eso puedes utilizar métodos de conversión como `Integer.parseInt()` o `Double.parseDouble()`.

```Java
String dato = entrada.nextLine();

int puntos = Integer.parseInt(dato);
double velocidad = Double.parseDouble(dato);
```

La diferencia está en que cada método espera un texto que represente un valor válido para el tipo solicitado.

| **Conversión**       | **Método**                    |
| -------------------- | ----------------------------- |
| `String` → `int`     | `Integer.parseInt(texto)`     |
| `String` → `double`  | `Double.parseDouble(texto)`   |
| `String` → `float`   | `Float.parseFloat(texto)`     |
| `String` → `long`    | `Long.parseLong(texto)`       |
| `String` → `boolean` | `Boolean.parseBoolean(texto)` |
##### Usar casting

El casting permite convertir un valor de un tipo compatible a otro. Por ejemplo, puedes convertir un `double` en un `int`:

```Java
double velocidad = 2.8;
int velocidadEntera = (int) velocidad;

System.out.println(velocidadEntera); // 2
```

Se pierde la parte decimal; el casting no redondea, sino que trunca el valor hacia cero.

### Operadores

Los **operadores** son símbolos utilizados para realizar operaciones sobre variables y valores. En un videojuego son fundamentales para calcular puntuaciones, actualizar posiciones, verificar colisiones y evaluar condiciones de victoria o derrota.

**Operadores aritméticos:**
```Java
int puntos = 10 + 5;       // Suma: 15
int vidas = 3 - 1;         // Resta: 2
int danio = 4 * 5;         // Multiplicación: 20
double velocidad = 10.0 / 4; // División: 2.5
int residuo = 10 % 3;      // Módulo: 1
```

**Jerarquía de operaciones**: Java sigue un orden de prioridad similar al de las matemáticas. Primero se resuelven los paréntesis, después las multiplicaciones, divisiones y módulos, y finalmente las sumas y restas. Cuando varios operadores tienen la misma prioridad, generalmente se evalúan de izquierda a derecha.

```Java
int resultado = 10 + 5 * 2;    // Resultado: 20
int resultado2 = (10 + 5) * 2; // Resultado: 30
```

**Operadores relacionales:**
```Java
puntos > 100   // ¿Los puntos son mayores que 100?
vidas == 0     // ¿El jugador se ha quedado sin vidas?
puntos < 50    // ¿Los puntos son menores que 50?
vidas >= 1     // ¿El jugador tiene al menos una vida?
puntos != 0    // ¿Los puntos son diferentes de cero?
```

**Operadores lógicos:**
```Java
vidas > 0 && puntos > 50
```

Los principales operadores lógicos son:

- `&&` (AND): ambas condiciones deben ser verdaderas.
- `||` (OR): basta con que una condición sea verdadera.
- `!` (NOT): invierte el valor lógico de una condición.

### Condicionales

Las **estructuras condicionales** permiten que un programa tome decisiones según determinadas condiciones. En los videojuegos son indispensables para controlar eventos, detectar victorias, gestionar colisiones y modificar el comportamiento de personajes.

**Estructura if**

La estructura `if` ejecuta un bloque de código únicamente cuando una condición es verdadera (`true`). Si la condición es falsa (`false`), el programa omite ese bloque y continúa con las siguientes instrucciones.

```Java
int vidas = 3;

if (vidas > 0) {
    System.out.println("El jugador sigue activo");
}
```

**Estructura if-else**

La estructura `if-else` permite establecer dos caminos posibles: uno cuando la condición es verdadera y otro cuando es falsa. El bloque `else` se ejecuta únicamente si la condición del `if` no se cumple.

```Java
int puntos = 120;

if (puntos >= 100) {
    System.out.println("Has ganado");
} else {
    System.out.println("Sigue jugando");
}
```

**Estructura if-else if-else**

La estructura `if-else if-else` permite evaluar varias condiciones en orden. Java comprueba cada condición hasta encontrar la primera verdadera y ejecuta únicamente el bloque correspondiente. Si ninguna se cumple, ejecuta el bloque `else`, cuando existe.

```Java
int puntos = 150;

if (puntos >= 200) {
    System.out.println("Rango: Oro");
} else if (puntos >= 100) {
    System.out.println("Rango: Plata");
} else if (puntos >= 50) {
    System.out.println("Rango: Bronce");
} else {
    System.out.println("Rango: Principiante");
}
```

> [!important]
> El orden de las condiciones influye en el resultado.

**Estructura switch-case**

La estructura `switch` permite seleccionar una acción entre varias alternativas según el valor de una expresión. Es especialmente útil cuando una variable puede tomar distintos valores definidos, como las opciones de un menú, los niveles de dificultad o los estados de un personaje.

```Java
int dificultad = 2;

switch (dificultad) {
    case 1:
        System.out.println("Dificultad fácil");
        break;
    case 2:
        System.out.println("Dificultad media");
        break;
    case 3:
        System.out.println("Dificultad difícil");
        break;
    default:
        System.out.println("Dificultad no válida");
        break;
}
```

Los elementos principales son:

- `switch`: evalúa la expresión que determina qué alternativa seleccionar.
- `case`: define un valor posible y el bloque de instrucciones que le corresponde.
- `break`: termina la ejecución del `switch` para evitar que continúe con los siguientes casos.
- `default`: define qué hacer cuando ningún `case` coincide con el valor evaluado.

### Bucles

Los **bucles** son estructuras de control que permiten repetir instrucciones múltiples veces. En el desarrollo de videojuegos son especialmente importantes porque facilitan la actualización continua del estado del juego. De hecho, el _Game Loop_ puede implementarse mediante estructuras iterativas que se ejecutan mientras la partida permanezca activa.

##### Bucle while

El bucle `while` repite un bloque de instrucciones mientras una condición sea verdadera (`true`). La condición se evalúa antes de cada repetición, por lo que, si es falsa desde el principio, el bloque no se ejecutará.

```Java
int vidas = 3;

while (vidas > 0) {
	System.out.println("Jugando...");
	vidas--;
}
```

##### Bucle `do-while`

El bucle `do-while` es similar a `while`, pero primero ejecuta las instrucciones y después comprueba la condición. Por esta razón, el bloque se ejecuta al menos una vez, aunque la condición sea falsa desde el inicio.

```Java
int intentos = 0;

do {
    System.out.println("Iniciando partida...");
    intentos++;
} while (intentos < 1);
```

##### Bucle for

El bucle `for` permite repetir instrucciones siguiendo una estructura que reúne la inicialización, la condición y la actualización de una variable de control. Es especialmente útil cuando se conoce previamente el número de repeticiones necesarias.

```Java
for (int i = 0; i < 5; i++) {
    System.out.println("Movimiento " + i);
}
```

La estructura contiene tres elementos:

- Inicialización (`int i = 0`): declara e inicializa la variable de control.
- Condición (`i < 5`): determina si el bucle debe continuar.
- Actualización (`i++`): incrementa la variable en una unidad después de cada iteración.

---

### Ejercicio 1. Calculadora básica

_Objetivo_: desarrollar un programa capaz de realizar operaciones aritméticas básicas a partir de los datos introducidos por el usuario.

_Descripción_: el programa solicitará dos números y un operador matemático. Posteriormente, utilizará una estructura `switch-case` para determinar qué operación realizar y mostrará el resultado en la consola.

Operaciones requeridas:

- Suma (`+`).
- Resta (`-`).
- Multiplicación (`*`).
- División (`/`).

Ejemplo de solución:
```Java
import java.util.Scanner;

public class Calculadora {
    public static void main(String[] args) {

        Scanner entrada = new Scanner(System.in);

        System.out.print("Introduce el primer número: ");
        double num1 = entrada.nextDouble();

        System.out.print("Introduce el segundo número: ");
        double num2 = entrada.nextDouble();

        System.out.print("Operación (+, -, *, /): ");
        char operador = entrada.next().charAt(0);

        switch (operador) {
            case '+':
                System.out.println("Resultado: " + (num1 + num2));
                break;

            case '-':
                System.out.println("Resultado: " + (num1 - num2));
                break;

            case '*':
                System.out.println("Resultado: " + (num1 * num2));
                break;

            case '/':
                if (num2 != 0) {
                    System.out.println("Resultado: " + (num1 / num2));
                } else {
                    System.out.println("Error: división entre cero.");
                }
                break;

            default:
                System.out.println("Operador no válido.");
        }

        entrada.close();
    }
}
```

#### Ejercicio 2. Conversor de unidades

_Objetivo_: desarrollar un programa que permita convertir una cantidad numérica entre diferentes unidades de medida mediante fórmulas matemáticas y estructuras condicionales.

_Descripción_: el programa solicitará una cantidad y una opción de conversión. Después, calculará el resultado y lo mostrará en la consola.

Conversiones requeridas:

- Kilómetros a metros.
- Metros a kilómetros.
- Celsius a Fahrenheit.
- Fahrenheit a Celsius.

Ejemplo de solución:
```Java
import java.util.Scanner;

public class Conversor {
    public static void main(String[] args) {

        Scanner entrada = new Scanner(System.in);

        System.out.println("=== Conversor de unidades ===");
        System.out.println("1. Kilómetros a metros");
        System.out.println("2. Metros a kilómetros");
        System.out.println("3. Celsius a Fahrenheit");
        System.out.println("4. Fahrenheit a Celsius");

        System.out.print("Selecciona una opción: ");
        int opcion = entrada.nextInt();

        System.out.print("Introduce la cantidad: ");
        double cantidad = entrada.nextDouble();

        double resultado;

        switch (opcion) {
            case 1:
                resultado = cantidad * 1000;
                System.out.println("Resultado: " + resultado + " metros");
                break;

            case 2:
                resultado = cantidad / 1000;
                System.out.println("Resultado: " + resultado + " kilómetros");
                break;

            case 3:
                resultado = (cantidad * 9 / 5) + 32;
                System.out.println("Resultado: " + resultado + " °F");
                break;

            case 4:
                resultado = (cantidad - 32) * 5 / 9;
                System.out.println("Resultado: " + resultado + " °C");
                break;

            default:
                System.out.println("Opción no válida.");
        }

        entrada.close();
    }
}
```


---

## Unidad 3. Introducción a la POO

#### Temas

- ¿Qué es un objeto?
- ¿Qué es una clase?
- POO
	- Encapsulamiento
	- Abstracción
	- Herencia
	- Polimorfismo

La **Programación Orientada a Objetos (POO)** es un paradigma de programación que organiza el software a partir de objetos que representan entidades del mundo real o elementos de un sistema digital. Este enfoque facilita el diseño de programas complejos mediante la división del problema en componentes más pequeños, reutilizables y fáciles de mantener. En el desarrollo de videojuegos, la POO resulta especialmente útil porque permite modelar personajes, enemigos, proyectiles, escenarios, inventarios y cualquier otro elemento del juego como objetos independientes que interactúan entre sí. Lenguajes como Java fueron diseñados para aprovechar las ventajas de este paradigma, convirtiéndolo en una herramienta fundamental para la creación de videojuegos modernos.

### ¿Qué es un objeto?

Un **objeto** es una entidad que posee características propias, denominadas atributos, y comportamientos, representados mediante métodos. Los objetos son las unidades fundamentales de la Programación Orientada a Objetos y pueden representar elementos reales o conceptuales dentro de una aplicación. En el contexto de los videojuegos, un objeto puede representar a un jugador, un enemigo, una moneda, una plataforma o cualquier elemento con el que se interactúe durante la partida. Cada objeto mantiene su propio estado y puede ejecutar acciones específicas de acuerdo con su propósito dentro del juego.

**Ejemplo:**

Un personaje de un videojuego puede tener:
- Nombre: "Mario"
- Vidas: 3
- Posición X: 100
- Posición Y: 200

Y realizar acciones como:
- Moverse
- Saltar
- Atacar

### ¿Qué es una clase?

Una **clase** es una plantilla o molde que define la estructura y comportamiento que tendrán los objetos creados a partir de ella. La clase especifica qué atributos y métodos poseerán sus instancias, permitiendo crear múltiples objetos con características similares. Desde la perspectiva del desarrollo de videojuegos, una clase puede utilizarse para definir un tipo de personaje, enemigo o elemento interactivo que posteriormente se utilizará múltiples veces dentro del juego.

**Ejemplo en Java:**
```Java
public class Jugador {

    String nombre;
    int vidas;

    void saltar() {
        System.out.println("El jugador salta");
    }
}
```

La clase define cómo será cualquier objeto de tipo **Jugador**.

### Relación entre Clase y Objeto

La relación entre una clase y un objeto puede entenderse mediante la analogía de un molde y una figura creada a partir de él.

#### Clase → Molde

Una clase define las características generales que tendrán los objetos.

**Ejemplo:**
```Java
public class Enemigo {
	int vida; // Atributo
		
    void recibirDanio(int danio) { // Método
        vida -= danio;
    }
}
```

- **Atributo:** 
	- Los **atributos** son variables declaradas dentro de una clase que representan las características o el estado de un objeto. En un videojuego, los atributos permiten almacenar información relevante sobre personajes, enemigos, proyectiles o cualquier elemento interactivo.

- **Método**: es un bloque de código definido dentro de una clase que representa una acción o comportamiento, como atacar, saltar o recibir daño.

Esta clase describe cómo debe ser cualquier enemigo del videojuego.

#### Objeto → Instancia

Un objeto es una instancia concreta creada a partir de una clase. Cada instancia posee valores propios para sus atributos.

**Ejemplo:**
```Java
Enemigo enemigo1 = new Enemigo();
Enemigo enemigo2 = new Enemigo();

enemigo1.vida = 100;
enemigo2.vida = 50;
```

| **Elemento**    | **Definición**                                                      |
| --------------- | ------------------------------------------------------------------- |
| `Enemigo`       | Clase que define la estructura y el comportamiento de los enemigos. |
| `enemigo1`      | Variable de referencia que apunta al primer objeto.                 |
| `new`           | Palabra reservada que crea una nueva instancia de la clase.         |
| `Enemigo()`     | Llamada al constructor de la clase para inicializar el objeto.      |
| `enemigo2`      | Variable de referencia que apunta al segundo objeto.                |
| `enemigo1.vida` | Acceso al atributo `vida` del primer enemigo.                       |
| `100` y `50`    | Valores asignados al atributo `vida` de cada objeto.                |
Aunque ambos objetos pertenecen a la misma clase, cada uno posee un estado independiente.

##### Constructor

Es un bloque especial de una clase que se ejecuta al crear un objeto y permite inicializar sus atributos. Tiene el mismo nombre que la clase y no posee un tipo de retorno.

Ejemplo en Java:
```Java
public class Enemigo {
    int vida;

    public Enemigo(int vidaInicial) {
        vida = vidaInicial;
    }
}
```

Para crear un objeto e inicializar su vida:
```Java
Enemigo enemigo1 = new Enemigo(100);
```

En este caso, el constructor asigna `100` al atributo `vida` del enemigo al momento de crearlo.
### Analogía aplicada a videojuegos

Si una clase representa el diseño de un enemigo tipo "Zombie", cada zombie que aparece en el mapa durante la partida corresponde a un objeto diferente creado a partir de esa misma clase.

### Los Cuatro Pilares de la Programación Orientada a Objetos

Los cuatro pilares de la POO constituyen los principios fundamentales que permiten construir software modular, reutilizable y mantenible. En esta unidad se realizará una primera aproximación conceptual a cada uno de ellos, ya que serán estudiados con mayor profundidad en unidades posteriores.

#### 1. Encapsulamiento

El **encapsulamiento** consiste en proteger los datos internos de un objeto para evitar que sean modificados de manera inadecuada desde otras partes del programa. Para lograrlo, Java proporciona modificadores de acceso como `private`, que restringen el acceso directo a los atributos.

> [!Note]
> Los modificadores de acceso en Java son palabras reservadas que establecen el nivel de visibilidad de los atributos, métodos y otros elementos de una clase. Su finalidad es controlar desde qué partes del programa se puede acceder a ellos, favoreciendo la encapsulación y la organización del código.
>
Java cuenta con cuatro niveles de acceso: `public`, `protected`, `private` y el _acceso por defecto_, también denominado package-private, que se obtiene cuando no se especifica ningún modificador.
>
El modificador `public` permite acceder al elemento desde cualquier clase que tenga acceso a él. `protected` permite el acceso desde clases del mismo paquete y desde clases que heredan de la clase que declara el elemento, incluso si estas se encuentran en otro paquete, sujeto a las reglas de acceso de Java. `private` restringe el acceso directo al elemento a la propia clase en la que está declarado. Por último, el acceso por defecto permite acceder al elemento únicamente desde clases pertenecientes al mismo paquete.
>
Estos modificadores pueden utilizarse tanto en atributos como en métodos. Por ejemplo, en el desarrollo de videojuegos, un atributo `vida` podría declararse como `private` para evitar que otras clases lo modifiquen directamente, mientras que un método `recibirDanio()` podría declararse como `public` para permitir que otros objetos soliciten esa acción. De esta manera, se controla cómo interactúan los componentes del videojuego y se protege la integridad de sus datos.

En el desarrollo de videojuegos, el encapsulamiento permite proteger información sensible de un personaje, como su posición, salud o puntuación, evitando alteraciones incorrectas que puedan producir errores en la lógica del juego.

**Ejemplo:**
```Java
public class Jugador {
    private int x;
    private int y;
}
```

En este caso, las coordenadas del jugador están protegidas y no pueden ser modificadas directamente desde otras clases.

Puede imaginarse que el encapsulamiento actúa como una barrera de seguridad que controla cómo interactúan los distintos componentes del videojuego.

#### 2. Abstracción

La **abstracción** consiste en representar los aspectos esenciales de un objeto ignorando los detalles innecesarios para un contexto determinado. Gracias a la abstracción, es posible modelar elementos complejos mediante estructuras más simples y comprensibles.

En el desarrollo de videojuegos, la abstracción permite representar objetos reales mediante clases. Por ejemplo, un personaje dentro del juego no necesita incluir absolutamente todas las características de una persona real; únicamente aquellas que son relevantes para la mecánica del juego, como posición, velocidad, puntos de vida o capacidad de ataque.

**Ejemplo:**
```Java
public class Personaje {
    String nombre;
    int vida;
    int velocidad;
}
```

Esta clase representa únicamente las características necesarias para el funcionamiento del videojuego.

##### Ejemplo conceptual

Un automóvil real posee miles de componentes mecánicos. En un videojuego de carreras podría representarse únicamente mediante atributos como:

- Velocidad
- Combustible
- Posición
- Estado del vehículo

La abstracción permite simplificar la realidad para facilitar su implementación en software.

#### 3. Herencia

La **herencia** es un mecanismo que permite crear nuevas clases a partir de otras existentes, reutilizando atributos y comportamientos ya definidos. Gracias a este principio es posible evitar la duplicación de código y establecer relaciones jerárquicas entre entidades similares.

Dentro de un videojuego es común encontrar múltiples personajes que comparten características generales. Por ejemplo, un héroe, un enemigo y un comerciante pueden tener nombre, posición y puntos de vida. La herencia permite definir estas características comunes en una clase base y reutilizarlas posteriormente.

**Ejemplo conceptual:**
```Text
Personaje
│
├── Jugador
├── Enemigo
└── NPC
```

> [!Note]
> En esta unidad aún no se implementará técnicamente la herencia; sin embargo, resulta importante comprender que este mecanismo permite construir jerarquías de clases que reflejan las relaciones existentes entre los elementos de un videojuego.

#### 4. Polimorfismo

El **polimorfismo** es la capacidad que tienen distintos objetos de responder de manera diferente a una misma acción. Este principio permite que elementos relacionados compartan una interfaz común mientras implementan comportamientos específicos según sus características particulares.

En el desarrollo de videojuegos, diversos personajes pueden ejecutar una misma acción general, como atacar o moverse, pero cada uno puede realizarla de manera distinta. Por ejemplo, un arquero dispara flechas, un mago lanza hechizos y un guerrero utiliza una espada; sin embargo, todos están ejecutando la acción "atacar".


---

## Unidad 4. Modelado del videojuego

Antes de comenzar a programar un videojuego es necesario realizar un proceso de **modelado**, cuyo propósito consiste en identificar los elementos que existirán dentro del sistema y definir cómo se relacionarán entre sí. En Ingeniería de Software, el modelado permite transformar una idea o problema en una representación estructurada que facilite su implementación mediante código. En el desarrollo de videojuegos, esta etapa resulta fundamental porque ayuda a identificar los objetos, reglas y comportamientos que conformarán la experiencia de juego. Para el caso de _Snake_, antes de escribir algoritmos complejos, es conveniente preguntarse: **¿qué objetos existen en nuestro juego?**. A partir de esta pregunta se identifican tres elementos principales: **Snake**, que representa al jugador; **Food**, que representa la comida que debe consumir la serpiente; y **Position**, que representa la ubicación de los elementos dentro del tablero.

### Análisis inicial del videojuego Snake

Desde una perspectiva orientada a objetos, el videojuego _Snake_ puede modelarse como un conjunto de entidades que interactúan constantemente durante la ejecución del juego. La serpiente necesita conocer dónde se encuentra dentro del tablero, la comida requiere una posición específica para aparecer y ambos elementos deben compartir una forma común de representar coordenadas. Este análisis permite identificar responsabilidades claras para cada clase y construir una base sólida sobre la cual se desarrollarán posteriormente las mecánicas del videojuego.

```Text
Snake
│
└── tiene una Position

Food
│
└── tiene una Position

Position
├── x
└── y
```

### Clase Position

La clase **Position** constituye el primer contacto formal del estudiante con la Programación Orientada a Objetos aplicada a videojuegos. El objetivo es representar una ubicación dentro del tablero mediante coordenadas. Gracias a esta clase, cualquier objeto del juego que necesite una posición podrá reutilizar la misma estructura de datos.

#### Atributos

Para la clase `Position`, los atributos representan las coordenadas horizontales y verticales dentro del tablero.

```Java
public class Position {
	private int x;
	private int y;
}
```

En este ejemplo:

- `x` representa la coordenada horizontal.
- `y` representa la coordenada vertical.

Si el tablero fuera una cuadrícula, una posición `(5,3)` significaría que el objeto se encuentra en la columna 5 y fila 3.

### Constructor

Un constructor es un bloque especial de código perteneciente a una clase cuya función consiste en **inicializar los atributos de un objeto cuando este es creado**. _Su nombre debe coincidir exactamente con el de la clase_ y, a diferencia de los métodos convencionales, no tiene un tipo de retorno. En términos sencillos, funciona como una configuración inicial que se realiza automáticamente al crear un objeto, estableciendo los valores con los que comenzará a funcionar.

En el desarrollo de videojuegos, los constructores permiten que los objetos aparezcan con valores iniciales válidos desde el momento en que son creados. Por ejemplo, al crear un enemigo, su constructor puede establecer automáticamente su cantidad de vida, velocidad, nombre y nivel de dificultad. De esta manera, _cada objeto comienza con las características necesarias para participar en el videojuego_, sin tener que asignar sus valores individualmente después de crearlo.

**Ejemplo:**
```Java
public class Position {

    private int x;
    private int y;

    public Position(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```

Creación de un objeto:
```Java
Position posicionInicial = new Position(5, 3);
```

La palabra clave `this` hace referencia al propio objeto con el que se está trabajando dentro de una clase. Permite identificar sus atributos y métodos, diferenciarlos de otras variables y acceder a sus propios elementos. _Se utiliza especialmente en los constructores_ cuando se necesita distinguir un atributo de la clase de un parámetro que tiene el mismo nombre. En términos sencillos, `this` significa **este objeto**, es decir, el objeto actual que está ejecutando una instrucción.

### Getters

Los getters son _métodos públicos_ utilizados para consultar u obtener el valor de los atributos privados de una clase. Funcionan como un medio de acceso controlado a la información de un objeto, permitiendo que otras partes del programa puedan conocer sus datos sin necesidad de acceder directamente a las variables que los almacenan. Generalmente, su nombre comienza con la palabra `get`, seguida del nombre del atributo que se desea consultar.

Forman parte de las buenas prácticas de encapsulamiento, ya que permiten proteger la información interna de un objeto y controlar la manera en que otros componentes del programa pueden consultarla. Por ejemplo, en un videojuego, un método `getVida()` permite conocer cuántos puntos de vida tiene un personaje sin permitir que otras clases modifiquen directamente ese valor.

**Ejemplo:**
```Java
public class Position {

    private int x;
    private int y;

    public Position(int x, int y) {
        this.x = x;
        this.y = y;
    }
    public int getX() {
        return x;
    }
    public int getY() {
        return y;
    }
}
```

Uso:
```Java
Position posicion = new Position(10, 4);

System.out.println(posicion.getX());
System.out.println(posicion.getY());
```

### Encapsulamiento

En videojuegos, el encapsulamiento evita que otros componentes modifiquen accidentalmente información crítica, como la posición de un personaje o su cantidad de vidas.

```Java
private int x;
private int y;
```

La palabra reservada `private` impide que otras clases accedan directamente a estos atributos.

### Clase Direction

Durante el desarrollo de Snake, la serpiente solamente puede desplazarse en cuatro direcciones: arriba, abajo, izquierda y derecha. Una forma adecuada de representar y controlar este comportamiento es mediante una enumeración o **enum**, que permite establecer las opciones de movimiento disponibles para el personaje.

Un **enum** es un tipo especial de dato que permite definir un conjunto fijo y limitado de valores constantes. A diferencia de una variable convencional, que puede almacenar diferentes valores dentro de su tipo de dato, una enumeración establece previamente las opciones permitidas. Esto facilita la organización del código, mejora su legibilidad y reduce la posibilidad de introducir valores incorrectos o no contemplados durante el desarrollo.

En el caso de Snake, podemos crear una enumeración llamada `Direccion` que contenga únicamente las cuatro direcciones posibles. De esta manera, cuando necesitemos modificar el movimiento de la serpiente, podremos utilizar uno de esos valores en lugar de escribir textos o números que representen cada dirección. Esto permite que el programa identifique claramente hacia dónde debe desplazarse el personaje y facilita la administración de su comportamiento.

#### enum

```Java
public enum Direction {
    UP,
    DOWN,
    LEFT,
    RIGHT
}
```

Uso:
```Java
Direction direccionActual = Direction.RIGHT;
```

Aplicación en Snake:
```Java
if (direccionActual == Direction.UP) {
    System.out.println("La serpiente se mueve hacia arriba");
}
```

La ventaja de utilizar un enum es que se evita escribir cadenas de texto como `"arriba"` o `"derecha"`, reduciendo errores tipográficos y facilitando el mantenimiento del código.

### Clase Food

La clase **Food** representa el alimento que la serpiente debe consumir para crecer y aumentar la puntuación del jugador.

Desde la perspectiva del modelado orientado a objetos, la comida posee una posición específica dentro del tablero. Para ello se reutiliza la clase `Position` previamente definida.

#### Composición básica

La composición es una relación entre clases en la que un objeto contiene uno o varios objetos de otras clases como parte de su propia estructura. En términos sencillos, significa que un objeto está formado por otros objetos que le permiten tener características o funcionalidades específicas. De esta manera, en lugar de concentrar toda la información y el comportamiento en una sola clase, podemos dividir las responsabilidades en diferentes clases que trabajan conjuntamente.

En este tipo de relación, los objetos que forman parte de otro se consideran componentes de su estructura. Por ejemplo, en un videojuego como Snake, un objeto `Food` (comida) necesita conocer su ubicación dentro del escenario. Para representar esa ubicación, puede utilizar un objeto `Position` (posición), que almacena las coordenadas donde debe aparecer la comida.

```Java
public class Food {
    private Position position;
}
```

En este ejemplo, `Food` contiene un atributo de tipo `Position`, lo que significa que cada objeto de comida tiene asociada una posición dentro del escenario. En lugar de almacenar directamente las coordenadas `x` e `y` dentro de `Food`, se utiliza otra clase especializada en administrar posiciones.

La frase **Food tiene una Positio** describe precisamente esta relación de composición. Este enfoque permite reutilizar clases, organizar mejor el código y facilitar el mantenimiento del videojuego, ya que cada clase se encarga de una responsabilidad específica.

> [!Note]
> En sentido estricto, la composición implica que el objeto principal controla el ciclo de vida de sus componentes; es decir, estos forman parte de él y dependen de su existencia. Si únicamente existe una referencia a otro objeto sin esa dependencia, podría tratarse de una _asociación_ o _agregación_, dependiendo del contexto.










---
---

# MÓDULO 2

# Programación Orientada a Objetos Aplicada a Videojuegos

#### Objetivo

Construir el modelo completo del videojuego utilizando principios de POO.

## Unidad 1. Profundización en POO

#### Encapsulamiento

Uso de:

```Java
private
public
```

#### Abstracción

Identificar únicamente los atributos relevantes.

Ejemplo:

```Java
Snake
```

No necesita color de ojos.

Sí necesita:
- posición
- dirección
- cuerpo

---

## Unidad 2. Colecciones en Java

#### Temas

- ArrayList
- LinkedList

Aplicación:

```Java
LinkedList<Position>
```

para el cuerpo de la serpiente.

---

## Unidad 3. Diseño del modelo Snake

#### Clase Snake

Temas:

- Composición.
- Objetos dentro de objetos.
- Métodos de negocio.

Implementación:

```Java
move()
grow()
setDirection()
```

---

## Unidad 4. Introducción a la Arquitectura del Proyecto

##### ¿Por qué no poner todo en una sola clase?

Problemas:

- Difícil mantenimiento.
- Difícil escalabilidad.
- Código acoplado.

#### Introducción a la arquitectura

##### Model

Representa datos.
- Snake
- Food
- Position
- Direction

##### Engine

Controla reglas del juego.
- GameLoop

##### UI

Dibuja información.
- GameView

##### Config

Centraliza configuración.
- GameConfig

#### Desarrollo del proyecto

Implementación completa de:

```
model
├── Position
├── Food
├── Direction
└── Snake
```

---

#### Entregable

La serpiente puede:

- Existir.
- Moverse lógicamente.
- Crecer.
- Cambiar dirección.

Aún no hay interfaz visual.

---
---

# MÓDULO 3

# Fundamentos de Desarrollo de Videojuegos con JavaFX

## Objetivo

Crear la interfaz gráfica y comprender cómo funciona un motor básico de videojuegos.

## Unidad 1. Introducción a JavaFX

#### Temas

- Stage.
- Scene.
- Canvas.
- GraphicsContext.

---

## Unidad 2. Arquitectura de un videojuego

#### Teoría

Todo videojuego sigue:

```
Input
↓
Update
↓
Render
```

---

## Unidad 3. El Game Loop

Concepto fundamental.

Un videojuego:
- No espera acciones.
- Se actualiza continuamente.

---

## Unidad 4. El motor del videojuego

Implementación de:
- Timeline
- KeyFrame

#### Aplicación de POO

##### Abstracción

```Java
GameLoop
```

representa el mecanismo interno del juego.

##### Encapsulamiento

Variables internas:

```Java
private Timeline timeline;
private boolean gameOver;
```

#### Desarrollo del proyecto

##### Clase GameView

Implementar:

```Java
render()
drawSnake()
drawFood()
```

##### Clase SnakeGame

Implementar:
- Stage
- Scene
- Eventos de teclado

##### Clase Launcher

Configurar punto de entrada.

---

#### Entregable

Ya existe:
- Ventana.
- Serpiente visible.
- Comida visible.
- Movimiento mediante teclado.

---
---

# MÓDULO 4

# Desarrollo Completo del Videojuego Snake

#### Objetivo

Finalizar el videojuego aplicando arquitectura, POO y lógica de videojuegos.

## Unidad 1. Diseño del Motor del Juego

#### Clase

```Java
GameLoop
```

Implementación completa.

---

## Unidad 2. Detección de Colisiones

#### Temas

Colisión con:
- Paredes.
- Cuerpo propio.
- Comida.

---

## Unidad 3. POO Avanzada

Aquí se realiza una revisión formal de los cuatro pilares.

#### Encapsulamiento

Protección del estado interno.

Ejemplos dentro de:
- Snake
- Position
- Food

#### Abstracción

Separar:
- Qué hace una clase
de
- Cómo lo hace

#### Herencia

Uso conceptual y ejemplos.

Por ejemplo:
```
GameObject
↓
Java
Snake
Food
```

(Extensión opcional del proyecto.)

#### Polimorfismo

Uso conceptual y práctico.

Ejemplo:
```Java
draw(GameObject object)
```

Capaz de trabajar con distintos objetos.

---

## Unidad 4. Integración del videojuego

Implementación final de:

```Java
GameLoop
```

- Crecimiento.
- Puntuación.
- Colisiones.
- Game Over.

---

## Unidad 5. Refactorización y Mejores Prácticas

#### SOLID (introducción)

#### Separación de responsabilidades

#### Organización por capas

#### Arquitectura del videojuego

