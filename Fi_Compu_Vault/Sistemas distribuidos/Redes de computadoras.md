### 1. ¿Cuál es la diferencia entre una red LAN y MAN?

La principal diferencia es su **alcance geográfico**. Una **LAN (Local Area Network)** conecta múltiples usuarios dentro de una zona geográfica pequeña, generalmente de hasta **1 km**, y normalmente ofrece una comunicación de alta velocidad. Una **MAN (Metropolitan Area Network)** cubre una zona más extensa, aproximadamente de **1 a 10 km**, pudiendo conectar diferentes redes LAN dentro de una misma ciudad o área metropolitana.

### 2. ¿Cuál es la función del protocolo IEEE 802.11?

El **IEEE 802.11** establece las especificaciones para las **redes inalámbricas**, es decir, define características y mecanismos utilizados para permitir la comunicación de dispositivos mediante conexiones inalámbricas. Dentro de la familia IEEE 802, el documento identifica específicamente al 802.11 como el estándar para redes inalámbricas.

### 3. ¿Qué ventajas tiene usar celdas en comparación con usar paquetes en la comunicación de datos?

Las **celdas** son unidades de información de **longitud fija**, mientras que los paquetes pueden tener tamaños variables. En ATM, por ejemplo, una celda tiene **53 bytes: 5 bytes de encabezado y 48 bytes de datos**.

La ventaja principal de utilizar celdas de tamaño fijo es que permiten realizar la **multiplexación y conmutación de manera más rápida y predecible**, reduciendo el procesamiento necesario en los equipos de red. Esto facilita conseguir **alta velocidad y bajo retardo**, características importantes para transportar diferentes tipos de tráfico, como voz, video y datos.

### 4. ¿En qué consiste el sistema GSM y cuáles son sus principales componentes?

El documento proporcionado **no desarrolla específicamente el sistema GSM ni enumera sus componentes**, por lo que esta respuesta requiere conocimiento complementario.

**GSM (Global System for Mobile Communications)** es un estándar de comunicación móvil utilizado para proporcionar servicios de telefonía y transmisión de datos mediante redes celulares.

Sus principales componentes son:

- **Estación móvil (MS):** teléfono o dispositivo utilizado por el usuario.
- **BTS (Base Transceiver Station):** proporciona la comunicación inalámbrica con los dispositivos móviles.
- **BSC (Base Station Controller):** controla varias estaciones base.
- **MSC (Mobile Switching Center):** realiza la conmutación y gestión de las comunicaciones.
- **HLR (Home Location Register):** almacena información de los usuarios registrados.
- **VLR (Visitor Location Register):** mantiene información temporal de los usuarios presentes en una determinada zona.
- **AuC (Authentication Center):** participa en la autenticación de los usuarios.
- **EIR (Equipment Identity Register):** mantiene información relacionada con los equipos móviles.

### 5. ¿Cuál es la similitud entre una topología en árbol y una de estrella?

Ambas utilizan una **estructura jerárquica basada en conexiones centrales**. En una topología de estrella, todas las computadoras se conectan a un dispositivo o computadora central. En una topología de árbol existe una computadora principal que funciona como **raíz**, a partir de la cual se organiza la red.

Por ello, ambas facilitan la **organización y administración de los dispositivos mediante puntos centrales de conexión**.

### 6. Investiga las características de los medios físicos de comunicación para redes de cómputo.

Los medios físicos son los elementos utilizados para transportar las señales que representan los datos. El documento los identifica como **medios de comunicación** y menciona como ejemplos las líneas telefónicas, líneas dedicadas y canales LAN.

Los principales medios físicos utilizados en redes son:

|Medio|Características principales|
|---|---|
|**Cable de par trenzado**|Está formado por pares de conductores de cobre trenzados. Es económico, sencillo de instalar y ampliamente utilizado en redes LAN.|
|**Cable coaxial**|Utiliza un conductor central rodeado por aislamiento y una malla conductora. Tiene buena protección contra interferencias y fue utilizado ampliamente en redes antiguas.|
|**Fibra óptica**|Transmite información mediante pulsos de luz. Ofrece gran capacidad de transmisión, largas distancias y alta resistencia a interferencias electromagnéticas.|
|**Radio / inalámbrico**|Utiliza ondas electromagnéticas para transmitir información sin necesidad de un cable físico. Permite movilidad, aunque puede verse afectado por interferencias y obstáculos.|
|**Microondas**|Utiliza ondas de radio de alta frecuencia y puede emplearse para enlaces inalámbricos de larga distancia.|
|**Satélite**|Utiliza satélites como estaciones de retransmisión. Permite cubrir grandes regiones geográficas, aunque presenta mayor retardo que muchos enlaces terrestres.|

### 7. ¿Qué esquemas de comunicación se utilizan para las redes satelitales?

El documento clasifica las redes de difusión como aquellas donde la comunicación se realiza desde un dispositivo hacia múltiples dispositivos y menciona específicamente las **señales de satélite, radio y televisión** como ejemplos.

En redes satelitales pueden utilizarse principalmente esquemas de comunicación **punto a punto** y **punto a multipunto o difusión (broadcast)**. En el segundo caso, una estación transmite información que puede ser recibida por múltiples estaciones terrestres.

### 8. En el modelo OSI, ¿cuál es la diferencia entre un protocolo y una interfaz?

Un **protocolo** es el conjunto de reglas que permite la comunicación entre entidades o procesos de una misma capa en diferentes computadoras. En el modelo OSI, la comunicación entre capas equivalentes se realiza mediante protocolos.

Una **interfaz**, en cambio, define la comunicación entre **capas diferentes dentro de una misma computadora**. Es decir:

**Protocolo → comunicación entre capas equivalentes de diferentes computadoras.**

**Interfaz → comunicación entre capas adyacentes dentro de una misma computadora.**

### 9. ¿Qué tipos de redes existen en la Internet?

Las redes pueden clasificarse de diferentes maneras. De acuerdo con el documento, existen:

**Según su servicio:**

- Redes públicas.
- Redes privadas.

**Según su funcionamiento:**

- Redes de conmutación.
- Redes de difusión (Broadcast).

**Según su extensión:**

- **LAN:** área local.
- **MAN:** área metropolitana.
- **WAN:** área amplia.

En particular, una **WAN** puede conectar usuarios a través de ciudades, países o continentes y puede utilizar líneas telefónicas, satélites y otras redes de comunicación.

### 10. ¿Cuál es la principal desventaja de una topología en anillo?

La principal desventaja es que la comunicación depende de la **continuidad del anillo**. Si uno de los enlaces o dispositivos falla y no existen mecanismos de redundancia, puede interrumpirse la comunicación de una parte importante o de toda la red.

El documento describe la topología en anillo como una red que forma un **anillo continuo por el cual puede viajar la información**.

### 11. ¿Qué beneficios aporta usar una topología de árbol en una red de difusión de contenidos?

Una topología de árbol permite organizar la distribución de información mediante una **estructura jerárquica**. Existe una computadora principal que funciona como raíz y proporciona una salida externa única.

En una red de difusión de contenidos, esta estructura permite distribuir la información desde un punto principal hacia diferentes ramas y posteriormente hacia los usuarios finales. Esto facilita la **organización, administración y distribución jerárquica de los contenidos**, además de permitir ampliar la red agregando nuevas ramas.

### 12. ¿Qué beneficios aporta usar una topología completa o de malla en una red de datos?

Una topología completa o de malla proporciona **múltiples conexiones entre los dispositivos**, por lo que existen diferentes caminos posibles para transportar la información.

Sus principales beneficios son:

- Mayor **redundancia**.
- Mayor **tolerancia a fallos**.
- Existencia de rutas alternativas.
- Mayor disponibilidad de la comunicación.
- Posibilidad de mantener la comunicación aunque falle alguno de los enlaces.

El documento identifica la **topología completa** como una de las topologías utilizadas en redes de computadoras.

La principal desventaja es que requiere una gran cantidad de conexiones, por lo que aumenta su **costo y complejidad** conforme crece el número de dispositivos.

---

## 13. Cálculo de la transmisión del archivo

**Datos:**

- Tamaño de cada paquete = **1,500 bytes**
- Velocidad del canal = **128,000 bit/s**
- Tiempo entre transmisiones = **90 μs**
- Tamaño del archivo = **5 MB**

### Paso 1. Convertir el tamaño del paquete a bits

Sabemos que: 1 byte=8 bits

Por lo tanto: 1500×8=12,000 bits

Cada paquete contiene **12,000 bits**.

### Paso 2. Calcular el tiempo de transmisión de un paquete

Tp=12,000/128,000
Tp=0.09375 s

Es decir: Tp=93.75 ms

### Paso 3. Calcular cuántos paquetes se necesitan

Tomando: 5 MB=5,000,000 bytes

Entonces:

N=5,000,000/1,500
N=3333.33N=3333.33

Como no podemos enviar una fracción de paquete, necesitamos: 3334 paquetes

### Paso 4. Calcular el tiempo de transmisión de los paquetes

T_trans=3334(0.09375)
T_trans=312.5625 s

### Paso 5. Considerar los 90 microsegundos entre transmisiones

Hay 3333 intervalos entre los 3334 paquetes:

T_espera=3333(90×10−6)
T_espera=0.29997 s

### Paso 6. Tiempo total

T_total=312.5625+0.29997
T_total≈312.86 segundos

En minutos: 312.86/60≈5.21 minutos

**Respuesta:**

> Se requieren aproximadamente **312.86 segundos**, es decir, aproximadamente **5 minutos con 13 segundos**, para transmitir el archivo de 5 MB bajo las condiciones indicadas.

El ejercicio se relaciona directamente con el concepto de **conmutación de paquetes**, donde los datos se dividen en fragmentos llamados paquetes para su transmisión por la red.