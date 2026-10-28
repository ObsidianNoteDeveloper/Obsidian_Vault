
# Sistema distribuido para la recopilación y procesamiento de eventos de red

### Planteamiento 

En una red de computadoras se generan continuamente diferentes eventos, como conexiones, solicitudes y comunicaciones entre dispositivos. El procesamiento de esta información puede dividirse entre diferentes componentes que trabajen de manera concurrente y se comuniquen entre sí. 

Por ello, se propone desarrollar un sistema distribuido para la recopilación, transmisión y procesamiento de eventos de red, utilizando diferentes procesos o servicios independientes que colaboren para realizar las distintas tareas del sistema.

### Objetivo 

Diseñar e implementar un sistema distribuido capaz de recibir eventos de red generados de manera simulada, distribuir su procesamiento entre diferentes componentes y almacenar los resultados para su posterior consulta. 

### Elementos de Sistemas Distribuidos 

El proyecto permitirá aplicar conceptos fundamentales de la asignatura, entre ellos:
- Comunicación entre procesos y nodos. 
- Arquitectura cliente-servidor.
- Concurrencia.
- Paso de mensajes. 
- Sincronización.
- Comunicación mediante sockets.
- Distribución de tareas.
- Manejo de fallos y disponibilidad.
- Escalabilidad del sistema. 
 
### Tecnologías propuestas 

La implementación se realizará principalmente utilizando Java sobre Linux, empleando comunicación mediante sockets. Se utilizará PostgreSQL para el almacenamiento de los eventos y HTTP/REST para permitir la consulta de la información. El proyecto se gestionará mediante Maven y se utilizarán pruebas unitarias con JUnit.

### Funcionamiento general 

El sistema contará con varios componentes que colaborarán entre sí: 
1. Generadores de eventos
2. Servidor de procesamiento
3. Base de datos
4. API para consulta 

Los generadores enviarán eventos al servidor, el cual procesará y almacenará la información. Posteriormente, los datos podrán consultarse mediante una interfaz de comunicación HTTP. 

![](Diagrama1.drawio.png)

### Resultado esperado 

Obtener un prototipo funcional de un sistema distribuido que permita demostrar la comunicación y coordinación entre diferentes componentes, así como el procesamiento concurrente y el intercambio de información entre nodos.

# Ruta de desarrollo del proyecto

## Etapa 1. Java y sockets TCP

Aprende a crear un servidor que escuche un puerto y un cliente que se conecte, envíe un mensaje y reciba una respuesta.
- Resultado: comunicación cliente-servidor funcional.

## Etapa 2. Concurrencia

Aprende `Thread`, `Runnable` y `ExecutorService`. Modifica el servidor para atender varios clientes sin bloquear las demás conexiones.
- Resultado: varios clientes conectados simultáneamente.

## Etapa 3. PostgreSQL y JDBC

Aprende SQL básico, diseño de tablas, conexiones JDBC, `PreparedStatement` y transacciones.
- Resultado: los eventos recibidos quedan almacenados y pueden consultarse.

## Etapa 4. API HTTP/REST

Aprende HTTP, JSON, métodos `GET` y códigos de estado. Implementa una API en Java que consulte los eventos almacenados.
- Resultado: tu compañera podrá consultar los eventos desde su interfaz en Python.

## Etapa 5. Integración y pruebas

Aprende pruebas unitarias con JUnit, manejo de desconexiones, validación de entradas y configuración de ejecución en Linux.
- Resultado: prototipo integrado y demostrable.

---

# Antecedentes

Algunos de los temas y conceptos que debo estudiar para desarrollar el proyecto

| **Tema**         | **Qué necesitas aprender**                           | **Para qué lo usarás**                 |
| ---------------- | ---------------------------------------------------- | -------------------------------------- |
| Clases y objetos | Clases, constructores, atributos, métodos            | Representar los eventos de red         |
| Excepciones      | `try`, `catch`, `finally`, `IOException`             | Manejar errores de comunicación        |
| Entrada y salida | `InputStream`, `OutputStream`, lectores y escritores | Enviar y recibir mensajes              |
| Redes            | IP, puertos, TCP, cliente-servidor                   | Comunicar los clientes con el servidor |
| Concurrencia     | `Thread`, `Runnable`, `ExecutorService`              | Atender múltiples clientes             |
| Colecciones      | `List`, `Map`, `Queue`                               | Administrar eventos y resultados       |
| SQL              | `CREATE`, `INSERT`, `SELECT`, `WHERE`                | Almacenar y consultar eventos          |

# Recursos de aprendizaje

- Java: [Tutorial de sockets](https://docs.oracle.com/javase/tutorial/networking/sockets/).
    
- Apache Maven: [Guía de inicio](https://maven.apache.org/guides/getting-started/).
    
- PostgreSQL: [Tutorial oficial de SQL](https://www.postgresql.org/docs/current/tutorial.html).
    
- Spring Boot: [Documentación de referencia](https://docs.spring.io/spring-boot/index.html).
    
- JUnit: [Guía de usuario](https://junit.org/junit5/docs/current/user-guide/).






