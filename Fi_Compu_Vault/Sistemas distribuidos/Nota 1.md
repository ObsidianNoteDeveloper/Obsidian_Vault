
# SISTEMAS DISTRIBUIDOS

## Guía formal de estudio para examen

---

# 1. Introducción a los sistemas distribuidos

## 1.1 Sistema operativo

Un **sistema operativo (SO)** es el software encargado de administrar los recursos de una computadora y proporcionar servicios tanto a los programas como a los usuarios. Actúa como intermediario entre el hardware y las aplicaciones.

Una computadora moderna necesita ejecutar varias tareas aparentemente al mismo tiempo. Por ejemplo, puede estar reproduciendo música, ejecutando un navegador, descargando un archivo y respondiendo a las acciones del usuario. El sistema operativo se encarga de administrar estos recursos y coordinar los procesos necesarios. Entre sus principales funciones se encuentran la gestión de procesos, planificación de procesos, gestión de memoria, gestión de concurrencia, gestión de entrada/salida, gestión de archivos, gestión de dispositivos, seguridad y protección, y gestión de redes.

El sistema operativo es especialmente importante en los sistemas distribuidos porque cada computadora que participa en el sistema necesita administrar sus propios recursos y procesos, además de colaborar con otras computadoras mediante la red.

---

## 1.2 Procesos

Un **proceso** es una instancia de un programa que se encuentra en ejecución. Es importante distinguir entre programa y proceso: un programa es un conjunto de instrucciones almacenadas, mientras que un proceso es ese programa cuando está siendo ejecutado.

Por ejemplo, tener `notepad.exe` almacenado en el disco corresponde al programa. Cuando se abre el Bloc de notas, el sistema operativo crea un proceso asociado con ese programa.

Un proceso incluye el código del programa, los datos que está utilizando, el contador de programa, los registros del procesador, información de memoria, su estado actual y los recursos que tiene asignados. Cada proceso posee un identificador denominado **PID (Process ID)**, utilizado por el sistema operativo para identificarlo.

Los procesos pueden encontrarse principalmente en los estados **ejecutando, listo y bloqueado**. Un proceso ejecutando está utilizando la CPU; uno listo puede ejecutarse pero está esperando que la CPU quede disponible; y uno bloqueado no puede continuar porque espera algún evento, como una operación de entrada/salida, la llegada de datos, un recurso o una señal de otro proceso.

---

## 1.3 Creación y terminación de procesos

Un proceso puede ser creado por diferentes motivos. Puede crearse un proceso para ejecutar un trabajo programado, cuando un usuario inicia una aplicación, cuando el sistema necesita proporcionar un servicio o cuando un proceso existente solicita la creación de otro.

Cuando un proceso crea a otro, el primero recibe el nombre de **proceso padre**, mientras que el segundo recibe el nombre de **proceso hijo**. Los procesos padre e hijo pueden comunicarse y cooperar entre sí.

En Unix/Linux, la llamada al sistema **`fork()`** se utiliza para crear un nuevo proceso. Una característica importante de `fork()` es que la llamada retorna en ambos procesos. En el proceso hijo, el valor de retorno es `0`; en el proceso padre, el valor de retorno es mayor que cero y corresponde al PID del proceso hijo.

El orden en que aparecen los mensajes de padre e hijo no necesariamente es fijo, porque depende de la planificación realizada por el sistema operativo.

Entre las funciones relacionadas con procesos se encuentran `fork()`, `getpid()`, `getppid()`, `wait()`, `exit()` y `exec()`. 

`fork()` crea un proceso, `getpid()` obtiene el PID actual, `getppid()` obtiene el PID del padre, `wait()` permite esperar a que termine un proceso hijo, `exit()` finaliza un proceso y `exec()` sustituye el programa que está ejecutando un proceso por otro.

Una combinación particularmente importante es:

**`fork()` → creación de proceso → `exec()` → ejecución de otro programa.**

Un proceso puede terminar normalmente, por un error, por un error fatal, por superar un límite de recursos, por falta de memoria, por la terminación solicitada por otro proceso o por intervención del usuario.

---

## 1.4 Planificación de procesos

Debido a que normalmente existen más procesos que procesadores disponibles, el sistema operativo utiliza **colas de procesos** para organizar aquellos que esperan utilizar la CPU.

La **planificación** es el mecanismo mediante el cual el sistema operativo decide qué proceso debe utilizar la CPU. El componente encargado de tomar esta decisión se denomina **planificador o scheduler**.

Entre los algoritmos de planificación estudiados se encuentran 
- **FCFS (First Come, First Served)**
- **Round Robin**
- **Shortest Job First (SJF)**
- planificación por **prioridades**
- **Multilevel Queue**

El objetivo de la planificación es aprovechar eficientemente la CPU y proporcionar tiempos de respuesta adecuados.

---

## 1.5 Concurrencia

La **concurrencia** ocurre cuando varios procesos o hilos avanzan durante un mismo periodo de tiempo, aunque no necesariamente estén ejecutándose exactamente en el mismo instante.

En una CPU de un solo núcleo, por ejemplo, el sistema operativo puede ejecutar una secuencia como:

**Proceso A → Proceso B → Proceso A → Proceso C → Proceso B.**

Mediante cambios rápidos entre procesos se produce la sensación de ejecución simultánea.

Cuando la CPU cambia de un proceso a otro, el sistema operativo debe guardar el estado del proceso actual y recuperar el estado del siguiente. Este mecanismo se denomina **cambio de contexto o context switch**.

En sistemas multinúcleo algunos procesos o hilos pueden ejecutarse realmente de manera simultánea. Por ello es importante distinguir:

**Concurrencia:** varias tareas progresan durante un mismo periodo.

**Paralelismo:** varias tareas se ejecutan físicamente al mismo tiempo utilizando diferentes recursos de procesamiento.

---

## 1.6 Hilos

Un **hilo o thread** es una unidad de ejecución dentro de un proceso. Un proceso puede contener uno o varios hilos.

Cuando un proceso posee un único hilo existe un flujo de ejecución único. Cuando posee varios hilos se habla de **multithreading**.

Los hilos pertenecientes al mismo proceso comparten determinados recursos, especialmente el espacio de memoria del proceso, aunque cada hilo posee su propio contador de programa, registros y pila.

Los hilos permiten realizar varias tareas dentro de un proceso, mejorar el aprovechamiento de la CPU, construir aplicaciones concurrentes y atender múltiples tareas o solicitudes. Son especialmente importantes en servidores y sistemas distribuidos.

Una distinción importante es que los hilos comparten el espacio de memoria del proceso, pero el sistema operativo sí puede planificarlos y asignarles tiempo de CPU.

---

# 2. Redes y comunicación

## 2.1 Red de computadoras

Una **red de computadoras** es un conjunto de computadoras y dispositivos interconectados capaces de intercambiar información y compartir recursos.

Una red permite compartir datos, comunicarse entre usuarios, compartir dispositivos y servicios y utilizar recursos independientemente de su ubicación.

Esta característica es fundamental para los sistemas distribuidos, ya que las diferentes computadoras que forman parte del sistema necesitan intercambiar información.

La relación fundamental puede expresarse de la siguiente manera:

> **Una red permite conectar computadoras; un sistema distribuido utiliza esas computadoras conectadas para trabajar coordinadamente.**

Por lo tanto, las redes constituyen una infraestructura fundamental sobre la cual pueden construirse sistemas distribuidos.

---

## 2.2 Modelo OSI

El **modelo OSI (Open Systems Interconnection)** es un modelo conceptual que divide la comunicación de una red en siete capas.

|Capa|Nombre|Función principal|
|---|---|---|
|7|Aplicación|Servicios de red para las aplicaciones|
|6|Presentación|Formato, codificación, compresión y cifrado|
|5|Sesión|Administración de sesiones|
|4|Transporte|Comunicación extremo a extremo|
|3|Red|Direccionamiento lógico y enrutamiento|
|2|Enlace de datos|Tramas y direccionamiento físico|
|1|Física|Transmisión de bits|

La **capa física** transmite bits mediante el medio físico y considera elementos como cables, conectores y señales.

La **capa de enlace de datos** organiza los bits en tramas y permite la comunicación entre dispositivos directamente conectados. Puede encargarse de la detección de errores, acceso al medio y direccionamiento físico, como las direcciones MAC.

La **capa de red** determina cómo transportar paquetes desde un origen hasta un destino. Aquí se encuentran conceptos como direcciones IP, enrutamiento y routers.

La **capa de transporte** proporciona comunicación extremo a extremo entre aplicaciones. Puede encargarse de segmentación, control de flujo, control de errores y entrega confiable, dependiendo del protocolo. TCP y UDP son ejemplos relacionados con esta capa.

La **capa de sesión** administra las sesiones de comunicación entre aplicaciones.

La **capa de presentación** se relaciona con la representación de los datos, incluyendo codificación, conversión de formatos, compresión y cifrado.

La **capa de aplicación** proporciona servicios de red a las aplicaciones. Algunos ejemplos son HTTP/HTTPS, FTP, DNS, SMTP y SSH.

---

# 3. Sistemas distribuidos

## 3.1 Definición

Un **sistema distribuido** es una colección de computadoras independientes que trabajan juntas y que, desde el punto de vista del usuario, pueden aparentar funcionar como un único sistema.

Aunque físicamente existen varias computadoras independientes, el objetivo es que el usuario pueda utilizar los servicios sin tener que preocuparse necesariamente por dónde se encuentra cada recurso.

Un sistema distribuido necesita, por tanto, computadoras capaces de ejecutar procesos, una red que permita su comunicación y mecanismos de coordinación que permitan que los diferentes componentes trabajen conjuntamente.

---

## 3.2 Tecnologías que impulsaron los sistemas distribuidos

El desarrollo de los sistemas distribuidos estuvo favorecido por diferentes avances tecnológicos. Los **microprocesadores** permitieron construir computadoras más pequeñas, económicas y potentes. Las **redes de área local** permitieron conectar múltiples computadoras y facilitar el intercambio de información. El desarrollo de tecnologías de **almacenamiento** permitió manejar grandes cantidades de información y compartirla entre diferentes sistemas.

---

## 3.3 Sistemas centralizados y distribuidos

Un **sistema centralizado** concentra el procesamiento y los recursos principales en una computadora o sistema central.

En contraste, un sistema distribuido utiliza diferentes computadoras conectadas mediante una red y coordinadas para proporcionar servicios.

Los sistemas distribuidos pueden proporcionar una mejor relación precio/rendimiento, mayor capacidad de cómputo, distribución de aplicaciones, tolerancia a fallos parciales y escalabilidad.

Entre las ventajas frente a computadoras aisladas se encuentran los datos compartidos, dispositivos compartidos, comunicación y balanceo de carga.

El **balanceo de carga** consiste en distribuir la carga de trabajo entre diferentes computadoras o recursos. De esta manera, si un servidor recibe demasiadas solicitudes, otros servidores pueden atender parte de ellas.

---

## 3.4 Desventajas y retos

Los sistemas distribuidos también presentan problemas que hacen que su diseño sea más complejo.

La **complejidad del software** aumenta porque es necesario coordinar diferentes computadoras y procesos.

Los **fallos parciales** representan un problema importante, porque una parte del sistema puede dejar de funcionar mientras el resto continúa operando.

La **comunicación por red** puede presentar retrasos, pérdida de paquetes, interrupciones, congestión y fallos de conexión.

La **sincronización** es necesaria porque diferentes computadoras pueden ejecutar operaciones al mismo tiempo.

La **consistencia de datos** debe mantenerse cuando varias computadoras trabajan con información compartida.

Finalmente, la **seguridad** es más compleja debido a que existen múltiples puntos de comunicación y acceso.

---

# 4. Taxonomía de sistemas distribuidos y modelos de máquina

## 4.1 Taxonomía según software y hardware

Una clasificación presentada en los apuntes distingue los sistemas de acuerdo con la fortaleza del software y del hardware.

Cuando se tiene **software débil y hardware débil**, se encuentran los **sistemas operativos de red** y los sistemas de archivos en red. Un ejemplo es **NFS (Network File System)**.

Cuando se tiene **software fuerte y hardware fuerte**, se encuentran los **sistemas paralelos**, como los clusters y sistemas operativos para multiprocesadores.

Cuando se tiene **software fuerte y hardware débil**, se encuentran los sistemas realmente distribuidos. En estos casos se busca proporcionar la percepción de un **sistema único**, aunque internamente existan diferentes computadoras. Algunos ejemplos son la conexión remota, la copia remota de archivos y los sistemas globales de archivos compartidos.

Esta clasificación permite relacionar la capacidad del hardware con el nivel de integración proporcionado por el software.

---

# 5. Taxonomía de Flynn

La **taxonomía de Flynn** clasifica arquitecturas de computación considerando dos elementos: el número de flujos de instrucciones y el número de flujos de datos.

Se obtienen cuatro categorías principales: **SISD, SIMD, MISD y MIMD**.

||Un flujo de datos|Múltiples flujos de datos|
|---|---|---|
|Una instrucción|SISD|SIMD|
|Múltiples instrucciones|MISD|MIMD|

### SISD

**SISD (Single Instruction, Single Data)** significa una instrucción y un flujo de datos. Corresponde al modelo tradicional en el que un procesador ejecuta una secuencia de instrucciones sobre un flujo de datos.

### SIMD

**SIMD (Single Instruction, Multiple Data)** significa una instrucción y múltiples datos. Una misma instrucción puede aplicarse simultáneamente sobre diferentes elementos de datos. Es apropiado para operaciones vectoriales, procesamiento de imágenes y operaciones numéricas repetitivas.

### MISD

**MISD (Multiple Instruction, Single Data)** significa múltiples instrucciones sobre un flujo de datos. Es una arquitectura poco común en sistemas generales, pero representa conceptualmente la ejecución de diferentes operaciones sobre el mismo flujo de datos.

### MIMD

**MIMD (Multiple Instruction, Multiple Data)** significa múltiples instrucciones y múltiples datos. Diferentes procesadores pueden ejecutar diferentes instrucciones sobre diferentes datos. Esta clasificación es especialmente importante para comprender sistemas multiprocesador y arquitecturas distribuidas.

La idea fundamental para el examen es recordar:

**SISD = 1 instrucción / 1 dato.**

**SIMD = 1 instrucción / varios datos.**

**MISD = varias instrucciones / 1 dato.**

**MIMD = varias instrucciones / varios datos.**

---

# 6. Arquitectura de sistemas distribuidos

Una **arquitectura distribuida** describe la organización lógica y física de un sistema.

Una arquitectura está formada por **componentes lógicos** y **conectores**. Un componente lógico es una unidad modular que realiza una función determinada. Los conectores son mecanismos que permiten la comunicación, coordinación y cooperación entre componentes.

Los estilos arquitectónicos surgen de la manera en que estos componentes lógicos y conectores se relacionan.

En la organización física pueden aparecer estructuras de almacenamiento y organización de datos como pilas, colas, colas de prioridad, listas enlazadas, listas doblemente enlazadas y árboles. Estas estructuras permiten organizar información que posteriormente puede ser utilizada por los componentes del sistema.

---

# 7. Estilos de arquitectura

## 7.1 Arquitectura por capas

En una **arquitectura por capas**, los componentes lógicos se organizan en diferentes niveles.

Un componente de la capa LiL_i puede invocar operaciones de la capa inmediatamente inferior Li−1L_{i-1}. Por lo tanto, las invocaciones normalmente se realizan desde las capas superiores hacia las inferiores.

Este modelo permite separar responsabilidades y organizar el funcionamiento del sistema de forma jerárquica.

Una aplicación de este estilo se encuentra en servicios orientados a sistemas de archivos o de datos.

---

## 7.2 Arquitectura orientada a componentes

En una **arquitectura orientada a componentes**, cada objeto representa un componente lógico del sistema.

Los componentes se encuentran interconectados mediante mecanismos de invocación remota, como **RPC (Remote Procedure Call)**.

Un componente puede solicitar a otro componente remoto que ejecute una determinada operación. El objetivo es permitir que la comunicación entre componentes distribuidos pueda realizarse de manera estructurada.

---

## 7.3 Arquitectura orientada a datos

La **arquitectura orientada a datos** se concentra en la ubicación o localidad de los datos.

Una característica importante es reducir los costos de comunicación procurando que los datos utilizados por un componente se encuentren en una ubicación conveniente.

Este enfoque aparece en aplicaciones web distribuidas y bases de datos distribuidas.

---

## 7.4 Arquitectura orientada a eventos

En una **arquitectura orientada a eventos**, los componentes se comunican mediante eventos.

Los componentes que producen información actúan como **publicadores**, mientras que los componentes interesados actúan como **suscriptores**.

Un publicador genera un evento y los suscriptores reciben aquellos eventos a los que están registrados.

Este modelo se relaciona directamente con el patrón **Publish/Subscribe** y puede utilizarse para sistemas de notificaciones.

---

# 8. Arquitecturas centralizadas

En una **arquitectura centralizada**, la interrelación de los componentes sigue una jerarquía definida. Algunos componentes requieren información o servicios proporcionados por otros componentes.

El modelo **cliente-servidor** constituye un ejemplo fundamental de arquitectura centralizada.

## Cliente

El **cliente** es el componente que realiza una solicitud de servicio. Normalmente es quien inicia la comunicación.

## Servidor

El **servidor** es el componente que proporciona el servicio. Normalmente permanece esperando solicitudes, procesa la petición recibida y devuelve una respuesta.

La comunicación tradicional puede representarse conceptualmente como:

**Emisor ↔ canal de comunicación ↔ receptor.**

La comunicación puede ser bidireccional, ya que el receptor puede responder posteriormente al emisor.

Un ejemplo cotidiano es la navegación web. El servidor web almacena páginas, documentos y recursos, mientras que el navegador funciona como cliente y solicita esos recursos mediante protocolos como HTTP o HTTPS.

---

# 9. Arquitectura multiestrato o multitier

La **arquitectura multiestrato** distribuye la funcionalidad de una aplicación entre diferentes plataformas o computadoras.

La interfaz puede encontrarse en la computadora del usuario, mientras que los servicios funcionales pueden localizarse en una o varias computadoras.

Un modelo frecuente es la arquitectura de tres capas:

**Presentación → lógica de negocio → datos.**

La capa de **presentación** se encarga de la interacción con el usuario. La capa de **lógica de negocio** implementa las reglas y operaciones de la aplicación. La capa de **datos** administra la información, normalmente mediante una base de datos.

Este modelo es habitual en sistemas de información y permite separar responsabilidades entre diferentes componentes.

---

# 10. Mecanismos epidémicos

Los **mecanismos epidémicos** se utilizan para mantener y propagar información entre diferentes componentes de un sistema distribuido.

Existen dos modalidades fundamentales.

En el modo **Pull**, también denominado envío inducido, el receptor solicita la información que necesita. Por lo tanto, la comunicación comienza porque el receptor realiza una petición.

En el modo **Push**, el envío es automático. El emisor transmite la información a otros componentes sin esperar necesariamente una solicitud específica.

La diferencia fundamental es:

**Pull → el receptor solicita.**

**Push → el emisor envía.**

Estos mecanismos permiten distribuir información sin necesidad de que todos los componentes mantengan comunicación directa permanente.

---

# 11. Arquitecturas P2P no estructuradas

Las arquitecturas **Peer-to-Peer (P2P) no estructuradas** están formadas por nodos que pueden actuar como clientes y servidores, sin que exista necesariamente una organización rígida de la red.

En este modelo la información no se encuentra necesariamente asociada a una ubicación predeterminada dentro de la red.

Entre los ejemplos estudiados se encuentran **Gnutella, Freenet y Groove**.

Estas aplicaciones permiten el intercambio de información entre usuarios que contribuyen y utilizan recursos de la red.

---

# 12. Arquitecturas descentralizadas estructuradas

En una arquitectura descentralizada estructurada, la **topología de la red está fuertemente controlada**.

A diferencia de una red no estructurada, el contenido no puede colocarse arbitrariamente. Los datos se asignan a una ubicación determinada, lo que permite realizar consultas de manera más eficiente.

Una tecnología importante en este tipo de sistemas son las **DHT (Distributed Hash Tables)** o tablas hash distribuidas.

Una DHT asigna identificadores a los nodos de manera consistente dentro de un espacio grande de identificadores. De esta forma, un dato puede asociarse con un nodo determinado y localizarse mediante mecanismos definidos.

Entre los ejemplos principales se encuentran:

**Chord, CAN y Pastry.**

La idea fundamental es que una estructura conocida de la red permite realizar búsquedas de información de manera más eficiente que en una red P2P completamente no estructurada.

---

# 13. Arquitecturas híbridas descentralizadas

Las arquitecturas híbridas combinan características de sistemas descentralizados con determinados componentes especializados.

## Super-peers

Un **super-peer** es un nodo que funciona como índice o administrador de determinada información del sistema.

Los super-peers pueden organizarse formando una red P2P de dos o más niveles. Los nodos ordinarios se conectan con super-peers, mientras que estos coordinan o indexan información.

## Trackers

Un **tracker** es un servidor dedicado que mantiene información sobre los peers que comparten o almacenan determinado contenido.

Un ejemplo representativo de este mecanismo es **BitTorrent**, donde los trackers pueden proporcionar información necesaria para localizar peers relacionados con determinado contenido.

## Broker

Un **broker** es un componente que actúa como intermediario entre diferentes componentes del sistema.

Su función es mediar la comunicación o las solicitudes entre las partes del sistema.

Como ejemplo se encuentra **Globule**.

---

# 14. Naming y binding

## 14.1 Naming

El **naming** es el mecanismo mediante el cual se identifican recursos, objetos, servicios o entidades mediante nombres.

En un sistema distribuido es necesario identificar recursos aunque estos se encuentren físicamente en diferentes computadoras.

Por ejemplo, un servicio puede identificarse mediante un nombre lógico en lugar de utilizar directamente una dirección física.

## 14.2 Binding

El **binding** es la asociación entre un nombre y el recurso correspondiente.

Por ejemplo:

**nombre → recurso**

Un ejemplo conocido es el funcionamiento conceptual de DNS:

**[www.ejemplo.com](http://www.ejemplo.com/) → dirección IP.**

Por lo tanto, para el examen puede utilizarse la siguiente definición:

> **Naming permite identificar recursos mediante nombres, mientras que binding establece la asociación entre ese nombre y el recurso correspondiente.**

---

# 15. Comunicación cliente-servidor

La comunicación **cliente-servidor** es un modelo fundamental de los sistemas distribuidos.

El cliente inicia una solicitud y el servidor proporciona un servicio. La comunicación normalmente sigue una secuencia de:

**Solicitud → procesamiento → respuesta.**

Por ejemplo, cuando un navegador solicita una página web, el navegador funciona como cliente, envía una solicitud al servidor y el servidor procesa la petición y devuelve la información solicitada.

Este modelo permite separar responsabilidades: el cliente se encarga principalmente de solicitar y presentar servicios, mientras que el servidor se encarga de proporcionar dichos servicios.

---

# 16. Paso de mensajes

El **paso de mensajes** es un mecanismo de comunicación en el cual los procesos intercambian información mediante mensajes.

En un sistema distribuido los procesos pueden encontrarse en diferentes computadoras, por lo que necesitan mecanismos explícitos para comunicarse.

Conceptualmente existen dos operaciones fundamentales:

**Enviar mensaje → recibir mensaje.**

El mensaje puede contener información, instrucciones, resultados o datos necesarios para coordinar los procesos.

El paso de mensajes es especialmente importante cuando los procesos no comparten directamente memoria.

---

# 17. Sincronización en sistemas distribuidos

La sincronización es uno de los problemas fundamentales de los sistemas distribuidos porque los diferentes procesos pueden ejecutarse simultáneamente y no existe necesariamente un reloj global perfectamente sincronizado.

El objetivo de la sincronización es coordinar las acciones de los diferentes procesos y establecer relaciones de orden entre los acontecimientos.

---

# 18. Relojes físicos

Los **relojes físicos** representan el tiempo real mediante dispositivos de medición del tiempo.

En un sistema distribuido cada computadora puede tener su propio reloj físico. Debido a diferencias de hardware, temperatura, frecuencia y otros factores, los relojes pueden presentar pequeñas diferencias.

Por esta razón, dos computadoras pueden indicar horas ligeramente diferentes aunque intenten representar el mismo instante.

La **sincronización de relojes** busca reducir estas diferencias.

---

# 19. Algoritmos de sincronización de relojes

Los sistemas distribuidos necesitan algoritmos que permitan sincronizar relojes físicos.

El objetivo general es que los relojes de los diferentes nodos mantengan una diferencia controlada.

En términos generales, un algoritmo de sincronización mide o estima las diferencias existentes y ajusta los relojes de los participantes.

Es importante distinguir la sincronización física de la sincronización lógica. La primera busca aproximar los relojes al tiempo real; la segunda busca establecer un orden lógico de acontecimientos.

---

# 20. Relojes lógicos

Los **relojes lógicos** no buscan representar directamente la hora real. Su objetivo principal es establecer un orden entre acontecimientos de un sistema distribuido.

Esto es necesario porque un sistema distribuido no dispone necesariamente de una única referencia temporal global.

El concepto fundamental es la **relación de causalidad**. Si un acontecimiento aa puede haber influido en un acontecimiento bb, se establece que:

**a → b**

La relación de causalidad permite determinar que un acontecimiento ocurrió antes que otro desde el punto de vista lógico.

---

# 21. Relojes de Lamport

El **reloj lógico de Lamport** asigna valores numéricos a los acontecimientos para preservar la relación causal.

La propiedad fundamental es:

**Si a → b, entonces C(a) < C(b).**

Esto significa que si el acontecimiento aa precede causalmente a bb, el reloj lógico de aa debe ser menor.

Sin embargo, la relación inversa no necesariamente se cumple. Es decir:

**C(a) < C(b)** no significa necesariamente que **a → b**.

Por lo tanto, un reloj de Lamport permite preservar el orden causal cuando este existe, pero no siempre permite determinar si dos eventos son concurrentes.

---

# 22. Relojes vectoriales

Los **relojes vectoriales** amplían la capacidad de los relojes lógicos.

En lugar de utilizar un único valor, cada proceso mantiene un vector con información sobre el avance lógico de los diferentes procesos.

Los relojes vectoriales permiten distinguir entre:

**Eventos causalmente relacionados**

y

**Eventos concurrentes.**

Esto constituye una ventaja respecto a los relojes de Lamport cuando se necesita conocer con mayor precisión la relación causal entre eventos distribuidos.

---

# 23. Control de concurrencia

El **control de concurrencia** consiste en coordinar múltiples operaciones que pueden ejecutarse simultáneamente para evitar resultados incorrectos o inconsistentes.

Este problema aparece cuando diferentes procesos acceden a recursos compartidos.

Por ejemplo, si dos procesos modifican simultáneamente el mismo dato, el resultado puede depender del orden en que se realicen las operaciones.

En sistemas distribuidos, el control de concurrencia es más complejo porque los procesos pueden encontrarse en diferentes máquinas.

---

# 24. Transacciones

Una **transacción** es un conjunto de operaciones que debe ejecutarse de manera coherente respecto al estado de los datos.

Una referencia fundamental son las propiedades **ACID**:

**Atomicidad:** la transacción se realiza completamente o no se realiza.

**Consistencia:** la transacción debe llevar los datos de un estado válido a otro estado válido.

**Aislamiento:** las transacciones concurrentes no deben interferir incorrectamente entre sí.

**Durabilidad:** una vez confirmada una transacción, sus resultados deben permanecer.

En sistemas distribuidos, estas propiedades son especialmente importantes cuando una operación involucra recursos ubicados en diferentes nodos.

---

# 25. Sincronización externa e interna

La **sincronización externa** busca relacionar los relojes de un sistema distribuido con una referencia temporal externa.

La **sincronización interna** busca mantener sincronizados entre sí los relojes de los diferentes nodos del sistema.

La diferencia fundamental es:

**Externa → sincronización respecto a una referencia externa.**

**Interna → sincronización entre los propios nodos.**

---

# 26. Grupo de comunicación

Un **grupo de comunicación** es un conjunto de procesos o nodos que participan en una comunicación coordinada.

El uso de grupos permite que un mensaje pueda dirigirse a varios procesos relacionados en lugar de establecer comunicaciones independientes con cada uno.

Los grupos son importantes para sistemas que requieren coordinación, replicación y difusión de información.

---

# 27. Exclusión mutua distribuida

La **exclusión mutua** busca garantizar que únicamente un proceso pueda acceder a una sección crítica en un momento determinado.

En una computadora individual puede utilizarse un mutex para controlar el acceso a una sección crítica.

En un sistema distribuido el problema es más complejo porque los procesos se encuentran en diferentes computadoras y necesitan coordinarse mediante mensajes.

El objetivo continúa siendo el mismo:

**solamente un proceso puede ejecutar la sección crítica simultáneamente.**

Los algoritmos de exclusión mutua distribuida permiten alcanzar este objetivo sin depender de una única memoria compartida.

---

# 28. Algoritmos de elección

Los **algoritmos de elección** se utilizan para seleccionar un proceso coordinador dentro de un conjunto de procesos distribuidos.

Un ejemplo conocido es el **algoritmo del Bully**.

La idea general del algoritmo Bully es que, cuando es necesario elegir un coordinador, los procesos participan en la elección y se selecciona el proceso activo con mayor prioridad o identificador, de acuerdo con las reglas del algoritmo.

El nuevo coordinador informa a los demás procesos sobre su elección.

---

# 29. Migración de procesos

La **migración de procesos** consiste en trasladar un proceso de una computadora a otra.

El objetivo puede ser distribuir la carga, aprovechar recursos disponibles o mejorar el rendimiento.

Por ejemplo, si un nodo está muy cargado mientras otro tiene recursos disponibles, un sistema distribuido puede considerar mover procesos hacia el nodo con mayor disponibilidad.

---

# 30. Estrategias de asignación

Las **estrategias de asignación** determinan en qué nodo deben ejecutarse determinados procesos o tareas.

Una asignación adecuada puede utilizar información relacionada con:

- carga de CPU;
    
- memoria disponible;
    
- comunicación necesaria;
    
- disponibilidad de recursos;
    
- ubicación de los datos;
    
- estado de los nodos.
    

La finalidad es utilizar eficientemente los recursos distribuidos y evitar concentrar excesivamente la carga en un único nodo.

---

# 31. Algoritmos distribuidos

Un **algoritmo distribuido** es un algoritmo cuyos componentes se ejecutan en diferentes procesos o nodos que necesitan comunicarse y coordinarse para alcanzar un objetivo común.

A diferencia de un algoritmo centralizado, no necesariamente existe un único proceso que conozca todo el estado del sistema.

Esto hace necesarios mecanismos de comunicación, sincronización, coordinación y tolerancia a fallos.

---

# 32. Concurrencia en sistemas distribuidos

La concurrencia en sistemas distribuidos ocurre cuando diferentes procesos avanzan simultáneamente o durante un mismo intervalo de tiempo en diferentes nodos.

El reto consiste en garantizar que las operaciones concurrentes produzcan resultados correctos.

La concurrencia se encuentra directamente relacionada con el control de acceso a recursos, sincronización, transacciones y exclusión mutua.

---

# 33. Calendarización

La **calendarización o planificación distribuida** consiste en decidir cuándo y dónde deben ejecutarse determinadas tareas.

En un sistema distribuido esta decisión puede considerar varios nodos y recursos.

El objetivo es distribuir el trabajo de manera adecuada, aprovechar los recursos disponibles y evitar sobrecargas.

La calendarización se relaciona directamente con el balanceo de carga y las estrategias de asignación.

---

# 34. Consenso

El **consenso** es el proceso mediante el cual diferentes procesos distribuidos llegan a un acuerdo sobre una decisión o valor.

El problema es complejo porque algunos procesos pueden fallar o porque los mensajes pueden retrasarse.

Un sistema de consenso debe buscar que los procesos participantes alcancen una decisión coherente aun cuando existan determinadas condiciones adversas.

El consenso es fundamental en sistemas distribuidos porque permite coordinar decisiones que afectan a múltiples nodos.

---

# 35. Detección de terminación

La **detección de terminación** consiste en determinar cuándo un cálculo distribuido ha finalizado.

Este problema es más complejo que en un programa centralizado porque un proceso puede encontrarse inactivo mientras todavía existen mensajes en tránsito.

Por ello, no basta con observar que todos los procesos están momentáneamente inactivos. También es necesario considerar el estado de las comunicaciones y determinar que no quedan actividades pendientes.

---

# 36. Tolerancia a fallos

La **tolerancia a fallos** es la capacidad de un sistema de continuar funcionando aunque algunos componentes fallen.

Una característica importante de los sistemas distribuidos es que pueden ofrecer **tolerancia a fallos parciales**, lo que significa que la falla de una computadora no necesariamente debe provocar la caída completa del sistema.

Para conseguir tolerancia a fallos pueden utilizarse mecanismos como redundancia, replicación, recuperación, detección de fallos y redistribución de servicios.

---

# 37. Estabilidad

La **estabilidad** dentro de los algoritmos distribuidos se relaciona con la capacidad del sistema para alcanzar y mantener un comportamiento correcto y controlado después de cambios, perturbaciones o eventos internos.

El significado exacto de este concepto puede depender de la definición utilizada por la profesora o del material específico de la asignatura. En los apuntes disponibles no se desarrolla una definición formal adicional, por lo que este punto debe revisarse con la diapositiva o definición que utilice la profesora para el examen.

---

# 38. Arquitecturas distribuidas

## 38.1 Tolerancia a fallas

La arquitectura de un sistema distribuido debe considerar desde su diseño que cualquiera de sus componentes puede fallar.

Esto implica evitar dependencias innecesarias de un único componente y utilizar mecanismos que permitan detectar fallos, sustituir componentes o continuar proporcionando servicios.

La tolerancia a fallas se relaciona con la redundancia y replicación de componentes.

---

# 39. Clusters

Un **cluster** es un conjunto de computadoras que trabajan coordinadamente para proporcionar capacidad de procesamiento o servicios.

Los nodos de un cluster pueden cooperar para ejecutar tareas, distribuir carga o proporcionar alta disponibilidad.

Los clusters se relacionan con la clasificación de sistemas de **software fuerte y hardware fuerte**, presentada en los apuntes, donde se encuentran los sistemas paralelos.

---

# 40. Virtualización

La **virtualización** permite crear representaciones virtuales de recursos físicos, como máquinas, sistemas operativos, almacenamiento o redes.

Una máquina física puede ejecutar varias máquinas virtuales, cada una con su propio sistema operativo y recursos asignados.

En sistemas distribuidos, la virtualización permite abstraer los recursos físicos y facilitar su administración, aislamiento y asignación.

---

# 41. Redes sin servidores

Las **redes sin servidores**, relacionadas con arquitecturas descentralizadas, reducen o eliminan la dependencia de un servidor central.

Los participantes pueden proporcionar y consumir servicios directamente entre sí.

Las arquitecturas P2P constituyen un ejemplo importante de este enfoque.

En lugar de depender exclusivamente de:

**cliente → servidor**

se puede utilizar:

**peer ↔ peer.**

---

# 42. Grid computing

El **Grid Computing** consiste en coordinar recursos computacionales distribuidos para ejecutar tareas que pueden beneficiarse de la utilización conjunta de diferentes recursos.

Los recursos pueden encontrarse físicamente separados y pertenecer a diferentes sistemas.

El objetivo es aprovechar la capacidad computacional disponible de múltiples recursos para resolver problemas o ejecutar trabajos.

---

# 43. Cloud computing

El **Cloud Computing o computación en la nube** proporciona recursos y servicios computacionales a través de una red.

Los recursos pueden incluir procesamiento, almacenamiento, bases de datos, aplicaciones y servicios.

Una característica importante es que el usuario puede consumir recursos sin necesariamente conocer la ubicación física exacta de la infraestructura que los proporciona.

Esto se relaciona directamente con conceptos de sistemas distribuidos como virtualización, escalabilidad, distribución de recursos y tolerancia a fallos.

---

# 44. Internet de las cosas (IoT)

El **Internet of Things (IoT)** consiste en la conexión de objetos y dispositivos físicos capaces de recopilar, procesar o intercambiar información mediante redes.

Un sistema IoT puede involucrar sensores, dispositivos embebidos, redes, servidores y servicios distribuidos.

Por esta razón, IoT puede utilizar muchos conceptos de sistemas distribuidos: comunicación entre nodos, procesamiento distribuido, sincronización, almacenamiento, seguridad y tolerancia a fallos.

---

# 45. Seguridad en sistemas distribuidos

La seguridad es una función importante de los sistemas operativos y adquiere todavía mayor importancia en sistemas distribuidos.

Dentro de una computadora pueden utilizarse contraseñas, usuarios, permisos, control de acceso, protección de memoria, protección de archivos y aislamiento de procesos.

En una red se requieren mecanismos adicionales como **firewalls, filtrado de tráfico, autenticación, cifrado, control de acceso y sistemas de detección y prevención de intrusiones**.

Un **firewall** controla el tráfico de red de acuerdo con determinadas reglas. Una representación conceptual es:

**Internet → Firewall → Red interna.**

En Linux, una herramienta tradicional para configurar reglas de filtrado es **iptables**.

---

# 46. Consistencia de datos

La **consistencia de datos** es la propiedad mediante la cual los diferentes componentes de un sistema mantienen información coherente.

En un sistema distribuido pueden existir múltiples copias de la misma información. Si un nodo modifica una copia, puede ser necesario propagar dicha modificación hacia otros nodos.

Por ello, la replicación, sincronización, comunicación y control de concurrencia están directamente relacionados con la consistencia.

---

# 47. Replicación

La **replicación** consiste en mantener múltiples copias de información o componentes dentro de diferentes nodos.

Su propósito puede ser mejorar la disponibilidad, tolerancia a fallos o rendimiento.

Sin embargo, mantener varias copias genera el problema de garantizar que las réplicas permanezcan consistentes.

---

# 48. Transparencia en sistemas distribuidos

La **transparencia** busca ocultar al usuario la complejidad derivada de la distribución.

El usuario debería poder utilizar un recurso sin necesitar conocer todos los detalles relacionados con su ubicación o implementación.

Entre las formas de transparencia relacionadas con los sistemas distribuidos se encuentran la transparencia de:

**ubicación:** el usuario no necesita conocer dónde está el recurso.

**migración:** el recurso puede cambiar de ubicación sin que el usuario tenga que modificar su interacción.

**replicación:** existen varias copias, pero el usuario puede percibirlas como un único recurso.

**concurrencia:** varios usuarios pueden acceder a recursos compartidos sin necesitar conocer toda la coordinación interna.

**paralelismo:** diferentes operaciones pueden ejecutarse simultáneamente sin que el usuario tenga que administrar directamente esa ejecución.

**fallos:** el sistema intenta ocultar determinados fallos y continuar proporcionando el servicio.

La transparencia es uno de los conceptos fundamentales para que un sistema distribuido pueda aparentar ser un sistema único.

---

# 49. Escalabilidad

La **escalabilidad** es la capacidad de un sistema para crecer cuando aumenta la demanda.

En los sistemas distribuidos, el crecimiento puede conseguirse agregando nuevos nodos, procesadores, almacenamiento o servicios.

Los apuntes describen esta característica como **crecimiento proporcional**: el sistema puede incorporar nuevos recursos o computadoras cuando aumenta la demanda.

---

# 50. Balanceo de carga

El **balanceo de carga** consiste en distribuir el trabajo entre diferentes recursos.

Los recursos que pueden distribuirse incluyen procesamiento, memoria, almacenamiento y servicios.

Un sistema puede utilizar varios servidores para atender solicitudes. Si un servidor recibe demasiada carga, otras máquinas pueden procesar parte de las solicitudes.

El balanceo de carga permite aprovechar mejor los recursos y evitar que un único nodo se convierta en un cuello de botella.

---

# 51. Relación entre todos los conceptos

Los conceptos de la materia forman una cadena lógica.

El **sistema operativo** administra los recursos de cada computadora. Dentro de él se ejecutan **procesos e hilos**, los cuales pueden trabajar de manera concurrente.

Las computadoras se conectan mediante **redes**, cuya comunicación puede estudiarse mediante modelos como **OSI**.

Cuando diferentes computadoras cooperan mediante procesos que se comunican y coordinan, se construye un **sistema distribuido**.

A partir de ahí aparecen problemas específicos: **naming, binding, paso de mensajes, sincronización, relojes físicos y lógicos, concurrencia, transacciones, exclusión mutua, elección, consenso, migración, calendarización, tolerancia a fallos y consistencia**.

Estos problemas se resuelven mediante diferentes **algoritmos distribuidos** y pueden organizarse utilizando diferentes **arquitecturas**, como cliente-servidor, multiestrato, orientada a componentes, orientada a datos, orientada a eventos, P2P estructurada, P2P no estructurada e híbrida.

Finalmente, estos principios aparecen en tecnologías reales como **clusters, virtualización, Grid Computing, Cloud Computing e IoT**.

---

# 52. Resumen conceptual para el examen

La idea central de la materia puede resumirse de la siguiente forma:

**Sistema operativo → administra recursos y procesos.**

**Proceso → programa en ejecución.**

**Hilo → unidad de ejecución dentro de un proceso.**

**Concurrencia → varias tareas progresan durante un mismo periodo.**

**Red → permite comunicar computadoras.**

**Sistema distribuido → varias computadoras independientes cooperan y pueden percibirse como un sistema único.**

**Naming → identifica recursos mediante nombres.**

**Binding → asocia un nombre con un recurso.**

**Cliente → solicita servicios.**

**Servidor → proporciona servicios.**

**Paso de mensajes → permite la comunicación entre procesos.**

**Reloj físico → representa el tiempo real.**

**Reloj lógico → establece orden lógico de acontecimientos.**

**Lamport → mantiene el orden causal mediante valores lógicos.**

**Vector clock → permite analizar causalidad y concurrencia con mayor precisión.**

**Concurrencia → múltiples procesos pueden avanzar de manera intercalada.**

**Exclusión mutua → controla el acceso a una sección crítica.**

**Elección → selecciona un coordinador.**

**Migración → mueve procesos entre nodos.**

**Consenso → permite que procesos lleguen a un acuerdo.**

**Tolerancia a fallos → permite continuar funcionando ante fallos parciales.**

**Escalabilidad → permite crecer agregando recursos.**

**Balanceo de carga → distribuye el trabajo entre recursos.**

**Replicación → mantiene varias copias de información o servicios.**

**Transparencia → oculta al usuario parte de la complejidad de la distribución.**

**Cluster → conjunto de computadoras que cooperan.**

**Virtualización → abstrae recursos físicos mediante recursos virtuales.**

**Grid Computing → coordina recursos distribuidos para ejecutar trabajos.**

**Cloud Computing → proporciona recursos y servicios computacionales mediante una red.**

**IoT → conecta dispositivos físicos capaces de intercambiar información.**

---

# 53. Mapa general del temario

La estructura completa de la materia puede visualizarse conceptualmente de esta manera:

**1. Introducción**

→ Sistemas distribuidos  
→ Taxonomía  
→ Flynn: SISD, SIMD, MISD, MIMD  
→ Redes  
→ Cliente-servidor  
→ Naming y binding

**2. Sincronización**

→ Relojes físicos  
→ Sincronización externa e interna  
→ Relojes lógicos  
→ Lamport  
→ Vector clocks  
→ Concurrencia  
→ Control de concurrencia  
→ Transacciones  
→ Grupos de comunicación  
→ Exclusión mutua  
→ Elección  
→ Migración  
→ Estrategias de asignación

**3. Algoritmos distribuidos**

→ Concurrencia  
→ Calendarización  
→ Consenso  
→ Elección  
→ Detección de terminación  
→ Tolerancia a fallos  
→ Estabilidad

**4. Arquitecturas distribuidas**

→ Tolerancia a fallas  
→ Clusters  
→ Virtualización  
→ Migración y asignación  
→ Redes sin servidores  
→ Grid Computing  
→ Cloud Computing  
→ IoT

La relación fundamental entre todos estos bloques es que un sistema distribuido está compuesto por **múltiples procesos ejecutándose en diferentes nodos**, los cuales necesitan **comunicarse, sincronizarse y coordinarse** para proporcionar servicios de manera coherente, escalable y tolerante a fallos.

---

# 54. Conceptos que debes poder explicar de memoria

Para preparar el examen, no basta con reconocer los términos. Debes ser capaz de explicar con tus propias palabras qué significa cada uno y cómo se relaciona con los demás.

Las preguntas conceptuales más importantes que debes dominar son:

**¿Qué es un sistema distribuido?**  
Una colección de computadoras independientes que trabajan juntas y que pueden aparentar funcionar como un único sistema.

**¿Por qué una red es importante para un sistema distribuido?**  
Porque permite la comunicación entre las diferentes computadoras que forman el sistema.

**¿Cuál es la diferencia entre proceso e hilo?**  
El proceso es una instancia de un programa en ejecución, mientras que un hilo es una unidad de ejecución dentro de un proceso.

**¿Cuál es la diferencia entre concurrencia y paralelismo?**  
La concurrencia significa que varias tareas progresan durante un mismo periodo; el paralelismo implica ejecución simultánea real.

**¿Qué diferencia existe entre naming y binding?**  
Naming identifica recursos mediante nombres y binding establece la asociación entre esos nombres y los recursos.

**¿Qué diferencia existe entre reloj físico y reloj lógico?**  
El reloj físico representa el tiempo real, mientras que el reloj lógico busca establecer un orden entre acontecimientos.

**¿Qué garantiza Lamport?**  
Si existe una relación causal a→ba \rightarrow b, entonces el valor lógico de aa será menor que el de bb.

**¿Para qué sirven los relojes vectoriales?**  
Para representar relaciones causales y distinguir acontecimientos concurrentes.

**¿Qué es exclusión mutua distribuida?**  
Es el mecanismo que garantiza que solamente un proceso distribuido acceda a una sección crítica a la vez.

**¿Qué es consenso?**  
Es el proceso mediante el cual diferentes procesos llegan a un acuerdo sobre una decisión o valor.

**¿Qué es tolerancia a fallos?**  
Es la capacidad de continuar proporcionando servicio a pesar de que algunos componentes fallen.

**¿Qué diferencia existe entre una arquitectura centralizada y una descentralizada?**  
La centralizada organiza los componentes alrededor de una estructura jerárquica o componentes centrales, mientras que una descentralizada distribuye la responsabilidad entre múltiples nodos.

**¿Qué diferencia existe entre P2P estructurada y no estructurada?**  
La P2P estructurada controla la organización de nodos y la ubicación de los datos para facilitar las búsquedas; la no estructurada no mantiene una organización rígida de este tipo.

**¿Qué es una DHT?**  
Una tabla hash distribuida que permite asociar datos con nodos dentro de un espacio de identificadores y realizar búsquedas eficientes.

**¿Qué diferencia existe entre Push y Pull?**  
En Pull el receptor solicita la información; en Push el emisor la envía.

**¿Qué es un cluster?**  
Un conjunto de computadoras que cooperan para proporcionar capacidad de procesamiento o servicios.

**¿Qué es Cloud Computing?**  
Un modelo en el que recursos y servicios computacionales se proporcionan mediante una red, ocultando al usuario parte de la infraestructura física.

---

# 55. Idea final para estudiar la materia

La materia puede entenderse como el estudio de **cómo hacer que varias computadoras independientes trabajen coordinadamente como un sistema**.

Para lograrlo primero se necesita comprender cómo funciona cada computadora mediante el **sistema operativo**, los **procesos**, los **hilos**, la **planificación** y la **concurrencia**. Después es necesario comprender cómo se comunican las computadoras mediante las **redes**, los modelos de comunicación y el **paso de mensajes**.

A partir de ahí aparecen los problemas propios de la distribución: cada computadora posee su propio reloj, los procesos pueden ejecutarse simultáneamente, los mensajes pueden retrasarse, pueden ocurrir fallos parciales y los datos pueden encontrarse replicados. Por eso se estudian **sincronización, relojes lógicos, control de concurrencia, transacciones, exclusión mutua, elección, consenso, detección de terminación y tolerancia a fallos**.

Finalmente, los sistemas pueden organizarse mediante diferentes **arquitecturas distribuidas**, desde modelos centralizados como **cliente-servidor** y **multiestrato**, hasta modelos descentralizados como **P2P estructurado, P2P no estructurado e híbrido**. Estos conceptos permiten comprender tecnologías modernas como **clusters, Grid Computing, Cloud Computing e IoT**.

La idea que conviene conservar como eje de todo el curso es:

> **Un sistema distribuido no consiste simplemente en conectar varias computadoras. Consiste en lograr que múltiples computadoras y procesos independientes se comuniquen, coordinen y cooperen para proporcionar un servicio común, enfrentando problemas de concurrencia, sincronización, comunicación, consistencia, seguridad y fallos.**

![](../Sistemas%20distribuidos/img/ArquitecturasSisDis.png)

