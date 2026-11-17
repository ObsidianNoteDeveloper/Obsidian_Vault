
[001 Construcción de Cables UTP para conexión directa y cruzada](#001%20Construcción%20de%20Cables%20UTP%20para%20conexión%20directa%20y%20cruzada)
[002 Componentes del cableado estructurado Norma ANSI/EIA/TIA 568](#002%20Componentes%20del%20cableado%20estructurado%20Norma%20ANSI/EIA/TIA%20568)
[003 Identificación de un sistema de cableado estructurado](#003%20Identificación%20de%20un%20sistema%20de%20cableado%20estructurado)
[004 Manejo de Dispositivos de Interconectividad, hub y switch](#004%20Manejo%20de%20Dispositivos%20de%20Interconectividad,%20hub%20y%20switch)
[005 Instalación de una red básica en las plataformas: Windows de Microsoft y Linux distribución Debian](#005%20Instalación%20de%20una%20red%20básica%20en%20las%20plataformas%20Windows%20de%20Microsoft%20y%20Linux%20distribución%20Debian)
[006 Encaminamiento y análisis de paquetes](#006%20Encaminamiento%20y%20análisis%20de%20paquetes)
[007 Configuración básica del router](#007%20Configuración%20básica%20del%20router)
[008 TCP y UDP](#008%20TCP%20y%20UDP)
[009 SSH: Secure Shell](#009%20SSH%20Secure%20Shell)
[010 Funciones de la capa de presentación](#010%20Funciones%20de%20la%20capa%20de%20presentación)
[011 Servidor DHCP](#011%20Servidor%20DHCP)

# Capa 1 del Modelo OSI (Física)

---

## 001 Construcción de Cables UTP para conexión directa y cruzada

1. Explique la razón por la cual los alambres del cable UTP están trenzados. 
2. ¿Qué es un par trenzado: UTP (UnShielded Twisted Pair) cable par trenzado no blindado (no apantallado)?. Explique las características así como ventajas y desventajas. 
3. ¿Qué es un par trenzado: STP (Shielded Twisted Pair) cable de par trenzado blindado (apantallado)? Explique las características así como ventajas y desventajas. 
4. Mencione las categorías de cables UTP que existen. Explique más a detalle las principales aplicaciones de los cables de la categoría UTP 5e (5 enhance - mejorada) y UTP 6. 
5. ¿Qué categoría de cable UTP es conveniente utilizar en nuevas instalaciones de cableado y por qué? 
6. Mencione las características de otros medios de transmisión: el cable coaxial y la fibra óptica. 
7. Si se va a tender un cable que transmita voz a través de cable UTP ¿Qué pines se utilizarían, cómo se armaría? 
8. Investigue la configuración para un cable cruzado en redes de tipo Gigabit Ethernet 
9. ¿Qué significan las normas ANSI/EIA/TIA T568-A y ANSI/EIA/TIA T568-B 
10. ¿Cuál es la importancia de la capa 1 del modelo OSI? 
11. Investigue costos del cable UTP categorías 5e, 6 y 6a.

**1. Diferencia entre UTP y STP.**

|Cable|Característica|
|---|---|
|UTP|Par trenzado sin blindaje metálico.|
|STP|Par trenzado con blindaje para reducir interferencias.|

El trenzado de los conductores reduce las interferencias electromagnéticas y la diafonía.

**2. Categorías de cable.**

- Cat 5e: soporta Ethernet Gigabit (1000BASE-T).
    
- Cat 6: mayor desempeño y mejor control de interferencias.
    
- Cat 6a: diseñado para soportar 10 Gigabit Ethernet hasta 100 metros.
    

**3. Estándares T568-A y T568-B.**

Memoriza el orden de los ocho conductores:

**T568-A**
1 - Blanco/Verde
2 - Verde
3 - Blanco/Naranja
_4 - Azul_
_5 - Blanco/Azul_
6 - Naranja
_7 - Blanco/Café_
_8 - Café_

**T568-B**
1 - Blanco/Naranja
2 - Naranja
3 - Blanco/Verde
_4 - Azul_
_5 - Blanco/Azul_
6 - Verde
_7 - Blanco/Café_
_8 - Café_

**4. Diferencia entre cable directo y cruzado.**

|Cable|Configuración|Uso tradicional|
|---|---|---|
|Directo|B-B o A-A|Dispositivos diferentes, como PC-switch.|
|Cruzado|A-B|Dispositivos similares, como PC-PC o switch-switch.|

**5. Otros conceptos:** RJ-45, NIC, capa física del modelo OSI, continuidad eléctrica y tester.

**Pregunta probable:** ¿Cómo se construye un cable cruzado?

Respuesta: se utiliza T568-A en un extremo y T568-B en el otro.





---

## 002 Componentes del cableado estructurado Norma ANSI/EIA/TIA 568

1. ¿Cuál es la función de las siguientes organizaciones: ANSI, EIA y TIA? 
2. Mencione las características de los seis subsistemas funcionales que conforman el cableado estructurado. 
3. ¿Qué es un panel de parcheo? 
4. ¿Qué es un rack? 
5. ¿Qué es un jack? 
6. ¿Qué es una roseta? 
7. ¿Qué es una placa de pared y cuál es su utilidad? 
8. ¿Qué es un patch cord y cuál es su objetivo principal? 
9. Investigue costos de patch panels, placas de pared y pinzas de impacto 
10. Realice un diagrama mostrando la trayectoria de conexiones desde el equipo de cómputo en el área de trabajo hasta el equipo activo ubicado en el cuarto de telecomunicaciones. Haga uso de los elementos que indica el cableado estructurado (rosetas, canaletas, rack, panel de parcheo, etcétera.)


**1. Organismos de normalización.**

|Organismo|Significado|
|---|---|
|ANSI|American National Standards Institute.|
|EIA|Electronic Industries Alliance.|
|TIA|Telecommunications Industry Association.|

**2. Normas importantes.**

|Norma|Función|
|---|---|
|ANSI/TIA 568|Cableado de telecomunicaciones.|
|ANSI/TIA 569|Rutas y espacios de telecomunicaciones.|
|ANSI/TIA 606|Administración de la infraestructura.|
|ANSI/TIA 607|Puesta a tierra y puenteado.|

**3. Componentes que debes identificar.**

|Componente|Función|
|---|---|
|Rack|Estructura para montar equipos.|
|Patch panel|Organiza y termina los cables horizontales.|
|Jack RJ-45|Conector hembra para terminar el cable.|
|Roseta|Punto de conexión en el área de trabajo.|
|Placa de pared|Soporte físico para las salidas de telecomunicaciones.|
|Patch cord|Cable flexible para interconectar equipos.|
|Pinza de impacto|Inserta y corta los conductores en terminales IDC.|

**4. Los seis subsistemas del cableado estructurado.**

Memoriza sus nombres:

1. Cableado horizontal.
2. Cableado vertical o backbone.
3. Área de trabajo.
4. Cuarto de telecomunicaciones.
5. Cuarto de equipos.
6. Entrada de servicios.

**Pregunta probable:** ¿Cuál es la distancia máxima del cableado horizontal?

Respuesta que debes recordar: 90 metros para el enlace permanente y hasta 100 metros considerando los cables de conexión del canal.






---

## 003 Identificación de un sistema de cableado estructurado 

1. ¿Cuáles son los medios para canalizaciones admitidos por el estándar ANSI/EIA/TIA 569? 
2. ¿Qué es una escalerilla por techo? Indique sus características y objetivos 
3. ¿Qué componentes se encuentran en un cuarto de telecomunicaciones? 
4. ¿Qué topología usa un sistema de cableado estructurado? 
5. ¿Cuáles son las características principales de los 6 subsistemas del cableado estructurado? Indíquelas 
6. Realice un dibujo donde identifique claramente los 6 subsistemas del cableado estructurado en un edificio 
7. ¿Qué es un equipo activo? Liste ejemplos 
8. ¿Qué es un equipo pasivo? Liste ejemplos 
9. ¿Qué tipos de canaletas existen? Realice una tabla indicando tipo, características y costos 
10. Investigue cuál es la fórmula que permite calcular la cantidad de cables que puede albergar una canaleta 
11. ¿A qué se hace referencia cuando se menciona la regla 5-4-3?

**1. Topología del cableado estructurado.**

Se utiliza una topología en estrella jerárquica: los nodos del área de trabajo se conectan al cuarto de telecomunicaciones y, mediante el backbone, se interconectan los distintos niveles.

**2. Equipos activos y pasivos.**

|Activos|Pasivos|
|---|---|
|Switch|Patch panel|
|Router|Rack|
|Hub|Canaletas|
|Access Point|Jack|
|Repetidor|Cable UTP|

La diferencia es que los activos procesan, regeneran o encaminan señales y requieren alimentación; los pasivos proporcionan infraestructura de conexión y distribución.

**3. Canalizaciones.**

Estudia qué son las canaletas, escalerillas y rutas de cableado, así como su función para proteger, organizar y distribuir los conductores.

**4. Regla 5-4-3.**

Es un concepto histórico de Ethernet compartida mediante repetidores: hasta cinco segmentos, cuatro repetidores y tres segmentos poblados por estaciones. Es una regla que puede aparecer como pregunta de definición.

**Pregunta probable:** ¿Qué subsistema se identifica al medir el cable desde el jack hasta el patch panel?

Respuesta: cableado horizontal.




---

# Capa 1 y 2 del Modelo OSI (Física y Enlace de datos)

---

## 004 Manejo de Dispositivos de Interconectividad, hub y switch

1. Realice una tabla comparativa que contenga al menos cinco características de un hub y un switch. 
2. ¿Cómo funciona el método de CSMA/CD? 
3. ¿Qué es una colisión? 
4. ¿Cuál es la importancia de la capa 2 del modelo OSI? 
5. Describa los dos tipos de parámetros dúplex para las comunicaciones en una red Ethernet: Half dúplex y Full dúplex. 
6. Investigue cómo es una conexión en cascada. Realice un diagrama y mencione las características de esta conexión, así como su funcionamiento. 
7. Investigue cómo es una conexión en apilamiento. Realice un diagrama y mencione las características de esta conexión, así como su funcionamiento. 
8. ¿Qué es un analizador de paquetes y cuál es su utilidad? 
9. Mencione otras tres herramientas de análisis de paquetes y sus características 
10. Mencione otras tres herramientas de simulación de redes y sus características. 
11. Para emplear el software Cisco Packet Tracer debe contar con una cuenta en Skills for All, consulte el Anexo de este manual para crearla, si ya tiene una cuenta, puede consultar el mismo anexo para utilizar el software.

**1. Hub vs. Switch.**

|Característica|Hub|Switch|
|---|---|---|
|Capa OSI|1, física|2, enlace|
|Direccionamiento|No utiliza MAC para decidir destino|Utiliza direcciones MAC|
|Transmisión|Replica hacia todos los puertos|Reenvía hacia el puerto correspondiente|
|Colisiones|Dominio compartido|Separa dominios por puerto|
|Ancho de banda|Compartido|Dedicado por puerto|
|Inteligencia|No aprende direcciones|Aprende direcciones MAC|

**2. CSMA/CD.**

Carrier Sense Multiple Access with Collision Detection.

Su funcionamiento:

1. El dispositivo escucha el medio.
2. Si está libre, transmite.
3. Si detecta una colisión, detiene la transmisión.
4. Espera un tiempo aleatorio.
5. Intenta transmitir nuevamente.

**3. Parámetros dúplex.**

- Half Duplex: permite transmitir o recibir, pero no ambas acciones simultáneamente.
- Full Duplex: permite transmitir y recibir simultáneamente.

**4. Conexiones.**

- Cascada: conexión de un switch con otro mediante puertos de red.
- Apilamiento: interconexión de switches mediante interfaces de stacking para administrarlos como una unidad lógica.

**5. Herramientas.**

- Wireshark: captura y analiza paquetes.
- Cisco Packet Tracer: simula redes y dispositivos.
- tcpdump: captura tráfico desde la terminal.

**Pregunta probable:** ¿Por qué un switch mejora el rendimiento respecto a un hub?

Respuesta: porque aprende las direcciones MAC y reenvía las tramas al puerto correspondiente en lugar de replicarlas a todos los puertos.




---
# Capa 2 del Modelo OSI (Enlace de datos)

---

## 005 Instalación de una red básica en las plataformas: Windows de Microsoft y Linux distribución Debian

1. ¿Qué es un cliente, protocolo, adaptador y servicio en una red? 
2. En el ámbito de las redes existen dos tipos de direcciones: físicas y lógicas. Describa las características de cada una. 
3. Investigue las clases de direcciones lógicas. 
4. ¿Qué es y qué funciones realiza una máscara de red? 
5. Explique el funcionamiento de: a. Un DNS b. Una puerta de enlace c. Un servidor DHCP 
6. Investigue cómo se configura una tarjeta de red en modo gráfico en Linux Distribución Debian 
7. Investigue el objetivo, funcionamiento y al menos 3 parámetros del comando ping 
8. ¿Para qué se usa el comando apt-get install ifconfig o apt install ifconfig? 
9. ¿Para qué se usa el comando ip addr y cuál es la sintaxis para usarlo? 
10. ¿Con qué otros nombres se puede identificar a la NIC además de eth0? 
11. ¿Para qué sirve el protocolo TCP/IP? 
12. ¿Cuál es el significado e importancia de WINS? 
13. ¿Por qué es importante conocer el modelo del chipset de la NIC? 
14. ¿Qué significan cada uno de los parámetros en la versión del kernel (ejemplo: kernel 2.6.7.3)? Explique los 4 parámetros para las versiones actuales. 
15. ¿Cómo se desactiva un firewall en el sistema operativo Linux? 
16. ¿Cómo se desactiva un firewall en el sistema operativo Windows? 
17. Investigar los pasos para instalar el controlador de tarjeta de red en Windows


 **1. Conceptos indispensables**

|Concepto|Qué debes saber|
|---|---|
|Dirección IP|Identifica lógicamente un dispositivo en una red.|
|Dirección MAC|Identificador físico de la interfaz de red.|
|Máscara de red|Determina qué parte de la IP identifica la red y qué parte al host.|
|Gateway|Puerta de enlace para comunicarse con otras redes.|
|DNS|Traduce nombres de dominio a direcciones IP.|
|DHCP|Asigna automáticamente parámetros de configuración IP.|
|NIC|Tarjeta o interfaz de red.|
|TCP/IP|Conjunto de protocolos para la comunicación en redes.|
|WINS|Servicio de resolución de nombres NetBIOS en redes Windows.|

**2. Clases de direcciones IPv4.**

|Clase|Primer octeto|Uso tradicional|
|---|---|---|
|A|1–126|Redes grandes|
|B|128–191|Redes medianas|
|C|192–223|Redes pequeñas|
|D|224–239|Multidifusión|
|E|240–255|Experimental|

También debes reconocer las direcciones privadas:

- Clase A: 10.0.0.0/8
- Clase B: 172.16.0.0/12
- Clase C: 192.168.0.0/16

### **3. Comandos que debes memorizar**

**Windows (CMD)**

|Comando|Función|
|---|---|
|`ipconfig`|Muestra la configuración IP.|
|`ipconfig /all`|Muestra información detallada de las interfaces.|
|`ipconfig /release`|Libera la dirección IP asignada por DHCP.|
|`ipconfig /renew`|Solicita una nueva configuración DHCP.|
|`ping 8.8.8.8`|Comprueba conectividad mediante ICMP.|
|`hostname`|Muestra el nombre del equipo.|

**Linux Debian**

|Comando|Función|
|---|---|
|`ifconfig`|Muestra o configura interfaces de red.|
|`ip addr`|Muestra direcciones IP de interfaces.|
|`ip link`|Muestra información de interfaces de red.|
|`ping 8.8.8.8`|Comprueba conectividad.|
|`ip route`|Muestra la tabla de encaminamiento.|
|`apt install paquete`|Instala paquetes.|
|`sudo`|Ejecuta comandos con privilegios elevados.|

**¡Atención con esta pregunta!**

¿Para qué sirve `ip addr`?

Respuesta: permite consultar las direcciones IP asignadas a las interfaces de red y su estado.

¿Para qué sirve `ping`?

Respuesta: envía solicitudes ICMP Echo Request y espera respuestas Echo Reply para comprobar la conectividad con otro dispositivo.

Los parámetros de `ping` que conviene reconocer son:

- `-c`: cantidad de paquetes en Linux.
- `-t`: continúa enviando paquetes en Windows hasta detenerlo.
- `-n`: cantidad de solicitudes en Windows.
- `-4`: fuerza el uso de IPv4 en sistemas que lo admiten.

**3. Firewall.**

Debes saber que el firewall controla el tráfico de red mediante reglas de filtrado. El cuestionario previo pregunta cómo desactivarlo en Linux y Windows. Prioriza conocer dónde se administra y qué función tiene, en lugar de memorizar comandos de desactivación.




---
# Capa 3 del Modelo OSI (Red)

---

## 006 Encaminamiento y análisis de paquetes

1. Describa las funciones de la capa 3 (capa de red) del Modelo OSI 
2. ¿Cuáles son los principales campos que forman la trama Ethernet? 
3. ¿Cuáles son los principales campos que forman un paquete IP? 
4. ¿Para qué se usa el comando apt-get install tcpdump o apt install tcpdump? 
5. Defina el concepto de encaminamiento 
6. Investigue el objetivo y funcionamiento del protocolo ARP 
7. Descargue el software NeoTrace (o equivalente) y visualice en el modo Node View el camino que siguen los paquetes hacia un servidor localizado en: a. www.google.com b. www.youtube.com c. wikipedia.com d. Otra liga de su preferencia Realice impresiones de pantalla e inclúyalas en la entrega de este previo. 


### **1. Capa de red del modelo OSI**

La capa 3 se encarga principalmente del direccionamiento lógico y el encaminamiento de paquetes entre redes diferentes.

Conceptos:

- Dirección IP.
- Encaminamiento.
- Tabla de rutas.
- Router.
- Paquete IP.
- ARP.
- ICMP.

### **2. ARP (Address Resolution Protocol)**

Es un protocolo que permite obtener la dirección MAC asociada a una dirección IPv4 dentro de una red local.

Ejemplo:

Una computadora quiere enviar información a `192.168.1.20`, pero no conoce su MAC. Envía una solicitud ARP preguntando quién tiene esa dirección IP.

El dispositivo correspondiente responde con su dirección MAC.

**Memoriza la diferencia:**

- IP: dirección lógica.
- MAC: dirección física.
- ARP: relaciona una dirección IPv4 con una MAC.

### **3. Comandos importantes**

|Comando|Sistema|Función|
|---|---|---|
|`arp -a`|Windows|Muestra la tabla ARP.|
|`arp -d *`|Windows|Elimina las entradas de la tabla ARP.|
|`ping IP`|Ambos|Comprueba conectividad.|
|`route print`|Windows|Muestra la tabla de rutas.|
|`route -n`|Linux|Muestra la tabla de rutas numéricamente.|
|`ip route`|Linux|Consulta rutas IP.|
|`tracert dominio`|Windows|Muestra los saltos hacia un destino.|
|`traceroute dominio`|Linux|Rastrea la ruta hacia un destino.|
|`tcpdump`|Linux|Captura paquetes desde la terminal.|

Comandos de instalación que aparecen en los cuestionarios:

```Bash
apt install tcpdump
apt install wireshark
```

### **4. Wireshark**

Debes saber qué es un analizador de paquetes y cómo se utiliza.

Wireshark permite capturar, examinar y filtrar paquetes que circulan por una interfaz de red.

Filtros importantes:

|Filtro|Qué muestra|
|---|---|
|`arp`|Paquetes ARP|
|`icmp`|Paquetes ICMP|
|`ip`|Paquetes IPv4|
|`tcp`|Paquetes TCP|
|`udp`|Paquetes UDP|
|`dns`|Paquetes DNS|

**Pregunta muy probable:** ¿Qué sucede cuando ejecutas `ping` y posteriormente consultas `arp -a`?

Respuesta: al comunicarse con dispositivos de la red local, el equipo puede generar solicitudes ARP para conocer sus direcciones MAC. Después, esas asociaciones pueden aparecer en la tabla ARP.

Importante: para destinos externos, normalmente se resuelve mediante ARP la MAC de la puerta de enlace, no la MAC del servidor remoto.




---

## 007 Configuración básica del router

1. Investigue las siguientes 3 funciones de la capa de red: a. Determinación del camino b. Encaminamiento c. Establecimiento de la llamada 
2. ¿Qué es un router y cuál es su funcionamiento? 
3. ¿Cuáles son los modos de configuración que maneja el router? Indique sus privilegios 
4. Investigue las formas de acceso a un router CISCO 
5. ¿Qué son los servicios ADSL y POTS? 
6. ¿Qué es una tabla de encaminamiento? 
7. Explique las características principales del encaminamiento estático. 
8. Explique las características principales del encaminamiento dinámico. 
9. ¿Cómo funcionan los protocolos por vector-distancia? Menciona dos ejemplos. 
10. ¿Cómo funcionan los protocolos por estado-enlace? Menciona dos ejemplos. 
11. Investigue la sintaxis de los comandos para configurar una ruta de encaminamiento estática en un router CISCO. 
12. Investigue los componentes internos de un router y descríbalos a continuación 
13. Investigue a qué se refieren cada uno de los componentes de la instrucción line vty 0 4 
14. Investigue los comandos correspondientes que deben emplearse en el router para configurar el encaminamiento dinámico 


### **1. ¿Qué es un router?**

Es un dispositivo de capa 3 del modelo OSI que interconecta diferentes redes y determina por dónde deben enviarse los paquetes IP.

### **2. Conceptos que debes diferenciar**

|Concepto|Descripción|
|---|---|
|Determinación del camino|Selección de la mejor ruta hacia el destino.|
|Encaminamiento|Proceso de dirigir paquetes hacia otras redes.|
|Tabla de encaminamiento|Contiene información de las rutas conocidas por el router.|
|Ruta estática|Se configura manualmente.|
|Ruta dinámica|Se aprende mediante protocolos de encaminamiento.|

**3. Encaminamiento estático vs. dinámico.**

|Estático|Dinámico|
|---|---|
|Configuración manual.|Aprende rutas automáticamente.|
|No intercambia información de rutas mediante protocolos dinámicos.|Intercambia información de encaminamiento.|
|Adecuado para redes pequeñas o estables.|Adecuado para redes con mayor complejidad.|
|No se adapta automáticamente a cambios de topología.|Puede adaptarse a cambios de topología.|

### **4. Protocolos de encaminamiento**

Debes identificar las dos categorías:

|Categoría|Funcionamiento|Ejemplos|
|---|---|---|
|Vector-distancia|Comparte información de rutas y métricas con vecinos.|RIP, EIGRP (avanzado/híbrido).|
|Estado-enlace|Construye una visión de la topología de la red.|OSPF, IS-IS.|

### **5. Modos de configuración Cisco**

Esta parte es especialmente importante para preguntas abiertas.

**Jerarquía de comandos Cisco IOS**

**Modo usuario**
Símbolo: `Router>`
Acceso básico y limitado.
`enable`

**Modo privilegiado**
Símbolo: `Router#`
Permite consultar y administrar el dispositivo.
`configure terminal`

**Configuración global**
Símbolo: `Router(config)#`
Permite modificar la configuración general.
`interface ...` / `line vty 0 4`

**Configuración específica**
Símbolos: `Router(config-if)#` o `Router(config-line)#`
Configuración de interfaces o líneas de acceso.

### **6. Comandos Cisco que debes aprender**

```Bash
enable
configure terminal
hostname R1
interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
show ip interface brief
show running-config
show ip route
```

**¿Para qué sirve cada uno?**

|Comando|Función|
|---|---|
|`enable`|Entra al modo privilegiado.|
|`configure terminal`|Entra a configuración global.|
|`hostname R1`|Cambia el nombre del router.|
|`interface ...`|Selecciona una interfaz.|
|`ip address`|Asigna IP y máscara.|
|`no shutdown`|Habilita la interfaz.|
|`show ip interface brief`|Resume el estado de las interfaces.|
|`show running-config`|Muestra la configuración activa.|
|`show ip route`|Muestra la tabla de encaminamiento.|

**7. Ruta estática.**

Debes reconocer la sintaxis:

```bash
ip route RED DESTINO MASCARA SIGUIENTE_SALTO
```

Ejemplo:

```bash
ip route 192.168.2.0 255.255.255.0 10.0.0.2
```

Esto indica que para llegar a `192.168.2.0/24` se debe utilizar como siguiente salto `10.0.0.2`.

**8. Línea VTY.**

```bash
line vty 0 4
```

Significa que se seleccionan las líneas virtuales de terminal de la 0 a la 4, utilizadas para acceso remoto.

También debes recordar:

- ADSL: tecnología de acceso a Internet mediante líneas telefónicas.
- POTS: Plain Old Telephone Service, servicio telefónico convencional.



---
# Capa 4 del Modelo OSI (Transporte)

---

## 008 TCP y UDP

1. Mencione al menos 2 funciones de la capa de transporte del Modelo OSI 
2. Mencione algunos protocolos de transporte (no incluya TCP ni UDP). 
3. ¿Qué es el protocolo de transporte TCP? 
4. ¿Qué es el protocolo de transporte UDP? 
5. Dibuje un datagrama UDP. 
6. Dibuje un segmento TCP. 
7. ¿Qué es un socket y qué se necesita para crearlo? 
8. ¿Para qué se usa el comando apt-get install gcc o apt install gcc? 
9. ¿Para qué se usa el comando apt-get install ssh o apt install ssh? 
10. ¿Qué es un puerto? 
11. ¿Cuáles son los rangos de puertos existentes? 
12. ¿Qué rangos de puertos pueden utilizarse para establecer comunicaciones?


### **1. TCP vs. UDP**

|Característica|TCP|UDP|
|---|---|---|
|Conexión|Orientado a conexión|No orientado a conexión|
|Confiabilidad|Garantiza entrega ordenada y retransmisión|No garantiza entrega|
|Control de flujo|Sí|No|
|Control de congestión|Sí|No|
|Velocidad/overhead|Mayor overhead|Menor overhead|
|Unidad de datos|Segmento|Datagrama|

**Ejemplos de aplicaciones:**

- TCP: HTTP, HTTPS, SSH, FTP.
- UDP: DNS, DHCP, VoIP y streaming en determinados escenarios.

### **2. Establecimiento de conexión TCP**

Memoriza el Three-Way Handshake:

## **TCP: Three-Way Handshake**

**Cliente**
- 1. SYN
Solicita conexión →

- 3. ACK
Confirma recepción →

`Conexión establecida`

**Servidor**

- 2. SYN-ACK
← Confirma y solicita

### **3. Puertos**

Un puerto identifica un proceso o servicio de comunicación dentro de un host.

|Rango|Clasificación|
|---|---|
|0–1023|Puertos conocidos (Well-known).|
|1024–49151|Puertos registrados.|
|49152–65535|Puertos dinámicos o privados.|

Puertos que debes reconocer:

|Protocolo|Puerto|
|---|---|
|FTP|20 y 21|
|SSH|22|
|Telnet|23|
|SMTP|25|
|DNS|53|
|DHCP servidor|67|
|DHCP cliente|68|
|HTTP|80|
|POP3|110|
|HTTPS|443|

### **4. Sockets**

Un socket es un punto de comunicación que permite intercambiar datos entre procesos mediante una red.

Para establecer una comunicación se necesita identificar, entre otros elementos, la dirección IP, el puerto y el protocolo de transporte.

**Diferencia entre cliente y servidor:**

- Servidor: espera solicitudes y ofrece un servicio.
- Cliente: inicia la comunicación y solicita el servicio.

### **5. Comandos del laboratorio**

```Bash
apt install gcc
apt install ssh
```

¿Para qué sirve `gcc`? Para instalar el compilador de C utilizado para compilar los programas de sockets.

¿Para qué sirve `ssh`? Para instalar el cliente SSH y las herramientas relacionadas disponibles en el paquete.

También debes entender el proceso de compilación:

```Bash
gcc programa.c -o programa
./programa
```

El primer comando compila el código fuente y genera un ejecutable llamado `programa`. El segundo ejecuta el programa.



---
# Capa 6 del Modelo OSI (Presentación)

---

## 009 SSH: Secure Shell

1. ¿Qué es el reenvío por X11? 
2. ¿Qué es un sniffer? 
3. Mencione cuáles son las versiones del protocolo SSH y explique sus características. 
4. ¿Cuáles son las secuencias de eventos a llevar a cabo en una conexión SSH? 
5. ¿A qué nos referimos con la Autenticación? 
6. Explique detalladamente los pasos que se producen cuando un cliente contacta a un servidor a través del protocolo SSH. 
7. ¿Qué algoritmo de cifrado emplea el protocolo SSH? 
8. ¿En dónde es conveniente utilizar SSH? 
9. ¿Cuáles son los objetivos principales de la capa 6 del modelo OSI?


### **1. ¿Qué es SSH?**

SSH (Secure Shell) es un protocolo que permite establecer conexiones remotas seguras entre un cliente y un servidor.

Su principal característica es que cifra la comunicación, incluyendo la autenticación y los datos transmitidos.

**Diferencias que debes memorizar:**

|Protocolo|Característica|
|---|---|
|SSH|Comunicación remota cifrada.|
|Telnet|Comunicación remota sin cifrado.|
|SCP|Transferencia segura de archivos mediante SSH.|
|FTP|Transferencia de archivos tradicional.|

SSH utiliza el puerto TCP 22 por defecto.

### **2. Autenticación**

El manual trabaja con dos formas principales:

**Autenticación mediante contraseña:** el usuario introduce sus credenciales para acceder al servidor.

**Autenticación mediante clave pública:** se genera un par de claves criptográficas:

- Clave privada: permanece en el cliente y debe protegerse.
- Clave pública: se copia al servidor y se utiliza para verificar la autenticación.

### **3. Comandos que debes memorizar**

**Instalación**

```
apt install ssh
```

**Conexión remota**

```
ssh usuario@192.168.2.10
```

**Generación de claves**

```
ssh-keygen
```

**Transferencia de clave pública**

```
ssh-copy-id usuario@192.168.2.10
```

**Agregar clave al agente SSH**

```
ssh-add ~/.ssh/id_rsa
```

**Transferencia de archivos**

```
scp archivo.txt usuario@192.168.2.10:/home/usuario/
```

**Salir de la sesión**

```
exit
```

El manual también utiliza comandos como:

```
ssh-keygen -p -f /home/redes/.ssh/id_rsa
```

Este comando permite cambiar la frase de contraseña que protege una clave privada.

### **4. Conceptos del cuestionario previo**

- X11 Forwarding: permite reenviar aplicaciones gráficas de un equipo remoto hacia el equipo cliente.
- Sniffer: herramienta que captura y analiza tráfico de red.
- Autenticación: proceso mediante el cual se verifica la identidad de un usuario.
- SSH-1 y SSH-2: versiones del protocolo; SSH-2 es la versión segura y vigente, mientras que SSH-1 es obsoleta.

**Pregunta probable:** ¿Cuál es la diferencia entre autenticación mediante contraseña y autenticación mediante clave pública?

Respuesta: la primera verifica las credenciales introducidas por el usuario; la segunda utiliza un par de claves criptográficas, donde la clave privada permanece protegida en el cliente y la clave pública se registra en el servidor.



---

## 010 Funciones de la capa de presentación 

1. ¿Cuál es la capa 6 del modelo OSI? (Dé una descripción general). 
2. ¿Cuáles son las funciones principales de la Capa de Presentación? 
3. Mencione algunos formatos de sonido, imágenes, películas y texto. 
4. ¿Qué es la compresión de datos? 
5. ¿Qué es la compresión con pérdida de datos y qué es la compresión sin pérdida? 
6. ¿Qué es criptografía? 
7. Describa en qué consiste la criptografía simétrica. 
8. Describa en qué consiste la criptografía asimétrica. 
9. Menciona algunos algoritmos de cifrado. 
10. ¿De qué forma interactúa la capa 6 con sus capas aledañas (capa 5 y 7)?

### **1. Capa 6 del modelo OSI**

La capa de presentación se encarga de representar los datos de forma que los sistemas puedan interpretarlos correctamente.

Sus funciones principales son:

1. Traducción y codificación de datos.
2. Compresión y descompresión.
3. Cifrado y descifrado.

### **2. Formatos de archivos**

|Tipo|Ejemplos|
|---|---|
|Sonido|MP3, WAV, AAC|
|Imágenes|JPEG, PNG, GIF|
|Video|MP4, AVI, MKV|
|Texto|ASCII, UTF-8, Unicode|

### **3. Compresión**

|Tipo|Característica|Ejemplos|
|---|---|---|
|Con pérdida|Elimina información para reducir el tamaño.|JPEG, MP3.|
|Sin pérdida|Permite recuperar los datos originales.|ZIP, PNG, FLAC.|

**Pregunta probable:** ¿En qué situaciones se utiliza compresión con pérdida?

Respuesta: cuando se busca reducir considerablemente el tamaño de archivos multimedia, como imágenes, audio y video, aceptando una pérdida de calidad.

### **4. Criptografía**

Es el conjunto de técnicas que permiten proteger información mediante transformaciones matemáticas.

|Tipo|Característica|Ejemplos|
|---|---|---|
|Simétrica|Utiliza una misma clave para cifrar y descifrar.|AES, 3DES.|
|Asimétrica|Utiliza un par de claves pública y privada.|RSA, ECC.|

**Diferencia fundamental:**

- Simétrica: rápida, pero requiere compartir de forma segura la clave.
- Asimétrica: permite intercambiar información y verificar identidades mediante claves relacionadas matemáticamente.

También debes saber cómo interactúa la capa 6 con las capas 5 (sesión) y 7 (aplicación): recibe los datos de la capa de aplicación, los representa o transforma y los entrega a la capa de sesión; en recepción realiza el proceso inverso.

---
# Capa 7 del Modelo OSI (Aplicación)

---

## 011 Servidor DHCP

1. Investigue los pasos que se llevan a cabo para el establecimiento de la sesión entre un servidor DHCP y una máquina cliente. 
2. Investigue las características de funcionamiento del protocolo BOOTP 
3. Investigue las características de los diferentes modos de asignación de direcciones de un servidor DHCP. 
4. Explique el concepto de “concesión”


### **1. ¿Qué es DHCP?**

DHCP significa Dynamic Host Configuration Protocol.

Es un protocolo cliente-servidor que asigna automáticamente parámetros de configuración de red a los dispositivos.

Entre los parámetros que puede proporcionar están:

- Dirección IP.
- Máscara de red.
- Puerta de enlace.
- Servidores DNS.

**Puerto y protocolo:**

|Elemento|Valor|
|---|---|
|Protocolo de transporte|UDP|
|Puerto del servidor|67|
|Puerto del cliente|68|

### **2. Tres modos de asignación DHCP**

|Modo|Funcionamiento|
|---|---|
|Manual|El administrador asocia una IP específica con un cliente.|
|Automática|El servidor asigna una dirección permanente o de larga duración.|
|Dinámica|El servidor asigna una dirección por un tiempo limitado mediante una concesión.|

### **3. Proceso DHCP**

Memoriza DORA:

## **Proceso DORA**

1. **Discover**
    El cliente busca servidores DHCP disponibles.
    
2. **Offer**
    El servidor ofrece una dirección IP.
    
3. **Request**
    El cliente solicita la dirección ofrecida.
    
4. **Acknowledge**
    El servidor confirma la asignación.

### **4. Comandos de Debian del manual**

Estos son especialmente importantes porque aparecen directamente en el procedimiento de la práctica.

**Instalación del servidor:**

```
apt install isc-dhcp-server
```

**Configuración de la interfaz de red:**

```
ifconfig
```

**Edición de la configuración del servicio:**

```
nano /etc/default/isc-dhcp-server
```

En el archivo se especifica la interfaz que utilizará el servidor:

```
INTERFACESv4="enp0s3"
```

**Configuración de interfaces de red:**

```
nano /etc/network/interfaces
```

**Reinicio de los servicios de red:**

```
/etc/init.d/networking restart
```

**Reinicio del servicio DHCP:**

```
/etc/init.d/isc-dhcp-server restart
```

**Comprobación de la configuración:**

```
ifconfig
```

### **5. Datos de configuración que aparecen en el manual**

El procedimiento utiliza los siguientes parámetros para el servidor:

|Parámetro|Valor|
|---|---|
|Dirección IP|192.168.1.8|
|Máscara|255.255.255.0|
|Red|192.168.1.0|
|Broadcast|192.168.1.255|
|Gateway|192.168.1.1|

**Pregunta probable:** ¿Por qué el servidor DHCP utiliza UDP y cuáles son sus puertos?

Respuesta: utiliza UDP porque permite el intercambio de mensajes sin establecer previamente una conexión TCP. El servidor escucha en el puerto 67 y el cliente utiliza el puerto 68.

---
---

# Resumen de comandos: hoja de memorización

Esta es probablemente la sección a la que debes dedicar más tiempo después de estudiar los conceptos. Te recomiendo aprender los comandos agrupados por su función, no como una lista aislada.

## **A. Comandos de red: Windows y Debian**

|Comando|Función|
|---|---|
|`ipconfig`|Consultar IP en Windows.|
|`ipconfig /all`|Consultar configuración detallada.|
|`ipconfig /release`|Liberar IP DHCP.|
|`ipconfig /renew`|Renovar IP DHCP.|
|`ifconfig`|Consultar interfaces en Linux.|
|`ip addr`|Consultar direcciones IP.|
|`ip link`|Consultar interfaces.|
|`ip route`|Consultar rutas.|
|`ping IP`|Comprobar conectividad.|
|`arp -a`|Consultar tabla ARP.|
|`arp -d *`|Borrar entradas ARP en Windows.|
|`route print`|Consultar rutas en Windows.|
|`tracert IP`|Rastrear ruta en Windows.|
|`traceroute IP`|Rastrear ruta en Linux.|

## **B. Comandos de Linux y administración**

|Comando|Función|
|---|---|
|`apt install paquete`|Instalar un paquete.|
|`nano archivo`|Editar un archivo desde terminal.|
|`sudo comando`|Ejecutar con privilegios elevados.|
|`ifconfig`|Consultar interfaces de red.|
|`tcpdump`|Capturar paquetes.|
|`gcc archivo.c -o programa`|Compilar un programa en C.|
|`./programa`|Ejecutar un programa.|

## **C. Comandos SSH**

|Comando|Función|
|---|---|
|`ssh usuario@IP`|Conectarse remotamente.|
|`ssh-keygen`|Generar claves.|
|`ssh-copy-id usuario@IP`|Copiar clave pública al servidor.|
|`ssh-add ~/.ssh/id_rsa`|Agregar clave al agente SSH.|
|`scp archivo usuario@IP:/ruta`|Copiar archivos remotamente.|
|`exit`|Cerrar sesión.|

## **D. Comandos Cisco**

|Comando|Función|
|---|---|
|`enable`|Modo privilegiado.|
|`configure terminal`|Configuración global.|
|`hostname R1`|Cambiar nombre.|
|`interface ...`|Seleccionar interfaz.|
|`ip address IP MÁSCARA`|Asignar dirección.|
|`no shutdown`|Activar interfaz.|
|`show running-config`|Consultar configuración activa.|
|`show ip route`|Consultar tabla de rutas.|
|`show ip interface brief`|Consultar estado de interfaces.|
|`ip route ...`|Configurar ruta estática.|
|`line vty 0 4`|Configurar acceso remoto.|

# Preguntas que debes poder contestar sin consultar el manual

##### **¿Cuál es la diferencia entre T568-A y T568-B?**
El orden de los conductores de los pares verde y naranja cambia.

##### **¿Qué configuración utiliza un cable cruzado?**
T568-A en un extremo y T568-B en el otro.

##### **¿Por qué están trenzados los conductores UTP?**
Para reducir interferencias electromagnéticas y diafonía.

##### **¿Qué diferencia existe entre UTP y STP?**
UTP no tiene blindaje metálico y STP sí.

##### **¿Qué norma regula el cableado estructurado?**
ANSI/TIA 568.

##### **¿Cuáles son los seis subsistemas del cableado estructurado?**
Horizontal, vertical, área de trabajo, cuarto de telecomunicaciones, cuarto de equipos y entrada de servicios.

##### **¿Cuál es la diferencia entre un equipo activo y uno pasivo?**
El activo procesa o regenera señales; el pasivo proporciona infraestructura de conexión.

##### **¿En qué capa OSI trabaja un hub?**
Capa 1.

##### **¿En qué capa OSI trabaja un switch tradicional?**
Capa 2.

##### **¿Qué es una colisión?**
La interferencia que ocurre cuando dos dispositivos transmiten simultáneamente en un medio compartido.

##### **¿Qué diferencia existe entre Half Duplex y Full Duplex?**
Half Duplex transmite o recibe alternativamente; Full Duplex realiza ambas acciones simultáneamente.

##### **¿Qué es una dirección MAC?**
Identificador de enlace asociado a una interfaz de red.

##### **¿Qué función tiene una máscara de red?**
Distingue la porción de red y la porción de host de una dirección IP.

##### **¿Qué función tiene DNS?**
Resolver nombres de dominio a direcciones IP.

##### **¿Qué función tiene DHCP?**
Asignar automáticamente parámetros de configuración IP.

##### **¿Qué hace el comando ipconfig /all?**
Muestra información detallada de la configuración de red de Windows.

##### **¿Qué hace ip addr?**
Muestra las direcciones IP de las interfaces de Linux.

##### **¿Qué protocolo utiliza ping?**
ICMP.

##### **¿Qué función tiene ARP?**
Resolver una dirección IPv4 a una dirección MAC en la red local.

##### **¿Qué hace arp -a?**
Muestra la tabla ARP.

##### **¿Qué función tiene Wireshark?**
Capturar y analizar paquetes de red.

##### **¿Qué diferencia existe entre encaminamiento estático y dinámico?**
El estático se configura manualmente y el dinámico aprende rutas mediante protocolos.

##### **¿Qué hace no shutdown en Cisco?**
Habilita administrativamente una interfaz.

##### **¿Qué es una ruta estática?**
Una ruta configurada manualmente por el administrador.

##### **¿Cuál es la diferencia entre TCP y UDP?**
TCP ofrece comunicación confiable y orientada a conexión; UDP no establece conexión ni garantiza entrega.

##### **¿Qué es un socket?**
Un punto de comunicación entre procesos, identificado mediante direcciones y puertos.

##### **¿Qué significan SYN, SYN-ACK y ACK?**
Los tres pasos del establecimiento de conexión TCP.

##### **¿Qué puerto utiliza SSH?**
TCP 22, por defecto.

##### **¿Cuál es la diferencia entre clave pública y privada?**
La pública se comparte; la privada se mantiene protegida por su propietario.

##### **¿Qué significan DORA y cuáles son sus pasos?**
Discover, Offer, Request y Acknowledge: el proceso de asignación DHCP.

##### Fin de cuestionario

1B, 2C, 3B, 4B, 5A, 6B, 7A, 8D, 9A, 10B, 11C, 12B, 13A, 14A, 15A, 16C, 17B, 18C, 19C, 20B, 21B, 22C, 23B, 24B, 25A, 26B, 27C, 28B, 29A, 30A

3C
15B
19A
23A
30C

---

**Comandos de Linux**
El comando `ip addr` permite consultar las direcciones IP de las interfaces de red.
No confundas estos comandos:

| Comando    | Función                                |
| ---------- | -------------------------------------- |
| `ip addr`  | Consultar direcciones IP e interfaces. |
| `ip link`  | Consultar información de interfaces.   |
| `ip route` | Consultar la tabla de rutas.           |
| `ping`     | Comprobar conectividad.                |

---

**Tabla de enrutamiento en Windows**
El comando `route print` muestra la tabla de rutas IP de Windows.
En cambio, `arp -a` muestra la tabla de correspondencias entre direcciones IP y MAC.

---

**Consulta de interfaces en Cisco**
El comando:
```
show ip interface brief
```
permite consultar rápidamente las interfaces, sus direcciones IP y su estado.

Por otro lado:
```
show running-config
```
muestra la configuración activa del router.

---

**Capa de presentación del modelo OSI**
La capa 6 se relaciona con la representación de los datos, incluyendo:

- Traducción de formatos.
- Compresión y descompresión.
- Cifrado y descifrado.

El enrutamiento de paquetes corresponde a la capa 3 (red).

---

1B, 2C, 3B, 4C, 5B, 6A, 7B, 8C, 9A, 10B, 11A, 12C, 13B, 14B, 15A, 16D, 17A, 18A, 19B, 20A, 21B, 22C, 23B, 24B, 25C, 26A, 27B, 28B, 29C, 30A

---

**Pregunta 5. Dirección 169.254.x.x**

**5.** En Debian se ejecuta:

```
ifconfig
```

El resultado muestra que la interfaz `enp0s3` tiene la dirección `169.254.10.25`. ¿Qué situación podría explicar esta dirección?

B) El equipo tiene configurada correctamente una dirección del servidor DHCP.

C) El equipo tiene una dirección de autoconfiguración local, posiblemente porque no obtuvo una asignación DHCP.

Tu respuesta: **B** · Correcta: **C**

Una dirección `169.254.x.x` pertenece al rango de direcciones link-local (APIPA). Windows puede autoconfigurarse con una dirección de este tipo cuando no consigue obtener una dirección mediante DHCP.

**Qué debes recordar:** si un cliente tiene una dirección `169.254.x.x`, investiga primero si puede comunicarse con el servidor DHCP.

---

**Pregunta 6. Renovación DHCP**

**6.** Un técnico necesita renovar la configuración IP de un cliente Windows porque sospecha que recibió parámetros incorrectos del servidor DHCP. ¿Qué secuencia debe ejecutar?

A)

```
ipconfig /renew
ipconfig /release
```

B)

```
ipconfig /release
ipconfig /renew
```

Tu respuesta: **A** · Correcta: **B**

La secuencia correcta es:

```
ipconfig /release
ipconfig /renew
```

- `/release`: libera la configuración DHCP actual.
    
- `/renew`: solicita una nueva configuración al servidor DHCP.

Invertir el orden no cumple el procedimiento solicitado.

---

**Pregunta 7. Selección de rutas**

**7.** Un router presenta la siguiente tabla de enrutamiento:

|Destino|Máscara|Siguiente salto|
|---|---|---|
|192.168.1.0|255.255.255.0|Directamente conectada|
|192.168.2.0|255.255.255.0|Directamente conectada|
|0.0.0.0|0.0.0.0|192.168.1.1|

Un paquete tiene como destino `192.168.2.50`. ¿Qué ruta debe utilizar el router?

B) La ruta `192.168.1.0/24`.

C) La ruta `192.168.2.0/24`.

Tu respuesta: **B** · Correcta: **C**

El destino es `192.168.2.50`. La tabla tiene una ruta directamente conectada:

`192.168.2.0/24`

Esa es la ruta que debe utilizarse porque incluye la dirección destino.

**Regla importante:** el router selecciona la ruta más específica que coincida con el destino (longest prefix match).

---

**Pregunta 9. Comando route print**

Incorrecta

Tu respuesta: **A** · Correcta: **B**

```
route print
```

Muestra la tabla de enrutamiento de Windows: rutas de red, destinos, máscaras, gateways e interfaces.

No muestra las asociaciones IP-MAC. Para eso se utiliza:

```
arp -a
```

**Pregunta 10. Resolución de direcciones**

Incorrecta

Tu respuesta: **B** · Correcta: **C**

El protocolo **ARP** permite resolver una dirección IPv4 a una dirección MAC dentro del segmento de red local.

Recuerda la diferencia:

|Protocolo|Función|
|---|---|
|ARP|IP → MAC|
|DNS|Nombre de dominio → IP|
|DHCP|Asignación de parámetros IP|
|ICMP|Mensajes de control y diagnóstico|

**Pregunta 16. show ip interface brief**

Incorrecta

Tu respuesta: **D** · Correcta: **C**

```
show ip interface brief
```

Presenta un resumen de las interfaces del router, sus direcciones IP y sus estados.

No muestra la tabla ARP.

Diferencia estos comandos:

|Comando|Información|
|---|---|
|`show ip interface brief`|Resumen de interfaces|
|`show running-config`|Configuración activa|
|`show ip route`|Tabla de enrutamiento|
|`show interface`|Detalles de una interfaz|

**Pregunta 18. Interfaz administratively down**

Incorrecta

Tu respuesta: **A** · Correcta: **B**

Si una interfaz aparece como `administratively down`, significa que está deshabilitada administrativamente.

Debes entrar al modo de configuración de interfaz y ejecutar:

```
Router(config)# interface FastEthernet 0/0
Router(config-if)# no shutdown
```

`no shutdown` habilita la interfaz. No debes confundirlo con `ip route`, que sirve para configurar rutas estáticas.