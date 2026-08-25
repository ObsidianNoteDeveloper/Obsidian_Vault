Fundamental | Tier 0

---
Section 1 / 12

# Introducción a las redes

Dos tipos primarios de redes: `Local Area Networks (LANs)` y `Wide Area Networks (WANs)`.

La siguiente tabla muestra algunos `key concepts` (conceptos clave) de redes.

| **Conceptos**  | **Descripción**                                                         |
| -------------- | ----------------------------------------------------------------------- |
| `Nodes`        | Dispositivos individuales conectados a una red.                         |
| `Links`        | Vías de comunicación que conectan los nodos (cableadas o inalámbricas). |
| `Data Sharing` | El propósito principal de una red es permitir el intercambio de datos.  |

#### Red de Área Local (LAN)

Una `Local Area Network (LAN)` conecta dispositivos a corta distancia, como dentro de una casa, una escuela o un pequeño edificio de oficinas. A continuación se presentan algunas de sus características clave:

|**Característica**|**Descripción**|
|---|---|
|`Geographical Scope`|Cubre un área pequeña.|
|`Ownership`|Generalmente es propiedad y está gestionada por una sola persona u organización.|
|`Speed`|Altas tasas de transferencia de datos.|
|`Media`|Utiliza conexiones cableadas (cables de Ethernet) o inalámbricas (Wi-Fi).|

#### Red de Área Amplia (WAN)

Una `Wide Area Network (WAN)` abarca una gran área geográfica, conectando múltiples LAN. A continuación se presentan algunas de sus características clave:

|**Característica**|**Descripción**|
|---|---|
|`Geographical Scope`|Cubre ciudades, países o continentes.|
|`Ownership`|A menudo es de propiedad colectiva o distribuida (p. ej., proveedores de servicios de internet).|
|`Speed`|Tasas de transferencia de datos más lentas en comparación con las LAN debido al viaje de datos a larga distancia.|
|`Media`|Utiliza fibra óptica, enlaces satelitales y líneas de telecomunicaciones arrendadas.|
> [!Note] Nota
> Internet es el mayor ejemplo de una `WAN`, ya que conecta millones de `LANs` en todo el mundo.

En redes de computadoras, un **ISP (Internet Service Provider)**, o **Proveedor de Servicios de Internet**, es una empresa u organización que proporciona a personas, hogares y empresas el acceso a Internet y, en muchos casos, otros servicios relacionados como telefonía, televisión por cable, alojamiento web o correo electrónico.

---
Section 2 / 12

# Conceptos de Redes

### Modelo OSI

| Capa                            | Definición simplificada                                                                                                                                                                |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Capa Física (1)**             | Transmite bits a través del medio físico (cables o señales inalámbricas). Se encarga del hardware y las conexiones físicas.                                                            |
| **Capa de Enlace de Datos (2)** | Envía datos entre dispositivos de la misma red. Usa direcciones **MAC** y detecta errores en la transmisión.                                                                           |
| **Capa de Red (3)**             | Dirige los paquetes entre diferentes redes. Usa direcciones **IP** y selecciona la mejor ruta hacia el destino.                                                                        |
| **Capa de Transporte (4)**      | Garantiza la entrega de los datos entre el origen y el destino. Utiliza protocolos como **TCP** (confiable) y **UDP** (rápido). Entrega confiable y secuencial de los datos (TCP/UDP). |
| **Capa de Sesión (5)**          | Establece, mantiene y finaliza la comunicación entre dos aplicaciones.                                                                                                                 |
| **Capa de Presentación (6)**    | Convierte el formato de los datos para que ambos dispositivos los entiendan. También cifra, descifra y comprime la información.                                                        |
| **Capa de Aplicación (7)**      | Proporciona servicios de red directamente a las aplicaciones del usuario, como navegar por Internet, enviar correos o transferir archivos.                                             |

### Modelo 

| Capa                   | Definición simplificada                                                                                                       |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Capa de Enlace**     | Se encarga de la conexión física y de enviar datos dentro de la red local. Utiliza tecnologías como **Ethernet** y **Wi-Fi**. |
| **Capa de Internet**   | Envía paquetes entre diferentes redes usando direcciones **IP** y determina la mejor ruta hacia el destino.                   |
| **Capa de Transporte** | Garantiza la comunicación entre el origen y el destino mediante **TCP** (confiable) o **UDP** (rápido).                       |
| **Capa de Aplicación** | Proporciona servicios de red a las aplicaciones, como navegar por Internet, enviar correos y transferir archivos.             |

![[Pasted image 20260731145336.png]]

### Protocolos de red comunes

| **Protocolo**                                             | **Descripción**                                                                                                                                                                                                                                       |
| --------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `HTTP (Protocolo de Transferencia de Hipertexto)`         | Se utiliza principalmente para transferir páginas web. Opera en la Capa de Aplicación, permitiendo que los navegadores y servidores se comuniquen en la entrega de contenido web.                                                                     |
| `FTP (Protocolo de Transferencia de Archivos)`            | Facilita la transferencia de archivos entre sistemas, funcionando también en la Capa de Aplicación. Proporciona una forma para que los usuarios suban o descarguen archivos hacia y desde los servidores.                                             |
| `SMTP (Protocolo para la Transferencia Simple de Correo)` | Gestiona la transmisión de correo electrónico. Operando en la Capa de Aplicación, es responsable de enviar mensajes de un servidor a otro, asegurando que lleguen a sus destinatarios previstos.                                                      |
| `TCP (Protocolo de Control de Transmisión)`               | Garantiza una transmisión de datos fiable mediante la comprobación y recuperación de errores, operando en la Capa de Transporte. Establece una conexión entre el emisor y el receptor para garantizar la entrega de los datos en el orden correcto.   |
| `UDP (Protocolo de Datagramas de Usuario)`                | Permite una comunicación rápida y sin conexión, que opera sin recuperación de errores. Esto lo hace ideal para aplicaciones que requieren velocidad por encima de la fiabilidad, como los servicios de streaming. UDP opera en la Capa de Transporte. |
| `IP (Protocolo de Internet)`                              | Crucial para enrutar paquetes a través de los límites de la red, funcionando en la Capa de Internet. Se encarga del direccionamiento y enrutamiento de paquetes para asegurar que viajen desde el origen hasta el destino a través de diversas redes. |
|                                                           |                                                                                                                                                                                                                                                       |

---
Section 3 / 12

# Componentes de una red

| **Componente**                          | **Descripción**                                                                            |
| --------------------------------------- | ------------------------------------------------------------------------------------------ |
| `End Devices`                           | Ordenadores, smartphones, tabletas, dispositivos IoT / inteligentes                        |
| `Intermediary Devices`                  | Switches, routers, módems, puntos de acceso                                                |
| `Network Media and Software Components` | Cables, protocolos, software de gestión y firewalls                                        |
| `Servers`                               | Servidores web, servidores de archivos, servidores de correo, servidores de bases de datos |
### Dispositivos finales

Un `dispositivo final` (`end device`), también conocido como `host`, es cualquier dispositivo que en última instancia envía o recibe datos dentro de una red.

### Dispositivos intermediarios

Un `dispositivo intermediario` (`intermediary device`) tiene el papel único de facilitar el flujo de datos entre `dispositivos finales` (`end devices`), ya sea dentro de una red de área local o entre diferentes redes.

|Dispositivo|Definición simplificada|
|---|---|
|**Tarjeta de Interfaz de Red (NIC)**|Es el componente que permite a un dispositivo conectarse a una red. Puede ser **Ethernet (cable)** o **Wi-Fi (inalámbrica)** y posee una **dirección MAC** única para identificar el dispositivo en la red.|
|**Router**|Conecta diferentes redes y dirige los paquetes de datos hacia su destino usando **direcciones IP**. También permite el acceso a Internet y puede incluir funciones de seguridad como firewall.|
|**Switch**|Conecta dispositivos dentro de una misma red (LAN). Utiliza **direcciones MAC** para enviar los datos únicamente al dispositivo correcto, mejorando el rendimiento de la red.|
|**Hub**|Conecta dispositivos en una red, pero envía los datos a **todos** los dispositivos conectados. Es un dispositivo antiguo y menos eficiente que un switch.|

### Medios de red y componentes de software

Los `Medios de Red y Componentes de Software` (`Network Media and Software Components`) son elementos vitales que permiten la comunicación y el funcionamiento sin problemas dentro de una red.

|Componente|Definición simplificada|
|---|---|
|**Cableado y conectores**|Son los cables y conectores que unen los dispositivos de una red y permiten transmitir datos. Su calidad influye en la velocidad y estabilidad de la conexión.|
|**Protocolos de red**|Son las reglas que permiten que los dispositivos se comuniquen correctamente a través de la red. Definen cómo se envían, reciben y procesan los datos.|
|**Software de gestión de red**|Son herramientas que permiten supervisar, administrar y mantener una red, detectando fallos, monitoreando el rendimiento y mejorando la seguridad.|
|**Firewall de software**|Es un programa de seguridad instalado en un dispositivo que controla el tráfico de red y bloquea conexiones no autorizadas o maliciosas.|

| Componente                     | Ejemplos                                                                                |
| ------------------------------ | --------------------------------------------------------------------------------------- |
| **Cableado y conectores**      | Cable Ethernet, fibra óptica, conector **RJ-45**.                                       |
| **Protocolos de red**          | **TCP/IP, HTTP, HTTPS, FTP, SMTP**.                                                     |
| **Software de gestión de red** | Herramientas para monitorear dispositivos, tráfico y rendimiento de la red.             |
| **Firewall de software**       | Firewall de Windows, `ufw` en Linux, firewalls integrados en otros sistemas operativos. |

### Servidores

Un `servidor` (`server`) es un ordenador potente diseñado para proporcionar servicios a otros ordenadores, conocidos como clientes, a través de una red.

---
Section 4 / 12

# Comunicación de red

-  Direcciones MAC
-  Direcciones IP
-  Puertos

### Direcciones MAC

Una `dirección de control de acceso a medios (MAC)` es un identificador único asignado a la tarjeta de interfaz de red (NIC) de un dispositivo, lo que permite que sea reconocido en una red local.

Cada dirección MAC tiene 48 bits de longitud y generalmente se representa en formato hexadecimal, apareciendo como seis pares de dígitos hexadecimales separados por dos puntos o guiones (p. ej., `00:1A:2B:3C:4D:5E`).

La unicidad de una dirección MAC proviene de su estructura: los primeros 24 bits representan el `identificador único organizacional (OUI)` asignado al fabricante, mientras que los 24 bits restantes son específicos del dispositivo individual.

> [!example]
> _**El comando de Windows [GETMAC](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/getmac) devolverá la dirección MAC de cada tarjeta de interfaz de red en el host.**_

El `protocolo de resolución de direcciones (ARP)` juega un papel crucial al mapear direcciones IP a direcciones MAC, permitiendo que los dispositivos encuentren la dirección MAC asociada con una dirección IP conocida dentro de la misma red. Este mapeo cierra la brecha entre el direccionamiento IP lógico y el direccionamiento físico del hardware dentro de la LAN.

### Direcciones IP

Una `dirección de protocolo de internet (IP)` es una etiqueta numérica asignada a cada dispositivo conectado a una red que utiliza el protocolo de internet para la comunicación. Funcionando en la `capa de red (Capa 3)` del modelo OSI.

Los routers utilizan las direcciones IP para determinar la ruta óptima para que los datos lleguen a su destino previsto a través de redes interconectadas.

- La **dirección IP** identifica un dispositivo de forma lógica y permite que los datos viajen entre diferentes redes.
- La **dirección MAC** identifica físicamente una interfaz de red y permite la entrega de las tramas dentro de una red local.
- Cuando un equipo quiere enviar datos en la LAN, primero convierte la IP en una MAC mediante **ARP**.
- Los **routers** toman decisiones usando las **direcciones IP**, mientras que los **switches** utilizan las **direcciones MAC** para entregar las tramas dentro de la red local.

> [!Note]
> En pocas palabras: **la IP responde a "¿a qué dispositivo debe llegar la información en la red?", mientras que la MAC responde a "¿a qué interfaz de red debo entregar esta trama en este enlace local?"**. Ambas son necesarias y complementarias para que la comunicación funcione correctamente.

### Puertos

Un `puerto` es un número asignado a procesos o servicios específicos en una red para ayudar a los ordenadores a clasificar y dirigir el tráfico de red correctamente. Funciona en la `capa de transporte (Capa 4)` del modelo OSI y trabaja con protocolos como TCP y UDP.

Los números de puerto van de `0` a `65535`.

|Tipo de puerto|Rango|Uso principal|Ejemplos|
|---|---|---|---|
|**Puertos bien conocidos**|**0-1023**|Reservados para los servicios y protocolos más comunes de Internet. Son administrados por la IANA.|HTTP (80), HTTPS (443), FTP (20 y 21).|
|**Puertos registrados**|**1024-49151**|Asignados por la IANA a aplicaciones y servicios específicos, generalmente instalados por los usuarios o empresas.|Microsoft SQL Server (1433).|
|**Puertos dinámicos o privados**|**49152-65535**|Utilizados temporalmente por los clientes para establecer conexiones con servidores. El sistema operativo los asigna automáticamente y se liberan al finalizar la comunicación.|Conexiones temporales de un navegador web o aplicaciones cliente.|

> [!Note]
> La **IANA (Internet Assigned Numbers Authority)** es una organización encargada de **administrar y asignar recursos únicos de Internet**

---
Section 5 / 12

# Protocolo de configuración dinámica de host (DHCP)

### Introducción a DHCP

`DHCP` es un protocolo de gestión de red que se utiliza para automatizar el proceso de configuración de dispositivos en redes IP.

El proceso de DHCP implica una serie de interacciones entre el cliente (el dispositivo que solicita una dirección IP) y el servidor DHCP (el servicio que se ejecuta en un dispositivo de red y que asigna direcciones IP). Este proceso a menudo se conoce como `DORA`, un acrónimo de `Discover`, `Offer`, `Request` y `Acknowledge`

---
Section 6 / 12

# Traducción de Direcciones de Red (NAT)

La idea es que `NAT` permite que múltiples dispositivos en una red privada compartan una única dirección IP pública. Esto no solo ayuda a conservar el conjunto limitado de direcciones IP públicas, sino que también añade una capa de seguridad a la red interna.

### Cómo Funciona NAT

Considera una red doméstica con varios dispositivos, como un portátil, un smartphone y una videoconsola, cada uno con una dirección IP privada única asignada: el portátil en 192.168.1.10, el smartphone en 192.168.1.11 y la videoconsola en 192.168.1.12. El router doméstico que gestiona esta red tiene dos interfaces críticas. La interfaz LAN (Red de Área Local) se conecta a la red privada con una dirección IP de 192.168.1.1, mientras que la interfaz WAN (Red de Área Amplia), conectada a la red del ISP, tiene una dirección IP pública, 203.0.113.50.

|Pregunta|Respuesta|Explicación|
|---|---|---|
|**1. NAT que permite múltiples IP privadas compartir una IP pública usando puertos únicos**|**PAT** (Port Address Translation)|También llamado **NAT Overload**. Usa diferentes números de puerto para distinguir las conexiones.|
|**2. RFC que especifica los rangos de IP privadas**|**RFC 1918**|Define los rangos privados: `10.0.0.0/8`, `172.16.0.0/12` y `192.168.0.0/16`.|
|**3. NAT con mapeo uno a uno entre IP privada y pública**|**Static NAT**|Cada IP privada tiene asociada una IP pública específica.|
|**4. NAT que asigna una IP pública de un pool según sea necesario**|**Dynamic NAT**|El router toma una IP disponible de un conjunto (_pool_) de IP públicas.|
|**5. Dispositivo que normalmente realiza NAT en una red doméstica**|**Router**|El router de casa traduce las IP privadas de los dispositivos a la IP pública proporcionada por el ISP.|

---
Section 7 / 12

# Sistema de Nombres de Dominios (DNS)

#### Jerarquía del DNS

El DNS está organizado como un árbol, comenzando desde la raíz y ramificándose en diferentes capas.

|**Capa**|**Descripción**|
|---|---|
|`Servidores raíz`|La cima de la jerarquía del DNS.|
|`Dominios de nivel superior (TLD)`|Como `.com`, `.org`, `.net`, o códigos de país como `.uk`, `.de`.|
|`Dominios de segundo nivel`|Por ejemplo, `example` en `example.com`.|
|`Subdominios o Nombre de host`|Por ejemplo, `www` en `www.example.com`, o `accounts` en `accounts.google.com`.|
#### Proceso de Resolución de DNS (Traducción de Dominio)

Cuando introducimos un nombre de dominio en nuestro navegador, el ordenador necesita encontrar la dirección IP correspondiente. Este proceso se conoce como `resolución de DNS` o `traducción de dominio`. Los siguientes pasos muestran cómo funciona este proceso.

|**Paso**|**Descripción**|
|---|---|
|`Paso 1`|Escribimos `www.example.com` en nuestro navegador.|
|`Paso 2`|Nuestro ordenador comprueba su caché de DNS local (una pequeña área de almacenamiento) para ver si ya conoce la dirección IP.|
|`Paso 3`|Si no la encuentra localmente, consulta a un `servidor DNS recursivo`. Este suele ser proporcionado por nuestro Proveedor de Servicios de Internet o un servicio de DNS de terceros como Google DNS.|
|`Paso 4`|El `servidor DNS recursivo` contacta a un `servidor raíz`, que lo dirige al `servidor de nombres TLD` apropiado (como los dominios `.com`, por ejemplo).|
|`Paso 5`|El `servidor de nombres TLD` dirige la consulta al `servidor de nombres autoritativo` para `example.com`.|
|`Paso 6`|El `servidor de nombres autoritativo` responde con la dirección IP para `www.example.com`.|
|`Paso 7`|El servidor recursivo devuelve esta dirección IP a tu ordenador, que entonces puede conectarse directamente al servidor del sitio web.|

---
Section 8 / 12

# Arquitectura de internet










