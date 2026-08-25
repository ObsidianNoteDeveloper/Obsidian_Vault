
- [[#Práctica 1]]
- 



# Qué es VHDL

**VHDL** es un **lenguaje de descripción de hardware** (_VHSIC Hardware Description Language_). Se utiliza para **describir circuitos electrónicos digitales**, especialmente circuitos que posteriormente pueden implementarse en una **FPGA** o convertirse en un circuito integrado (ASIC).

> [!Note] 
> La idea importante es que **VHDL no es como C++, Python o Java**. En esos lenguajes describes principalmente una serie de instrucciones que ejecutará un procesador. En VHDL describes **cómo debe comportarse y/o estar conectado un circuito de hardware**.


# Qué es una FPGA

Una **FPGA** (_Field-Programmable Gate Array_, o **matriz de compuertas programables en campo**) es un **circuito integrado que puedes configurar para que se comporte como un circuito digital personalizado**.

La idea más importante es esta:

> **Una FPGA no ejecuta un programa como una CPU; se configura para convertirse en un circuito.**

###### Mi FPGA

MAX 10: 10M50DAF484C7G


## FPGA vs CPU

Esta diferencia es **muy importante**:

|CPU|FPGA|
|---|---|
|Ejecuta instrucciones|Implementa circuitos|
|Tiene una arquitectura fija|Puedes configurar su arquitectura|
|C, C++, Python, Java, etc.|VHDL, Verilog, SystemVerilog|
|Operaciones principalmente secuenciales|Puede realizar muchas operaciones en paralelo|
|El hardware ya está diseñado|El hardware lógico puede ser reconfigurado|
|Ejemplo: Intel Core|Ejemplo: Intel MAX 10|

# Práctica 1

### Los operadores VHDL y las compurtas lógicas

**Código completo**

```VHDL
library IEEE;

use IEEE.std_logic_1164.ALL;
use IEEE.std_logic_arith.ALL;
use IEEE.std_logic_unsigned.ALL;

entity alarma is
	port(	E:in std_logic;
			p:in std_logic;
			c:in std_logic;
			a:out std_logic);
end alarma;

architecture Behavioral of alarma is
begin
	A<=E and P and not C;
end Behavioral;
```

Podemos dividirlo conceptualmente en **cuatro partes**:

| Parte          | Función                                    |
| -------------- | ------------------------------------------ |
| `library`      | Indica bibliotecas que utilizaremos        |
| `use`          | Importa elementos de esas bibliotecas      |
| `entity`       | Define las entradas y salidas del circuito |
| `architecture` | Define cómo funciona internamente          |

`IEEE` es una biblioteca ampliamente utilizada en VHDL.

IEEE significa:

> **Institute of Electrical and Electronics Engineers**

Dentro de esta biblioteca existen diferentes paquetes con tipos, funciones y operaciones útiles para describir hardware.

```VHDL
library IEEE; 
use IEEE.std_logic_1164.ALL;
```

### ¿Qué es `std_logic`?

Esta parte es **muy importante**. Podrías pensar inicialmente que:

```VHDL
std_logic
```

es equivalente a un `boolean` de otros lenguajes. Pero realmente es más interesante. Un `boolean` normalmente tiene:

```VHDL
TRUE
FALSE
```

Mientras que `std_logic` puede representar diferentes estados eléctricos/lógicos. Entre ellos están:

| Valor | Significado aproximado |
| ----- | ---------------------- |
| `'0'` | 0 lógico               |
| `'1'` | 1 lógico               |
| `'U'` | No inicializado        |
| `'X'` | Valor desconocido      |
| `'Z'` | Alta impedancia        |
| `'W'` | Desconocido débil      |
| `'L'` | 0 débil                |
| `'H'` | 1 débil                |
| `'-'` | Don't care             |

Para tu circuito, principalmente nos interesan:

```VHDL
'0'
'1'
```

Por ejemplo:

```VHDL
E : in std_logic;
```

significa:

> `E` es una señal de entrada capaz de representar un estado lógico.

### `entity alarma is`

Ahora comienza la descripción del circuito:

```VHDL
entity alarma is
```

`entity` significa que vamos a definir la **entidad del circuito**.

El nombre de la entidad es:

```VHDL
alarma
```

Aquí estamos diciendo:

> Voy a crear un componente de hardware llamado `alarma`.

### `port`

Después tenemos:

```VHDL
port(
```

El `port` define las conexiones que tiene nuestro circuito con el exterior. Puedes imaginarlo como los **pines de un circuito integrado**. Nuestro circuito tiene cuatro conexiones.

### Las entradas `E`, `P` y `C`

Tenemos:

```VHDL
E : in std_logic;
P : in std_logic;
C : in std_logic;
```

La estructura general es:

```
nombre : dirección tipo;
```

Por ejemplo:

```VHDL
E : in std_logic;
```

significa:

```
E
│
├── dirección: entrada
│
└── tipo: std_logic
```

`in` significa:

> Esta señal entra al circuito.

Por lo tanto:

```VHDL
E : in std_logic;
```

significa:

> `E` es una entrada de un bit.

Lo mismo ocurre con:

```VHDL
P : in std_logic;
C : in std_logic;
```

Tenemos entonces:

```
E ──► entrada
P ──► entrada
C ──► entrada
```

### La salida `A`

Tenemos:

```VHDL
A : out std_logic
```

Aquí:

```VHDL
out
```

significa:

> Esta señal sale del circuito.

Por tanto:

```
E ──►
P ──►   ALARMA   ──► A
C ──►
```

`A` es nuestra salida.

### `architecture Behavioral`

Esta parte es fundamental. Una entidad dice:

> "Tengo estas entradas y salidas."

La arquitectura dice:

> "Así es como funciona internamente."

Tenemos:

```VHDL
architecture Behavioral of alarma is
```

Podemos separarlo:

```
architecture
    │
    └── Behavioral
            │
            └── of alarma
```

Estamos creando una arquitectura llamada:

```VHDL
Behavioral
```

para la entidad:

```
alarma
```

### ¿Por qué "Behavioral"?

VHDL permite describir hardware de diferentes maneras.

Por ejemplo:

**Behavioral**

Describes **qué hace** el circuito:

```VHDL
A <= E and P and not C;
```

### `begin`

Después tenemos:

```VHDL
begin
```

Aquí comienza la parte donde escribimos las instrucciones que describen el comportamiento de la arquitectura.

### La línea más importante

Finalmente tenemos:

```
A <= E and P and not C;
```

Esta línea describe **todo el circuito**.

Vamos a analizarla.

Primero:

```VHDL
A <=
```

En VHDL:

```VHDL
<=
```

es el operador de **asignación de señal**.

Aquí estamos diciendo:

> La señal `A` toma el resultado de la expresión que está a la derecha.

Por lo tanto:

```VHDL
A <= ...
```

puede leerse como:

> "La salida A está determinada por..."

### Toda la expresión

Tenemos:

```VHDL
A <= E and P and not C;
```

Entonces:

```
A = E AND P AND NOT C
```

La alarma solamente se activa cuando:

```
E = 1
P = 1
C = 0
```


### Archivos generados por Quartus

En tu proyecto:

|Archivo/carpeta|¿Para qué sirve?|
|---|---|
|`alarma.qpf`|**Proyecto de Quartus.** Guarda información general del proyecto y qué archivos forman parte de él.|
|`alarma.qsf`|**Configuración del proyecto.** Aquí Quartus guarda asignaciones de pines, dispositivo FPGA, opciones de compilación, archivos fuente, etc.|
|`alarma.vhd`|⭐ **Tu código VHDL.** Este es el archivo que normalmente vas a escribir/modificar.|
|`alarma.vhd.bak`|Copia de respaldo (`backup`) del archivo VHDL.|
|`db/`|Base de datos interna que Quartus utiliza durante la compilación para almacenar información del diseño.|
|`incremental_db/`|Información utilizada para **compilación incremental**, permitiendo reutilizar partes que no cambiaron y acelerar compilaciones posteriores.|
|`output_files/`|⭐ **Resultados de la compilación.** Aquí pueden aparecer archivos generados por Quartus, como archivos de programación para cargar el diseño en la FPGA.|
|`simulation/`|Archivos relacionados con la **simulación** del diseño, dependiendo de cómo hayas configurado el proyecto.|

##### La idea importante

Puedes imaginar tu proyecto así:

```Text
DDM_Practica1/
│
├── alarma.vhd          ← TU DISEÑO
│
├── alarma.qpf          ← Proyecto Quartus
├── alarma.qsf          ← Configuración
│
├── db/                 ← Archivos internos
├── incremental_db/     ← Datos para compilación incremental
├── output_files/       ← Resultados de compilación
└── simulation/         ← Archivos de simulación
```

El flujo sería aproximadamente:

```Text
alarma.vhd
    │
    ▼
Quartus analiza tu VHDL
    │
    ▼
Síntesis
    │
    ▼
Optimización / asignación
    │
    ▼
Place & Route
    │
    ▼
Generación de archivos
    │
    ├──► output_files/
    ├──► db/
    └──► incremental_db/
```

Por eso **no debes pensar que cada archivo representa una parte del circuito**. Muchos son simplemente archivos auxiliares que Quartus necesita para administrar, compilar, optimizar y simular tu diseño.

Para tu práctica de `alarma`, los que principalmente te interesan son **`alarma.vhd`, `alarma.qpf` y `alarma.qsf`**. Los demás son generados y utilizados por Quartus.

Una forma sencilla de recordarlo:

> **`.vhd` = lo que tú diseñas**  
> **`.qpf` / `.qsf` = cómo Quartus organiza y configura el proyecto**  
> **`output_files/`, `db/`, `incremental_db/`, `simulation/` = lo que Quartus genera/utiliza durante el proceso**


### Proceso de compilación y ejecución en Quartus

![[Pasted image 20260814085912.png]]

![[Pasted image 20260814090053.png]]

![[Pasted image 20260814090130.png]]

![[Pasted image 20260814090811.png]]

![[Pasted image 20260814090851.png]]

![[Pasted image 20260814113946.png]]