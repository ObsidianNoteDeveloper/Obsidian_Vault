










---
---

# Comunicación cliente-servidor mediante sockets TCP sobre Ethernet

Implementar un sistema de comunicación cliente-servidor mediante sockets en lenguaje C, utilizando el protocolo TCP sobre una red Ethernet para permitir el intercambio de información entre dos computadoras físicas con diferentes sistemas operativos.

- Comprender el funcionamiento de los sockets y su utilización para establecer comunicaciones entre procesos.
    
- Identificar las diferencias entre los sockets UNIX (`AF_UNIX`) y los sockets de Internet (`AF_INET`).
    
- Configurar una red local mediante direcciones IPv4 estáticas.
    
- Establecer conectividad entre dos computadoras mediante un cable Ethernet.
    
- Implementar un servidor TCP capaz de recibir información y enviar una respuesta a un cliente.
    
- Implementar un cliente TCP que establezca una conexión remota con el servidor.
    
- Analizar las funciones principales de la API de sockets de Linux y su relación con el modelo cliente-servidor.

---

### Concepto de socket

Un socket es un mecanismo de comunicación que permite el intercambio de información entre dos procesos. Funciona como un punto de comunicación mediante el cual una aplicación puede enviar y recibir datos utilizando los servicios proporcionados por el sistema operativo.

Los sockets pueden utilizarse para establecer comunicaciones entre procesos de una misma computadora o entre procesos que se encuentran en diferentes equipos conectados mediante una red.

### Familias de sockets

Para esta práctica se consideran dos familias principales:

**AF_UNIX:** permite la comunicación entre procesos que se ejecutan dentro de un mismo sistema operativo. Utiliza direcciones asociadas a archivos especiales del sistema de archivos y no requiere direcciones IP ni puertos de red.

**AF_INET:** permite establecer comunicaciones mediante el protocolo IPv4. Utiliza direcciones IP y números de puerto para identificar los extremos de una comunicación.

### Protocolo TCP

TCP (Transmission Control Protocol) es un protocolo de transporte orientado a conexión. Antes de intercambiar información, establece una conexión lógica entre el cliente y el servidor mediante el procedimiento conocido como **Three-Way Handshake**. 

Este procedimiento comprende tres etapas:

1. SYN: el cliente solicita establecer una conexión.
2. SYN-ACK: el servidor reconoce la solicitud y responde.
3. ACK: el cliente confirma la respuesta del servidor.

Una vez establecida la conexión, ambos extremos pueden intercambiar información mediante un flujo de bytes.

Entre sus principales características se encuentran la entrega confiable de datos, la detección de errores, el control de flujo y la retransmisión de segmentos cuando es necesario.

### Direccionamiento IPv4

IPv4 es un protocolo de la capa de red que utiliza direcciones de 32 bits para identificar interfaces dentro de una red.

Se asignaron direcciones IP estáticas a las dos computadoras, utilizando la misma subred.

La máscara de subred `255.255.255.0` indica que los primeros 24 bits identifican la red, mientras que los últimos 8 bits identifican los dispositivos.

### Comunicación cliente-servidor

El modelo cliente-servidor establece una relación en la que un proceso servidor permanece disponible para recibir solicitudes, mientras que un proceso cliente inicia la comunicación.

_El servidor crea un socket_, lo asocia con una dirección y un puerto, comienza a escuchar solicitudes y acepta las conexiones entrantes.

Por su parte, _el cliente crea un socket_, especifica la dirección IP y el puerto del servidor e inicia la conexión.

Una vez establecida la comunicación, ambos procesos pueden intercambiar información.

## Topología de red

La práctica utiliza una conexión Ethernet entre dos computadoras físicas.

| Dispositivo   | Sistema operativo        | Función  | Dirección IPv4 |
| ------------- | ------------------------ | -------- | -------------- |
| ASUS Vivobook | Windows 11 + Ubuntu WSL2 | Servidor | 192.168.10.1   |
| MacBook Pro   | macOS                    | Cliente  | 192.168.10.2   |

Parámetros de configuración:

|Parámetro|Valor|
|---|---|
|Tipo de conexión|Ethernet|
|Protocolo de red|IPv4|
|Máscara de subred|255.255.255.0|
|Protocolo de transporte|TCP|
|Puerto de comunicación|5000|
|Familia de sockets|AF_INET|
|Tipo de socket|SOCK_STREAM|

> [!Note]
> La dirección IP `192.168.10.1` corresponde a la interfaz Ethernet de Windows. Ubuntu WSL2 utiliza una interfaz de red virtual independiente, por lo que requiere un mecanismo de reenvío de puertos para recibir conexiones provenientes de la red física.

## Desarrollo del ejercicio

### Preparación del entorno de programación

Se utilizó Ubuntu mediante WSL2 para desarrollar y ejecutar el programa servidor en lenguaje C.

Se creó el directorio de trabajo:

```bash
mkdir -p ~/Documentos/Programacion/SisDistribuidos/sockets
```

Posteriormente, se ingresó al directorio:

```bash
cd ~/Documentos/Programacion/SisDistribuidos/sockets
```

Se utilizó GCC para compilar los programas en Ubuntu.

### Configuración de la red Ethernet

En la computadora ASUS se configuró manualmente la dirección IPv4 del adaptador Ethernet 2, correspondiente al controlador Realtek USB GbE Family Controller.

Se establecieron los siguientes parámetros:

- Dirección IPv4: `192.168.10.1`
- Máscara de subred: `255.255.255.0`
- Puerta de enlace: no especificada.

En la MacBook Pro se configuró la interfaz Ethernet con los siguientes parámetros:

- Dirección IPv4: `192.168.10.2`
- Máscara de subred: `255.255.255.0`
- Router: no especificado.

De esta manera, ambas computadoras quedaron dentro de la misma red IPv4.

### Verificación de conectividad

Para comprobar la comunicación entre los equipos se utilizó el comando `ping` desde la terminal de macOS:

```bash
ping -c 4 192.168.10.1
```

Se obtuvo el siguiente resultado:

```bash
4 packets transmitted, 4 packets received,
0.0% packet loss

round-trip min/avg/max/stddev =
2.515/2.914/3.409/0.326 ms
```

El resultado demuestra que la MacBook Pro pudo enviar cuatro solicitudes ICMP a la computadora ASUS y recibir correctamente las cuatro respuestas.

El tiempo promedio de ida y vuelta fue de aproximadamente 2.914 milisegundos, sin pérdida de paquetes.

Por lo tanto, se comprobó la conectividad IP entre ambas computadoras mediante Ethernet.

### Implementación del servidor TCP

El servidor se desarrolló utilizando la familia de direcciones `AF_INET` y el tipo de socket `SOCK_STREAM`.

El programa utiliza el puerto TCP 5000 y permanece escuchando conexiones entrantes.

Cuando un cliente establece una conexión, el servidor recibe un carácter, incrementa su valor en una unidad y devuelve el resultado al cliente.

### Implementación del cliente TCP

El cliente se desarrolló para ejecutarse en macOS.

Su función consiste en crear un socket TCP, conectarse a la dirección IP del servidor y enviar un carácter.

Posteriormente, espera la respuesta del servidor, la recibe y muestra el resultado en pantalla.

> [!Note]
> Para facilitar su utilización, la dirección IP del servidor se proporciona como argumento al ejecutar el programa.

## Configuración de red entre Windows y WSL2

Debido a que el servidor se ejecuta dentro de Ubuntu WSL2, es necesario considerar que su dirección IP pertenece a una red virtual distinta de la interfaz Ethernet de Windows.

Para permitir el acceso desde la MacBook se utiliza `netsh interface portproxy`, que permite redirigir las conexiones TCP recibidas por Windows hacia el servidor de Ubuntu.

Primero se obtiene la dirección IP interna de WSL2:

```bash
hostname -I
```

Después, desde PowerShell con privilegios de administrador, se configura el reenvío del puerto 5000:

```powershell
netsh interface portproxy add v4tov4 listenaddress=192.168.10.1 listenport=5000 connectaddress=IP_DE_WSL connectport=5000
```

La dirección `IP_DE_WSL` debe sustituirse por la dirección IPv4 obtenida mediante `hostname -I`.

```powershell
netsh interface portproxy add v4tov4 listenaddress=192.168.10.1 listenport=5000 connectaddress=172.29.43.71 connectport=5000
```

Se configura una regla de entrada en el Firewall de Windows para permitir las conexiones TCP provenientes de la MacBook hacia el puerto 5000:

```powershell
New-NetFirewallRule -DisplayName "Sockets TCP 5000" -Direction Inbound -Protocol TCP -LocalPort 5000 -LocalAddress 192.168.10.1 -RemoteAddress 192.168.10.2 -Action Allow -Profile Any
```

Para consultar la configuración del reenvío se utiliza:

```powershell
netsh interface portproxy show all
```

## Resultados esperados de la comunicación TCP

Una vez configurado el reenvío de puertos, el servidor se ejecuta en Ubuntu WSL2 y el cliente en la MacBook Pro.

El cliente envía el carácter `A` al servidor.

El servidor incrementa el valor ASCII del carácter recibido:

A = 65
A + 1 = 66

El valor 66 corresponde al carácter `B`.

Finalmente, el servidor devuelve el carácter `B` al cliente.

La salida esperada del cliente es:

```bash
Conectando con 192.168.10.1:5000...
Conexion establecida
Caracter enviado: A
Respuesta del servidor: B
```

La salida esperada del servidor es:

```bash
Socket del servidor creado: 3
Servidor asociado al puerto 5000
Servidor esperando conexiones...

Cliente conectado: 192.168.10.2
Caracter recibido: A
Respuesta enviada: B
Conexion finalizada
```

Estos resultados representan el comportamiento esperado de la aplicación; deben registrarse como resultados experimentales únicamente después de ejecutar y verificar la comunicación TCP.

## Código del servidor — `servidor01.c`

Este programa se ejecuta en Ubuntu WSL2 dentro de tu ASUS Vivobook.

```C
#include <sys/types.h>
#include <sys/socket.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>

#define PORT 5000

int main() {

    int server_sockfd, client_sockfd;
    int opt = 1;

    struct sockaddr_in server_address;
    struct sockaddr_in client_address;

    socklen_t client_len;

    char ch;
    char client_ip[INET_ADDRSTRLEN];

    // 1. Crear el socket del servidor
    server_sockfd = socket(AF_INET, SOCK_STREAM, 0);

    if (server_sockfd == -1) {
        perror("Error al crear el socket");
        exit(EXIT_FAILURE);
    }

    printf("Socket del servidor creado: %d\n",
           server_sockfd);

    // 2. Permitir reutilizar la direccion del puerto
    if (setsockopt(server_sockfd, SOL_SOCKET, SO_REUSEADDR,
                   &opt, sizeof(opt)) == -1) {

        perror("Error en setsockopt");
        close(server_sockfd);
        exit(EXIT_FAILURE);
    }

    // 3. Inicializar la estructura de direccion
    memset(&server_address, 0, sizeof(server_address));

    server_address.sin_family = AF_INET;
    server_address.sin_port = htons(PORT);

    // Escuchar en todas las interfaces IPv4
    server_address.sin_addr.s_addr = INADDR_ANY;

    // 4. Asociar el socket con la direccion y puerto
    if (bind(server_sockfd,
             (struct sockaddr *)&server_address,
             sizeof(server_address)) == -1) {

        perror("Error en bind");
        close(server_sockfd);
        exit(EXIT_FAILURE);
    }

    printf("Servidor asociado al puerto %d\n", PORT);

    // 5. Preparar el servidor para recibir conexiones
    if (listen(server_sockfd, 5) == -1) {

        perror("Error en listen");
        close(server_sockfd);
        exit(EXIT_FAILURE);
    }

    printf("Servidor esperando conexiones...\n");

    // 6. Ciclo permanente para atender clientes
    while (1) {

        client_len = sizeof(client_address);

        // Aceptar una conexion entrante
        client_sockfd = accept(server_sockfd,
                               (struct sockaddr *)&client_address,
                               &client_len);

        if (client_sockfd == -1) {
            perror("Error en accept");
            continue;
        }

        // Obtener la direccion IP del cliente
        inet_ntop(AF_INET,
                  &client_address.sin_addr,
                  client_ip,
                  sizeof(client_ip));

        printf("\nCliente conectado: %s\n", client_ip);

        // 7. Recibir un caracter del cliente
        if (read(client_sockfd, &ch, 1) == 1) {

            printf("Caracter recibido: %c\n", ch);

            // Incrementar el valor del caracter
            ch++;

            // 8. Enviar la respuesta al cliente
            if (write(client_sockfd, &ch, 1) == 1) {

                printf("Respuesta enviada: %c\n", ch);

            } else {

                perror("Error al enviar respuesta");
            }

        } else {

            printf("No se recibieron datos del cliente\n");
        }

        // 9. Cerrar la conexion con el cliente
        close(client_sockfd);

        printf("Conexion finalizada\n");
    }

    // Cerrar el socket principal
    close(server_sockfd);

    return 0;
}

```

Funcionamiento del servidor: después de crear y configurar el socket, el servidor permanece dentro de un ciclo infinito esperando conexiones. Cuando acepta un cliente, recibe un carácter, incrementa su valor y devuelve el resultado. Posteriormente cierra la conexión y queda disponible para atender otro cliente.

#### Declaraciones 

```C
    int server_sockfd, client_sockfd;
    struct sockaddr_in server_address;
    struct sockaddr_in client_address;
    socklen_t client_len;

    char ch;
    char client_ip[INET_ADDRSTRLEN];
```

Estas declaraciones corresponden a la definición de variables y estructuras necesarias para establecer una comunicación mediante sockets TCP utilizando IPv4 (`AF_INET`).

En el programa `servidor01.c`, estas variables permiten almacenar los descriptores de los sockets, las direcciones IP de los equipos involucrados y los datos que se intercambian entre el servidor y el cliente.



## Código del cliente — `cliente01.c`

Este programa se ejecuta en la MacBook Pro mediante la terminal de macOS.

```C

#include <sys/types.h>
#include <sys/socket.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>

#define PORT 5000

int main(int argc, char *argv[]) {

    int client_sockfd;

    struct sockaddr_in server_address;

    char ch = 'A';

    // 1. Verificar que se proporcione la IP del servidor
    if (argc != 2) {

        printf("Uso: %s <IP_SERVIDOR>\n", argv[0]);

        return EXIT_FAILURE;
    }

    // 2. Crear el socket del cliente
    client_sockfd = socket(AF_INET, SOCK_STREAM, 0);

    if (client_sockfd == -1) {

        perror("Error al crear el socket");

        exit(EXIT_FAILURE);
    }

    printf("Socket del cliente creado\n");

    // 3. Inicializar la estructura de direccion
    memset(&server_address, 0, sizeof(server_address));

    server_address.sin_family = AF_INET;
    server_address.sin_port = htons(PORT);

    // Convertir la IP del servidor a formato binario
    if (inet_pton(AF_INET, argv[1],
                  &server_address.sin_addr) != 1) {

        printf("Direccion IP invalida\n");

        close(client_sockfd);

        return EXIT_FAILURE;
    }

    // 4. Establecer conexion con el servidor
    printf("Conectando con %s:%d...\n", argv[1], PORT);

    if (connect(client_sockfd,
                (struct sockaddr *)&server_address,
                sizeof(server_address)) == -1) {

        perror("Error en connect");

        close(client_sockfd);

        exit(EXIT_FAILURE);
    }

    printf("Conexion establecida\n");

    // 5. Enviar un caracter al servidor
    printf("Caracter enviado: %c\n", ch);

    if (write(client_sockfd, &ch, 1) != 1) {

        perror("Error al enviar informacion");

        close(client_sockfd);

        return EXIT_FAILURE;
    }

    // 6. Recibir la respuesta del servidor
    if (read(client_sockfd, &ch, 1) == 1) {

        printf("Respuesta del servidor: %c\n", ch);

    } else {

        printf("No se recibio respuesta del servidor\n");
    }

    // 7. Cerrar el socket
    close(client_sockfd);

    printf("Conexion cerrada\n");

    return 0;
}

```

Funcionamiento del cliente: el programa recibe la dirección IP del servidor como argumento. Después crea un socket TCP, configura la dirección de destino y solicita una conexión. Una vez establecida, envía el carácter `A`, espera la respuesta y finalmente cierra el socket.

## Compilación y ejecución de los programas

Una vez creados los archivos fuente, se deben compilar utilizando el compilador correspondiente a cada sistema operativo.

### Compilar el servidor en Ubuntu WSL2

Ubicarse en el directorio de trabajo:

```
cd ~/Documentos/Programacion/SisDistribuidos/sockets
```

Compilar:

```
gcc servidor01.c -o servidor01
```

Ejecutar:

```
./servidor01
```

El servidor permanecerá ejecutándose y esperando conexiones.

### Compilar el cliente en macOS

En la MacBook, guardar el código como `cliente01.c` y ejecutar:

```
clang cliente01.c -o cliente01
```

Para establecer la conexión con el servidor:

```
./cliente01 192.168.10.1
```

### Verificar el puerto TCP

Desde macOS también se puede comprobar si el puerto del servidor es accesible:

```
nc -vz 192.168.10.1 5000
```

Si la conexión está disponible, se mostrará un mensaje indicando que el puerto está abierto.

