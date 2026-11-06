
Programa 1
- Programa original, proporcionado por el profesor

`Rx.vhd`
```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.NUMERIC_STD.ALL;


entity Rx is
  Port ( clk    : in std_logic;
         LEDS   : out std_logic_vector(7 downto 0);
         RX_WIRE: in std_logic
        );
end Rx;

architecture Behavioral of Rx is

signal BUFF   : std_logic_vector(9 downto 0);
signal flag   : std_logic:='0';
signal INDICE : INTEGER RANGE 0 to 9:=0;
signal PRE    : INTEGER RANGE 0 to 5208;
signal PRE_val: INTEGER RANGE 0 to 41600;
signal baud   : std_logic_vector(2 downto 0);

begin

    RX_dato:process(clk,RX_WIRE)
            begin
                if(clk'event and clk='1')then
                    if(flag='0' and RX_WIRE='0')then
                       flag<='1';
                       INDICE<=0;
                       PRE<=0;
                    end if;
               
                    if(flag='1')then
                        BUFF(INDICE)<=RX_WIRE;
                        if(PRE<PRE_val)then
                            PRE<=PRE+1;
                        else
                            PRE<=0;    
                        end if;
                        if(PRE=PRE_val/2)then
                            if(INDICE<9)then
                                INDICE<=INDICE+1;
                        else
                                if(BUFF(0)='0' and BUFF(9)='1')then
                                    LEDS<=BUFF(8 downto 1);
                                else
                                    LEDS<="00000000";    
                                end if;
                                flag<='0';
                         end if;
                     end if;
                    end if;
                   end if;    
              end process;
           
baud<="100";

with(baud)select
    PRE_VAL<=41600 when "000",  --1200 bauds
             20800 when "001",  --2400 bauds
             10400 when "010",  --4800 bauds
             5200  when "011",  --9600 bauds
             2600  when "100",  --19200 bauds
             1300  when "101",  --38400 bauds
             866   when "110",  --57600 bauds
             432   when others; --115200 bauds        

end Behavioral;
```


Programa 2
- controlar un LED de la FPGA DE10-Lite mediante caracteres ASCII recibidos desde la computadora.

`Rx.vhd`
```VHDL

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;
use IEEE.NUMERIC_STD.ALL;

entity Rx is
    generic (
        CLOCK_HZ : integer := 50000000;
        BAUD_RATE : integer := 19200
    );
    port (
        clk         : in  std_logic;
        RX_WIRE     : in  std_logic;
        DATO        : out std_logic_vector(7 downto 0);
        DATO_VALIDO : out std_logic
    );
end Rx;

architecture Behavioral of Rx is

    constant CLKS_PER_BIT : integer := CLOCK_HZ / BAUD_RATE;

    type estado_type is (IDLE, START, DATA, STOP);

    signal estado : estado_type := IDLE;

    signal rx_meta : std_logic := '1';
    signal rx_sync : std_logic := '1';

    signal contador : integer range 0 to CLKS_PER_BIT := 0;
    signal indice : integer range 0 to 7 := 0;

    signal buffer_dato : std_logic_vector(7 downto 0) := (others => '0');
    signal dato_reg : std_logic_vector(7 downto 0) := (others => '0');

begin

    -- Sincronizacion de la entrada UART
    process(clk)
    begin
        if rising_edge(clk) then
            rx_meta <= RX_WIRE;
            rx_sync <= rx_meta;
        end if;
    end process;

    -- Recepcion de datos UART
    process(clk)
    begin
        if rising_edge(clk) then

            DATO_VALIDO <= '0';

            case estado is

                when IDLE =>
                    contador <= 0;
                    indice <= 0;

                    if rx_sync = '0' then
                        estado <= START;
                    end if;

                when START =>
                    if contador < (CLKS_PER_BIT / 2) - 1 then
                        contador <= contador + 1;
                    else
                        contador <= 0;

                        if rx_sync = '0' then
                            estado <= DATA;
                        else
                            estado <= IDLE;
                        end if;
                    end if;

                when DATA =>
                    if contador < CLKS_PER_BIT - 1 then
                        contador <= contador + 1;
                    else
                        contador <= 0;

                        buffer_dato(indice) <= rx_sync;

                        if indice < 7 then
                            indice <= indice + 1;
                        else
                            estado <= STOP;
                        end if;
                    end if;

                when STOP =>
                    if contador < CLKS_PER_BIT - 1 then
                        contador <= contador + 1;
                    else
                        contador <= 0;
                        estado <= IDLE;

                        if rx_sync = '1' then
                            dato_reg <= buffer_dato;
                            DATO_VALIDO <= '1';
                        end if;
                    end if;

            end case;
        end if;
    end process;

    DATO <= dato_reg;

end Behavioral;

```


`Control_LED.vhd`
```VHDL

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity Control_LED is
    port (
        clk         : in  std_logic;
        DATO        : in  std_logic_vector(7 downto 0);
        DATO_VALIDO : in  std_logic;
        LED         : out std_logic
    );
end Control_LED;

architecture Behavioral of Control_LED is

    signal estado_led : std_logic := '0';

begin

    process(clk)
    begin
        if rising_edge(clk) then

            if DATO_VALIDO = '1' then

                case DATO is

                    when x"41" =>
                        estado_led <= '1'; -- ASCII A: encender

                    when x"44" =>
                        estado_led <= '0'; -- ASCII D: apagar

                    when others =>
                        null; -- Ignorar otros caracteres

                end case;

            end if;

        end if;
    end process;

    LED <= estado_led;

end Behavioral;

```


`Sistema_UART.vhd`
```VHDL

library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity Sistema_UART is
    port (
        CLOCK_50 : in  std_logic;
        UART_RX  : in  std_logic;
        LED      : out std_logic
    );
end Sistema_UART;

architecture Behavioral of Sistema_UART is

    signal dato_recibido : std_logic_vector(7 downto 0);
    signal dato_valido   : std_logic;

begin

    -- Instancia del receptor UART
    U1: entity work.Rx
        generic map (
            CLOCK_HZ => 50000000,
            BAUD_RATE => 19200
        )
        port map (
            clk => CLOCK_50,
            RX_WIRE => UART_RX,
            DATO => dato_recibido,
            DATO_VALIDO => dato_valido
        );

    -- Instancia del controlador del LED
    U2: entity work.Control_LED
        port map (
            clk => CLOCK_50,
            DATO => dato_recibido,
            DATO_VALIDO => dato_valido,
            LED => LED
        );

end Behavioral;

```







