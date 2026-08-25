
### Ejercicio

Crear:

```
<?phpecho "Hola Mundo";
```

## 1. Crear una carpeta para el curso

Abre una terminal:

```BASH
cd ~/Proyectos mkdir php-cursocd php-curso
```

---

## 2. Abrir la carpeta en VS Code

Desde la terminal:

```
code .
```

Se abrirá VS Code en esa carpeta.

---

## 3. Crear un archivo

Crea un archivo llamado:

```
hola.php
```

---

## 4. Escribir el código

Dentro de `hola.php` escribe:

```PHP
<?php

echo "Hola Mundo";
```
---

## 5. Guardar el archivo

**Ctrl + S**

---

## 6. Ejecutar desde la terminal

Abre la terminal integrada de VS Code (**Ctrl + Shift + T** o **Terminal → New Terminal**).

Ejecuta:

```
php hola.php
```

Resultado esperado:

```
Hola Mundo
```

---

### 7. Visualizar en un servidor local

Con el comando:

```bash
php -S localhost:8000
```

```bash
redgnar055@redgnar055-Latitude-E7470:~/Proyectos/php-curso$ php -S localhost:8000
[Mon Jun 15 11:08:35 2026] PHP 8.3.6 Development Server (http://localhost:8000) started
```

Acceder directamente al archivo:

```bash
http://localhost:8000/hola.php
```