
### Índice

[[#Descripción del Módulo]]

[[#Tema 1. Fundamentos de POO]]
	[[#1.1 Conceptos de objeto]] 
	[[#1.2 Clases]]
	[[#1.3 Atributos]] 
	[[#1.4 Métodos]]
	[[#Ejercicio de Integración]]
	
[[#Tema 2. Interacción entre objetos]]
	[[#2.1 Comunicación entre objetos]]
	[[#2.2 Simulación de colisiones]]
	[[#2.3 Actualización de estados]]
	
[[#Tema 3. Organización del proyecto]]
	[[#3.1 Separación de clases]]
	[[#3.2 Modularidad]]
	[[#3.3 Organización de archivos]] 

[[#Actividad Integradora]]

---
---

## Descripción del Módulo 

Este módulo introduce los fundamentos de la **Programación Orientada a Objetos (POO)** aplicados al desarrollo de videojuegos, permitiendo comprender cómo se estructuran personajes, enemigos, sistemas y mecánicas dentro de un proyecto interactivo. A lo largo de los temas se estudian conceptos esenciales como objetos, clases, atributos y métodos, los cuales constituyen la base para modelar entidades dentro de un videojuego de forma organizada y reutilizable. Además, se analiza cómo los objetos interactúan entre sí mediante comunicación, colisiones y actualización de estados, permitiendo construir sistemas dinámicos como combate, movimiento e inteligencia artificial. Finalmente, el módulo aborda principios de organización profesional del proyecto, incluyendo separación de clases, modularidad y estructura de archivos, con el objetivo de desarrollar videojuegos más escalables, ordenados y fáciles de mantener.

---
---
# Tema 1. Fundamentos de POO

La **Programación Orientada a Objetos (POO)** es un paradigma de desarrollo que organiza el software a partir de “objetos”, los cuales representan entidades del mundo real o del sistema que se está construyendo. Cada objeto se define mediante una clase, que establece sus características (atributos) y comportamientos (métodos), permitiendo estructurar el código de forma más clara, modular y reutilizable. Entre sus principios fundamentales se encuentran el encapsulamiento, que protege la información interna del objeto; la herencia, que permite reutilizar y extender funcionalidades; y el polimorfismo, que facilita el uso de una misma interfaz para distintos tipos de objetos. En conjunto, estos fundamentos permiten desarrollar sistemas más organizados, escalables y fáciles de mantener, siendo ampliamente utilizados en áreas como el desarrollo de software, videojuegos y aplicaciones web.

---
## 1.1 Conceptos de objeto 

En la **Programación Orientada a Objetos (POO)**, un _objeto_ es una representación de algo que existe dentro de un sistema, con características y comportamientos propios. En el contexto de los videojuegos, los objetos son la base de todo lo que ves e interactúas: un jugador, un enemigo, una bala, un ítem o incluso el escenario pueden modelarse como objetos. Cada uno contiene información (atributos) y acciones (métodos) que definen cómo se comporta dentro del juego.

> [!note]
> Un objeto combina **datos + comportamiento**. No es solo información, también “sabe” qué puede hacer.

Por ejemplo, en un videojuego sencillo, un objeto _Jugador_  podría tener atributos como `vida`, `posición` y `nombre`, y métodos como `mover()`, `atacar()` o `recibir_daño()`. Esto permite que el código sea más organizado, ya que cada entidad del juego gestiona su propia lógica, en lugar de tener todo mezclado en funciones globales.

> [!warning]
Creer que un objeto es solo una variable cuando en realidad, es una estructura completa que modela comportamiento.


---
## 1.2 Clases

En la Programación Orientada a Objetos (POO), una **clase** es una plantilla o modelo que define cómo serán los objetos dentro de un programa. Una clase establece las características y comportamientos que compartirán todos los objetos creados a partir de ella. En el desarrollo de videojuegos, las clases son fundamentales porque permiten organizar de manera estructurada todos los elementos del juego, desde personajes y enemigos hasta armas, vehículos o sistemas de inventario.

Cuando un desarrollador diseña un videojuego, normalmente comienza identificando las entidades principales que existirán dentro del mundo virtual. Cada una de estas entidades puede convertirse en una clase. Por ejemplo, un videojuego de aventura puede incluir clases como:

- Jugador
- Enemigo
- NPC
- Arma
- Proyectil
- Inventario

Cada clase representa un “molde” que define qué información tendrá un objeto y qué acciones podrá realizar.

#### Las clases dentro de un videojuego

Las clases permiten que los videojuegos estén organizados y sean escalables. En lugar de programar cada personaje desde cero, se crea una clase base que sirva como referencia para múltiples objetos.

Por ejemplo, en un juego de disparos, todos los enemigos pueden compartir ciertas características:

- Vida
- Velocidad
- Daño
- Posición

Y también ciertos comportamientos:

- Moverse
- Atacar
- Recibir daño

La clase funciona como una estructura reutilizable. Gracias a esto, el desarrollador puede crear muchos enemigos diferentes sin repetir lógica constantemente.

> [!important] 
> Una clase no es el personaje del juego en sí, sino el diseño que define cómo serán todos los personajes creados a partir de ella.

#### Construcción de una clase base

En videojuegos es común utilizar **clases base** para representar entidades generales del juego. Una clase base contiene atributos y comportamientos comunes que posteriormente pueden heredarse hacia otras clases más específicas.

Por ejemplo, una clase general llamada `Personaje` podría incluir:

- Vida
- Nombre
- Posición
- Movimiento

A partir de ella podrían derivarse otras entidades:

- Jugador
- Enemigo
- Jefe final (Boss)

Esto permite reutilizar lógica y mantener una estructura más limpia.

---

## 1.3 Atributos 

En la Programación Orientada a Objetos (POO), los **atributos** son las características o propiedades que describen a un objeto. Representan la información que un objeto necesita almacenar para existir y comportarse dentro de un sistema. En el desarrollo de videojuegos, los atributos permiten definir el estado de personajes, enemigos, armas y cualquier otro elemento del juego, haciendo posible que cada entidad tenga propiedades únicas y dinámicas.

Por ejemplo, un personaje dentro de un videojuego puede necesitar almacenar información como:

- Nombre
- Vida
- Energía
- Velocidad
- Posición
- Nivel
- Inventario

Todos estos datos son atributos porque describen las condiciones actuales del personaje dentro del mundo virtual.

#### Los atributos en los videojuegos

En los videojuegos, prácticamente todo funciona mediante atributos. Cada objeto del juego posee información específica que determina cómo interactúa con el entorno y con otros objetos.

Un enemigo puede tener:

- Vida
- Daño
- Velocidad de ataque

Mientras que un vehículo puede tener:

- Combustible
- Velocidad máxima
- Resistencia

Los atributos permiten que el juego tenga variedad, estadísticas y mecánicas dinámicas.

> [!tip]
> Los atributos representan “lo que un objeto es” o “lo que un objeto tiene”.

#### Diseño de atributos para un personaje

Cuando se diseña un personaje para un videojuego, uno de los primeros pasos consiste en definir qué atributos necesita para funcionar correctamente dentro del juego.

Algunos de los atributos más comunes son:

|Atributo|Función|
|---|---|
|Vida|Cantidad de daño que puede soportar|
|Posición|Lugar donde se encuentra en el mapa|
|Velocidad|Rapidez con la que se mueve|
|Energía|Recursos para habilidades especiales|
|Nivel|Progreso del personaje|
|Experiencia|Puntos acumulados|
|Daño|Fuerza de ataque|

Estos atributos ayudan a construir la jugabilidad y las mecánicas del sistema.

> [!abstract] Atributos estáticos y dinámicos
>
Existen atributos que permanecen constantes y otros que cambian durante la partida.
>
> **Atributos estáticos**
Cambian poco o nunca:
>- Nombre
>- Tipo de personaje
>- Clase
>
>**Atributos dinámicos**
Se modifican constantemente:
>- Vida
>- Energía
>- Posición
>- Munición
>
Esto permite que el videojuego reaccione en tiempo real a las acciones del jugador.

> [!warning] 
> **Buen diseño de atributos**  
Un exceso de atributos puede volver un sistema difícil de mantener. Es importante definir únicamente las propiedades necesarias para el funcionamiento del juego.

---

## 1.4 Métodos

En la Programación Orientada a Objetos (POO), los **métodos** son las acciones o comportamientos que un objeto puede realizar. Mientras que los atributos representan las características de un objeto, los métodos definen lo que ese objeto es capaz de hacer dentro del sistema. En el desarrollo de videojuegos, los métodos son esenciales porque permiten controlar la interacción entre personajes, enemigos, escenarios y mecánicas de juego.

Por ejemplo, un personaje dentro de un videojuego puede realizar acciones como:

- Moverse
- Saltar
- Atacar
- Recibir daño
- Recoger objetos
- Curarse

Cada una de estas acciones se representa mediante métodos que controlan el comportamiento del personaje durante la partida.

#### Los métodos dentro de un videojuego

En un videojuego moderno, prácticamente todo ocurre gracias a métodos. Cada vez que el jugador presiona una tecla o realiza una acción, el sistema ejecuta métodos específicos para responder a esa interacción.

Por ejemplo:

- Al presionar una tecla de movimiento → se ejecuta el método de desplazamiento.
- Al atacar → se activa el método de combate.
- Al recibir un impacto → se ejecuta el método que reduce la vida.

Los métodos permiten que el mundo del juego sea dinámico e interactivo.

> [!tip]
> Los métodos representan “lo que un objeto puede hacer”.

#### Métodos comunes en personajes de videojuegos

Cuando se diseña un personaje en un videojuego, normalmente se implementan métodos básicos que permiten controlar su comportamiento.

Algunos de los más comunes son:

|Método|Función|
|---|---|
|Moverse|Desplazar al personaje|
|Saltar|Cambiar de posición vertical|
|Atacar|Realizar daño a un enemigo|
|Recibir daño|Reducir puntos de vida|
|Curarse|Recuperar salud|
|Defenderse|Disminuir daño recibido|

Estos métodos forman parte de la lógica central del gameplay.

> [!info]
El término **gameplay** se refiere a la forma en que un videojuego se juega y a la experiencia interactiva que tiene el jugador mientras utiliza el juego. En otras palabras, describe cómo funcionan las mecánicas, controles, reglas y acciones dentro del videojuego.

#### Métodos en inteligencia artificial

Los enemigos controlados por computadora también utilizan métodos para comportarse dentro del juego.

Por ejemplo:

- Patrullar
- Perseguir jugador
- Atacar automáticamente
- Huir
- Defenderse

Esto permite crear enemigos más complejos y realistas.

---

> [!success]
> **Diseño modular**  
> Dividir las acciones en métodos pequeños facilita el mantenimiento y mejora la organización del proyecto.

---

## Integración de los fundamentos de POO

Después de comprender qué son los objetos, las clases, los atributos y los métodos, el siguiente paso consiste en combinar todos estos elementos para modelar una entidad completa dentro del juego. En este caso, la integración se enfoca en el desarrollo de un personaje jugable con características y comportamientos básicos.

En los videojuegos, un personaje jugable representa una de las entidades más importantes del sistema, ya que es el medio principal de interacción entre el jugador y el mundo virtual. Para construirlo correctamente, es necesario integrar tanto la información que lo describe como las acciones que puede realizar.

#### Integración de objetos y clases

El proceso comienza identificando al personaje como un **objeto** dentro del videojuego. Este objeto se crea a partir de una **clase**, la cual funciona como una plantilla que define todas sus propiedades y comportamientos.

La clase del personaje puede incluir información relacionada con:

- Vida
- Posición
- Velocidad
- Energía
- Nombre

Además de acciones como:

- Moverse
- Atacar
- Saltar
- Recibir daño

La integración de estos componentes permite representar un personaje completo y funcional dentro del sistema.

> [!tip]  
> Un personaje jugable no se construye únicamente con datos o acciones aisladas; surge de la integración entre atributos y métodos dentro de una misma estructura organizada.

#### Construcción de un personaje jugable

Al diseñar un personaje para un videojuego, es importante definir primero qué papel tendrá dentro de la experiencia de juego.

Por ejemplo:

- ¿Será rápido o resistente?
- ¿Podrá usar armas?
- ¿Tendrá habilidades especiales?
- ¿Cómo interactuará con enemigos y escenarios?

Estas decisiones influyen directamente en los atributos y métodos que formarán parte del personaje.

Los atributos representan el estado del personaje durante la partida. Algunos de los más comunes son:

|Atributo|Función|
|---|---|
|Vida|Resistencia del personaje|
|Posición|Ubicación dentro del mapa|
|Velocidad|Rapidez de movimiento|
|Energía|Uso de habilidades especiales|
|Daño|Poder ofensivo|

Gracias a estos atributos, el personaje puede reaccionar dinámicamente a las acciones del juego.

Por ejemplo:

- Al recibir daño, disminuye la vida.
- Al moverse, cambia la posición.
- Al correr, aumenta temporalmente la velocidad.

Los métodos permiten que el personaje interactúe con el entorno y otros objetos del juego.

Entre los comportamientos básicos más importantes se encuentran:

- Movimiento
- Ataque
- Defensa
- Recepción de daño
- Interacción con objetos

Estos métodos modifican constantemente los atributos del personaje, generando una experiencia interactiva y dinámica.

---

> [!warning] 
> **Importancia del diseño equilibrado**  
> Un personaje con demasiadas habilidades o atributos desbalanceados puede afectar negativamente la jugabilidad y la experiencia del usuario.

#### Relación entre atributos y métodos

La integración real ocurre cuando los métodos utilizan y modifican atributos para producir comportamientos dentro del juego.

Por ejemplo:

|Método|Atributo afectado|
|---|---|
|Moverse|Posición|
|Atacar|Energía|
|Recibir daño|Vida|
|Correr|Velocidad|

Esto permite que el personaje cambie continuamente de estado mientras el jugador interactúa con el sistema.

> [!success] Ejemplo conceptual de integración
>
Imagina un videojuego de aventura donde el jugador controla un guerrero.
>
**El personaje posee atributos como:**
>
>- Vida
>- Energía
>- Velocidad
>- Fuerza
>
**Y métodos como:**
>
>- Moverse
>- Atacar
>- Defenderse
>- Recibir daño
>
Cuando el jugador presiona una tecla:
>
>- El método de movimiento actualiza la posición.
>- El método de ataque reduce la vida del enemigo.
>- El método de recibir daño disminuye la salud del personaje.
>
Todo el sistema funciona gracias a la integración entre objetos, clases, atributos y métodos.

---
---
# Tema 2. Interacción entre objetos

El tema de **Interacción entre objetos** aborda la manera en que las distintas entidades de un videojuego se comunican y colaboran entre sí para generar comportamientos dinámicos dentro del sistema. En la Programación Orientada a Objetos (POO), los objetos no funcionan de forma aislada, sino que constantemente intercambian información mediante métodos y atributos para responder a eventos, ejecutar acciones y modificar el estado del juego. En el desarrollo de videojuegos, esta interacción permite crear mecánicas fundamentales como el combate entre jugador y enemigo, la recolección de objetos, las colisiones y la inteligencia artificial. Comprender cómo se relacionan los objetos es esencial para diseñar videojuegos más organizados, interactivos y escalables, ya que permite construir sistemas donde cada entidad cumple una función específica dentro del mundo virtual.

---

## 2.1 Comunicación entre objetos

En la Programación Orientada a Objetos (POO), los objetos no funcionan de manera aislada; constantemente necesitan interactuar entre sí para construir sistemas dinámicos y funcionales. Esta interacción se conoce como **comunicación entre objetos** y permite que distintas entidades colaboren para ejecutar acciones dentro de un programa. En el desarrollo de videojuegos, esta comunicación es fundamental, ya que prácticamente todas las mecánicas dependen de la interacción entre personajes, enemigos, escenarios y otros elementos del juego.

Por ejemplo, en un videojuego de acción:

- El jugador ataca a un enemigo.
- El enemigo recibe daño.
- Un proyectil impacta contra un objeto.
- Un ítem aumenta la vida del personaje.

Cada una de estas situaciones ocurre gracias a la comunicación entre objetos mediante métodos y atributos.

#### Comunicación entre objetos en videojuegos

En un videojuego, cada entidad suele representarse como un objeto independiente. Sin embargo, para que el mundo virtual funcione correctamente, estos objetos deben intercambiar información y reaccionar mutuamente.

Por ejemplo:

- Un enemigo necesita detectar la posición del jugador.
- El jugador necesita afectar la vida del enemigo al atacar.
- Un objeto de curación necesita modificar la salud del personaje.

La interacción entre objetos permite que el videojuego sea interactivo, dinámico y coherente.

> [!info]
> La comunicación entre objetos ocurre cuando un objeto utiliza métodos o información de otro objeto para realizar una acción.

#### Simulación de interacción entre jugador y enemigo

Uno de los ejemplos más comunes en videojuegos es la interacción entre un jugador y un enemigo. Ambos son objetos independientes, pero constantemente intercambian información durante la partida.

**El jugador puede:**

- Atacar
- Defenderse
- Moverse
- Recibir daño

**El enemigo puede:**

- Detectar jugador
- Perseguir
- Atacar
- Perder vida

Cuando el jugador realiza un ataque, se produce una comunicación entre ambos objetos:

1. El jugador ejecuta un método de ataque.
2. El enemigo recibe el impacto.
3. La vida del enemigo disminuye.

Este proceso representa una interacción básica entre objetos dentro del sistema.

La comunicación entre objetos normalmente se realiza mediante métodos. Un objeto puede invocar acciones que afectan directamente el estado de otro objeto.

Por ejemplo:
- El jugador llama al método de daño del enemigo.
- El enemigo responde modificando su atributo de vida.

Gracias a esto:
- Los personajes reaccionan dinámicamente.
- El sistema mantiene coherencia.
- Se generan mecánicas jugables complejas.

---

> [!warning] Importancia de la organización  
> Una mala comunicación entre objetos puede provocar errores, comportamientos incoherentes o sistemas difíciles de mantener.


---

## 2.2 Simulación de colisiones

La simulación de colisiones es uno de los elementos más importantes en el desarrollo de videojuegos, ya que permite detectar e interpretar el contacto entre objetos dentro del entorno virtual. Gracias a este sistema, el juego puede reaccionar cuando dos entidades se encuentran, chocan o interactúan físicamente. En Programación Orientada a Objetos (POO), las colisiones forman parte de la interacción entre objetos y permiten construir mecánicas fundamentales como combate, recolección de objetos, detección de obstáculos y físicas básicas.

En un videojuego, una colisión ocurre cuando dos objetos ocupan el mismo espacio o entran en contacto dentro del escenario. Este evento puede generar distintas respuestas dependiendo del tipo de interacción y de las reglas del juego.

Por ejemplo:

- Un jugador toca una moneda y la recoge.
- Una bala impacta contra un enemigo.
- Un personaje choca contra una pared.
- Un vehículo colisiona con otro automóvil.

Todas estas situaciones forman parte de la lógica de colisiones.

> [!note]  
Una colisión no es únicamente un choque visual; es un evento lógico que informa al sistema que dos objetos interactuaron.

#### Tipos de colisiones en videojuegos

Dependiendo del diseño del juego, pueden existir distintos tipos de colisiones.

**Colisiones de combate**
Ocurren cuando un ataque impacta a un enemigo o jugador.
Por ejemplo:

- Una espada toca a un enemigo.
- Un proyectil golpea un objetivo.
- Un hechizo alcanza un personaje.

Este tipo de colisión normalmente:

- Reduce vida.
- Activa animaciones.
- Genera efectos visuales o sonidos.

**Colisiones con el entorno**
Permiten que los objetos interactúen con el escenario.
Por ejemplo:

- Un personaje no puede atravesar una pared.
- Un vehículo rebota contra un obstáculo.
- Un personaje aterriza sobre una plataforma.

Estas colisiones ayudan a definir límites y físicas dentro del juego.

**Colisiones de interacción**
Se utilizan para activar eventos o acciones especiales.
Por ejemplo:

- Recoger monedas.
- Abrir cofres.
- Activar interruptores.
- Entrar a nuevas zonas.

En este caso, la colisión sirve como mecanismo de activación.

> [!danger] Importancia del rendimiento  
En videojuegos con muchos objetos, las colisiones pueden consumir gran cantidad de recursos si no se optimizan correctamente.


---

## 2.3 Actualización de estados

La actualización de estados es un proceso fundamental en el desarrollo de videojuegos, ya que permite modificar las condiciones y propiedades de los objetos conforme ocurren eventos dentro del juego. En Programación Orientada a Objetos (POO), los objetos cambian constantemente de estado dependiendo de las acciones del jugador, las interacciones con otros objetos o las reglas del sistema. Gracias a este mecanismo, los videojuegos pueden reaccionar dinámicamente y generar experiencias más interactivas y realistas.

Un estado representa la situación actual de un objeto dentro del juego. Por ejemplo, un personaje puede encontrarse:

- Con vida completa
- Herido
- Atacando
- Defendiéndose
- Eliminado

La actualización de estados consiste en modificar estas condiciones conforme avanza la partida.

En videojuegos, prácticamente todos los objetos poseen estados que cambian continuamente.

Por ejemplo:
- Un enemigo puede pasar de “patrullando” a “atacando”.
- Un personaje puede pasar de “vivo” a “derrotado”.
- Una puerta puede cambiar de “cerrada” a “abierta”.

Estos cambios permiten que el mundo virtual responda a las acciones del jugador y a los eventos del entorno.

> [!info]
> Un estado representa la condición actual de un objeto dentro del sistema.

> [!warning]  Importancia de la sincronización  
Una actualización incorrecta de estados puede provocar errores como enemigos inmortales, personajes invisibles o comportamientos incoherentes.

---

## Ejemplo de Interacción entre objetos

La simulación de colisiones y actualización de estados permite construir uno de los sistemas más importantes en el desarrollo de videojuegos: el sistema de combate. Este tipo de sistema combina múltiples elementos de la Programación Orientada a Objetos (POO) para crear interacciones dinámicas entre entidades del juego, permitiendo que personajes, enemigos y objetos respondan de forma coherente a las acciones realizadas durante la partida.

En un videojuego, el combate representa una secuencia constante de comunicación entre objetos. Los personajes atacan, reciben daño, detectan impactos y modifican sus estados dependiendo de las acciones del jugador y de las reglas del sistema. Gracias a esta integración, el videojuego adquiere dinamismo, desafío e interactividad.

#### Integración de la interacción entre objetos

El sistema de combate comienza con la comunicación entre distintas entidades del juego.

Por ejemplo:

- El jugador detecta un enemigo.
- El enemigo responde al jugador.
- Ambos intercambian ataques.
- El sistema actualiza sus estados.

Cada entidad funciona como un objeto independiente, pero todos colaboran mediante métodos y atributos para construir el combate.

> [!important]
> El combate en videojuegos surge de la interacción constante entre objetos que modifican mutuamente sus estados.

#### Integración de colisiones en combate

Las colisiones permiten detectar cuándo ocurre un impacto entre entidades del juego.

Por ejemplo:

- Una espada alcanza a un enemigo.
- Un proyectil impacta a un personaje.
- Un enemigo toca al jugador.

Cuando se detecta una colisión:

1. El sistema identifica los objetos involucrados.
2. Se ejecuta la lógica correspondiente.
3. Se actualizan atributos y estados.

Gracias a esto, el combate puede reaccionar visual y funcionalmente dentro del gameplay.

> [!warning]
Un sistema de combate mal equilibrado puede provocar experiencias injustas o poco dinámicas para el jugador.

El combate produce cambios constantes en los estados de las entidades involucradas.

Algunos ejemplos:

- Vida disminuye al recibir daño.
- Un enemigo cambia de “patrulla” a “ataque”.
- Un personaje derrotado pasa a estado “eliminado”.

Estos cambios permiten que el juego responda dinámicamente a las acciones del jugador.

> [!success] Flujo básico de un sistema de combate
>
Un sistema básico de combate normalmente sigue esta secuencia:
>
>1. El jugador realiza un ataque.
>2. Se detecta una colisión.
>3. El enemigo recibe daño.
>4. Su vida disminuye.
>5. El sistema actualiza su estado.
>6. Si la vida llega a cero:
>    - El enemigo es eliminado.
>    - Se activan efectos visuales o sonoros.
>    - El juego continúa.


---
---
# Tema 3. Organización del proyecto

El tema de **Organización del proyecto** aborda la manera en que un videojuego puede estructurarse de forma ordenada y modular para facilitar su desarrollo, mantenimiento y escalabilidad. En proyectos de videojuegos, no solo es importante programar mecánicas y personajes, sino también organizar correctamente las clases, sistemas, carpetas y recursos que forman parte del juego. Una buena organización permite separar responsabilidades entre módulos como combate, control, inteligencia artificial, interfaces y recursos multimedia, evitando desorden y facilitando el trabajo individual o colaborativo. Además, este enfoque ayuda a construir proyectos más profesionales, comprensibles y preparados para crecer conforme se agregan nuevas funciones, niveles o entidades dentro del videojuego.

## 3.1 Separación de clases

La separación de clases es una práctica fundamental dentro de la Programación Orientada a Objetos (POO), ya que permite organizar correctamente los componentes de un sistema y distribuir responsabilidades entre diferentes entidades del programa. En el desarrollo de videojuegos, esta organización resulta especialmente importante debido a la gran cantidad de objetos, mecánicas y sistemas que interactúan constantemente dentro del juego. Separar adecuadamente las clases facilita la construcción de proyectos más ordenados, reutilizables y escalables.

En lugar de colocar toda la lógica del videojuego en un único archivo o estructura, la separación de clases divide el sistema en componentes especializados. Cada clase se encarga de una función específica, permitiendo que el código sea más claro y fácil de mantener.

Por ejemplo, en un videojuego básico pueden existir clases como:

- Jugador
- Enemigo
- Proyectil
- Inventario
- Sistema de combate
- Sistema de puntuación

Cada una cumple una responsabilidad concreta dentro del juego.

A medida que un videojuego crece, también aumenta la complejidad del proyecto. Si toda la lógica se concentra en un solo lugar, el sistema se vuelve difícil de entender, modificar y expandir.

La separación de clases ayuda a:

- Organizar la lógica del juego.
- Evitar duplicación de código.
- Facilitar mantenimiento.
- Mejorar escalabilidad.
- Permitir trabajo colaborativo.

> [!note]  
> Cada clase debe tener una responsabilidad específica dentro del sistema del videojuego.

Uno de los objetivos principales de separar clases es distribuir responsabilidades correctamente.

Por ejemplo:
- El jugador no debería controlar directamente la puntuación global.
- El enemigo no debería administrar el inventario del jugador.
- El sistema de combate no debería encargarse del movimiento del mapa.

Cada clase debe enfocarse únicamente en las tareas relacionadas con su función.

> [!warning] Error común  
Colocar demasiadas responsabilidades en una sola clase genera estructuras difíciles de mantener y reutilizar.

Una correcta separación de clases también facilita reutilizar entidades.

Por ejemplo:

- Todos los enemigos pueden compartir una estructura base.
- Solo cambian atributos o comportamientos específicos.
- El sistema reutiliza lógica común sin duplicarla.

Esto es muy utilizado en videojuegos profesionales para optimizar desarrollo y mantenimiento.

---

## 3.2 Modularidad

La modularidad es un principio de diseño que consiste en dividir un sistema grande en partes más pequeñas e independientes llamadas módulos. En el desarrollo de videojuegos, este enfoque permite organizar la lógica del juego en componentes especializados que trabajan de manera coordinada, facilitando la construcción de proyectos más ordenados, reutilizables y fáciles de mantener. Dentro de la Programación Orientada a Objetos (POO), la modularidad ayuda a separar responsabilidades y evitar que toda la lógica del videojuego quede concentrada en un único bloque de código.

Un módulo representa una sección específica del sistema encargada de una tarea concreta. Por ejemplo, un videojuego puede dividirse en módulos como:

- Sistema de combate
- Sistema de movimiento
- Sistema de inventario
- Sistema de físicas
- Sistema de sonido
- Sistema de inteligencia artificial

Cada uno funciona de forma relativamente independiente, pero todos colaboran para construir la experiencia completa del videojuego.

Uno de los objetivos principales de la modularidad es separar la lógica según el tipo de funcionalidad del videojuego.

Por ejemplo:

- El sistema de combate administra ataques y daño.
- El sistema de control interpreta las entradas del jugador.
- El sistema de físicas gestiona movimiento y colisiones.

Cada módulo trabaja de forma independiente, pero todos se comunican entre sí cuando es necesario.

> [!warning] Error común  
> Mezclar lógica de combate, físicas y controles en una misma estructura provoca sistemas difíciles de mantener y expandir.



---

## 3.3 Organización de archivos 

La organización de archivos es una parte fundamental del desarrollo de videojuegos, ya que permite estructurar correctamente todos los recursos, sistemas y componentes del proyecto. En Programación Orientada a Objetos (POO), esta organización ayuda a mantener separadas las clases, módulos y funcionalidades del juego, facilitando el mantenimiento, la escalabilidad y el trabajo colaborativo. A medida que un videojuego crece, también aumenta la cantidad de archivos relacionados con programación, gráficos, sonidos, animaciones y configuraciones, por lo que una estructura ordenada se vuelve indispensable.

En proyectos pequeños puede parecer suficiente guardar todos los archivos en una sola carpeta, pero en videojuegos medianos o grandes esto genera confusión y dificulta el desarrollo. Una buena organización permite localizar rápidamente recursos y entender la arquitectura general del sistema.

En desarrollo de videojuegos, normalmente se utilizan carpetas especializadas para separar recursos y sistemas según su función.

Por ejemplo:
```Text
Videojuego/
│
├── Personajes/
│   ├── Jugador/
│   ├── Enemigos/
│   └── NPC/
│
├── Sistemas/
│   ├── Combate/
│   ├── Fisicas/
│   ├── Inventario/
│   ├── Colisiones/
│   └── InteligenciaArtificial/
│
├── Escenarios/
│   ├── Mapas/
│   ├── Niveles/
│   └── ObjetosDelEntorno/
│
├── Sonidos/
│   ├── Musica/
│   ├── Efectos/
│   └── Voces/
│
├── Interfaces/
│   ├── Menus/
│   ├── HUD/
│   └── Pantallas/
│
├── Recursos/
│   ├── Imagenes/
│   ├── Sprites/
│   ├── Animaciones/
│   └── Texturas/
│
├── Guardado/
│   ├── Partidas/
│   └── Configuracion/
│
└── Documentacion/
    ├── Diagramas/
    └── DiseñoDelJuego/
```

Dicha organización de archivos es esencial en el desarrollo de videojuegos, ya que permite estructurar correctamente clases, módulos y recursos del proyecto. Mediante la separación de sistemas, carpetas y componentes especializados, es posible construir videojuegos más ordenados, escalables y fáciles de mantener. Una buena organización no solo mejora la claridad del proyecto y facilita el trabajo en equipo, sino que también permite administrar de manera eficiente la complejidad creciente de los videojuegos modernos.

---
---

## Actividad Integradora

#### Objetivo

Evaluar la capacidad de desarrollar un sistema de videojuego en consola utilizando Programación Orientada a Objetos (POO), aplicando conceptos de clases, objetos, atributos, métodos, interacción entre entidades y organización modular del proyecto.

#### Desarrollo de la actividad

Para esta actividad se desarrolló un sistema de combate en consola donde interactúan dos objetos principales:

- Jugador
- Enemigo

El sistema fue diseñado utilizando Programación Orientada a Objetos, permitiendo representar atributos, métodos e interacción entre entidades dentro de un entorno de videojuego sencillo.

#### Características implementadas

El sistema incluye:

#### **Atributos**
Los objetos contienen atributos que representan su estado dentro del juego.

**Jugador**
- Nombre
- Vida
- Posición
- Estado

**Enemigo**
- Nombre
- Vida
- Posición
- Estado

#### **Métodos implementados**

Se desarrollaron distintos métodos para controlar el comportamiento de los objetos.

**Métodos del jugador**

- `mover()`
- `atacar()`
- `recibirDaño()`

**Métodos del enemigo**

- `mover()`
- `atacar()`
- `recibirDaño()`

Estos métodos permiten la interacción dinámica entre ambos personajes.

#### Organización modular del proyecto

El proyecto fue organizado utilizando múltiples archivos independientes para aplicar principios de modularidad y separación de responsabilidades.

## Estructura del proyecto

```
VideojuegoConsola/
│
├── main
├── jugador
├── enemigo
└── personaje
```

#### Explicación de la estructura

| Archivo     | Función                                      |
| ----------- | -------------------------------------------- |
| `main`      | Controla la ejecución principal del sistema  |
| `personaje` | Clase base con atributos y métodos generales |
| `jugador`   | Clase Jugador                                |
| `enemigo`   | Clase Enemigo                                |

#### Pseudocodigo

**Clase base Personaje**

```Text
CLASE Personaje  
  
	ATRIBUTOS  
		nombre  
		vida  
		posicion  
		estado  
  
	METODO inicializar(nombre, vida, posicion)  
	  
		asignar nombre  
		asignar vida  
		asignar posicion  
		estado ← "Vivo"  
	  
	FIN METODO  
  
	METODO mover(nueva_posicion)  
	  
		posicion ← nueva_posicion  
		ESCRIBIR nombre + " se movió a " + posicion  
	  
	FIN METODO  
  
	METODO recibirDaño(daño)  
	  
		vida ← vida - daño  
		ESCRIBIR nombre + " recibió " + daño + " de daño"  
		SI vida <= 0 ENTONCES  
			estado ← "Derrotado"  
			ESCRIBIR nombre + " ha sido derrotado"  
		FIN SI  
		
	FIN METODO  
  
FIN CLASE
```

**Clase Jugador**

```Text
CLASE Jugador HEREDA Personaje  
  
	METODO atacar(enemigo)  
	  
		daño ← 20  
		ESCRIBIR nombre + " ataca a " + enemigo.nombre  
		enemigo.recibirDaño(daño)  
	  
	FIN METODO  
  
FIN CLASE
```

**Clase Enemigo**

```Text
CLASE Enemigo HEREDA Personaje  
  
METODO atacar(jugador)  
  
daño ← 15  
  
ESCRIBIR nombre + " ataca a " + jugador.nombre  
  
jugador.recibirDaño(daño)  
  
FIN METODO  
  
FIN CLASE
```

**Archivo principal** (main)

```Text
INICIO  
  
jugador ← NUEVO Jugador("Heroe", 100, 0)  
enemigo ← NUEVO Enemigo("Goblin", 60, 10)  
  
ESCRIBIR "=== INICIO DEL COMBATE ==="  
  
jugador.mover(5)  
enemigo.mover(7)  
  
jugador.atacar(enemigo)  
enemigo.atacar(jugador)  
  
jugador.atacar(enemigo)  
jugador.atacar(enemigo)  
  
ESCRIBIR "=== ESTADOS FINALES ==="  
  
ESCRIBIR jugador.nombre +  
	": Vida = " + jugador.vida +  
	", Estado = " + jugador.estado  
  
ESCRIBIR enemigo.nombre +  
	": Vida = " + enemigo.vida +  
	", Estado = " + enemigo.estado  
  
FIN
```

#### Explicación del funcionamiento

El sistema inicia creando un objeto Jugador y un objeto Enemigo. Ambos poseen atributos como vida, posición y estado.

Durante la ejecución:

1. Los personajes se mueven.
2. El jugador ataca al enemigo.
3. El enemigo responde atacando.
4. La vida de ambos personajes cambia.
5. El estado se actualiza automáticamente cuando la vida llega a cero.

Esto permite simular una interacción básica de combate dentro de un videojuego en consola.

#### Resultados obtenidos

Durante la simulación se observaron:

- Interacción entre objetos.
- Actualización dinámica de atributos.
- Cambios de estado.
- Comunicación entre clases.
- Uso correcto de modularidad y separación de archivos.

El sistema funcionó correctamente y permitió representar los conceptos fundamentales de Programación Orientada a Objetos aplicados a videojuegos.

#### Evidencia solicitada

Se debe adjuntar:

- Captura de pantalla de la ejecución del programa.
- Evidencia visual donde se observe:
    - Movimiento de personajes
    - Ataques
    - Cambios de vida
    - Estados finales
    - Resultado del combate

