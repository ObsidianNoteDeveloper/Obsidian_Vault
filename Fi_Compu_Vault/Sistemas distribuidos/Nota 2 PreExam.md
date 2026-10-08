
Resuelve las siguientes preguntas con explicaciones breves para estudiar antes de mi examen 

1. ¿Qué es un proceso?

Un **proceso** es un programa que está **en ejecución**. Tiene su propio espacio de memoria, recursos, estado de ejecución e identificador (PID). Por ejemplo, cuando ejecutas un programa en C, el sistema operativo crea un proceso para ejecutarlo.

---

2. ¿Qué es un hilo?

Un **hilo (thread)** es la unidad más pequeña de ejecución dentro de un proceso. Un proceso puede tener varios hilos que se ejecutan de manera concurrente y **comparten la memoria y recursos del proceso**.

**Ejemplo:** un navegador puede tener diferentes hilos para cargar páginas, reproducir contenido y atender la interfaz.

---

3. ¿Cuál es la diferencia entre hilo y un proceso?

La principal diferencia es que un **proceso tiene su propio espacio de memoria y recursos**, mientras que los **hilos pertenecientes al mismo proceso comparten memoria y recursos**.

|Proceso|Hilo|
|---|---|
|Tiene memoria independiente|Comparte memoria con otros hilos del proceso|
|Mayor costo de creación|Menor costo de creación|
|Comunicación más compleja|Comunicación más sencilla|
|Tiene su propio PID|Pertenece a un proceso|

**Para recordar:**
	**Proceso** = programa en ejecución.  
	**Hilo** = unidad de ejecución dentro de un proceso.

---

4. ¿Qué es un sistema distribuido? explica y proporciona ejemplos

Un **sistema distribuido** es un conjunto de computadoras independientes que **trabajan conjuntamente mediante una red** y coordinan sus acciones para proporcionar un servicio o realizar una tarea.

Aunque existen varias computadoras, el sistema puede presentarse al usuario como si fuera un único sistema.

**Ejemplos:**

- Servicios de almacenamiento en la nube.
- Sistemas bancarios distribuidos.
- Google y otros buscadores.
- Plataformas como Netflix.
- Sistemas de bases de datos distribuidas.
- Un sistema cliente-servidor con varios clientes.

**Idea clave:**
	Varias computadoras + comunicación por red + coordinación = sistema distribuido.

---

5. Cual de las siguientes son desventajas de un sistema distribuido, explique por qué:
	a) Software, redes y seguridad
	b) Hardware, software y seguridad
	**c) Redes, seguridad y confiabilidad**
	d) Software, redes y localización

Son áreas problemáticas porque:

- **Redes:** pueden existir retrasos, pérdida de mensajes o interrupciones de comunicación.
- **Seguridad:** existen más puntos de acceso y comunicación que deben protegerse.
- **Confiabilidad:** la falla de una computadora, servidor o enlace puede afectar al sistema.

---

6. Describa los aspectos de diseño de un sistema distribuido 

Los principales aspectos de diseño son:

- **Transparencia:** ocultar al usuario la distribución de los recursos.
- **Comunicación:** permitir que los procesos intercambien información.
- **Concurrencia:** permitir que varias tareas se ejecuten simultáneamente.
- **Sincronización:** coordinar procesos y eventos.
- **Tolerancia a fallos:** continuar funcionando aunque algún componente falle.
- **Escalabilidad:** permitir aumentar usuarios, equipos o recursos sin degradar demasiado el sistema.
- **Seguridad:** proteger información, procesos y comunicaciones.
- **Gestión de recursos:** administrar adecuadamente los recursos distribuidos.

---

7. ¿Qué tipo de taxonomía no pertenece a un sistema distribuido, y por qué?
	a) Software fuerte + hardware fuerte
	b) Software débil + hardware débil
	c) Software fuerte + hardware débil
	**d) Ninguna de las anteriores**

Las combinaciones propuestas pueden utilizarse para clasificar sistemas según la relación entre la capacidad del **software y hardware**. Por lo tanto, no hay una combinación de las primeras tres que necesariamente sea ajena a los sistemas distribuidos.

---

8. Elija la opción con las tecnologías que dan soporte a los sistemas distribuidos, y explica por qué esa opción es la correcta
	a) Microprocesadores y redes de área local
	b) Multiprogramación y redes de área local
	**c) Procesos, hilos y redes de área local**
	d) Procesos y redes de área local
	e) Hilos y redes de área local

Estas tecnologías son fundamentales porque:

- **Procesos:** permiten ejecutar programas y tareas.
- **Hilos:** permiten realizar múltiples actividades concurrentemente.
- **Redes:** permiten que las diferentes computadoras intercambien información.

---

9. ¿Cuál es una área de desventaja de los sistemas distribuidos y por qué?
	a) Hardware
	b) Multiprocesamiento
	**c) Confiabilidad**
	d) Seguridad
	e) Transparencia 

En un sistema distribuido existen múltiples componentes: computadoras, procesos, redes y servidores. Si alguno falla, puede afectar el funcionamiento del sistema.

Por eso se necesitan mecanismos de **tolerancia a fallos, redundancia y recuperación**.

> **Ojo:** seguridad y transparencia también representan retos en sistemas distribuidos, pero si la pregunta pide una opción específica sobre **desventajas**, la respuesta esperada suele ser **confiabilidad**.

---

10. Elija la opción del programa ejecutándose en cualquier computadora
	a) Hilo
	**b) Proceso**
	c) Subproceso
	d) Proceso hijo
	e) Proceso padre 

Un **proceso** es precisamente un programa que está siendo ejecutado por el sistema operativo.

**Memoriza:**

> Programa almacenado → programa.  
> Programa ejecutándose → **proceso**.

---

11. ¿Cuál de las siguientes opciones es una técnica que se utiliza en sistemas peer to peer para organización de la información, en el caso de utilizar un servidor de índices.
	a) Tablas hash
	b) Indexación por caminos aleatorios
	**c) Tablas hash distribuidas (DHT)**
	d) Indexación por modelo epidemiológico
	e) Ninguna de las anteriores

La respuesta que corresponde a la técnica conocida es:

Las **DHT (Distributed Hash Tables)** permiten distribuir información de manera descentralizada entre diferentes nodos y localizar rápidamente los recursos.

---

12. ¿Cuál de las opciones es la principal característica de una arquitectura descentralizada en sistemas distribuidos y por qué?
	a) La repartición de información 
	**b) Son sistemas con distribución horizontal sin jerarquías**
	c) Utilizan redes de área local
	d) Utilizan redes de área local y computadoras personales
	e) Ninguna de las anteriores

Una arquitectura descentralizada no depende de un único servidor central. Los nodos pueden participar directamente en las funciones del sistema.

Por ello se caracteriza por una **distribución horizontal**, sin una jerarquía central dominante.

**Ejemplo:** sistemas **Peer-to-Peer (P2P)**.

---

13. Aplicación que tiene la información que hay que difundir, publica esta información sin tener que saber quién está interesado en recibirla. Envía la información a través de canales. Justifique la respuesta.
	a) Mediador
	b) Broker
	**c) Productor de información**
	d) Consumidor
	e) Canal

En un sistema basado en **publicación/suscripción**, el **productor** genera y publica la información sin necesidad de conocer directamente a los consumidores.

El canal permite transportar o distribuir la información.

Para recordar: **Productor → publica → Canal → recibe el Consumidor**

---

14. Elije los sistemas distribuidos que se caracterizan por publicar la información sólo si es extraordinaria. Justifica la elección
	a) Sistemas distribuidos basados en componentes
	b) Sistemas distribuidos orientados a objetos
	**c) Sistemas distribuidos basados en eventos**
	d) Sistemas distribuidos por capas
	e) Ninguno de los anteriores

Los sistemas **basados en eventos** generan y distribuyen información cuando ocurre determinado evento.

Por ejemplo, un sistema de monitoreo puede enviar una notificación únicamente cuando detecta una situación anormal.

**Idea clave:**

> Ocurre un evento → se genera/publica información → los interesados pueden recibirla.

---

15. Son un conjunto de reglas que gobiernan la interacción de procesos concurrentes en sistemas distribuidos, estos son utilizados en un gran número de campos como sistemas operativos, redes de computadoras o comunicación de datos.
	a) Paquetes 
	b) TCP/UDP
	c) Datagramas
	d) Sockets
	**e) Protocolos**

Los **protocolos** son conjuntos de reglas que establecen cómo deben comunicarse e interactuar diferentes procesos o sistemas.

Por ejemplo, **TCP/IP, HTTP y UDP** utilizan reglas definidas para permitir la comunicación entre sistemas.

---

##### 🔑 Cinco conceptos que debes dominar

**Proceso:** programa en ejecución.  
**Hilo:** unidad de ejecución dentro de un proceso.  
**Sistema distribuido:** varias computadoras que colaboran mediante una red.  
**DHT:** estructura distribuida para localizar información entre nodos.  
**Protocolo:** conjunto de reglas para la comunicación.

---

Diseñe la arquitectura de un sistema distribuido que en la implementación cuente con 5 servidores de base de datos, 4 equipos de procesamiento de datos y 4 equipos de hospedaje de la aplicación, que atiende las peticiones de los usuarios de cualquier dispositivo móvil o de cómputo. Justifica el por qué esta arquitectura.

![](ArquitecturaSD1.png)

![](JustificacionASD1.png)

---

Realice el esquema de capas de organización computacional, donde se encuentra el sistema operativo y describa cada una 

![](EsquemaCapas.png)

---

Realice un cuadro sinóptico de los tipos de topologías en redes de computadoras, sus ventajas y desventajas.
![](Pasted%20image%2020261007224838.png)

![](TopologiaRed.png)

![](Pasted%20image%2020261007224817.png)
