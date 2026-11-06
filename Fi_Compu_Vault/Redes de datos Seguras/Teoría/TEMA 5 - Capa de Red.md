
La **capa 3 (Red)** del **Modelo OSI** es la encargada de **direccionar y enrutar los datos entre diferentes redes**, permitiendo que la información viaje desde el origen hasta el destino aunque ambos dispositivos estén en redes distintas.

**Funciones principales de la capa de red**
1. Direccionamiento lógico
2. Enrutamiento
3. Encapsulación
4. Fragmentación y reensamblado

**Dispositivos que trabajan en la capa 3**
- Routers
- Switches de capa 3 (multicapa)
- Firewalls con capacidades de enrutamiento

**Protocolos asociados**
- IP (Internet Protocol)
- ICMP (usado por comandos como `ping`)
- IPsec (seguridad a nivel de red)
- OSPF, RIP, EIGRP, BGP (protocolos de enrutamiento)


---
---


## 1 Protocolos del nivel de red

##### ICMP (Internet Control Message Protocol)

Protocolo utilizado para enviar mensajes de control y diagnóstico entre dispositivos de red. Se emplea en herramientas como **ping** y **traceroute** para comprobar conectividad y detectar fallos.

Permite diagnosticar problemas de red, verificar la disponibilidad de equipos y analizar rutas de comunicación.

---

##### ARP (Address Resolution Protocol)

Permite relacionar una dirección IP con una dirección física MAC dentro de una red local. Es fundamental para que los dispositivos puedan comunicarse en redes Ethernet.

Ayuda a comprender cómo se produce la comunicación real entre equipos y a detectar problemas de conectividad local o ataques de suplantación (ARP Spoofing).

---

##### DHCP (Dynamic Host Configuration Protocol)

Protocolo encargado de asignar automáticamente direcciones IP y otros parámetros de red a los dispositivos.

Simplifica la administración de redes y es esencial para configurar y mantener infraestructuras de comunicación eficientes.

---

#### Funciones principales de la capa de red

La **Capa de Red** proporciona direccionamiento lógico mediante direcciones IP y permite transportar paquetes entre redes diferentes.

###### Direccionamiento lógico

Identifica de forma única a los dispositivos mediante direcciones IP.

**Importancia:** Permite diseñar, administrar y segmentar redes correctamente.

---

##### Enrutamiento

Determina la mejor ruta para que los paquetes lleguen a su destino.

**Importancia:** Es la base del funcionamiento de Internet y de las redes corporativas.

---

##### Reenvío de paquetes

Consiste en enviar los paquetes hacia el siguiente salto de la ruta seleccionada.

**Importancia:** Garantiza que la información avance de manera eficiente por la red.

---

##### Control y diagnóstico

Permite detectar errores y monitorear el estado de la comunicación mediante protocolos como ICMP.

**Importancia:** Facilita la solución de problemas y el mantenimiento de servicios.

---

##### Servicio IP

Proporciona el mecanismo básico para transportar paquetes entre dispositivos sin garantizar la entrega.

**Importancia:** Es el protocolo fundamental sobre el que funcionan la mayoría de los servicios de Internet.

---

#### Protocolos de Enrutamiento

##### BGP (Border Gateway Protocol)

Protocolo utilizado para intercambiar información de rutas entre sistemas autónomos en Internet.

Es el protocolo que permite la interconexión global de Internet y es fundamental en grandes redes y proveedores de servicios.

---

##### IGP (Interior Gateway Protocol)

Conjunto de protocolos utilizados para intercambiar rutas dentro de una misma organización o sistema autónomo. Ejemplos: RIP, OSPF y EIGRP.

Son los protocolos más utilizados en redes empresariales para optimizar la comunicación interna.

---

#### IPX (Internetwork Packet Exchange)

Protocolo desarrollado por Novell para el intercambio de paquetes entre redes. Fue ampliamente utilizado antes de la popularización de TCP/IP.

Forma parte de la evolución histórica de las redes y ayuda a comprender el desarrollo de los protocolos modernos.

---

#### DLS / DLSw (Data Link Switching)

Tecnología diseñada para transportar protocolos de capa de enlace a través de redes IP, permitiendo conectar redes locales remotas como si estuvieran directamente conectadas.

Muestra cómo se integraron tecnologías heredadas con infraestructuras modernas basadas en IP.

##### Funcionamiento

1. Captura las tramas de capa 2.
2. Las encapsula dentro de paquetes IP.
3. Las transporta a través de la red.
4. Las desencapsula en el destino para su procesamiento.

**Importancia:** Permitió la interoperabilidad entre sistemas antiguos y redes modernas, facilitando migraciones tecnológicas.


---
---


## 2 Redes y Subredes

#### Estructura de una dirección IPv4

Una dirección IPv4 está formada por **32 bits** divididos en cuatro octetos (ejemplo: 192.168.1.10). Se compone de una parte que identifica la **red** y otra que identifica al **host**.

Es la base para comprender cómo se identifican y comunican los dispositivos dentro de una red.

---

#### IPv4 e IPv6

##### IPv4

Protocolo de direccionamiento de 32 bits que permite aproximadamente 4.3 mil millones de direcciones únicas.

##### IPv6

Protocolo de direccionamiento de 128 bits diseñado para solucionar el agotamiento de direcciones IPv4 y mejorar la escalabilidad de Internet.

Las redes modernas utilizan ambos protocolos y es necesario administrarlos y configurarlos correctamente.

---

#### Subnetting

Es la técnica utilizada para dividir una red en varias subredes más pequeñas y manejables.

Permite optimizar recursos, mejorar la seguridad y facilitar la administración de redes.

##### Reducción del tráfico de broadcast

Al segmentar una red, los mensajes broadcast solo afectan a los dispositivos de la misma subred.

**Importancia:** Mejora el rendimiento y disminuye la congestión de la red.

##### Máscara de subred

Indica qué parte de una dirección IP corresponde a la red y cuál al host.

**Importancia:** Es indispensable para crear y administrar subredes.

##### División de la red

Consiste en separar una red grande en varios segmentos lógicos.

**Importancia:** Facilita el crecimiento ordenado y seguro de la infraestructura.

---

#### Fundamentos de Direccionamiento IP y Enrutamiento

##### VLSM (Variable Length Subnet Mask)

Permite utilizar máscaras de diferentes tamaños dentro de una misma red.

Optimiza el uso de direcciones IP y se adapta mejor a las necesidades reales de cada segmento.

##### CIDR (Classless Inter-Domain Routing)

Sistema de direccionamiento que utiliza prefijos como /24, /26 o /30 para definir el tamaño de la red.

Es el método estándar utilizado actualmente para asignar redes y crear rutas eficientes.

---

### Clases de Direcciones IPv4

#### ¿Qué son?

Son una clasificación histórica que divide las direcciones IPv4 según el tamaño de la red.

#### ¿Cómo funcionan?

Cada clase reserva una cantidad distinta de bits para identificar la red y los hosts.

#### ¿Para qué sirven?

Aunque CIDR las reemplazó, siguen siendo útiles para comprender los fundamentos del direccionamiento IP.

#### ¿Cómo usarlas?

Principalmente como referencia académica y conceptual para el estudio de redes.

##### Clase A

- Rango: **1.0.0.0 - 126.255.255.255**
- Primer octeto: 1 a 126
- Diseñada para redes muy grandes.

##### Clase B

- Rango: **128.0.0.0 - 191.255.255.255**
- Primer octeto: 128 a 191
- Diseñada para redes medianas.

##### Clase C

- Rango: **192.0.0.0 - 223.255.255.255**
- Primer octeto: 192 a 223
- Diseñada para redes pequeñas.

##### Clase D

- Rango: **224.0.0.0 - 239.255.255.255**
- Utilizada para tráfico multicast.

##### Clase E

- Rango: **240.0.0.0 - 255.255.255.255**
- Reservada para investigación y uso experimental.

Muchos conceptos modernos de direccionamiento surgieron a partir de este modelo y aún aparecen en documentación técnica.

---

### Clasificación de Direcciones IP

#### Dirección de Red

Identifica una red específica y no puede asignarse a un dispositivo.

**Ejemplo:** 192.168.1.0/24

---

#### Dirección Host

Identifica un dispositivo dentro de una red.

**Ejemplo:** 192.168.1.25

---

#### Dirección Broadcast

Permite enviar información a todos los dispositivos de una subred simultáneamente.

**Ejemplo:** 192.168.1.255 para una red /24.

Son fundamentales para configurar correctamente una red y evitar errores de direccionamiento.

---

### Máscara de Subred y Prefijo CIDR

La máscara de subred define los bits pertenecientes a la red. El prefijo CIDR representa esta misma información de forma simplificada.

|Máscara|Prefijo|
|---|---|
|255.255.255.0|/24|
|255.255.255.128|/25|
|255.255.255.192|/26|
|255.255.255.224|/27|
Toda planificación y segmentación de redes se basa en máscaras y prefijos.

---

#### Variación del prefijo /24

Un prefijo **/24** proporciona 256 direcciones totales (254 hosts utilizables). Al aumentar el prefijo, se crean más subredes pero disminuye la cantidad de hosts disponibles.

|Prefijo|Hosts utilizables|
|---|---|
|/24|254|
|/25|126|
|/26|62|
|/27|30|
|/28|14|
|/29|6|
|/30|2|

Permite diseñar redes eficientes, evitando desperdiciar direcciones IP y adaptando cada segmento a sus necesidades reales.


---
---


## 3 Tablas de Ruteo

Las **tablas de ruteo** son estructuras de datos utilizadas por hosts y routers para determinar la mejor ruta que debe seguir un paquete hasta llegar a su destino.

Son fundamentales para entender cómo se comunican las redes, diagnosticar problemas de conectividad y diseñar infraestructuras eficientes.

---

#### Componentes de una Tabla de Ruteo

Una tabla de ruteo generalmente contiene:

- **Red de destino:** red a la que se desea llegar.
- **Máscara o prefijo CIDR:** define el tamaño de la red destino.
- **Gateway o siguiente salto:** dispositivo al que se enviará el paquete.
- **Interfaz de salida:** adaptador de red utilizado para transmitir el tráfico.
- **Métrica:** valor que ayuda a elegir la mejor ruta entre varias disponibles.

Estos elementos permiten que los dispositivos tomen decisiones correctas sobre el envío de datos.

---

#### Tabla de Enrutamiento de Host

Es la tabla utilizada por una computadora, servidor o dispositivo final para decidir cómo enviar sus paquetes.

##### Funcionamiento

- Si el destino está en la misma red, envía directamente al host.
- Si el destino está en otra red, envía el tráfico a la puerta de enlace predeterminada (gateway).

Muchos problemas de comunicación se originan en configuraciones incorrectas de rutas, máscaras o gateways.

---

#### Tabla de Enrutamiento de Router

Es la tabla utilizada por un router para interconectar múltiples redes y seleccionar la mejor ruta disponible.

##### Funcionamiento

- Puede contener rutas estáticas configuradas manualmente.
- Puede aprender rutas automáticamente mediante protocolos como OSPF, RIP o BGP.
- Selecciona la ruta con la mejor métrica disponible.

Permite comprender cómo funciona Internet y cómo se conectan las redes empresariales y de centros de datos.

---

### Hosts Multihomed o Multiconectados

Un **host multihomed** es un dispositivo que posee dos o más interfaces de red activas, cada una con su propia dirección IP.

##### Funcionamiento

- Puede estar conectado a varias redes simultáneamente.
- Puede utilizar rutas diferentes según la disponibilidad de conexiones.
- Puede ofrecer redundancia en caso de fallo de una interfaz.

##### Ejemplo

Un servidor con:

- Una interfaz conectada a la red interna.
- Una interfaz conectada a Internet.
- Una interfaz dedicada a respaldos o administración.

Los hosts multiconectados son comunes en servidores, centros de datos y sistemas críticos donde se requiere alta disponibilidad, balanceo de carga y tolerancia a fallos.


---
---


## 4 Protocolos de enrutamiento 

Los **protocolos de enrutamiento** permiten que routers y dispositivos determinen la mejor ruta para enviar paquetes entre diferentes redes.

Son la base de la comunicación entre redes y permiten diseñar infraestructuras escalables, eficientes y tolerantes a fallos.

---

#### Redes Directamente Conectadas

Son las redes a las que un router está conectado físicamente mediante una de sus interfaces.

##### Funcionamiento

El router conoce automáticamente estas redes cuando la interfaz está activa.

Constituyen la información básica sobre la cual se construyen todas las demás rutas.

---

#### Enrutamiento Estático

Consiste en configurar manualmente las rutas dentro de un router.

##### Características

- Fácil de implementar en redes pequeñas.
- No se actualiza automáticamente.
- Requiere intervención del administrador ante cambios.

Proporciona control total sobre las rutas y se utiliza ampliamente en redes empresariales y de seguridad.

---

#### Enrutamiento Dinámico

Utiliza protocolos que intercambian información entre routers para descubrir y actualizar rutas automáticamente.

##### Características

- Se adapta a cambios en la red.
- Reduce la administración manual.
- Escala mejor en redes grandes.

Es indispensable en infraestructuras modernas donde existen múltiples rutas y cambios constantes.

---

#### `show ip route`

Es un comando utilizado en dispositivos Cisco para visualizar la tabla de enrutamiento.

##### Información que muestra

- Redes conocidas.
- Tipo de ruta.
- Métricas.
- Próximo salto.
- Interfaz de salida.

Es una de las herramientas más utilizadas para diagnosticar problemas de conectividad y verificar rutas.

---

#### Algoritmos de Enrutamiento Estático

Los algoritmos de enrutamiento estático siguen rutas definidas manualmente por el administrador.

##### Ventajas

- Simplicidad.
- Bajo consumo de recursos.
- Mayor control.

##### Desventajas

- Poca flexibilidad.
- Mayor trabajo administrativo.

**Importancia:** Son ideales para redes pequeñas o rutas críticas que no deben modificarse automáticamente.

---

#### Algoritmos de Enrutamiento Dinámico

Permiten calcular automáticamente las mejores rutas utilizando información intercambiada entre routers.

##### Características

- Detectan cambios en la topología.
- Actualizan rutas automáticamente.
- Utilizan métricas para seleccionar caminos óptimos.

**Importancia:** Facilitan la administración de redes medianas y grandes.

---

### Clasificación según su Ámbito de Operación

#### IGP (Interior Gateway Protocol)

Protocolos utilizados dentro de un mismo Sistema Autónomo (AS).

##### Ejemplos

- RIP
- OSPF
- EIGRP
- IS-IS

Son los protocolos más comunes en redes empresariales y corporativas.

---

#### EGP (Exterior Gateway Protocol)

Protocolos utilizados para intercambiar rutas entre distintos Sistemas Autónomos.

##### Ejemplo principal

- BGP

**¿Por qué es importante?**  
Porque permiten la comunicación global de Internet.

---

#### AS (Autonomous System)

Conjunto de redes administradas por una misma organización bajo una política de enrutamiento común.

##### Ejemplos

- Un proveedor de Internet (ISP).
- Una universidad.
- Una gran empresa.

BGP utiliza los Sistemas Autónomos para organizar el enrutamiento a escala mundial.

---

### Principales Familias de Protocolos Dinámicos

#### RIP (Routing Information Protocol)

Protocolo sencillo que utiliza el número de saltos como métrica.

##### Ventaja

Fácil configuración.

##### Desventaja

Escala limitada.

**Importancia:** Es fundamental para comprender los conceptos básicos del enrutamiento dinámico.

---

#### OSPF (Open Shortest Path First)

Protocolo de estado de enlace que calcula la ruta más corta utilizando el algoritmo SPF.

##### Ventajas

- Rápida convergencia.
- Alta escalabilidad.

**Importancia:** Es uno de los protocolos más utilizados en redes empresariales.

---

#### EIGRP (Enhanced Interior Gateway Routing Protocol)

Protocolo avanzado desarrollado por Cisco que combina características de distintos métodos de enrutamiento.

##### Ventajas

- Convergencia rápida.
- Bajo consumo de ancho de banda.

**Importancia:** Es muy utilizado en entornos Cisco.

---

#### IS-IS (Intermediate System to Intermediate System)

Protocolo de estado de enlace ampliamente utilizado en proveedores de servicios y grandes operadores de red.

##### Ventajas

- Alta escalabilidad.
- Excelente rendimiento.

**Importancia:** Es común en infraestructuras de telecomunicaciones y grandes redes troncales.

---

#### BGP (Border Gateway Protocol)

Protocolo utilizado para intercambiar rutas entre Sistemas Autónomos.

##### Ventajas

- Escalabilidad global.
- Control detallado de políticas de enrutamiento.

**Importancia:** Es el protocolo que mantiene funcionando Internet.

---

### Selección de Rutas

Cuando existen varias rutas hacia un destino, los routers siguen un proceso de selección.

#### Longest Prefix Match

El router elige la ruta con el prefijo más específico.

##### Ejemplo

- 192.168.0.0/16
- 192.168.1.0/24

Para llegar a 192.168.1.50, se selecciona la ruta **/24** porque es más específica.

**¿Por qué es importante?**  
Porque es la primera regla utilizada para decidir qué ruta emplear.

---

#### Distancia Administrativa (AD)

Valor que indica la confiabilidad de una fuente de rutas.

##### Ejemplos

- Conectada directamente: 0
- Ruta estática: 1
- EIGRP: 90
- OSPF: 110
- RIP: 120

Cuanto menor sea el valor, más confiable es la ruta.

**¿Por qué es importante?**  
Porque permite elegir entre rutas aprendidas por distintos protocolos.

---

#### Métrica

Valor utilizado por un protocolo para determinar cuál de varias rutas es la mejor.

##### Ejemplos

- RIP: número de saltos.
- OSPF: costo.
- EIGRP: ancho de banda y retardo.
- BGP: atributos de política.

**¿Por qué es importante?**  
Porque influye directamente en el rendimiento y la eficiencia de la red.



---
---


## 5 Servicios orientados a conexión

Los **servicios orientados a conexión** son aquellos que requieren establecer una conexión lógica entre el emisor y el receptor antes de intercambiar datos. Durante toda la comunicación se mantiene un camino definido para garantizar una transferencia ordenada y confiable.

Permiten comprender cómo funcionan sistemas de comunicación que priorizan la confiabilidad, el control de errores y la calidad del servicio.

---

#### Fases de un Servicio Orientado a Conexión

##### 1. Establecimiento

Antes de transmitir datos, los dispositivos negocian y crean una conexión entre el origen y el destino.

**Importancia:** Garantiza que ambos extremos estén listos para comunicarse y acuerden los parámetros de la conexión.

---

##### 2. Transferencia

Una vez establecida la conexión, se intercambian los datos siguiendo la ruta previamente definida.

**Importancia:** Permite una comunicación ordenada, controlando aspectos como la secuencia de los datos y la detección de errores.

---

##### 3. Liberación

Cuando la transferencia finaliza, la conexión se cierra y los recursos utilizados son liberados.

**Importancia:** Evita el consumo innecesario de recursos de red y mantiene la eficiencia del sistema.

---

#### Ejemplos de Servicios Orientados a Conexión

##### X.25

Protocolo diseñado para comunicaciones confiables en redes de área amplia (WAN), incorporando control de errores y confirmación de recepción.

**Importancia:** Fue una de las primeras tecnologías que permitió comunicaciones de datos confiables a larga distancia.

---

##### ATM (Asynchronous Transfer Mode)

Tecnología que transmite información mediante celdas de tamaño fijo, ofreciendo velocidad y calidad de servicio para voz, video y datos.

**Importancia:** Introdujo conceptos avanzados de gestión del tráfico que influyeron en redes modernas.

---

#### Funcionamiento General de un Servicio Orientado a Conexión

##### Secuencia General

1. El emisor solicita una conexión.
2. El receptor acepta la conexión.
3. Se establece una ruta lógica entre ambos dispositivos.
4. Se transfieren los datos de forma ordenada.
5. La conexión se libera al finalizar la comunicación.

Permite entender cómo se garantiza la entrega confiable de información en muchas tecnologías de red.

---

#### Circuito Virtual

Es una conexión lógica que simula un enlace dedicado entre dos dispositivos, aunque físicamente los datos puedan atravesar múltiples equipos intermedios.

##### Características

- Ruta previamente establecida.
- Comunicación ordenada.
- Control de errores y flujo.
- Identificación única de la conexión.

El concepto de circuito virtual es la base de tecnologías de comunicación avanzadas y ayuda a comprender mecanismos utilizados para garantizar calidad y confiabilidad en la transmisión de datos.



---
---

## 6 Servicios no orientados a conexión

Los **servicios no orientados a conexión** permiten enviar datos sin establecer previamente una conexión entre el emisor y el receptor. Cada paquete se envía de forma independiente y puede seguir rutas diferentes para llegar a su destino.

Son la base del funcionamiento de Internet y de protocolos fundamentales como IP, utilizados en prácticamente todas las comunicaciones modernas.

---

#### Funcionamiento

En este modelo no existe una fase de establecimiento de conexión. El emisor simplemente envía los datos y la red se encarga de transportarlos hasta el destino.

##### Características principales

- No requiere conexión previa.
- Menor consumo de recursos.
- Mayor rapidez en la transmisión.
- No garantiza entrega, orden ni corrección de los datos.

**¿Por qué es importante?**  
Porque permite entender cómo se transmite la información en redes IP y por qué algunas aplicaciones necesitan mecanismos adicionales de control.

---

#### Best Effort

El término **Best Effort** (mejor esfuerzo) significa que la red intenta entregar los paquetes al destino, pero no ofrece garantías sobre:

- Entrega de los datos.
- Tiempo de llegada.
- Orden de recepción.
- Disponibilidad de la ruta.

Si ocurre congestión o fallos en la red, algunos paquetes pueden perderse.

Explica el comportamiento de Internet y ayuda a diseñar aplicaciones capaces de manejar pérdidas de datos, retrasos o variaciones en la comunicación.

---

#### Datagramas

Un **datagrama** es una unidad de información que contiene todos los datos necesarios para llegar a su destino, incluyendo las direcciones de origen y destino.

##### Características

- Se procesa de manera independiente.
- Puede seguir rutas diferentes a otros datagramas de la misma comunicación.
- Puede llegar fuera de orden o no llegar.

##### Ejemplo

El protocolo **IP** transmite la información mediante datagramas IP, que son encaminados de forma independiente por los routers de la red.

Los datagramas son la unidad fundamental de comunicación en Internet y permiten comprender cómo funcionan el enrutamiento, la transmisión de datos y la tolerancia a fallos.



---
---


## 7 Ruteadores (Routers)




---
---


## 8 Seguridad a nivel de capa de red




---
---



