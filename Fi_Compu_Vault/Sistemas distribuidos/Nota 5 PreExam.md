
# **1. Sockets**

## **¿Qué es un socket?**

Es un mecanismo de comunicación que permite que dos procesos intercambien información a través de una red o dentro de un mismo equipo.

Un socket funciona como un punto de conexión entre un cliente y un servidor.

**Elementos principales:**

- IP: identifica el equipo dentro de la red.
- Puerto: identifica el proceso o servicio.
- Protocolo: establece cómo se transmiten los datos.

## **Tipos de sockets**

**TCP – Socket de flujo (SOCK****_****STREAM)**

- Orientado a conexión.
- Garantiza la entrega de datos.
- Mantiene el orden de los datos.
- Requiere establecer una conexión.
- Mayor control, pero puede tener más sobrecarga.

**UDP – Socket de datagramas (SOCK****_****DGRAM)**

- No necesita establecer conexión.
- No garantiza la entrega.
- No garantiza el orden de llegada.
- Transmite mensajes independientes (datagramas).
- Menor sobrecarga y generalmente menor latencia.

## **Diferencias entre TCP y UDP**

|Característica|TCP|UDP|
|---|---|---|
|Conexión|Sí|No|
|Fiabilidad|Garantizada por protocolo|No garantizada|
|Orden|Sí|No|
|Velocidad/sobrecarga|Mayor sobrecarga|Menor sobrecarga|
|Transmisión|Flujo de bytes|Datagramas|
|Ejemplo|HTTP/HTTPS|DNS, VoIP|

## **Modelo cliente-servidor**

Es la arquitectura donde un cliente solicita un servicio y un servidor procesa la solicitud y responde.

**Funcionamiento:**

1. El servidor crea un socket.
2. Asigna una dirección IP y un puerto (`bind`).
3. Espera solicitudes.
4. El cliente crea un socket y solicita comunicación.
5. El servidor recibe y procesa los datos.
6. El servidor envía una respuesta.

## **Funciones importantes de los sockets**

Estas son especialmente importantes si te preguntan sobre programación de sockets en C, Java o Python.

|Función|¿Qué hace?|
|---|---|
|`socket()`|Crea un socket.|
|`bind()`|Asocia el socket a una IP y puerto.|
|`listen()`|Pone al servidor TCP en espera.|
|`accept()`|Acepta una conexión TCP.|
|`connect()`|Solicita conexión con el servidor.|
|`send()`|Envía datos.|
|`recv()`|Recibe datos.|
|`sendto()`|Envía un datagrama UDP.|
|`recvfrom()`|Recibe un datagrama UDP.|
|`close()`|Cierra el socket.|

Importante: listen() y accept() son propios del flujo habitual de TCP, mientras que sendto() y recvfrom() son habituales en UDP.

## **Diferencia entre send() y sendto()**

- `send()`: normalmente envía datos mediante un socket conectado.
- `sendto()`: envía datos indicando la dirección del destinatario, habitual en UDP.


# **2. RPC (Remote Procedure Call)**

## **¿Qué es RPC?**

RPC significa _Remote Procedure Call_ (Llamada a Procedimiento Remoto).

Es un mecanismo que permite que un programa ejecute una función o procedimiento ubicado en otra computadora, como si fuera una llamada local.

**Ejemplo:** Un cliente solicita ejecutar una función `sumar(5, 3)` en un servidor. El servidor realiza la operación y devuelve el resultado `8`.

## **¿Cómo funciona RPC?**

1. El cliente llama a una función remota.
2. El Stub del cliente empaqueta los parámetros.
3. Se envía la solicitud por la red.
4. El Stub del servidor recibe y desempaqueta los parámetros.
5. El servidor ejecuta el procedimiento.
6. El resultado regresa al cliente.

## **Conceptos importantes de RPC**

|Concepto|Significado|
|---|---|
|Cliente|Solicita la ejecución del procedimiento.|
|Servidor|Ejecuta el procedimiento solicitado.|
|Stub cliente|Representa la función remota y prepara la solicitud.|
|Stub servidor|Recibe la solicitud y prepara la ejecución.|
|Marshalling|Empaquetar los parámetros para transmitirlos.|
|Unmarshalling|Desempaquetar los parámetros recibidos.|
|Binding|Asociar o localizar el servicio remoto.|

## **Ventajas de RPC**

- Facilita la comunicación entre computadoras.
- Oculta parte de la complejidad de la comunicación por red.
- Permite distribuir tareas entre diferentes equipos.
- Facilita la reutilización de servicios.

## **Desventajas de RPC**

- Depende de la disponibilidad de la red.
- Puede presentar latencia.
- Los errores de comunicación pueden interrumpir la ejecución.
- La comunicación remota es más compleja que una llamada local.

# **3. Diferencias entre Sockets y RPC**

|Sockets|RPC|
|---|---|
|Comunicación de bajo nivel.|Comunicación de más alto nivel.|
|El programador gestiona el envío y recepción.|El programador invoca procedimientos remotos.|
|Se trabaja directamente con conexiones o datagramas.|Se trabaja con funciones y parámetros.|
|Mayor control sobre la comunicación.|Mayor abstracción y facilidad de uso.|
|TCP y UDP son opciones habituales.|Puede utilizar sockets u otros transportes.|
**Para recordar:** Los sockets permiten establecer la comunicación; RPC facilita ejecutar procedimientos en otra computadora utilizando esa comunicación.


1. **Sockets:** mecanismo de comunicación entre procesos.
2. **TCP:** orientado a conexión, confiable y ordenado.
3. **UDP:** sin conexión, no garantiza entrega ni orden.
4. **SOCK****_****STREAM:** TCP.
5. **SOCK****_****DGRAM:** UDP.
6. **bind():** asigna IP y puerto.
7. **listen() y accept():** esperan y aceptan conexiones TCP.
8. **RPC:** permite ejecutar procedimientos remotamente.
9. **Stub:** intermediario entre cliente y servidor.
10. **Marshalling:** empaquetar datos.
11. **Unmarshalling:** desempaquetar datos.
12. **Binding:** localizar o asociar un servicio remoto.

