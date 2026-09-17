
Entidad Leds

```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.std_logic_arith.ALL;
use IEEE.std_logic_unsigned;


entity leds is
  Port (reloj_in: in std_logic;
        led1: out std_logic;
        led2: out std_logic;
        led3: out std_logic;
        led4: out std_logic
       );
end leds;

architecture Behavioral of leds is
    component divisor is
        generic (N: integer:=24);
        port(reloj:in std_logic;
             div_reloj: out std_logic
             );
    end component;
   
    component pwm is
        port(reloj_pwm:in std_logic;
             D: in std_logic_vector (7 downto 0);
             S: out std_logic
             );
    end component;
   
signal relojPWM: std_logic;
signal relojCiclo: std_logic;
signal a1: std_logic_vector (7 downto 0):=X"00"; -- 
signal a2: std_logic_vector (7 downto 0):=X"01";
signal a3: std_logic_vector (7 downto 0):=X"60";
signal a4: std_logic_vector (7 downto 0):=X"F8"; -- ¿Valor limite que se le puede dar?
       
begin
N1: divisor generic map (10)
    port map (reloj_in, relojPWM);
N2: divisor generic map (23)
    port map (reloj_in, relojCiclo);
P1: pwm port map (relojPWM, a1, led1);
P2: pwm port map (relojPWM, a2, led2);
P3: pwm port map (relojPWM, a3, led3);
P4: pwm port map (relojPWM, a4, led4);

process (relojCiclo)
    variable cuenta: integer range 0 to 255 :=0;
begin
    if (relojCiclo='1' and relojCiclo'event) then
        a1<=a4;
        a2<=a1;
        a3<=a2;
        a4<=a3;
    end if;        
end process;
end Behavioral;
```


Entidad divisor

```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.std_logic_arith.ALL;
use IEEE.std_logic_unsigned.ALL;


entity divisor is
  generic (N:integer:=24);
  Port (reloj: in std_logic;
        div_reloj: out std_logic
        );
end divisor;

architecture Behavioral of divisor is

begin

process(reloj)
variable cuenta: std_logic_vector(27 downto 0):= X"0000000";
begin
    if (rising_edge (reloj))then
        cuenta:=cuenta+1;
    end if;
   
    div_reloj<=cuenta(N);
   
end process;



end Behavioral;
``` 


Entidad pwd

```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.std_logic_arith.ALL;
use IEEE.std_logic_unsigned.ALL;

entity pwm is
  Port ( reloj_pwm: in std_logic;
         D: in std_logic_vector(7 downto 0);
         S: out std_logic  
        );
end pwm;

architecture Behavioral of pwm is

begin
process(reloj_pwm)
    variable cuenta: integer range 0 to 255:=0;
begin
    if(reloj_pwm='1' and reloj_pwm'event)then
        cuenta:=(cuenta+1)mod 256;
        if(cuenta < D)then
            S<='1';
        else
            S<='0';    
        end if;
    end if;    
end process;


end Behavioral;
```

# LED RGB

## RGB de cátodo común

- Pata larga → **cátodo (-)** → `GND`
- Las otras tres patas → **ánodo (+)** → señales **Rojo, Verde y Azul**
- Cada color debe llevar **su propia resistencia**, no una sola resistencia para las tres.

## RGB de ánodo común 



## Código para dos Leds RGB a cátodo común 

```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.std_logic_arith.ALL;
use IEEE.std_logic_unsigned.ALL;


entity leds is
    Port (
        reloj_in : in  std_logic;

        -- LED RGB 1
        led1_R : out std_logic;
        led1_G : out std_logic;
        led1_B : out std_logic;

        -- LED RGB 2
        led2_R : out std_logic;
        led2_G : out std_logic;
        led2_B : out std_logic
    );
end leds;


architecture Behavioral of leds is

    component divisor is
        generic (N : integer := 24);
        port (
            reloj     : in  std_logic;
            div_reloj : out std_logic
        );
    end component;


    component pwm is
        port (
            reloj_pwm : in  std_logic;
            D         : in std_logic_vector(7 downto 0);
            S         : out std_logic
        );
    end component;


    signal relojPWM  : std_logic;
    signal relojCiclo : std_logic;


    -- =====================================================
    -- LED RGB 1
    -- =====================================================

    signal rojo1  : std_logic_vector(7 downto 0) := X"EB";
    signal verde1 : std_logic_vector(7 downto 0) := X"27";
    signal azul1  : std_logic_vector(7 downto 0) := X"F5";


    -- =====================================================
    -- LED RGB 2
    -- =====================================================

    signal rojo2  : std_logic_vector(7 downto 0) := X"27";
    signal verde2 : std_logic_vector(7 downto 0) := X"F5";
    signal azul2  : std_logic_vector(7 downto 0) := X"E7";


begin


    -- =====================================================
    -- DIVISORES
    -- =====================================================

    -- Reloj para PWM
    N1 : divisor
        generic map (10)
        port map (reloj_in, relojPWM);


    -- Reloj para el corrimiento
    N2 : divisor
        generic map (23)
        port map (reloj_in, relojCiclo);


    -- =====================================================
    -- PWM LED RGB 1
    -- =====================================================

    P1 : pwm
        port map (relojPWM, rojo1, led1_R);

    P2 : pwm
        port map (relojPWM, verde1, led1_G);

    P3 : pwm
        port map (relojPWM, azul1, led1_B);


    -- =====================================================
    -- PWM LED RGB 2
    -- =====================================================

    P4 : pwm
        port map (relojPWM, rojo2, led2_R);

    P5 : pwm
        port map (relojPWM, verde2, led2_G);

    P6 : pwm
        port map (relojPWM, azul2, led2_B);


    -- =====================================================
    -- CORRIMIENTO DE COLORES
    -- =====================================================

    process (relojCiclo)
    begin

        if (relojCiclo = '1' and relojCiclo'event) then

            -- LED RGB 1 recibe el color del LED RGB 2
            rojo1  <= rojo2;
            verde1 <= verde2;
            azul1  <= azul2;

            -- LED RGB 2 recibe el color del LED RGB 1
            rojo2  <= rojo1;
            verde2 <= verde1;
            azul2  <= azul1;

        end if;

    end process;


end Behavioral;
```

## Código para cinco Leds RGB a cátodo común 

```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.std_logic_arith.ALL;
use IEEE.std_logic_unsigned.ALL;


entity leds is
    Port (
        reloj_in : in std_logic;

        -- LED RGB 1
        led1_R : out std_logic;
        led1_G : out std_logic;
        led1_B : out std_logic;

        -- LED RGB 2
        led2_R : out std_logic;
        led2_G : out std_logic;
        led2_B : out std_logic;

        -- LED RGB 3
        led3_R : out std_logic;
        led3_G : out std_logic;
        led3_B : out std_logic;

        -- LED RGB 4
        led4_R : out std_logic;
        led4_G : out std_logic;
        led4_B : out std_logic;

        -- LED RGB 5
        led5_R : out std_logic;
        led5_G : out std_logic;
        led5_B : out std_logic
    );
end leds;


architecture Behavioral of leds is

    component divisor is
        generic (N : integer := 24);
        port (
            reloj     : in std_logic;
            div_reloj : out std_logic
        );
    end component;


    component pwm is
        port (
            reloj_pwm : in std_logic;
            D         : in std_logic_vector(7 downto 0);
            S         : out std_logic
        );
    end component;


    signal relojPWM   : std_logic;
    signal relojCiclo : std_logic;


    -- =====================================================
    -- LED RGB 1
    -- =====================================================

    signal rojo1  : std_logic_vector(7 downto 0) := X"EB";
    signal verde1 : std_logic_vector(7 downto 0) := X"27";
    signal azul1  : std_logic_vector(7 downto 0) := X"F5";


    -- =====================================================
    -- LED RGB 2
    -- =====================================================

    signal rojo2  : std_logic_vector(7 downto 0) := X"27";
    signal verde2 : std_logic_vector(7 downto 0) := X"F5";
    signal azul2  : std_logic_vector(7 downto 0) := X"E7";


    -- =====================================================
    -- LED RGB 3
    -- =====================================================

    signal rojo3  : std_logic_vector(7 downto 0) := X"FF";
    signal verde3 : std_logic_vector(7 downto 0) := X"80";
    signal azul3  : std_logic_vector(7 downto 0) := X"00";


    -- =====================================================
    -- LED RGB 4
    -- =====================================================

    signal rojo4  : std_logic_vector(7 downto 0) := X"00";
    signal verde4 : std_logic_vector(7 downto 0) := X"FF";
    signal azul4  : std_logic_vector(7 downto 0) := X"00";


    -- =====================================================
    -- LED RGB 5
    -- =====================================================

    signal rojo5  : std_logic_vector(7 downto 0) := X"00";
    signal verde5 : std_logic_vector(7 downto 0) := X"00";
    signal azul5  : std_logic_vector(7 downto 0) := X"FF";


begin


    -- =====================================================
    -- DIVISORES
    -- =====================================================

    -- Reloj para PWM
    N1 : divisor
        generic map (10)
        port map (reloj_in, relojPWM);


    -- Reloj para el corrimiento
    N2 : divisor
        generic map (23)
        port map (reloj_in, relojCiclo);


    -- =====================================================
    -- PWM LED RGB 1
    -- =====================================================

    P1 : pwm
        port map (relojPWM, rojo1, led1_R);

    P2 : pwm
        port map (relojPWM, verde1, led1_G);

    P3 : pwm
        port map (relojPWM, azul1, led1_B);


    -- =====================================================
    -- PWM LED RGB 2
    -- =====================================================

    P4 : pwm
        port map (relojPWM, rojo2, led2_R);

    P5 : pwm
        port map (relojPWM, verde2, led2_G);

    P6 : pwm
        port map (relojPWM, azul2, led2_B);


    -- =====================================================
    -- PWM LED RGB 3
    -- =====================================================

    P7 : pwm
        port map (relojPWM, rojo3, led3_R);

    P8 : pwm
        port map (relojPWM, verde3, led3_G);

    P9 : pwm
        port map (relojPWM, azul3, led3_B);


    -- =====================================================
    -- PWM LED RGB 4
    -- =====================================================

    P10 : pwm
        port map (relojPWM, rojo4, led4_R);

    P11 : pwm
        port map (relojPWM, verde4, led4_G);

    P12 : pwm
        port map (relojPWM, azul4, led4_B);


    -- =====================================================
    -- PWM LED RGB 5
    -- =====================================================

    P13 : pwm
        port map (relojPWM, rojo5, led5_R);

    P14 : pwm
        port map (relojPWM, verde5, led5_G);

    P15 : pwm
        port map (relojPWM, azul5, led5_B);


    -- =====================================================
    -- CORRIMIENTO DE COLORES
    -- =====================================================

    process (relojCiclo)
    begin

        if (relojCiclo = '1' and relojCiclo'event) then

            -- LED 1 recibe el color del LED 5
            rojo1  <= rojo5;
            verde1 <= verde5;
            azul1  <= azul5;

            -- LED 2 recibe el color del LED 1
            rojo2  <= rojo1;
            verde2 <= verde1;
            azul2 <= azul1;

            -- LED 3 recibe el color del LED 2
            rojo3  <= rojo2;
            verde3 <= verde2;
            azul3  <= azul2;

            -- LED 4 recibe el color del LED 3
            rojo4  <= rojo3;
            verde4 <= verde3;
            azul4 <= azul3;

            -- LED 5 recibe el color del LED 4
            rojo5  <= rojo4;
            verde5 <= verde4;
            azul5 <= azul4;

        end if;

    end process;


end Behavioral;
```

## Código para Ánodo común 

```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.std_logic_arith.ALL;
use IEEE.std_logic_unsigned.ALL;

entity pwm is
  Port ( reloj_pwm: in std_logic;
         D: in std_logic_vector(7 downto 0);
         S: out std_logic  
        );
end pwm;

architecture Behavioral of pwm is

begin
process(reloj_pwm)
    variable cuenta: integer range 0 to 255:=0;
begin
    if(reloj_pwm='1' and reloj_pwm'event)then
        cuenta:=(cuenta+1)mod 256;
        if(cuenta < D)then
            S<='0';  -- Anodo comun: encendido
        else
            S<='1';  -- Anodo comun: apagado    
        end if;
    end if;    
end process;


end Behavioral;
``` 


## cátodo común vs. ánodo común

|                         | Cátodo común         | Ánodo común              |
| ----------------------- | -------------------- | ------------------------ |
| Pata común              | `GND`                | `3.3 V`                  |
| Patas R/G/B             | Ánodos (+)           | Cátodos (-)              |
| Resistencia             | Entre GPIO y ánodo   | Entre cátodo y GPIO      |
| GPIO `1`                | Encendido            | Apagado                  |
| GPIO `0`                | Apagado              | Encendido                |
| `pwm.vhd`               | Normal               | **Invertido**            |
| `leds.vhd`              | Valores RGB normales | **Valores RGB normales** |
| Resistencias para 5 RGB | 15 × 330 Ω           | **15 × 330 Ω**           |

```
              DE10-Lite

       3.3 V ─────┬──── Ánodo común LED 1
                  ├──── Ánodo común LED 2
                  ├──── Ánodo común LED 3
                  ├──── Ánodo común LED 4
                  └──── Ánodo común LED 5


GPIO ── 330 Ω ── Cátodo R LED 1
GPIO ── 330 Ω ── Cátodo G LED 1
GPIO ── 330 Ω ── Cátodo B LED 1

GPIO ── 330 Ω ── Cátodo R LED 2
GPIO ── 330 Ω ── Cátodo G LED 2
GPIO ── 330 Ω ── Cátodo B LED 2

             ...
```


### Entidad leds

```VHDL
entity leds is
    Port (
        reloj_in : in std_logic;

        led1_R, led1_G, led1_B : out std_logic;
        led2_R, led2_G, led2_B : out std_logic;
        led3_R, led3_G, led3_B : out std_logic;
        led4_R, led4_G, led4_B : out std_logic;
        led5_R, led5_G, led5_B : out std_logic
    );
end leds;
```

Esta parte define qué entra y qué sale de nuestro circuito, tenemos una entrada  `reloj_in` que es el reloj de la FPGA y tenemos 15 salidas.

Al tener 5 leds RGB significa que tendremos 15 leds independientes, recordando que cada led RGB contiene los siguientes colores: rojo, verde y azul.

### Componente divisor

```VHDL
component divisor is
    generic (N: integer := 24);
    port (
        reloj     : in std_logic;
        div_reloj : out std_logic
    );
end component;
```

Nuestro programa utilizará un componente llamado `divisor`, como en practicas anteriores, este componente sirve para hacer más lento el reloj. La FPGA trabaja con un reloj muy rápido que para fines prácticos el efecto de rotación de nuestro programa sería demasiado rápido como para poder visualizar el cambio de colores entre leds.


### Componente pwm

```VHDL
component pwm is
    port (
        reloj_pwm : in std_logic;
        D         : in std_logic_vector(7 downto 0);
        S         : out std_logic
    );
end component;
```

El componente de modulación por ancho de pulso (PWM) es el que nos permite controlar qué tanto se enciende cada uno de los Leds.

Nuestra FPGA nos puede dar dos voltajes, 0V (apagado) y 3.3 o 5 V (encendido), el dilema con solo dos estados es que no podemos pedirle a la tarjeta que nos de 1.5V para un brillo medio, para solucionar esto, el PWM enciende y apaga el LED miles de veces por segundo tan rápido que el ojo humano no nota el parpadeo. Lo que el ojo percibe es un "promedio" de luz.
- Si el LED pasa más tiempo apagado que encendido, se ve tenue
- Si el LED pasa más tempo encendido que apagado, se ve brillante.

### Valores de color para los LEDs

```VHDL
signal rojo1  : std_logic_vector(7 downto 0) := X"EB";
signal verde1 : std_logic_vector(7 downto 0) := X"27";
signal azul1  : std_logic_vector(7 downto 0) := X"F5";
```

Aquí estamos diciendo cuánto brillo tendrá cada uno de los leds del LED RGB.

Los valores en hexadecimal (por ejemplo EB, 27 F5) es la forma en la que le decimos a la FPGA cuanta intensidad queremos en cada led, podemos verlo de la siguiente forma:
- Rojo: Mucha intensidad de color
- Verde: Poca intensidad de color
- Azul: Mucha intensiadad de color, pero ligeramente menor al Rojo
Esta combinación de los tres colores nos permite ver un color en particular

Este proceso se repite en los otros cuatro leds.

### Declarar y predifinir un color especifico 

```VHDL
signal rojo1  : std_logic_vector(7 downto 0) := X"EB";
signal verde1 : std_logic_vector(7 downto 0) := X"27";
signal azul1  : std_logic_vector(7 downto 0) := X"F5";
```

Este bloque se encarga de declarar y predefinir un color en específico en formato RGB para el LED, `signal` le indica a la FPGA que está creando "cables internos" o registros de memoria dentro del chip para almacenar y transportar datos entre diferentes componentes.

`std_logic_vector(7 downto 0)` define que no es un pin de un solo bit, sino un bús de 8 bits y el operador `:= X"..."`lo usamos para asignar un valor inicial a las señales al encender la FPGA e indicamos el valor en el sistema hexadecimal

### Instanciación del componente pwm

```VHDL
P1: pwm port map (relojPWM, rojo1, led1_R); 
P2: pwm port map (relojPWM, verde1, led1_G); 
P3: pwm port map (relojPWM, azul1, led1_B);
```

Estas tres lineas son la instanciación del componente pwm en nuestro programa, lo que hace es crear tres controladores pwd independites (uno para cada color del LED RGB) a partir de un único componente pwd, es donde usamos `port map` para conectar las señales con las patas internas del componente pwm.


## Conclusión


Esta práctica nos permitió controlar cinco LEDs RGB mediante VHDL y una FPGA, comprendiendo cómo definir sus entradas y salidas dentro de una entidad y cómo utilizar componentes reutilizables como el divisor de frecuencia y el PWM. También se comprendió cómo representar los colores RGB mediante valores de 8 bits y cómo modificar la intensidad de cada color para obtener diferentes tonalidades. Finalmente, mediante la instanciación del PWM, se logró controlar de manera independiente los componentes rojo, verde y azul de cada LED. Con esto, se reforzaron los conocimientos sobre diseño digital, señales, control de brillo y programación de dispositivos FPGA mediante VHDL.

