
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

#### Crear `Cliente.java`

Se creó el archivo `Cliente.java` en el mismo paquete `red`

**Código implementado**
```Java
package red;  
  
import java.io.BufferedReader;  
import java.io.IOException;  
import java.io.InputStreamReader;  
import java.io.PrintWriter;  
import java.net.Socket;  
  
public class Cliente {  
  
    private static final String HOST = "172.29.43.71";  
    private static final int PUERTO = 5000;  
  
    public static void main(String[] args) {  
  
        System.out.println("Conectando con el servidor...");  
  
        try (  
                Socket socket = new Socket(HOST, PUERTO);  
  
                BufferedReader entrada = new BufferedReader(  
                        new InputStreamReader(socket.getInputStream())  
                );  
  
                PrintWriter salida = new PrintWriter(  
                        socket.getOutputStream(), true  
                )  
        ) {  
  
            // Obtener los datos reales de la conexión  
            String ipCliente =  
                    socket.getLocalAddress().getHostAddress();  
  
            int puertoCliente = socket.getLocalPort();  
  
            String ipServidor =  
                    socket.getInetAddress().getHostAddress();  
  
            int puertoServidor = socket.getPort();  
  
            System.out.println("Conexión establecida.");  
            System.out.println("IP del cliente: " + ipCliente);  
            System.out.println("Puerto local del cliente: " + puertoCliente);  
            System.out.println("IP del servidor: " + ipServidor);  
            System.out.println("Puerto del servidor: " + puertoServidor);  
  
            // Construir el evento con los datos reales del cliente  
            String evento =  
                    "IP=" + ipCliente  
                            + ";PROTOCOLO=TCP"  
                            + ";PUERTO=" + puertoCliente  
                            + ";TIPO=CONEXION";  
  
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

El cliente TCP es el componente encargado de iniciar la comunicación con el servidor, enviar un evento de red simulado y recibir una respuesta que confirme su procesamiento. Para esta primera etapa del proyecto, su propósito es comprobar el establecimiento de una conexión TCP y el intercambio de mensajes entre dos procesos Java.

###### Configuración de la conexión

```Java
private static final String HOST = "172.29.43.71";
private static final int PUERTO = 5000;
```

Se definen los parámetros necesarios para localizar el servidor. La variable `HOST` contiene la dirección IP utilizada para alcanzar el servidor ejecutado en Ubuntu mediante WSL2, mientras que `PUERTO` especifica el puerto `5000`, donde el servidor espera las conexiones entrantes.

> [!warning]
> La dirección utilizada corresponde a la configuración de red de las pruebas realizadas. Debido a que la dirección virtual de WSL2 puede cambiar, deberá actualizarse si deja de ser accesible.

###### Establecimiento de la conexión TCP

```Java
Socket socket = new Socket(HOST, PUERTO);
```

La clase `Socket` permite establecer una conexión TCP con el servidor. Al ejecutarse esta instrucción, Java intenta conectarse a la dirección y al puerto especificados. Si la conexión se establece correctamente, el programa puede intercambiar información con el servidor a través del socket.

En las pruebas realizadas, el cliente se ejecutó tanto desde Ubuntu en WSL2 como desde Windows mediante IntelliJ IDEA. Esto permitió comprobar la comunicación entre procesos ejecutados en distintos entornos operativos.

###### Preparación de los canales de comunicación 

```Java
BufferedReader entrada = new BufferedReader(
        new InputStreamReader(socket.getInputStream())
);

PrintWriter salida = new PrintWriter(
        socket.getOutputStream(), true
);
```

Se crean dos objetos para intercambiar mensajes mediante la conexión TCP. `PrintWriter` permite enviar texto al servidor, mientras que `BufferedReader` permite recibir su respuesta. El parámetro `true` de `PrintWriter` habilita el vaciado automático del flujo al utilizar `println()`, lo que permite enviar el mensaje sin tener que llamar explícitamente a `flush()`.

###### Obtención de la IP y los puertos de la conexión

```Java
String ipCliente =
        socket.getLocalAddress().getHostAddress();

int puertoCliente = socket.getLocalPort();

String ipServidor =
        socket.getInetAddress().getHostAddress();

int puertoServidor = socket.getPort();
```

Este apartado corresponde a la verificación de la conexión TCP. Se obtienen los valores de la dirección y del puerto, directamente del objeto `Socket`.

- `getLocalAddress()` obtiene la dirección IP local utilizada por el cliente en esa conexión.
- `getLocalPort()` obtiene el puerto local asignado automáticamente al cliente.
- `getInetAddress()` obtiene la dirección IP del servidor al que se conectó.
- `getPort()` obtiene el puerto de destino del servidor, que en esta prueba es el `5000`.

Estos datos permiten identificar los extremos de la conexión desde la perspectiva del cliente. Es importante señalar que la IP local obtenida no necesariamente corresponde a la dirección física de la computadora, ya que pueden intervenir interfaces virtuales y mecanismos de traducción de direcciones de red (NAT).

###### Construcción y envío del evento

```Java
String evento =
        "IP=" + ipCliente
        + ";PROTOCOLO=TCP"
        + ";PUERTO=" + puertoCliente
        + ";TIPO=CONEXION";

salida.println(evento);
```

Se construye un mensaje de texto que representa un evento de red simulado. El mensaje incluye la dirección IP local utilizada por el cliente, el protocolo de transporte, el puerto de origen y el tipo de evento.

El método `println()` transmite el mensaje al servidor y agrega un salto de línea. Esto es importante porque el servidor utiliza `readLine()` para determinar dónde termina el mensaje recibido.

> [!Note]
> En esta etapa, el evento es una representación de prueba creada por el programa; no constituye una captura automática del tráfico real de la red.

###### Recepción de la respuesta del servidor

```Java
String respuesta = entrada.readLine();

System.out.println(
        "Respuesta del servidor: " + respuesta
);
```

Después de enviar el evento, el cliente espera una respuesta del servidor. El método `readLine()` bloquea la ejecución hasta recibir una línea de texto o detectar el cierre de la conexión. En las pruebas realizadas, el servidor respondió con el mensaje `OK: evento recibido por el servidor`, confirmando que recibió el evento enviado.

###### Manejo de errores y cierre de recursos 

```Java
} catch (IOException e) {
    System.err.println(
            "No se pudo comunicar con el servidor: "
                    + e.getMessage()
    );
}
```

El bloque `catch` permite informar errores relacionados con la comunicación, como una conexión rechazada, un servidor inaccesible o un problema durante la lectura o escritura.

Además, el uso de `try-with-resources` permite cerrar automáticamente el socket y los flujos de entrada y salida cuando termina el bloque, incluso si ocurre una excepción. Esto evita mantener recursos de comunicación abiertos innecesariamente.

#### Crear `Cliente.py`.

En VS Code, se creó la carpeta `ClienteTCP`, y dentro se creó el archivo `cliente.py`.

**Código implementado**
```Python
import socket

# Dirección y puerto del servidor Java en Ubuntu/WSL2
HOST = "172.29.43.71"
PUERTO = 5000


def main():
    print("Conectando con el servidor...")

    try:
        # Establecer la conexión TCP
        with socket.create_connection(
            (HOST, PUERTO), timeout=5
        ) as cliente:

            # Obtener los datos reales de la conexión
            ip_cliente, puerto_cliente = cliente.getsockname()
            ip_servidor, puerto_servidor = cliente.getpeername()

            print("Conexión establecida.")
            print(f"IP del cliente: {ip_cliente}")
            print(f"Puerto local del cliente: {puerto_cliente}")
            print(f"IP del servidor: {ip_servidor}")
            print(f"Puerto del servidor: {puerto_servidor}")

            # Construir el evento de red
            evento = (
                f"IP={ip_cliente};"
                f"PROTOCOLO=TCP;"
                f"PUERTO={puerto_cliente};"
                f"TIPO=CONEXION"
            )

            # Enviar el evento terminado en salto de línea
            cliente.sendall((evento + "\n").encode("utf-8"))

            print(f"Evento enviado: {evento}")

            # Recibir la respuesta del servidor
            with cliente.makefile(
                "r", encoding="utf-8"
            ) as entrada:
                respuesta = entrada.readline()

            if respuesta:
                print(f"Respuesta del servidor: {respuesta.strip()}")
            else:
                print("El servidor cerró la conexión sin responder.")

    except (OSError, TimeoutError) as error:
        print(f"No se pudo comunicar con el servidor: {error}")


if __name__ == "__main__":
    main()

```

El código utiliza el módulo `socket` de Python, que forma parte de su biblioteca estándar. No se requirió instalar paquetes adicionales.

| **Instrucción**              | **Función**                                                         |
| ---------------------------- | ------------------------------------------------------------------- |
| `socket.create_connection()` | Establece la conexión TCP con el servidor Java.                     |
| `cliente.getsockname()`      | Obtiene la IP local y el puerto de origen del cliente.              |
| `cliente.getpeername()`      | Obtiene la IP y el puerto del servidor remoto.                      |
| `cliente.sendall()`          | Envía el mensaje completo por el socket.                            |
| `cliente.makefile()`         | Permite leer la respuesta del servidor como texto, línea por línea. |
| `encode("utf-8")`            | Convierte el mensaje de texto en bytes para transmitirlo.           |

El evento termina con `"\n"`. Esto es indispensable porque el servidor Java utiliza `readLine()` para detectar el final del mensaje. El servidor responder con una línea terminada en salto de línea para que Python pueda completar su lectura.

## Ejecución y verificación de los programas

En esta sección se describe el procedimiento para ejecutar el servidor y el cliente TCP desarrollados en Java, así como las pruebas realizadas para comprobar la comunicación entre Ubuntu mediante WSL2 y Windows 11.

El proyecto utiliza Maven para compilar las clases Java. Los programas se ejecutan desde el directorio del proyecto `ServidorTCP`, y las clases compiladas se encuentran en `target/classes`.

###### Verificación de la dirección IP y del puerto

Debido a que el servidor se ejecuta dentro de Ubuntu mediante WSL2, es necesario identificar la dirección IP utilizada por ese entorno para establecer la comunicación desde Windows.

Desde Windows PowerShell se ejecuta:
```powershell
wsl hostname -I
```

En las pruebas realizadas, el comando devolvió la dirección `172.29.43.71`, correspondiente a la dirección IP del entorno Ubuntu en WSL2.

A continuación, se verifica si el servidor es accesible a través del puerto TCP `5000`:
```powershell
Test-NetConnection 172.29.43.71 -Port 5000
```

El resultado relevante fue:
```powershell
RemoteAddress    : 172.29.43.71
RemotePort       : 5000
InterfaceAlias   : vEthernet (WSL (Hyper-V firewall))
SourceAddress    : 172.29.32.1
TcpTestSucceeded : True
```

El valor `TcpTestSucceeded : True` indica que fue posible establecer una conexión TCP con la dirección y el puerto especificados. La dirección `172.29.32.1` corresponde a la dirección de origen que Windows utilizó en esta prueba.

###### Ejecutar el servidor TCP

Primero, se inicia Ubuntu desde Windows PowerShell:
```powershell
wsl
```

Después, se accede al directorio del proyecto:
```bash
cd /mnt/c/Users/rojor/Documents/PROGRAMACION/Java/ServidorTCP
```

Antes de ejecutar el servidor, es necesario que el proyecto se encuentre compilado. Si se modificó el código fuente, puede compilarse con Maven:
```bash
mvn clean compile
```

Una vez compilado, se inicia el servidor con:
```bash
java -cp target/classes red.Servidor
```

Si el programa se ejecuta correctamente, muestra:
```text
Iniciando servidor TCP...
Servidor escuchando en el puerto 5000
```

En este momento, el servidor queda a la espera de conexiones entrantes. La terminal debe permanecer abierta mientras se realizan las pruebas con los clientes.

###### Ejecutar el cliente desde Ubuntu

Se abre otra terminal de Ubuntu mediante WSL2 y se accede al directorio del proyecto:
```bash
cd /mnt/c/Users/rojor/Documents/PROGRAMACION/Java/ServidorTCP
```

A continuación, se ejecuta el cliente:
```bash
java -cp target/classes red.Cliente
```

Durante las pruebas, la salida fue similar a la siguiente:
```Shell
Conectando con el servidor...
Conexión establecida.
IP del cliente: 172.29.43.71
Puerto local del cliente: 54986
IP del servidor: 172.29.43.71
Puerto del servidor: 5000
Evento enviado: IP=172.29.43.71;PROTOCOLO=TCP;PUERTO=54986;TIPO=CONEXION
Respuesta del servidor: OK: evento recibido por el servidor
```

El resultado confirma que el cliente pudo conectarse al servidor, obtener los datos de su conexión, enviar el evento simulado y recibir una respuesta.

> [!Note]
> En este caso, la IP local del cliente y la IP del servidor aparecen iguales porque el cliente se ejecutó dentro del mismo entorno Ubuntu y utilizó la dirección de WSL2 para conectarse. Esto no significa que los dos procesos sean el mismo: cada uno utiliza su propio socket y puerto dentro de la comunicación.

###### Ejecutar el cliente desde Windows mediante IntelliJ IDEA

Para verificar la comunicación entre distintos entornos operativos, se ejecuta el servidor en Ubuntu y el cliente desde Windows mediante IntelliJ IDEA.

El servidor debe permanecer activo en su terminal. En IntelliJ IDEA se ejecuta la clase `red.Cliente`, utilizando la configuración de ejecución del proyecto.

La salida obtenida fue:

```powershell
Conectando con el servidor...
Conexión establecida.
IP del cliente: 172.29.32.1
Puerto local del cliente: 61774
IP del servidor: 172.29.43.71
Puerto del servidor: 5000
Evento enviado: IP=172.29.32.1;PROTOCOLO=TCP;PUERTO=61774;TIPO=CONEXION
Respuesta del servidor: OK: evento recibido por el servidor

Process finished with exit code 0
```

En esta prueba, el cliente se ejecutó en Windows y utilizó la dirección `172.29.32.1` como dirección local de origen, mientras que el servidor se encontraba en Ubuntu, accesible mediante `172.29.43.71:5000`.

El mensaje `Process finished with exit code 0` indica que la ejecución del cliente terminó correctamente, sin que se reportara un error de ejecución.

###### Ejecutar el cliente desde Windows mediante VS Code (Python)

Se abrió una terminal de Windows en VS Code, en la carpeta donde se guardo `cliente.py` y se ejecuto:

```powershell
py cliente.py
```

###### Verificación de los mensajes recibidos por el servidor

Mientras se ejecutan los clientes, la terminal del servidor muestra las conexiones entrantes y los eventos recibidos. Por ejemplo:

```Shell
Servidor escuchando en el puerto 5000
Cliente conectado: /172.29.32.1:61774
Evento recibido: IP=172.29.32.1;PROTOCOLO=TCP;PUERTO=61774;TIPO=CONEXION
```

La primera línea confirma que el servidor continúa escuchando en el puerto configurado. La segunda muestra la dirección y el puerto de origen observados por el servidor para esa conexión. La tercera presenta el mensaje de evento enviado por el cliente.

La IP y el puerto de origen que muestra el servidor permiten identificar el extremo de la conexión TCP que observa la aplicación. Por su parte, los campos `IP` y `PUERTO` incluidos en el evento son datos transmitidos en el mensaje. En esta prueba coinciden con los valores obtenidos por el cliente, pero ambos conceptos deben distinguirse en el diseño del sistema.


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