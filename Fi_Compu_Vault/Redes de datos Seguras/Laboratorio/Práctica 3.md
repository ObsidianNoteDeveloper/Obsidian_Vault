
# Previo

### 1. ¿Cuáles son los medios para canalizaciones admitidos por el estándar ANSI/EIA/TIA 569?

El estándar **ANSI/EIA/TIA-569** establece recomendaciones para los espacios y canalizaciones que se utilizan en instalaciones de telecomunicaciones. Entre los principales medios de canalización se encuentran las **tuberías o conduits, charolas o bandejas portacables, escalerillas, canaletas, ductos y sistemas de distribución bajo piso o sobre techo**. Estos medios tienen como finalidad proteger y organizar los cables, además de facilitar su instalación, mantenimiento y posible ampliación de la red.

### 2. ¿Qué es una escalerilla por techo? Indique sus características y objetivos.

Una **escalerilla por techo** es una estructura metálica, normalmente formada por dos soportes laterales unidos mediante travesaños, que se instala en la parte superior de un edificio para transportar y organizar cables. Su apariencia es similar a una escalera, pero está diseñada para soportar cables de telecomunicaciones y energía. Entre sus principales características se encuentran que permite colocar una gran cantidad de cables, facilita el acceso para realizar mantenimiento y permite agregar o retirar cables con relativa facilidad. Su principal objetivo es mantener los cables organizados, evitar que estén sueltos y proporcionar una ruta segura para distribuirlos por el edificio.

### 3. ¿Qué componentes se encuentran en un cuarto de telecomunicaciones?

En un **cuarto de telecomunicaciones** se encuentran los elementos necesarios para concentrar, organizar y distribuir las conexiones de una red. Entre ellos podemos encontrar **racks, paneles de parcheo (patch panels), switches, routers, organizadores de cables, gabinetes, sistemas de alimentación eléctrica, UPS, equipos de conexión a tierra y diferentes tipos de cableado**. También pueden encontrarse servidores y otros equipos dependiendo del tamaño y las necesidades de la instalación. Este espacio funciona como un punto central donde se conectan y administran diferentes partes del sistema de cableado.

### 4. ¿Qué topología usa un sistema de cableado estructurado?

Un sistema de **cableado estructurado utiliza principalmente una topología en estrella**. Esto significa que los diferentes puntos de red de un edificio se conectan mediante cables hacia un punto central, normalmente ubicado en un cuarto de telecomunicaciones. Desde este punto se distribuyen las conexiones hacia las diferentes áreas o usuarios. Esta topología facilita la administración y el mantenimiento de la red, ya que si un cable presenta una falla, normalmente solamente se afecta el dispositivo conectado a ese cable y no toda la red.

### 5. ¿Cuáles son las características principales de los 6 subsistemas del cableado estructurado?

Los seis subsistemas del cableado estructurado son **entrada de servicios, cuarto de equipos, cableado troncal, cuarto de telecomunicaciones, cableado horizontal y área de trabajo**. La **entrada de servicios** es el punto donde los servicios externos de telecomunicaciones ingresan al edificio. El **cuarto de equipos** contiene los equipos principales que proporcionan los servicios de comunicación. El **cableado troncal o backbone** conecta los diferentes cuartos de telecomunicaciones y equipos del edificio, normalmente mediante cables de mayor capacidad. El **cuarto de telecomunicaciones** concentra y organiza las conexiones de una determinada zona o piso. El **cableado horizontal** conecta el cuarto de telecomunicaciones con las áreas de trabajo de un mismo piso. Finalmente, el **área de trabajo** es el lugar donde se encuentran los usuarios y dispositivos finales, como computadoras, teléfonos IP o impresoras.

### 6. Realice un dibujo donde identifique claramente los 6 subsistemas del cableado estructurado.

Puedes realizar el dibujo de manera sencilla siguiendo esta estructura:

```
                    ┌───────────────────────────┐
                    │  1. ENTRADA DE SERVICIOS  │
                    │   Internet / Telefonía    │
                    └─────────────┬─────────────┘
                                  │
                                  ▼
                    ┌───────────────────────────┐
                    │    2. CUARTO DE EQUIPOS   │
                    │   Routers / Servidores    │
                    └─────────────┬─────────────┘
                                  │
                         3. CABLEADO TRONCAL
                                  │
              ┌───────────────────┴───────────────────┐
              │                                       │
              ▼                                       ▼
   ┌──────────────────────┐              ┌──────────────────────┐
   │ 4. CUARTO DE         │              │ 4. CUARTO DE         │
   │    TELECOMUNICACIONES│              │    TELECOMUNICACIONES│
   └──────────┬───────────┘              └──────────┬───────────┘
              │                                     │
       5. CABLEADO HORIZONTAL               5. CABLEADO HORIZONTAL
              │                                     │
              ▼                                     ▼
   ┌──────────────────────┐              ┌──────────────────────┐
   │ 6. ÁREA DE TRABAJO   │              │ 6. ÁREA DE TRABAJO   │
   │ PC / Teléfono / etc. │              │ PC / Teléfono / etc. │
   └──────────────────────┘              └──────────────────────┘
```

Este esquema representa cómo los seis subsistemas se relacionan entre sí, desde el punto donde ingresan los servicios al edificio hasta llegar finalmente a los dispositivos de los usuarios.

### 7. ¿Qué es un equipo activo? Liste ejemplos.

Un **equipo activo** es un dispositivo de red que necesita energía eléctrica para funcionar y que participa directamente en el procesamiento, transmisión, distribución o control de los datos. Estos equipos pueden recibir información, procesarla y enviarla hacia otros dispositivos de la red. Algunos ejemplos son los **switches, routers, puntos de acceso inalámbricos (Access Points), módems, firewalls, servidores y repetidores**.

### 8. ¿Qué es un equipo pasivo? Liste ejemplos.

Un **equipo pasivo** es un componente que forma parte de la infraestructura de red, pero que normalmente no necesita alimentación eléctrica para realizar su función. Su objetivo principal es permitir la conexión, organización, protección y distribución del cableado. Algunos ejemplos son los **cables UTP, STP y de fibra óptica, patch panels, jacks RJ-45, conectores, rosetas, placas de pared, racks, canaletas, charolas y organizadores de cables**.

### 9. ¿Qué tipos de canaletas existen? Realice una tabla indicando tipo, características y costos.

Las **canaletas** son elementos utilizados para proteger y organizar cables, especialmente cuando estos deben instalarse sobre paredes, pisos o techos. Existen diferentes tipos dependiendo de su forma, material, capacidad y lugar de instalación. Los costos pueden variar considerablemente dependiendo del tamaño, marca y material, por lo que los siguientes valores deben considerarse **aproximados**.

|Tipo de canaleta|Características|Costo aproximado|
|---|---|---|
|**Canaleta PVC sencilla**|Ligera, económica y fácil de instalar. Se utiliza principalmente para cables UTP y pequeñas instalaciones.|$30–$80 MXN/m|
|**Canaleta con división**|Cuenta con separaciones internas para organizar diferentes tipos de cables y evitar interferencias.|$50–$120 MXN/m|
|**Canaleta tipo zócalo**|Se instala en la parte inferior de las paredes y puede utilizarse para ocultar cables de red y otros servicios.|$80–$180 MXN/m|
|**Canaleta metálica**|Fabricada generalmente de acero o aluminio. Es más resistente y adecuada para instalaciones industriales.|$150–$400 MXN/m|
|**Canaleta de piso**|Diseñada para proteger cables que deben pasar sobre el suelo y evitar que las personas tropiecen con ellos.|$100–$250 MXN/m|
|**Canaleta para esquinas**|Diseñada para realizar cambios de dirección y mantener una instalación más limpia y ordenada.|$50–$150 MXN/m|

### 10. Investigue cuál es la fórmula que permite calcular la cantidad de cables que puede albergar una canaleta.

Para calcular aproximadamente cuántos cables pueden colocarse dentro de una canaleta se puede utilizar la relación entre el **área disponible de la canaleta y el área que ocupa cada cable**, considerando además el porcentaje máximo de llenado permitido. La fórmula básica puede expresarse como: **Cantidad de cables = Área útil de la canaleta ÷ Área del cable**. Si se considera un porcentaje de ocupación máximo, se utiliza: **Cantidad de cables = (Área de la canaleta × porcentaje de llenado permitido) ÷ Área del cable**. Por ejemplo, si una canaleta tiene un área interna de 600 mm², se permite utilizar el 40 % de su capacidad y cada cable ocupa aproximadamente 25 mm², se tendría: (600 × 0.40) ÷ 25 = **9.6**, por lo que podrían colocarse aproximadamente **9 cables**. En una instalación real también deben considerarse las especificaciones del fabricante y los requisitos del estándar correspondiente.

### 11. ¿A qué se hace referencia cuando se menciona la regla 5-4-3?

La **regla 5-4-3** es una regla utilizada históricamente en redes Ethernet basadas en **10BASE5 y 10BASE2**, especialmente cuando se utilizaban repetidores y segmentos de cable coaxial. La regla indicaba que podía haber como máximo **5 segmentos de red conectados mediante 4 repetidores, pero solamente 3 de esos segmentos podían tener dispositivos conectados**. Su objetivo era limitar el tamaño de la red y evitar que los retardos de transmisión provocaran problemas de comunicación. Actualmente esta regla ya no se aplica de la misma manera a las redes Ethernet modernas, pero es importante conocerla porque forma parte de la evolución y los fundamentos de las redes de computadoras.