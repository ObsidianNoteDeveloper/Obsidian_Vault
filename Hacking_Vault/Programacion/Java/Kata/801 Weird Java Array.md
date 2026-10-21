
```Java
import java.util.*;

class Codewarrior {
    public static List<Integer>[] arrayOfLists = new List<Integer>[] {
        Arrays.asList(1, 2, 3),
        Arrays.asList(4, 5, 6),
        Arrays.asList(7, 8, 9),
    };
}
```

Java permite importar todas las clases e interfaces públicas que se encuentran directamente dentro del paquete `java.util` usando `*` (_Indica que deseo importar los tipos accesibles que están directamente dentro de `java.util`, en lugar de especificar cada uno por separado_).

```Java
import java.util.*;
```

- Se usa `import` para utilizar clases o interfaces de otros paquetes. 
- El paquete `java.util` es una colección de herramientas de Java.

**java.util**

Estas son algunas de las clases más útiles:

|Clase|¿Para qué sirve?|Ejemplo de uso|
|---|---|---|
|`Scanner`|Leer datos introducidos por el usuario.|Pedir su nombre o edad.|
|`ArrayList`|Crear listas que pueden cambiar de tamaño.|Guardar puntuaciones.|
|`Random`|Generar valores aleatorios.|Elegir un enemigo al azar.|
|`HashMap`|Guardar pares de clave y valor.|Relacionar jugadores con puntuaciones.|
|`HashSet`|Almacenar elementos sin duplicados.|Registrar identificadores únicos.|
|`Collections`|Realizar operaciones sobre colecciones.|Ordenar una lista.|

```Java
public static List<Integer>[] arrayOfLists = new List<Integer>[] {
	...
};
```

- `public`
	- **Modificador de acceso**
	- Permite acceder a la variable desde otras clases, siempre que las demás condiciones de acceso lo permitan.

- `static`
	- **Miembro de clase**
	- Significa que la variable pertenece a la clase y no a una instancia individual de esa clase. Puedes acceder a ella mediante el nombre de la clase, sin crear un objeto, si el contexto de acceso lo permite.
		- Hace que la variable pertenezca a la clase, no a cada objeto individual.

> [!Warning]
> Java no permite crear directamente un arreglo de `List<Integer>` usando `new List<Integer>[]`, debido a las restricciones de los tipos genéricos.

### Solución

```Java
import java.util.*;  
  
class Codewarrior {  
  
    @SuppressWarnings("unchecked")  
    public static List<Integer>[] arrayOfLists = (List<Integer>[]) new List<?>[] {  
            Arrays.asList(1, 2, 3),  
            Arrays.asList(4, 5, 6),  
            Arrays.asList(7, 8, 9)  
    };  
  
    public static void main(String[] args) {  
        System.out.println(Codewarrior.arrayOfLists[0]);
		System.out.println(Codewarrior.arrayOfLists[1].get(0));
    }  
}
```

- Se crea una variable llamada `arrayOfLists`, que contiene un arreglo de tres elementos. 
	- Cada elemento es una lista de números enteros.
	
- Declaración típica:
```Java
List<String>[] arrayOfLists = new ArrayList[];
```
> [!Warning]
> Esto dará un error de compilación (_Generic array creation_).
	
- Para usar un arreglo de listas de forma segura y evitar advertencias de compilador, la forma estándar es crear un arreglo de listas sin tipar (_raw type_) y luego aplicar un molde (_casr_):
```Java
List<String>[] arrayOfLists = (List<String>[]) new ArrayList[10];
```

En Java, el símbolo **`@`** se utiliza exclusivamente para definir y aplicar **anotaciones** (_annotations_).

- Las anotaciones son una forma de **metadatos** (es decir, datos sobre los datos). No cambian directamente la lógica de ejecución del código por sí mismas, pero le proporcionan información valiosa al **compilador**, a las **herramientas de análisis de código** o a los **frameworks** para que sepan cómo procesar o ejecutar ese código.

- Usos principales del `@` en Java
	1. Anotaciones estándar del compilador (In-built)
	2. Metadatos para Frameworks y Librerías
	3. Restriciones e Información de Tipos (Checker Framework / Lombok)
	4. Creación de Anotaciones Personalizadas (`@interface`)

```Java
@SuppressWarnings("unchecked")
```
Es una anotación que suprime una advertencia del compilador relacionada con conversiones de tipos que no pueden verificarse completamente.

```Java
public static List<Integer>[] arrayOfLists
```
- `List<Integer>[]`: indica un arreglo de referencias a listas de números enteros.
- `arrayOfLists`: es el nombre de la variable.

```Java
(List<Integer>[]) new List<?>[]
```
Crea un arreglo de listas y lo convierte al tipo de su referencia.
- El `<?>`  se llama **comodín (wildcard)** en Java, y se utiliza principalmente para sortear las restricciones del sistema de tipos al trabajar con arreglos y genéricos.

**Arrays.asList()** es un método utilitario muy útil en Java (que pertenece a la clase `java.util.Arrays`) que sirve para convertir un arreglo tradicional o una serie de valores en una lista (`List`).
- La lista tiene un tamaño fijo
- Se pueden modificar los elementos existentes usando `set()`
> [!Note] 
`Arrays.asList()` devuelve listas de tamaño fijo: puedes cambiar un elemento existente, pero no agregar ni quitar elementos.
