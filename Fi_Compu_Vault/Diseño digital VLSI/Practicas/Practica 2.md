
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

Para esta practica, aquí se encuentra el primer cambio, modificamos la entidad para usar los 6 displays con sus 7 segmentos y el `DP`. 

```VHDL
entity corri is
  Port ( clk: in std_logic;
         display0, display1, display2,display3,display4,display5: buffer std_logic_vector(7 downto 0)
         
        );
end corri;
```

Con este bloque lo que estamos haciendo es que los displays sean una salida de **8 bits** que, además pueden ser utilizados internamente dentro de la arquitectura esto gracias al uso de buffer.

## Funcionamiento del display de 7 segmentos

En el programa desarrollado en VHDL, el control de los segmentos se realiza mediante un vector de tipo `std_logic_vector`. Inicialmente, cada display utilizaba un vector de **7 bits**, declarado como `std_logic_vector(6 downto 0)`. Cada uno de estos bits correspondía al control de uno de los siete segmentos del display. Por medio de la instrucción `with Q select`, se establecía una relación entre el valor de la señal `Q` y el patrón de bits que debía enviarse al display. De esta manera, dependiendo del valor de `Q`, se mostraba un carácter determinado.

Por ejemplo, en la implementación inicial se utilizaban patrones como `"0000110"` para representar la letra **E**, `"0101011"` para la letra **n** y `"1000111"` para la letra **L**. Asimismo, el patrón `"1111111"` se utilizaba para mantener el display apagado y generar un espacio. Por lo tanto, el display no recibe directamente una letra o un número, sino una combinación de bits que determina qué segmentos deben activarse para formar visualmente el carácter correspondiente.

Posteriormente, el funcionamiento del display fue modificado para representar una secuencia alfanumérica. Para ello, fue necesario cambiar los patrones de bits utilizados anteriormente y adaptar el vector de control para trabajar con **8 bits**, mediante `std_logic_vector(7 downto 0)`. La incorporación del octavo bit permite contemplar el control del **punto decimal (DP)** además de los siete segmentos convencionales.

Con esta modificación, la instrucción `with Q select` establece una nueva correspondencia entre el valor de `Q` y los caracteres que deben mostrarse.

Es importante mencionar que los valores binarios utilizados dependen de la configuración eléctrica del display. En este caso se emplea una lógica en la que un determinado estado lógico activa o desactiva los segmentos de acuerdo con la configuración de la tarjeta FPGA. Por esta razón, los valores como `"10011001"` o `"10010010"` no representan directamente los números **4** y **5** en binario; son patrones de control que indican qué segmentos deben iluminarse para formar visualmente dichos números.





