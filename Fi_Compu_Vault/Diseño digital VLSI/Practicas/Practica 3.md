
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


# LED

Un LED es un diodo emisor de luz 


# LED RGB



