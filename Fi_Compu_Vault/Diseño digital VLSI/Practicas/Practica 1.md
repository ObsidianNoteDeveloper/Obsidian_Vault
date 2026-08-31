
## Índice



---

**VLSI**
- (**Very Large Scale Integration**, o _Integración a muy gran escala_ en español) es la tecnología que permite **combinar miles de millones de transistores en un solo chip de silicio** para crear un circuito integrado complejo

**VHDL**
- Es un lenguaje de programación especializado que se utiliza para **definir, simular y diseñar el comportamiento de los circuitos electrónicos digitales**, como los chips y microprocesadores.

# Introducción

El código describe el funcionamiento de un **reloj digital de formato HH:MM**. A partir de una señal de reloj (`clk`) proveniente de la FPGA, el circuito utiliza un [[#Divisor de frecuencia]] para generar una señal mucho más lenta que permite representar el paso de los segundos. Posteriormente, mediante varios contadores, se controlan las **unidades y decenas de los minutos**, así como las **unidades y decenas de las horas**.

Cada contador almacena un valor de 4 bits que representa un dígito decimal. Estos valores posteriormente se convierten en las señales necesarias para controlar los **cuatro displays de 7 segmentos**, permitiendo visualizar la hora actual. El circuito también incorpora [[#Señales de control]] (`n`, `e`, `z`, `u` y `d`) que permiten enlazar los diferentes contadores y realizar automáticamente los cambios de minuto y hora.

En términos generales, el funcionamiento puede entenderse de la siguiente manera:

`clk` **→ divisor de frecuencia → segundos → minutos → horas → displays**

Por lo tanto, el código implementa un **reloj digital mediante lógica secuencial**, donde los contadores avanzan automáticamente conforme transcurre el tiempo y los displays muestran el resultado en formato de cuatro dígitos.

```
┌─────┬─────┬─────┬─────┐
│     │     │     │     │
│  0  │  5  │  1  │  2  │
│     │     │     │     │
└─────┴─────┴─────┴─────┘
   ↑     ↑     ↑     ↑
  Qum   Qdm   Quh   Qdh

       12:50
```

| Concepto                  | Explicación sencilla                                 | En tu código                   |
| ------------------------- | ---------------------------------------------------- | ------------------------------ |
| **Divisor de frecuencia** | Hace más lenta una señal de reloj                    | `divisor`                      |
| **Contador**              | Va aumentando un número con cada pulso               | `cuenta`                       |
| **4 bits**                | Permiten representar valores de 0 a 15               | `std_logic_vector(3 downto 0)` |
| **Señal de control**      | Le indica a otra parte del circuito que ocurrió algo | `n`, `e`, `z`, `reset`         |
| **Bandera**               | Señal que indica que ocurrió una condición           | `n`, `e`, `z`                  |

#### Divisor de frecuencia 

Un **divisor de frecuencia** es un circuito que toma una señal que cambia **muy rápido** y genera otra señal que cambia **más lentamente**.

La FPGA tiene un reloj interno que puede trabajar a `50 MHz`, lo que significa `50,000,000 cambios por segundo`, utilizar un **divisor de frecuencia** hace que un reloj rápido genere una señal más lenta.

#### Señales de control 

Una señal de control es una señal que se utiliza para avisarle a otra parte del circuito que debe hacer algo.

# Estructura del código 

- Librerías 
- Entidad / Entradas y salidas
- Señales internas
- Divisor de frecuencia
- Contadores
- Reset automático
- Decodificación 7 segmentos 

## Librerías 

Las librerías contienen herramientas que VHDL necesita para trabajar con diferentes tipos de datos y operaciones.

Se incluyen las librerías de IEEE necesarias para trabajar con señales lógicas (`std_logic`), vectores de bits (`std_logic_vector`) y operaciones aritméticas utilizadas durante el funcionamiento del reloj digital.

```VHDL
library IEEE;

USE IEEE.STD_LOGIC_1164.ALL;
USE IEEE.STD_LOGIC_ARITH.ALL;
USE IEEE.STD_LOGIC_UNSIGNED.ALL;
```

## Entidad

La entidad `reloj` define las entradas y salidas del circuito. Nuestra entrada sera `clk`, una señal de reloj en la FPGA y las salidas serán cuatro `display`, cada una tendrá `std_logic_vector (6 downto 0)`, es decir, 7 bits, un bit para cada segmento del display.

```VHDL
entity reloj is

    port( clk: in std_logic;
            display1, display2, display3, display4:
            out std_logic_vector (6 downto 0)
         );

end reloj;
```

## Señales internas

Se declaran las señales utilizadas para almacenar los valores de los contadores de segundos, minutos y horas, así como las señales de control encargadas de indicar cuándo un contador debe reiniciarse o activar al siguiente contador.

```VHDL
architecture behavioral of reloj is

    signal segundo: std_logic;
    signal rapido : std_logic;
    signal Qs     : std_logic_vector (3 downto 0);
    signal Qum    : std_logic_vector (3 downto 0);
    signal Qdm    : std_logic_vector (3 downto 0);
    signal e      : std_logic;
    signal Qr     : std_logic_vector (1 downto 0);
    signal Quh    : std_logic_vector (3 downto 0);
    signal Qdh    : std_logic_vector (3 downto 0);
    signal n      : std_logic;
    signal z      : std_logic;
    signal u      : std_logic;
    signal d      : std_logic;
    signal reset  : std_logic;
``` 

|Señal|Función|
|---|---|
|`segundo`|Señal lenta utilizada para avanzar el contador|
|`Qum`|Unidades de minuto|
|`Qdm`|Decenas de minuto|
|`Quh`|Unidades de hora|
|`Qdh`|Decenas de hora|
|`n`|Bandera para pasar de unidades a decenas de minuto|
|`e`|Bandera para pasar de minutos a horas|
|`z`|Bandera para pasar de unidades a decenas de hora|
|`u`|Parte de control del límite de horas|
|`d`|Parte de control del límite de horas|
|`reset`|Reinicia las horas|

## Divisor de frecuencia 

Este bloque reduce la frecuencia de la señal `clk` proveniente de la FPGA mediante un contador de 28 bits. Al alcanzar un valor determinado, el contador vuelve a cero. Uno de sus bits se utiliza para generar la señal `segundo`, que posteriormente controla el avance de los contadores del reloj.

```VHDL
divisor: process(clk)

    variable cuenta: std_logic_vector (27 downto 0):=X"0000000";

begin

    if rising_edge (clk) then

        if (cuenta=X"48009E0") then
            cuenta:=X"0000000";
        else
            cuenta:=cuenta+1;
        end if;

    end if;

    segundo <= cuenta (24);
    rapido  <= cuenta (10);

end process;
```


## Contador de unidades del minuto

Este contador representa las unidades de los minutos, cuando llega a 9 activa la bandera `n`.
La bandera le indica al siguiente contador que las unidades de minuto terminaron una vuelta.

```VHDL
unidades: process (segundo)

    variable cuenta: std_logic_vector(3 downto 0) := "0000";

begin

    if rising_edge (segundo) then

        if cuenta ="1001" then
            cuenta:="0000";
            n <= '1';
        else
            cuenta:= cuenta +1;
            n <= '0';
        end if;

    end if;

    qum <= cuenta;

end process;
``` 

## Contador de decenas de minuto

Este contador representa las decenas de los minutos, a diferencia del anterior, este contador solo puede llegar hasta `5`.
Cuando llega a `5` debe regresar a `0`, en este punto se activa la bandera `e` que indica que hay que incrementar la hora.

```VHDL
decenas: process (n)

    variable cuenta: std_logic_vector(3 downto 0) := "0000";

begin

    if rising_edge (n) then

        if cuenta ="0101" then
            cuenta:="0000";
            e <= '1';
        else
            cuenta:= cuenta +1;
            e<= '0';
        end if;

    end if;

    Qdm <= cuenta;

end process;
``` 

## Contador de unidades de hora

Este contador representa las unidades de las horas cuyo valor solo llega a `4`, activa la bandera `z` para indicarle al siguiente contador que debe avanzar y ademas, `u` toma uno de los bits del contador para participar posteriormente en la generación del `reset`.

```VHDL
HoraU: Process(e,reset)

    variable cuenta: std_logic_vector(3 downto 0):="0000";

begin

    if rising_edge(e) then

        if cuenta="0100" then
            cuenta:= "0000";
            z<='1';
        else
            cuenta:=cuenta+1;
            z<='0';
        end if;

    end if;

    if reset='1' then
        cuenta:="0000";
    end if;

    Quh<=cuenta;
    u<=cuenta(2);

end Process;
```

## Contador de decenas de hora

Este contador representa las decenas de las horas y combinándolo con `Quh`, podemos tener de `00` a `23`, aquí aparece el mecanismo que evita que el reloj llegue a `24`.

```VHDL
HoraD: Process(z, reset)

    variable cuenta: std_logic_vector(3 downto 0):="0000";

begin

    if rising_edge(z) then

        if cuenta="0010" then
            cuenta:= "0000";
        else
            cuenta:=cuenta+1;
        end if;

    end if;

    if reset='1' then
        cuenta:="0000";
    end if;

    Qdh<=cuenta;
    d <=cuenta(1);

end Process;
```

## Reset automático

Aquí se realiza una operación lógica, que cuando determinadas condiciones de las horas se cumplen simultáneamente, `reset` se activa y los contadores de hora vuelven a cero

```VHDL
inicia: process (u,d)
begin

    reset <= (u and d);

end process;
```

## Conversión a displays

Los contadores almacenan cada dígito del reloj utilizando 4 bits. Por ejemplo, cuando `Qum = "0101"`, este valor binario representa el número decimal 5. Sin embargo, el display de 7 segmentos no interpreta directamente `"0101"` como el número que debe mostrar, por lo que es necesario convertir este valor en una combinación de señales que indique qué segmentos deben encenderse. Para ello, el código utiliza un decodificador mediante la estructura `with...select`, donde a cada valor binario le corresponde una combinación de 7 bits. En este caso, `Qum = "0101"` se convierte en `"0010010"`, lo que provoca que el display muestre el número 5. El mismo procedimiento se realiza para los cuatro displays: `Qum` controla `display1`, `Qdm` controla `display2`, `Quh` controla `display3` y `Qdh` controla `display4`. De esta manera, los cuatro contadores proporcionan los cuatro dígitos necesarios para representar la hora en los displays.

```VHDL
with Qum select
    display1 <= "1000000" when "0000", --0
                "1111001" when "0001", --1
                "0100100" when "0010", --2
                ...
                "0010000" when "1001", --9
                "1000000" when others;
```

