/home/redgnar055/Documentos/Redgnar/Programacion/Programacion_C/ElementosBasicos


---
Programación en C, C++, Java y UML
Capítulo 3 - El Lenguaje C: elementos básicos 

---

1. Hola Mundo Mejorado
2. Calculadora de operaciones básicas 
3. Analizador de caracteres 
4. Conversor de unidades
5. Sistemas de evaluación (booleanos)
6. Registro simple de usuario
7. Simulador de variables globales y locales
8. Detector de errores básicos 
9. Menú interactivo (mini sistema)
10. Sistema de pruebas de datos 

---

## 1. “Hola Mundo Mejorado”

**Objetivo:** Estructura básica + `main()` + `printf`

**Descripción:**  
Programa que imprima tu nombre, carrera y un mensaje personalizado.

**Refuerza:**

- Estructura general de un programa en C
- `#include <stdio.h>`
- Función `main()`
- Comentarios

---

Primer ejemplo:
```C
#include <stdio.h>

int main(){
	printf("Bienvenido a la programación en C\n");
	return 0;
}
```

En la terminal escribe:

```Bash
gcc programa.c -o programa
```

- `gcc` → compilador
- `programa.c` → tu código
- `-o programa` → nombre del ejecutable

Ejecutar el programa

```Bash
./programa
```

### Directivas del preprocedador

Una **directiva del preprocesador en C** es una instrucción especial que **se ejecuta antes de que el programa sea compilado**. Es decir, no es parte “directa” del lenguaje que ejecuta el CPU, sino que le dice al compilador **cómo preparar el código** antes de convertirlo en ejecutable.

El proceso en C es:

```
Código fuente → (Preprocesador) → (Compilador) → Ejecutable
```

Las directivas actúan en la etapa del **preprocesador**.

**Características principales**
	Siempre empiezan con `#`
	No llevan `;` al final
	No son funciones ni instrucciones normales
	Modifican el código antes de compilarse

**Ejemplos**

`#include` → Incluir librerías
`#define` → Definir constantes, [[macros]]
`#ifdef`, `#ifndef`, `#endif` 



==pag. 69== 


---

## 2. Calculadora de operaciones básicas

**Objetivo:** Variables + tipos de datos + entrada/salida

**Descripción:**  
Pide dos números y muestra suma, resta, multiplicación y división.

**Refuerza:**

- `int`, `float`
- `scanf` y `printf`
- Variables e inicialización

---

## 3. Analizador de caracteres

**Objetivo:** Tipo `char`

**Descripción:**  
El usuario ingresa un carácter y el programa indica:

- Si es letra, número o símbolo

**Refuerza:**

- Tipo `char`
- Entrada de datos
- Lógica básica

---

## 4. Conversor de unidades

**Objetivo:** Uso de constantes

**Descripción:**  
Convierte:

- Celsius ↔ Fahrenheit
- Metros ↔ kilómetros

**Refuerza:**

- `#define`
- Constantes simbólicas
- Operaciones con `float`

---

## 5. Sistema de evaluación (booleanos)

**Objetivo:** Tipo lógico

**Descripción:**  
Pide una calificación y determina si el alumno aprueba o reprueba.

**Refuerza:**

- Valores lógicos (`0` y `1`)
- Condiciones (`if`)
- Comparaciones

---

## 6. Registro simple de usuario

**Objetivo:** Variables + cadenas

**Descripción:**  
Solicita:

- Nombre
- Edad
- Carrera

Y luego imprime los datos formateados.

**Refuerza:**

- `char[]` (cadenas)
- Entrada de strings
- Variables múltiples

---

## 7. Simulador de variables globales y locales

**Objetivo:** Duración de variables

**Descripción:**  
Crea funciones que usen variables:

- Locales
- Globales

Y muestra cómo cambian.

**Refuerza:**

- Scope
- Variables globales vs locales
- Funciones

---

## 8. Detector de errores básicos

**Objetivo:** Depuración

**Descripción:**  
Programa con errores intencionales que debes corregir:

- Sintaxis
- Lógicos

**Refuerza:**

- Mensajes de error
- Debugging
- Buenas prácticas

---

## 9. Menú interactivo (mini sistema)

**Objetivo:** Estructura completa

**Descripción:**  
Menú con opciones:

1. Sumar
2. Restar
3. Salir

**Refuerza:**

- `switch` o `if`
- Entrada/salida
- Flujo del programa

---

## 10. Sistema de pruebas de datos

**Objetivo:** Pruebas y validación

**Descripción:**  
Valida datos de entrada:

- Que no sean negativos
- Que sean números válidos

**Refuerza:**

- Validación
- Errores en tiempo de ejecución
- Pruebas de software








