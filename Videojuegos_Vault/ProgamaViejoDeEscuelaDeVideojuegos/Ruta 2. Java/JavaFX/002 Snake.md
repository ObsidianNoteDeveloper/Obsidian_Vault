
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

¿Qué es un objeto?

¿Qué es una clase?

Relación entre:
```Java
Clase → Molde
Objeto → Instancia
```

#### Los 4 pilares de la POO

Primera introducción.

##### Encapsulamiento

```Java
private int x;
private int y;
```

##### Abstracción

Representar objetos reales mediante clases.

##### Herencia

Introducción conceptual.

##### Polimorfismo

Introducción conceptual.

**Nota:** todavía no se implementan completamente.

---

## Unidad 4. Modelado del videojuego

Antes de escribir código se modela Snake.

#### Pregunta guía

¿Qué objetos existen en nuestro juego?

Resultado:
- Snake
- Food
- Position

#### Desarrollo del proyecto

#### Clase Position

Primer contacto con POO.

```Java
public class Position
```

Temas:

- Atributos.
- Constructor.
- Getters.
- Encapsulamiento.

#### Clase Direction

Primer enum.

```Java
public enum Direction
```

#### Clase Food

Composición básica.

```Java
private Position position;
```

#### Clase GameConfig

Introducción a constantes.

```Java
public static final
```

---

#### Entregable del módulo

```
config
└── GameConfig

model
├── Position
├── Food
└── Direction
```

El alumno ya tiene sus primeras clases del juego.

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

