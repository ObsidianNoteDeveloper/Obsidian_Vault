
**Idea fundamental**

Circuito → lógica → VHDL

_Ejemplo_

Y=A⋅B

```VHDL
Y <= A and B;
```

Se convierte en una entidad y arquitectura 

### Estructura básica de un programa VHDL

**Estructura general**

```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity nombre is
	Port(
		entrada : in std_logic;
		salida : out std_logic;
	);
end nombre;

architecture Behavioral of nombre is

begin
	-- descripción del circuito
end Behavioral;
```

Y=A⋅B

```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity circuito is 
	Port (
		A : in std_logic;
		B : in sdt_logic;
		Y : out std_logic;
	);
end circuito;

architecture Behavioral of circuito is

begin
	Y <= A and B;
end Behavioral;
```

Librerías:
```VHDL
library IEEE;
```
Permite utilizar elementos definidos por IEEE

Paquete:
```VHDL
use IEEE.STD_LOGIC_1164.ALL;
```
Permite utilizar tipos como:
```VHDL
std_logic
std_logic_vector
```

Entidad
- Define la interfaz externa del circuito 
```VHDL
entity circuito is
```
Aquí se declaran:
- entradas
- salidas
- señales externas

Arquitectura
- Describe cómo funciona internamente el circuito
```VHDL
architecture Behavioral of circuito is
```

### Modos de los puertos 

| **Modo** | **Significado**  |
| -------- | ---------------- |
| `in`     | Entrada          |
| `out`    | Salida           |
| `inout`  | Entrada y salida |
Ejemplo:
```VHDL
entity circuito is
	Port(
		A : in std_logic;
		B : in std_logic;
		Y : out std_logic;
	);
end circuito;
```

### Tipos de datos básicos 

`std_logic`

Representa una señal digital 
```VHDL
A : in std_logic;
```
Puede representar, entre otros estados:
```
'0'
'1'
'Z'
'X'
```

### Vectores 

Para representar varios bits:
```VHDL
A : in std_logic_vector(3 downto 0);
```
Esto representa:
```
A(3) A(2) A(1) A(0)
```
Es decir, 4 bits

Otro ejemplo:
```VHDL
A : in std_logic_vector(7 downto 0);
```
Tiene 8 bits:
```VHDL
A(7) ... A(0)
```

### Declaración de señales

Una señal interna se declara dentro de la arquitectura:
```VHDL
architecture Behavioral of circuito is
	signal X : std_logic;
begin
	X <= A and B;
	Y <= X;
end Behavioral;
```
La señal:
```VHDL
signal X : std_logic;
```
representa una conexión interna del circuito 

> [!Note]
> La declaración de señales va antes de `begin`

### Asignación de señales 

La asignación básica es:
```VHDL
<=
```
Ejemplo:
```VHDL
Y <= A and B;
```

### Operadores lógicos

| **Operador** | **Operación** |
| ------------ | ------------- |
| `and`        | AND           |
| `or`         | OR            |
| `not`        | NOT           |
| `nand`       | NAND          |
| `nor`        | NOR           |
| `xor`        | XOR           |
| `xnor`       | XNOR          |
##### AND

Y=A⋅B

```
Y <= A and B;
```

##### OR

Y=A+B

```
Y <= A or B;
```

##### NOT

Y=A‾

```
Y <= not A;
```

##### NAND

```
Y <= A nand B;
```

##### NOR

```
Y <= A nor B;
```

##### XOR

```
Y <= A xor B;
```

##### XNOR

```
Y <= A xnor B;
```

### Precedencia y paréntesis

Si tienes: Y=A⋅B+C

puedes escribir:
```VHDL
Y <= (A and B) or C;
```

Si tienes: Y=(A+B)⋅C

es:
```VHDL
Y <= (A or B) and C;
```

---
### Ejercicio: circuito AND

Diseñe en VHDL un circuito AND de dos entradas

```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity and_gate is:
	Port (
		A : in std_logic;
		B : in std_logic;
		C : out std_logic;
	);
end and_gate;

architecture Behavioral of and_gate is
begin
	Y <= A and B;
end Behavioral;
```

---

### Ejercicio: circuito de varias compuertas

Supongamos: Y=(A⋅B)+C

```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity circuito is
	Port(
		A : in std_logic;
		B : in std_logic;
		C : in std_logic;
		Y : out std_logic;
	);
end circuito;

architecture Bahavioral of circuito is
begin
	
	Y <= (A and B) or C;
	
end Behavioral;
```

---

### Circuito con señales intermedias

Si el circuito es:
	X=A⋅B 
	Y=X+C
```VHDL
architecture Behavioral of circuito is

	signal X : std_logic;

begin

	X <= A and B;
	Y <= X or C;
end Behavioral;
```
Visualmente:
```
A ──┐
    AND ── X ──┐
B ──┘         OR ── Y
              │
C ────────────┘
```
Esto es muy útil cuando el circuito tiene **varias etapas**.

### Tablas de verdad

**AND**

| A   | B   | Y   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 1   |

```
Y <= A and B;
```

**OR**

|A|B|Y|
|---|---|---|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|1|

```
Y <= A or B;
```

**XOR**

|A|B|Y|
|---|---|---|
|0|0|0|
|0|1|1|
|1|0|1|
|1|1|0|

```
Y <= A xor B;
```
Regla rápida: **XOR da `1` cuando las entradas son diferentes.**

### Multiplexor 2:1

Un MUX 2:1 tiene:

```
       ┌───────┐
A ─────┤       │
	   │ MUX   ├── Y
B ─────┤       │
       └───┬───┘
           │
           S
```

Su ecuación es: Y=S‾A+SB
En VHDL:
```VHDL
Y <= ((not S) and A) or (S and B)
```

```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity mux2 is
	Port (
		A : in std_logic;
		B : in std_logic;
		S : in std_logic;
		Y : out std_logic;
	);
end mux2;

architecture Behavioral of mux2 is
begin

	Y <= ((not S) and A) or (S and B)
	
end Behavioral;
```
Si:
```
S = 0 → Y = A
S = 1 → Y = B
```

### Multiplexor usando `with select`

Esta forma es muy conveniente cuando el circuito tiene selección de entrada
```VHDL
with S select
	Y <= A when '0',
		B when '1';
```

### Decodificador 2 a 4

Un decodificador convierte una entrada binaria en una salida determinada.

Entradas:
```
A1 A0
```

Salidas:
```
Y3 Y2 Y1 Y0
```

Una implementación lógica puede ser:
```VHDL
Y0 <= (not A1) and (not A0);
Y1 <= (not A1) and A0;
Y2 <= A1 and (not A0);
Y3 <= A1 and A0; 
```

### Comparador básico 

Para comparar dos bits: Y=A  XOR  B
- indica si son diferentes.

Pero para igualdad: Y=A  XNOR  B
```
Y <= A xnor B;
```
Tabla:

|A|B|Igual|
|---|---|---|
|0|0|1|
|0|1|0|
|1|0|0|
|1|1|1|

### Operaciones con vectores

Cuando trabaje con varios bits:
```VHDL
A : in std_logic_vector(3 downto 0);
B : in std_logic_vector(3 downto 0);
Y : out std_logic_vector(3 downto 0);
```

puedes hacer operaciones bit a bit:
```
Y <= A and B;
```

Por ejemplo:
```
A = 1010
B = 1100

A AND B

1010
1100
----
1000
```

### Asignación de constantes

Puedes asignar directamente un valor:
```
Y <= '0';
```
o:
```
Y <= '1';
```

Para un vector:
```
Y <= "1010";
```
Si:
```
Y : out std_logic_vector(3 downto 0);
```
entonces:
```
Y <= "1010";
```
es válido.

### Indexar un vector 

Si tenemos:
```
A : std_logic_vector(3 downto 0);
```

podemos acceder a un bit:
```
A(0)
A(1)
A(2)
A(3)
```

Ejemplo:
```
Y <= A(0);
```

### MUX: tres formas 

**Forma 1: ecuación lógica**
```
Y <= ((not S) and A) or (S and B);
```

**Forma 2: `when else`**
```
Y <= A when S = '0' else B;
```

**Forma 3: `with select`**
```
with S select
    Y <= A when '0',
         B when '1';
```

### Circuito combinacional

Un **circuito combinacional** es aquel cuya salida depende únicamente de las entradas actuales.

Por ejemplo: Y=A⋅B
- No necesita memoria.

### Circuito secuencial

A diferencia del combinacional, un circuito secuencial depende de:
```
Entradas actuales
+
Estado anterior
```

Normalmente utiliza:
```
reloj
```

y elementos de almacenamiento:
```
Flip-Flop
Registro
Contador
```

Aquí es donde empiezan a aparecer con mayor importancia:
```
process
```

y:
```
rising_edge(clk)
```

### Entender antes de process

**Instrucciones secuenciales**

Dentro de un:
```
process
```

las instrucciones se ejecutan en el orden escrito.
Por ejemplo:
```VHDL
process(A, B)
begin
    Y <= A and B;
end process;
```
Aunque el código se ejecuta secuencialmente dentro del proceso, **la síntesis busca representar hardware**.

### Plantilla a memorizar

```VHDL
library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity circuito is
	Port(
		A : in std_logic;
		B : in std_logic;
		C : in std_logic;
		
	);
```









