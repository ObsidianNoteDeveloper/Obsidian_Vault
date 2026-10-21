
```Java
public class Kata {
  
  public static boolean collinearity(int x1, int y1, int x2, int y2) {
    return false;
  }
}
```

El ejercicio pide crear una función llamada `collinearity()` que reciba cuatro números enteros:

```Java
public static boolean collinearity(int x1, int y1, int x2, int y2)
```
Estos números representan las coordenadas de dos vectores:
- Primer vector: `(x1, y1)`
- Segundo vector: `(x2, y2)`

> [!Note]
> Si los dos vectores están sobre la misma línea recta, son colineales y la función debe devolver `true`.

En lugar de dividir coordenadas, puedes utilizar una propiedad matemática que permite comprobar la colinealidad mediante multiplicaciones:
$$
x_1 \cdot y_2 = y_1 \cdot x_2
 $$
**Solución final**


