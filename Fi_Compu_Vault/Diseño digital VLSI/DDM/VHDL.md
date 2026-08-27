
- [[#Práctica 1]]
- [[#Práctica 12]]




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



---
---
# Práctica 12

## Diseño de un reloj digital 

#### Especificaciones 

- 4 displays
	- los dos primero son para las horas
	- los otros dos para los minutos
	
- Cuando llegue a 23 horas con 59 minutos, se volverá a empezar la cuanta 

```VHDL
library IEEE;
use IEEE.std_logic_1164.ALL;
use IEEE.std_logic_arith.ALL;
use IEEE.std_logic_unsigned.ALL;

entity relojdigital is

    Port (
        reloj : in std_logic;
        display1, display2, display3, display4 :
            out std_logic_vector(6 downto 0)
    );

end relojdigital;

architecture Behavioral of relojdijital is

    signal segundo, N, E, auxiliar, Z : STD_LOGIC;
    signal U, D, H1, H2 :
        std_logic_vector(3 downto 0) := "0000";
		  
Begin

    Divisor : process(reloj)

        variable cuenta : std_logic_vector(27 downto 0)
            := X"0000000";

    begin

        if rising_edge(reloj) then
            if cuenta = X"48009E0" then
                cuenta := X"0000000";

            else
                cuenta := cuenta + 1;

            end if;

        end if;
        segundo <= cuenta(22);

    end process;

    Unidades : process(segundo)

        variable cuenta : std_logic_vector(3 downto 0)
            := "0000";

    begin

        if rising_edge(segundo) then
            if cuenta = "1001" then
                cuenta := "0000";
                N <= '1';

            else
                cuenta := cuenta + 1;
                N <= '0';

            end if;

        end if;
        U <= cuenta;

    end process;

    Decenas : process(N)

        variable cuenta : std_logic_vector(3 downto 0)
            := "0000";

    begin
        if rising_edge(N) then
            if cuenta = "0101" then
                cuenta := "0000";
                E <= '1';

            else
                cuenta := cuenta + 1;
                E <= '0';
            end if;

        end if;
        D <= cuenta;

    end process;

    HU : process(E)

        variable cuenta : std_logic_vector(3 downto 0)
            := "0000";

    begin

        if rising_edge(E) then

            if cuenta = "1001" then
                cuenta := "0000";
                Z <= '1';
                AUX <= '0';

            elsif H1 = "0011" AND H2 = "0010" then
                cuenta := "0000";
                AUX <= '1';
                Z <= '1';

            else
                cuenta := cuenta + 1;
                Z <= '0';
                AUX <= '0';

            end if;

        end if;
        H1 <= cuenta;

    end process;

    HD : process(Z)

        variable cuenta : std_logic_vector(3 downto 0)
            := "0000";

    begin

        if rising_edge(Z) then
            if AUX = '1' then
                cuenta := "0000";

            else
                cuenta := cuenta + 1;

            end if;

        end if;
        H2 <= cuenta;

    end process;


    with U select
        display1 <=
            "1000000" when "0000", -- 0
            "1111001" when "0001", -- 1
            "0100100" when "0010", -- 2
            "0110000" when "0011", -- 3
            "0011001" when "0100", -- 4
            "0010010" when "0101", -- 5
            "0000010" when "0110", -- 6
            "1111000" when "0111", -- 7
            "0000000" when "1000", -- 8
            "0010000" when "1001", -- 9
            "1000000" when others; -- 0


    with D select
        display2 <=
            "1000000" when "0000", -- 0
            "1111001" when "0001", -- 1
            "0100100" when "0010", -- 2
            "0110000" when "0011", -- 3
            "0011001" when "0100", -- 4
            "0010010" when "0101", -- 5
            "0000010" when "0110", -- 6
            "1111000" when "0111", -- 7
            "0000000" when "1000", -- 8
            "0010000" when "1001", -- 9
            "1000000" when others; -- 0


    with H1 select
        display3 <=
            "1000000" when "0000", -- 0
            "1111001" when "0001", -- 1
            "0100100" when "0010", -- 2
            "0110000" when "0011", -- 3
            "0011001" when "0100", -- 4
            "0010010" when "0101", -- 5
            "0000010" when "0110", -- 6
            "1111000" when "0111", -- 7
            "0000000" when "1000", -- 8
            "0010000" when "1001", -- 9
            "1000000" when others; -- 0



    with H2 select
        display4 <=
            "1000000" when "0000", -- 0
            "1111001" when "0001", -- 1
            "0100100" when "0010", -- 2
            "0110000" when "0011", -- 3
            "0011001" when "0100", -- 4
            "0010010" when "0101", -- 5
            "0000010" when "0110", -- 6
            "1111000" when "0111", -- 7
            "0000000" when "1000", -- 8
            "0010000" when "1001", -- 9
            "1000000" when others; -- 0


end Behavioral;
```


### RELOJ DIGITAL

Displays de 7 segmentos.

Los displays representan:

- display1 -> Unidades de minutos
- display2 -> Decenas de minutos
- display3 -> Unidades de horas
- display4 -> Decenas de horas

La cuenta que se pretende obtener es:  `HH:MM` 

Por ejemplo: `12:37` 

El reloj debe avanzar:

--             00:00
--             00:01
--             ...
--             23:59
--             00:00


#### 1. LIBRERÍAS

```VHDL
library IEEE;

-- Permite utilizar std_logic y std_logic_vector.
use IEEE.std_logic_1164.ALL;

-- Permite realizar operaciones aritméticas con vectores.
use IEEE.std_logic_arith.ALL;

-- Permite realizar operaciones aritméticas y comparaciones
-- entre vectores std_logic_vector.
use IEEE.std_logic_unsigned.ALL;
```

#### 2. ENTIDAD

La entidad representa la interfaz externa del circuito.

Aquí se declaran las entradas y salidas que posteriormente
podrán asociarse con los pines físicos de la FPGA mediante el Pin Planner de Quartus.


```VHDL
entity relojdigital is

    Port (
        -- Entrada de reloj de la FPGA.
        -- Es la señal de reloj de alta frecuencia de la tarjeta.
        reloj : in std_logic;

        -- Salidas de los cuatro displays de 7 segmentos.
        --
        -- Cada display necesita 7 señales:
        --
        --       A
        --      ---
        --   F |   | B
        --      -G-
        --   E |   | C
        --      ---
        --       D
        --
        -- Por eso cada salida tiene 7 bits: (6 downto 0).

        display1, display2, display3, display4 :
            out std_logic_vector(6 downto 0)
    );

end relojdigital;


-- ================================================================
-- 3. ARQUITECTURA
-- ================================================================
-- Aquí se describe el funcionamiento interno del reloj digital.
-- ================================================================

architecture Behavioral of relojdijital is


    -- ============================================================
    -- 3.1 SEÑALES DE CONTROL
    -- ============================================================
    --
    -- segundo:
    --   Señal utilizada para generar el avance de las unidades.
    --
    -- N:
    --   Señal de acarreo de unidades hacia decenas.
    --
    --   Ejemplo:
    --
    --       09 -> 10
    --        ↑
    --        N
    --
    -- E:
    --   Señal de acarreo de los minutos hacia las horas.
    --
    --   Ejemplo:
    --
    --       12:59 -> 13:00
    --
    -- auxiliar:
    --   Señal auxiliar utilizada para controlar el reinicio
    --   de las horas cuando se llega a 23.
    --
    -- Z:
    --   Señal de acarreo entre las unidades y decenas de hora.
    --
    -- ============================================================

    signal segundo, N, E, auxiliar, Z : STD_LOGIC;


    -- ============================================================
    -- 3.2 REGISTROS DE LOS DÍGITOS
    -- ============================================================
    --
    -- Cada uno de estos registros almacena un dígito decimal
    -- utilizando 4 bits.
    --
    -- U  -> Unidades de minutos
    -- D  -> Decenas de minutos
    -- H1 -> Unidades de horas
    -- H2 -> Decenas de horas
    --
    -- Ejemplo para 23:45:
    --
    -- U  = 5
    -- D  = 4
    -- H1 = 3
    -- H2 = 2
    --
    -- Todos comienzan en 0000.
    -- ============================================================

    signal U, D, H1, H2 :
        std_logic_vector(3 downto 0) := "0000";


Begin


    -- ============================================================
    -- 4. DIVISOR DE FRECUENCIA
    -- ============================================================
    --
    -- La FPGA posee un reloj de alta frecuencia.
    --
    -- Este bloque utiliza un contador para dividir esa frecuencia
    -- y generar la señal "segundo", que posteriormente será
    -- utilizada para avanzar el contador del reloj.
    --
    -- La variable "cuenta" tiene 28 bits:
    --
    --     cuenta(27 downto 0)
    --
    -- Cada flanco de subida del reloj incrementa el contador.
    --
    -- Cuando llega al valor:
    --
    --     X"48009E0"
    --
    -- el contador vuelve a cero.
    --
    -- Finalmente:
    --
    --     segundo <= cuenta(22);
    --
    -- utiliza el bit 22 del contador como señal de avance.
    --
    -- ============================================================

    Divisor : process(reloj)

        variable cuenta : std_logic_vector(27 downto 0)
            := X"0000000";

    begin

        -- Detecta el flanco ascendente del reloj.
        if rising_edge(reloj) then

            -- Comprueba si el contador llegó al límite.
            if cuenta = X"48009E0" then

                -- Reinicia el contador.
                cuenta := X"0000000";

            else

                -- Incrementa el contador.
                cuenta := cuenta + 1;

            end if;

        end if;

        -- Utiliza el bit 22 del contador como señal de segundo.
        segundo <= cuenta(22);

    end process;


    -- ============================================================
    -- 5. CONTADOR DE UNIDADES DE MINUTOS
    -- ============================================================
    --
    -- Este bloque cuenta:
    --
    --     0 -> 1 -> 2 -> ... -> 8 -> 9 -> 0
    --
    -- Cada vez que llega al 9 y debe regresar a 0, genera
    -- un pulso en la señal N.
    --
    -- N funciona como señal de acarreo hacia el contador
    -- de decenas.
    --
    -- Ejemplo:
    --
    --     08
    --     09
    --     10
    --      ↑
    --      N provoca el incremento de las decenas.
    --
    -- ============================================================

    Unidades : process(segundo)

        variable cuenta : std_logic_vector(3 downto 0)
            := "0000";

    begin

        -- Avanza una unidad en cada flanco ascendente
        -- de la señal segundo.
        if rising_edge(segundo) then

            -- Si estamos en 9...
            if cuenta = "1001" then

                -- Regresamos a 0.
                cuenta := "0000";

                -- Generamos el acarreo hacia las decenas.
                N <= '1';

            else

                -- En cualquier otro caso incrementamos.
                cuenta := cuenta + 1;

                -- No hay acarreo.
                N <= '0';

            end if;

        end if;

        -- La variable cuenta se copia al registro U.
        U <= cuenta;

    end process;


    -- ============================================================
    -- 6. CONTADOR DE DECENAS DE MINUTOS
    -- ============================================================
    --
    -- Este contador cuenta:
    --
    --     0 -> 1 -> 2 -> 3 -> 4 -> 5 -> 0
    --
    -- Como los minutos solamente pueden llegar hasta 59,
    -- las decenas de minutos solamente necesitan llegar hasta 5.
    --
    -- Cuando llega a 5 y recibe otro acarreo desde las unidades,
    -- vuelve a cero y genera E.
    --
    -- E será el acarreo que permitirá incrementar las horas.
    --
    -- Ejemplo:
    --
    --     12:59
    --        ↓
    --     E = 1
    --        ↓
    --     13:00
    --
    -- ============================================================

    Decenas : process(N)

        variable cuenta : std_logic_vector(3 downto 0)
            := "0000";

    begin

        -- Se activa cuando aparece el flanco ascendente
        -- de la señal de acarreo N.
        if rising_edge(N) then

            -- Si las decenas están en 5...
            if cuenta = "0101" then

                -- Regresamos a cero.
                cuenta := "0000";

                -- Generamos acarreo hacia las horas.
                E <= '1';

            else

                -- Incrementamos las decenas.
                cuenta := cuenta + 1;

                -- No hay acarreo hacia las horas.
                E <= '0';

            end if;

        end if;

        -- Guardamos el valor en D.
        D <= cuenta;

    end process;


    -- ============================================================
    -- 7. CONTADOR DE UNIDADES DE HORAS
    -- ============================================================
    --
    -- Este bloque controla las unidades de las horas.
    --
    -- Normalmente cuenta:
    --
    --     0 -> 1 -> 2 -> ... -> 8 -> 9 -> 0
    --
    -- Sin embargo, existe una condición especial:
    --
    --     23 -> 00
    --
    -- Por eso se comprueba:
    --
    --     H1 = 3
    --     H2 = 2
    --
    -- que representa la hora 23.
    --
    -- Cuando se detecta 23, se reinician las unidades y se
    -- genera Z para provocar el cambio de las decenas de hora.
    --
    -- ============================================================

    HU : process(E)

        variable cuenta : std_logic_vector(3 downto 0)
            := "0000";

    begin

        -- Se activa cuando ocurre el acarreo E.
        if rising_edge(E) then

            -- Caso normal: las unidades llegaron a 9.
            if cuenta = "1001" then

                -- Regresamos a cero.
                cuenta := "0000";

                -- Generamos acarreo hacia las decenas de hora.
                Z <= '1';

                -- No se necesita reinicio especial.
                AUX <= '0';


            -- Caso especial: estamos en 23 horas.
            elsif H1 = "0011" AND H2 = "0010" then

                -- Regresamos las unidades a cero.
                cuenta := "0000";

                -- Activamos la señal auxiliar.
                AUX <= '1';

                -- Generamos acarreo hacia las decenas.
                Z <= '1';


            else

                -- Incrementamos las unidades de hora.
                cuenta := cuenta + 1;

                -- No hay acarreo.
                Z <= '0';

                -- No hay reinicio especial.
                AUX <= '0';

            end if;

        end if;

        -- Guardamos el valor en H1.
        H1 <= cuenta;

    end process;


    -- ============================================================
    -- 8. CONTADOR DE DECENAS DE HORAS
    -- ============================================================
    --
    -- Este bloque controla las decenas de las horas.
    --
    -- Normalmente se incrementa cuando H1 genera un acarreo.
    --
    -- La señal AUX permite detectar el caso especial:
    --
    --     23:59 -> 00:00
    --
    -- Cuando AUX = 1, las decenas de hora regresan a cero.
    --
    -- ============================================================

    HD : process(Z)

        variable cuenta : std_logic_vector(3 downto 0)
            := "0000";

    begin

        -- Se activa cuando aparece un flanco ascendente
        -- de Z.
        if rising_edge(Z) then

            -- Si se detectó el final del día...
            if AUX = '1' then

                -- Reiniciamos las decenas de hora.
                cuenta := "0000";

            else

                -- En caso normal, incrementamos.
                cuenta := cuenta + 1;

            end if;

        end if;

        -- Guardamos el valor en H2.
        H2 <= cuenta;

    end process;


    -- ============================================================
    -- 9. DECODIFICADOR DE UNIDADES DE MINUTOS
    -- ============================================================
    --
    -- Convierte el valor binario de U en las 7 señales necesarias
    -- para mostrar el número correspondiente en display1.
    --
    -- Por ejemplo:
    --
    --     U = 0000 -> muestra 0
    --     U = 0001 -> muestra 1
    --     U = 0010 -> muestra 2
    --     ...
    --     U = 1001 -> muestra 9
    --
    -- Los valores utilizados corresponden a un display de
    -- 7 segmentos activo en bajo.
    --
    -- ============================================================

    with U select
        display1 <=
            "1000000" when "0000", -- 0
            "1111001" when "0001", -- 1
            "0100100" when "0010", -- 2
            "0110000" when "0011", -- 3
            "0011001" when "0100", -- 4
            "0010010" when "0101", -- 5
            "0000010" when "0110", -- 6
            "1111000" when "0111", -- 7
            "0000000" when "1000", -- 8
            "0010000" when "1001", -- 9
            "1000000" when others; -- 0


    -- ============================================================
    -- 10. DECODIFICADOR DE DECENAS DE MINUTOS
    -- ============================================================
    --
    -- Convierte D en las señales de los segmentos de display2.
    --
    -- D solamente utiliza los valores 0 a 5.
    --
    -- ============================================================

    with D select
        display2 <=
            "1000000" when "0000", -- 0
            "1111001" when "0001", -- 1
            "0100100" when "0010", -- 2
            "0110000" when "0011", -- 3
            "0011001" when "0100", -- 4
            "0010010" when "0101", -- 5
            "0000010" when "0110", -- 6
            "1111000" when "0111", -- 7
            "0000000" when "1000", -- 8
            "0010000" when "1001", -- 9
            "1000000" when others; -- 0


    -- ============================================================
    -- 11. DECODIFICADOR DE UNIDADES DE HORAS
    -- ============================================================
    --
    -- Convierte H1 en las señales de los segmentos de display3.
    --
    -- ============================================================

    with H1 select
        display3 <=
            "1000000" when "0000", -- 0
            "1111001" when "0001", -- 1
            "0100100" when "0010", -- 2
            "0110000" when "0011", -- 3
            "0011001" when "0100", -- 4
            "0010010" when "0101", -- 5
            "0000010" when "0110", -- 6
            "1111000" when "0111", -- 7
            "0000000" when "1000", -- 8
            "0010000" when "1001", -- 9
            "1000000" when others; -- 0


    -- ============================================================
    -- 12. DECODIFICADOR DE DECENAS DE HORAS
    -- ============================================================
    --
    -- Convierte H2 en las señales de los segmentos de display4.
    --
    -- Como se trata de un reloj de 24 horas, H2 solamente debe
    -- utilizar los valores 0, 1 y 2.
    --
    -- ============================================================

    with H2 select
        display4 <=
            "1000000" when "0000", -- 0
            "1111001" when "0001", -- 1
            "0100100" when "0010", -- 2
            "0110000" when "0011", -- 3
            "0011001" when "0100", -- 4
            "0010010" when "0101", -- 5
            "0000010" when "0110", -- 6
            "1111000" when "0111", -- 7
            "0000000" when "1000", -- 8
            "0010000" when "1001", -- 9
            "1000000" when others; -- 0


end Behavioral;
```







