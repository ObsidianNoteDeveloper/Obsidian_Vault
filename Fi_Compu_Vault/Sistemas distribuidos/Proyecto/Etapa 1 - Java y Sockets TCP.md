
La idea es avanzar como lo haría en un proyecto de ingeniería de software: 
- Primero estudiar los fundamentos
- Después practicar las herramientas
- Y finalmente implementar un prototipo que servirá como base para las siguientes etapas.

## Índice

[Fundamentos de comunicación en red](#Fundamentos%20de%20comunicación%20en%20red)
[Fundamentos de Java](#Fundamentos%20de%20Java)
[Clases de Java para sockets TCP](#Clases%20de%20Java%20para%20sockets%20TCP)
[Herramientas y conocimientos técnicos](#Herramientas%20y%20conocimientos%20técnicos)
[Guía paso a paso: construir el cliente-servidor](#Guía%20paso%20a%20paso%20construir%20el%20cliente-servidor)
[Ruta del Proyecto](#Ruta%20del%20Proyecto)


**Objetivo:**
	Comprender los conceptos para diseñar, programar, probar y explicar de forma técnica el sistema.
	Aprender como varios clientes pueden comunicarse simultáneamente con un servidor central, cómo se transmiten los eventos por las red, cómo se procesan y cómo se almacenan en PostgreSQL.


---

# Fundamentos de comunicación en red
## Introducción

La arquitectura cliente-servidor es un modelo de comunicación en el que uno o varios programas cliente solicitan servicios y un programa servidor recibe, procesa y responde a esas solicitudes.

- **Cliente:** representa un dispositivo de red simulado que genera eventos.
- **Servidor:** recibe los eventos de los clientes, los valida y los procesa.
- **Base de datos PostgreSQL:** almacena los eventos recibidos.
- **API REST:** permite consultar los datos procesados mediante solicitudes HTTP.
- **Interfaz gráfica:** permite al usuario visualizar los resultados

La comunicación TCP entre los clientes y el servidor es una parte del sistema; la API REST es otra.
- TCP es el transporte que se utilizara para recibir los eventos, mientras que HTTP/REST es la interfaz para consultar los datos.

## Conceptos básicos

**Cliente**
	Es un proceso o aplicación que solicita servicios, recursos o información a otro proceso denominado servidor. El cliente inicia la comunicación mediante una petición y recibe una respuesta con el resultado de la operación solicitada.

> [!Note]
>En nuestro proyecto de _recopilación de eventos de red_, cada cliente Java representa un dispositivo que genera eventos simulados al servidor central mediante una conexión TCP.

**Servidor**
	Es un proceso o aplicación que permanece disponible para recibir solicitudes de los clientes, procesarlas y proporcionar respuestas o servicios. Puede administrar recursos compartidos, ejecutar operaciones, almacenar información y atender múltiples conexiones.

> [!Note]
> El servidor Java recibe eventos de distintos clientes, valida su contenido y los almacena en una base de datos PostgreSQL.

**Petición y respuesta**
	La petición (request) es el mensaje que un cliente envía a un servidor para solicitar una operación o transmitir información. La respuesta (response) es el mensaje que el servidor devuelve para comunicar el resultado de la petición, confirmar su recepción o informar sobre un error.
	Este intercambio permite establecer un mecanismo de comunicación entre los procesos distribuidos.

> [!Example]
> - Petición: un cliente envía un evento que contiene una dirección IP, un protocolo y un puerto.
> - Procesamiento: el servidor recibe y valida el evento.
> - Respuesta: el servidor informa al cliente que el evento fue recibido y procesado correctamente, o indica el error correspondiente.

**Protocolo**
	Es un conjunto de reglas y convenciones que determinan cómo se establece una comunicación, cómo se estructuran e intercambian los mensajes y cómo se interpretan los datos entre dos o más entidades.
	Los protocolos permiten que los sistemas se comuniquen de manera compatible y predecible.

> [!Example]
> - TCP: proporciona una comunicación confiable y ordenada mediante un flujo de bytes.
> - HTTP: define el intercambio de solicitudes y respuestas para servicios web.
> - DNS: permite consultar información asociada con nombres de dominio.

<div style="text-align: center;">  
<img src="ModelTCP.png" width="300">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 1</b>. Modelo TCP IP. https://medium.com/
</div>

> [!Note]
> En este proyecto, TCP se utilizará para comunicar los clientes Java con el servidor, mientras que HTTP podrá utilizarse para exponer una API REST.

**Concurrencia**
	Es la capacidad de un sistema para gestionar múltiples tareas o procesos durante periodos de tiempo que se superponen, mediante la alternancia de ejecución o el paralelismo cuando existen varios núcleos de procesamiento.
	En un servidor, la concurrencia permite atender las comunicaciones de varios clientes sin tener que finalizar por completo la atención de uno para comenzar la de otro.

> [!Note]
> El servidor Java utiliza hilos (threads) para atender simultáneamente las conexiones de varios clientes que envían eventos de red.

**Escalabilidad**
	Es la capacidad de un sistema para incrementar su capacidad de procesamiento, almacenamiento o atención de solicitudes conforme aumenta la carga de trabajo, manteniendo un rendimiento aceptable.
	Existen dos estrategias principales:
		- Escalabilidad vertical: aumentar los recursos de una máquina, como CPU, memoria RAM o almacenamiento.
		- Escalabilidad horizontal: agregar más máquinas, instancias o nodos para distribuir la carga de trabajo.

> [!Example]
> Si aumenta el número de clientes que envían eventos, se pueden optimizar los hilos del servidor o distribuir la recepción y el procesamiento entre varias instancias.

**Tolerancia a fallos**
	Es la capacidad de un sistema para continuar ofreciendo sus servicios, total o parcialmente, cuando uno o varios de sus componentes presentan errores o dejan de funcionar.
	Puede implementarse mediante redundancia, replicación, detección de fallos, recuperación automática, reintentos controlados y mecanismos de respaldo.

> [!Note]
> Si nuestro cliente Java se desconecta inesperadamente, el servidor debe liberar sus recursos y continuar atendiendo a los demás clientes. Para tolerar la caída del servidor Java, sería necesario incorporar mecanismos adicionales de recuperación o redundancia.

**Arquitectura cliente-servidor**
	El cliente inicia una solicitud y el servidor espera conexiones para atenderlas. En este proyecto, los clientes representan dispositivos que generan eventos y el servidor central los recibe.

<div style="text-align: center;">  
<img src="clienteServidor.png" width="500">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 2</b>. Cliente/servidor. https://ee547.usc-ece.com
</div>

**Arquitectura centralizada**
	Es un modelo de organización en el que las principales funciones de procesamiento, administración o almacenamiento se concentran en un componente central, al cual acceden los demás componentes del sistema.
	Facilita la administración de los recursos, la aplicación de reglas comunes y el control de la información. Sin embargo, el componente central puede convertirse en un cuello de botella o en un punto único de fallo si no existen mecanismos de redundancia.

> [!Note] 
> El servidor Java central recibe todos los eventos de red y los almacena en una única base de datos PostgreSQL.

**Microservicios**
	Es un estilo arquitectónico que organiza una aplicación como un conjunto de servicios pequeños, independientes y especializados, cada uno responsable de una función específica. Estos servicios se comunican mediante interfaces y protocolos definidos, como HTTP o mensajería.
	Los microservicios permiten desarrollar, desplegar y escalar componentes de forma independiente, aunque introducen complejidad adicional en la comunicación, el monitoreo y la administración de fallos.

> [!Example]
> El sistema podría dividirse en un servicio de recepción de eventos, otro de consulta de eventos y otro de autenticación. Cada servicio tendría una responsabilidad claramente delimitada.

**Peer-to-peer (P2P)**
	Es una arquitectura de red en la que los nodos pueden actuar tanto como clientes como servidores, compartiendo recursos directamente sin depender necesariamente de un servidor central para todas las operaciones.
	Los nodos pueden intercambiar información, almacenamiento o capacidad de procesamiento. La organización puede ser descentralizada, aunque algunos sistemas P2P utilizan servidores auxiliares para facilitar el descubrimiento de nodos.

**Arquitectura orientada a eventos**
	Es un estilo arquitectónico en el que los componentes producen, transmiten y consumen eventos que representan hechos relevantes ocurridos en el sistema. Los componentes pueden reaccionar a dichos eventos sin necesitar una comunicación directa y sincrónica entre el productor y cada consumidor.
	Puede implementarse mediante colas de mensajes, intermediarios de eventos (_event brokers_) o mecanismos de publicación y suscripción (_publish/subscribe_).

> [!Example]
> Cuando un cliente genera un evento de red, el sistema lo recibe y lo distribuye para que otros componentes puedan almacenarlo, analizarlo o mostrarlo en una interfaz gráfica.

En este proyecto,  se implementara principalmente la arquitectura cliente-servidor con procesamiento centralizado y concurrencia mediante hilos.

## Dirección IP y puerto

La IP identifica una interfaz de red y el puerto identifica un punto de comunicación de una aplicación. Por ejemplo, `127.0.0.1:5000` indica el puerto 5000 del equipo local.

## TCP

Es un protocolo de transporte orientado a conexión que proporciona un flujo de bytes ordenado y confiable. Gestiona retransmisiones y entrega de datos, pero la aplicación debe definir cómo separar e interpretar los mensajes.

<div style="text-align: center;">  
<img src="TCP.png" width="300">  
</div>
<div style="text-align: center; color: #555555;">
<b>Imagen 3</b> Modelo cliente - servidor. https://gateoverflow.in/ 
</div>

En TCP, SYN y ACK son indicadores (flags) de la cabecera TCP que permiten establecer una conexión y confirmar la recepción de información entre dos dispositivos.

**SYN (Synchronize):** Es una bandera TCP utilizada para iniciar una conexión y sincronizar los números de secuencia iniciales de los dos extremos.

**ACK (Acknowledgment):** Es una bandera TCP que indica que el campo de confirmación es válido. Este campo permite confirmar los bytes recibidos y, durante el establecimiento de la conexión, reconocer el número de secuencia inicial del otro extremo.

TCP establece normalmente una conexión mediante un procedimiento de tres pasos llamado three-way handshake o negociación de tres vías.

| Paso | Banderas TCP | Función                                                                   |
| ---- | ------------ | ------------------------------------------------------------------------- |
| 1    | `SYN`        | El cliente inicia la conexión.                                            |
| 2    | `SYN + ACK`  | El servidor reconoce el SYN del cliente y sincroniza su propia secuencia. |
| 3    | `ACK`        | El cliente reconoce el SYN del servidor.                                  |
#### Funcionamiento usando TCP

El intercambio programado será:

1. El servidor crea un `ServerSocket` y queda escuchando.
2. El cliente crea un `Socket` e intenta conectarse a la IP y al puerto del servidor.
3. El servidor acepta la conexión mediante `accept()`.
4. El cliente envía un mensaje.
5. El servidor lo lee, lo procesa y responde.
6. El cliente lee la respuesta.
7. Ambos cierran los recursos.

Puntos a considerar:

- `accept()` bloquea la ejecución hasta que llega una conexión.
    
- `readLine()` espera hasta recibir un salto de línea o detectar el fin del flujo.
    
- Al cerrar el socket termina esa conexión, pero no implica que el proceso servidor deba apagarse.

En esta etapa el servidor atenderá un cliente a la vez. La atención simultánea mediante hilos corresponde a la etapa 2.

> [!Important]
> TCP no envía automáticamente objetos ni mensajes completos. Envía un flujo de bytes. En nuestro primer ejercicio utilizaremos mensajes de texto terminados en un salto de línea (`\n`), que el cliente y el servidor interpretarán como el final de cada mensaje.

# Fundamentos de Java 

| **Tema**                 | **Qué debo saber**                                 | **Cómo lo aplicare**                                |
| ------------------------ | -------------------------------------------------- | --------------------------------------------------- |
| Clases y objetos         | Crear clases, instanciar objetos y llamar métodos. | Separar el servidor y el cliente.                   |
| Método `main`            | Punto de entrada de una aplicación Java.           | Ejecutar cada programa.                             |
| Variables y tipos        | `String`, `int`, `boolean`.                        | Representar mensajes y puertos.                     |
| Parámetros y retorno     | Pasar argumentos y devolver resultados.            | Enviar datos entre métodos.                         |
| `try-catch`              | Capturar excepciones.                              | Controlar fallos de conexión.                       |
| `try-with-resources`     | Cerrar automáticamente recursos.                   | Liberar sockets y flujos.                           |
| Entrada/salida           | Lectores y escritores de datos.                    | Recibir y enviar mensajes.                          |
| Paquetes e importaciones | `package` e `import`.                              | Organizar las clases y usar las bibliotecas de red. |

# Clases de Java para sockets TCP

Principales clases para esta etapa.

| Clase               | Función                                                           |
| ------------------- | ----------------------------------------------------------------- |
| `ServerSocket`      | Abre un puerto y espera conexiones entrantes.                     |
| `Socket`            | Representa una conexión TCP establecida.                          |
| `InputStream`       | Permite leer bytes recibidos.                                     |
| `OutputStream`      | Permite escribir bytes para enviarlos.                            |
| `InputStreamReader` | Convierte bytes en caracteres.                                    |
| `BufferedReader`    | Lee texto eficientemente, por ejemplo con `readLine()`.           |
| `PrintWriter`       | Envía texto, por ejemplo con `println()`.                         |
| `IOException`       | Representa errores de entrada/salida, como problemas de conexión. |
Comprender qué objeto crea la conexión, cuál la acepta y cómo circulan los datos.

# Herramientas y conocimientos técnicos

### IntelliJ IDEA

Crear el proyecto Java, escribir las clases, ejecutarlas y consultar los errores. Utiliza el JDK configurado en el proyecto.

### JDK y Java

Verificar que Java está instalado y que puedes compilar y ejecutar programas desde la terminal.

### Terminal de Linux

Más adelante ejecutarás el sistema en Linux. Conviene familiarizarte con la terminal desde ahora, aunque puedes desarrollar inicialmente en Windows.


# Guía paso a paso: construir el cliente-servidor

## Comprobaciones iniciales

Abre una terminal y ejecuta:

```
java -version
javac -version
```

- `java` permite ejecutar aplicaciones Java.
- `javac` compila archivos `.java`.
- Ambos comandos deberían estar disponibles y corresponder a una instalación compatible del JDK.

Si trabajas en IntelliJ, comprueba también que el proyecto tenga un Project SDK configurado.

## 1. Crear el proyecto

En IntelliJ IDEA, seleccionar **New Proyect** y configurar lo siguiente antes de crear el proyecto:
- **Name:** ServidorTCP
- **Lenguage:** Java
- **Build systema:** Maven
- **JDK:** Java 21

> [!Note]
> Para el servidor se usaran las clases de red que Java ya incluye.

#### Paquete red

En el panel de proyectos de IntelliJ, abrir `src/main/java`.

1. Haz clic derecho sobre `java`.
2. Selecciona New → Package.
3. Escribe `red`.

> [!Note]
> Crear un proyecto Maven y conservar esa estructura. Aunque Maven no es indispensable para esta etapa, nos permite agregar las dependencias del proyecto más adelante.

La estructura inicial será:

```
SistemaEventosRed/
	`src/main/java/red/`
		`Servidor.java`
		`Cliente.java`
```

> [!Imprtant]
> Son dos programas separados. Primero se iniciara el servidor y después se ejecutara el cliente.

## 2. Programar el servidor TCP

#### Creación del archivo `Servidor.java`

- Hacer clic derecho sobre el paquete `red`
- Selecciona New → Java Class 
- Y escribe `Servidor`.

**Código implementado**
```Java
package red;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.net.ServerSocket;
import java.net.Socket;

public class Servidor {

    private static final int PUERTO = 5000;

    public static void main(String[] args) {

        System.out.println("Iniciando servidor TCP...");

        try (ServerSocket servidor = new ServerSocket(PUERTO)) {

            System.out.println(
                "Servidor escuchando en el puerto " + PUERTO
            );

            while (true) {

                Socket cliente = servidor.accept();

                System.out.println(
                    "Cliente conectado: "
                    + cliente.getRemoteSocketAddress()
                );

                try (Socket conexion = cliente;
                     BufferedReader entrada = new BufferedReader(
                         new InputStreamReader(
                             conexion.getInputStream()
                         )
                     );
                     PrintWriter salida = new PrintWriter(
                         conexion.getOutputStream(), true
                     )) {

                    String evento = entrada.readLine();

                    if (evento != null) {
                        System.out.println(
                            "Evento recibido: " + evento
                        );

                        salida.println(
                            "OK: evento recibido por el servidor"
                        );
                    }

                } catch (IOException e) {
                    System.err.println(
                        "Error en la conexión: " + e.getMessage()
                    );
                }

            }

        } catch (IOException e) {
            System.err.println(
                "No se pudo iniciar el servidor: "
                + e.getMessage()
            );
        }
    }
}
```

| **Instrucción**          | **Explicación**                                                    |
| ------------------------ | ------------------------------------------------------------------ |
| `new ServerSocket(5000)` | Abre el puerto TCP 5000 para escuchar conexiones.                  |
| `while (true)`           | Mantiene el servidor disponible para aceptar conexiones sucesivas. |
| `accept()`               | Espera a que un cliente se conecte y devuelve un `Socket`.         |
| `getInputStream()`       | Obtiene el flujo de entrada de la conexión.                        |
| `getOutputStream()`      | Obtiene el flujo de salida de la conexión.                         |
| `readLine()`             | Lee el evento enviado por el cliente.                              |
| `println()`              | Envía la respuesta y agrega un salto de línea.                     |
| `try-with-resources`     | Cierra automáticamente los recursos al salir del bloque.           |

El servidor no se limita a recibir una conexión: el ciclo `while` le permite aceptar nuevos clientes después de terminar la conexión anterior.

Limitación intencional: este servidor procesa un cliente a la vez. Mientras espera el mensaje de un cliente, no puede atender otro. En la etapa 2 se modificara este diseño para que cada conexión se atienda concurrentemente.

## 3. Programar el cliente TCP

Crear `Cliente.java` en el mismo paquete `red`

**Código implementado**
```Java
package red;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.net.Socket;

public class Cliente {

    private static final String HOST = "127.0.0.1";
    private static final int PUERTO = 5000;

    public static void main(String[] args) {

        System.out.println("Conectando con el servidor...");

        try (Socket socket = new Socket(HOST, PUERTO);
             BufferedReader entrada = new BufferedReader(
                 new InputStreamReader(
                     socket.getInputStream()
                 )
             );
             PrintWriter salida = new PrintWriter(
                 socket.getOutputStream(), true
             )) {

            System.out.println("Conexión establecida.");

            String evento =
                "IP=192.168.1.10;PROTOCOLO=TCP;"
                + "PUERTO=443;TIPO=CONEXION";

            salida.println(evento);

            System.out.println("Evento enviado: " + evento);

            String respuesta = entrada.readLine();

            System.out.println(
                "Respuesta del servidor: " + respuesta
            );

        } catch (IOException e) {
            System.err.println(
                "No se pudo comunicar con el servidor: "
                + e.getMessage()
            );
        }
    }
}
```

1. `new Socket(HOST, PUERTO)` intenta establecer la conexión TCP.
2. `salida.println(evento)` envía el evento simulado.
3. `entrada.readLine()` espera la respuesta del servidor.
4. Al terminar el bloque `try`, se cierra la conexión.

En este primer ejercicio, `127.0.0.1` significa que el cliente y el servidor se ejecutan en el mismo equipo. Cuando se trabaje con equipos distintos, se cambiarán esta dirección por la IP del equipo donde se ejecute el servidor.

El evento se transmite como texto delimitado por campos. Más adelante podremos sustituir este formato por JSON.

## 4. Ejecutar los programas

1. Ejecuta `Servidor.java`.
    En IntelliJ, abre la clase y pulsa el botón de ejecución. Debes ver algo parecido a:
	-Iniciando servidor TCP...
	-Servidor escuchando en el puerto 5000
	
	Deja el proceso ejecutándose. El servidor está esperando una conexión.

2. Ejecuta `Cliente.java`.
    
    Debe conectarse al servidor, enviar el evento y recibir la confirmación.

3. Revisa la consola del servidor.
    
    Debes encontrar la conexión y el evento recibido.

4. Ejecuta el cliente otra vez.
    
    El servidor debe aceptar una nueva conexión y procesar el nuevo envío sin necesidad de reiniciarse.

## Verificar el resultado esperado 

Si todo funciona correctamente, las salidas serán similares a las siguientes.

Consola del servidor
```Bash
Iniciando servidor TCP... Servidor escuchando en el puerto 5000 Cliente conectado: /127.0.0.1:xxxxx Evento recibido: IP=192.168.1.10;PROTOCOLO=TCP;PUERTO=443;TIPO=CONEXION
```

Consola del cliente
```Bash
Conectando con el servidor... Conexión establecida. Evento enviado: IP=192.168.1.10;PROTOCOLO=TCP;PUERTO=443;TIPO=CONEXION Respuesta del servidor: OK: evento recibido por el servidor
```

El valor xxxxx representa un puerto remoto temporal que el sistema operativo asigna al cliente.

Este resultado demuestra que las aplicaciones intercambian datos mediante TCP y que el servidor puede recibir un evento y responder al cliente.

Todavía no significa que el evento esté almacenado en una base de datos: por ahora únicamente se muestra en la consola.

# Practicas

Para comprobar esta estapa

**Listas de Ejercicios**

- [ ] Cambiar el contenido del evento
	Modifica la IP, el puerto y el tipo de evento. Comprueba que el servidor recibe exactamente lo que envía el cliente.

- [ ] Enviar tres eventos
	Haz que el cliente envíe tres líneas diferentes y que el servidor las lea en un ciclo hasta que termine el flujo. Recuerda que el protocolo debe definir cómo termina el envío.

- [ ] Responder con información del evento
	Modifica la respuesta del servidor para incluir el tipo de evento que recibió.

- [ ] Probar una desconexión
	Detén el servidor e intenta ejecutar el cliente. Identifica el error y explica por qué ocurre.

- [ ] Conectar desde otro equipo
	Cuando el ejercicio local funcione, prueba el servidor en un equipo Linux y el cliente en otro equipo de la misma red, utilizando la IP real del servidor y verificando el firewall.

> [!Note]
> Para el segundo ejercicio tendrás que aprender a leer múltiples líneas. Por ejemplo, puedes usar un ciclo que invoque `readLine()` repetidamente hasta que el resultado sea `null`. Así podrás enviar varios eventos por una misma conexión antes de cerrarla.

# Evaluación de conocimientos

- Explico la diferencia entre IP, puerto, socket y protocolo TCP.
	
- Comprendo la función de ServerSocket y Socket.
	
- Puedo crear un cliente que se conecte a un servidor.
	
- Puedo enviar un mensaje y leer una respuesta.
	
- Comprendo por qué se utilizan BufferedReader y PrintWriter.
	
- Utilizo try-with-resources para cerrar conexiones y flujos.
	
- Puedo explicar qué ocurre cuando el servidor no está disponible.
	
- Consigo ejecutar varias conexiones sucesivas sin reiniciar el servidor.

# Ruta del Proyecto 

**Etapa 1 — Comunicación TCP**
	Objetivo actual
	Cliente y servidor se conectan, intercambian un evento y reciben una respuesta.

Etapa 2 — Concurrencia
	Incorporar `Runnable` y `ExecutorService` para atender múltiples conexiones sin que una bloquee a las demás.

Etapa 3 — Persistencia
	Guardar los eventos recibidos en PostgreSQL mediante JDBC.

Etapa 4 — API REST
	Consultar los eventos y devolverlos en JSON para que la interfaz de Python de tu compañera pueda mostrarlos.