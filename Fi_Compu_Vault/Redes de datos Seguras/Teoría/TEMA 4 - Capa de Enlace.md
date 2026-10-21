
La capa de enlace de datos (capa 2 del modelo OSI) permite la comunicación entre dispositivos conectados al mismo enlace de red.

Se encarga de organizar los datos en tramas, utilizar direcciones MAC, controlar el acceso al medio físico y detectar ciertos errores durante la transmisión.

**1. ¿Qué es la capa de enlace de datos y cuáles son sus principales funciones?**

La capa de enlace de datos es la segunda capa del modelo de referencia OSI. Su función principal es proporcionar una transferencia de datos entre dispositivos conectados mediante un mismo enlace de red, organizando la información en unidades denominadas tramas.

Sus principales funciones son:

- Encapsulamiento: organiza los datos recibidos de la capa de red dentro de tramas.
    
- Direccionamiento físico: utiliza direcciones MAC para identificar las interfaces de red de origen y destino.
    
- Control de acceso al medio: determina cómo los dispositivos comparten y utilizan el medio de transmisión.
    
- Detección de errores: permite identificar alteraciones en una trama mediante mecanismos como la comprobación de redundancia cíclica (CRC).
    
- Control del enlace: puede gestionar aspectos de la comunicación entre dispositivos, según el protocolo utilizado.
    

_Explicación_: cuando una computadora envía información a otra dentro de una red local, la capa 2 se encarga de preparar esa información en una trama Ethernet, incorporando las direcciones MAC correspondientes y un mecanismo de detección de errores.

**2. ¿Cuáles son las subcapas de la capa de enlace de datos y cuál es la función de cada una?**

La capa de enlace de datos se divide conceptualmente en dos subcapas, definidas en la arquitectura IEEE 802:

|Subcapa|Función|
|---|---|
|LLC (Logical Link Control)|Proporciona una interfaz lógica con la capa de red e identifica o multiplexa protocolos de capa superior.|
|MAC (Media Access Control)|Gestiona el direccionamiento MAC y los mecanismos de acceso al medio de transmisión.|

_Explicación_:
La subcapa LLC permite que la capa de enlace interactúe con los protocolos superiores. Por su parte, la subcapa MAC interviene en el formato de las tramas, el direccionamiento físico y el acceso al medio.

Por ejemplo, en Ethernet, las direcciones MAC se utilizan para identificar las interfaces de origen y destino dentro de una trama.

Es importante recordar que esta división es propia de la arquitectura IEEE 802; no todos los protocolos de enlace implementan ambas subcapas de la misma manera.

**3. ¿Qué es una trama y cuáles son los campos principales de una trama Ethernet?**

Una trama es la unidad de datos que utiliza la capa de enlace para transmitir información a través de un enlace de red. Contiene información de control, direcciones físicas, los datos transportados y, en Ethernet, un campo para detectar errores.

Los campos principales de una trama Ethernet II son:





Las funciones de estos campos son:

- MAC destino: identifica la interfaz de destino de la trama.
    
- MAC origen: identifica la interfaz que transmite la trama.
    
- EtherType: indica el protocolo encapsulado, por ejemplo, IPv4 o IPv6.
    
- Datos y relleno: transportan el paquete de la capa superior y, cuando es necesario, el relleno mínimo.
    
- FCS (Frame Check Sequence): contiene el valor CRC utilizado para detectar errores en la trama.
    

Explicación: si una computadora transmite un paquete IP por Ethernet, la capa 2 lo encapsula en una trama. El dispositivo receptor comprueba su integridad y procesa el contenido si corresponde.


---

- ¿Qué es una interfaz de red?
- 