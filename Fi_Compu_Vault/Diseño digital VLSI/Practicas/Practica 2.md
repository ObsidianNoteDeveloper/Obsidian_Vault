
---

## Entidad

> [!Note]
> La entidad define la "interfaz" del circuito, es decir, **qué señales entran al circuito y qué señales salen de él**.

La entidad proporcionada en clase es:

```VHDL
entity corri is
  Port ( clk: in std_logic;
         display0, display1, display2, display3, display4, display5:
             buffer std_logic_vector(6 downto 0)
        );
end corri;
```

En este bloque se declara la identidad llamada `corri`, que nos indica que conexiones tendremos disponibles. Todo lo que ocurre dentro de `corri` se define posteriormente en la `architecture`.

En `Port` declaramos los puertos de **entrada** y **salida**.

Se usa `in`para las señales de entrada, y `std_logic` para representar diferentes estados lógicos (es uno de los tipos de datos más utilizados en VHDL), como el `0` y `1` que serán interpretados como nivel lógico bajo y alto respectivamente

**Entradas:**
- `clk`: Es el nombre de la señal de reloj que utilizaremos para sincronizar procesos  

Estamos declarando 6 displays de 7 segmentos, y se uso `std_logic_vector(6 downto 0)` para representar un bús de datos de 7 bits, `std_logic`toma valores como `0` y `1`, el `(6 downto 0)`define el tamaño del vector y el orden de sus bits. 

Para esta practic,a aquí se encuentra el primer cambio, modificamos la entidad para usar los 6 displays con sus 7 segmentos y el `DP` 




## Decodificador para un display de 7 segmentos

`with Q select`: dependiendo del valor que tenga `Q`, el programa selecciona qué valor va a mandar a `display`

`display0`: 


