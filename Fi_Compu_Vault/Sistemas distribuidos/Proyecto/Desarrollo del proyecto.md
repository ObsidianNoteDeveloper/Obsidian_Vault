
# Ruta de aprendizaje para tu proyecto

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






