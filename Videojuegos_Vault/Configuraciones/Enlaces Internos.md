
**Obsidian y GitHub interpretan de manera diferente los enlaces internos hacia encabezados**. En GitHub, los espacios de los títulos se convierten normalmente en `-`, mientras que Obsidian puede utilizar una interpretación diferente del encabezado.

Por ejemplo:

```
# Conceptos básicos
```

En GitHub se referencia como:

```
#conceptos-básicos
```

Mientras que en Obsidian podemos utilizar:

```
#Conceptos%20básicos
```

### Formato que vamos a utilizar

Para que las notas sean compatibles con **Obsidian y GitHub**, decidimos utilizar un formato híbrido:

```
[Nombre de la sección](#nombre-de-la-sección) [↗](#Nombre%20de%20la%20sección)
```

La idea es:

- **Primer enlace:** compatibilidad con **GitHub**.
- **`↗`:** enlace alternativo para **Obsidian**.
- **`%20`:** representa los espacios en la sintaxis utilizada para Obsidian.

### Plantilla para tus futuras notas

```
## Índice

[Sección 1](#sección-1) [↗](#Sección%201)

[Sección 2](#sección-2) [↗](#Sección%202)

[Sección 3](#sección-3) [↗](#Sección%203)
```

