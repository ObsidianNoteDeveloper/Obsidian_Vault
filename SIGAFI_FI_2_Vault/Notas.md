
## [[Tecnología de la Fase 1#CodeIgniter 4|CodeIgner]]

SIGAFI esta construido sobre **CodeIgniter 4**

## Arquitectura del sistema

MVC

```
CLIENTE
(JS + HTML + Bootstrap)

↓

CONTROLADORES
(Controllers)

↓

MODELOS
(Models)

↓

BASE DE DATOS
(MySQL probablemente)

↓

RESPUESTA
(Views)
```

## La arquitectura EXACTA que usa

```
Views
↕
Controllers
↕
Models
↕
Database
```

y además:

```
Services
Libraries
Helpers
Filters
```

como capas auxiliares.

---

## FRONTEND

### Bootstrap

UI/layout responsive.

```
botonesformulariosmodalesgridnavbar
```

### jQuery

Manipulación DOM y AJAX.

Probablemente cosas como:

```
$.ajax(...)$('#btn').click(...)
```

### Tabulator

MUY importante.

Es una librería avanzada de tablas.

Esto explica:

- tablas dinámicas
- filtros
- paginación
- edición inline

### Toastr

Notificaciones tipo:

```
"Registro guardado""Error""Enviado correctamente"
```

### Luxon

Manejo moderno de fechas.

---

## BACKEND

### Controladores

Ejemplo:

```
InsertInventarioController.php
```

Este recibe requests del frontend.

### Modelos

Ejemplo:

```
InsertInventarioModel.php
```

Aquí están:

- queries
- validaciones
- llamadas SQL

### Views

Renderizan HTML.

---

# Aspectos importantes del sistema 

### 1. EL SISTEMA USA JAVASCRIPT SEPARADO POR MÓDULO

Eso es MUY profesional.

Ejemplo:

```
insert-inventario.jsrevision-inventario-general.js
```

Esto significa:

- frontend desacoplado
- lógica separada
- arquitectura mantenible

### 2. EL SISTEMA USA PDFs

Esto es MUY interesante.

```
Libraries/PDF
```

y:

```
PDF_Oficio.php
```

Probablemente usan:

- DomPDF
- TCPDF
- MPDF

### 3. EL SISTEMA USA SERVICIOS

```
Services/NotificationServices.php
```

Esto indica arquitectura semi enterprise.

### 4. TIENE HELPERS

```
auth_helper.php
```

Seguramente:

- validar sesión
- permisos
- helpers globales

---

### 5. HAY FILTROS

```
Filters
```

Esto suele ser:

```
auth middleware
```

Ejemplo:

```
si no hay sesión:→ redirigir login
```

### 6. TIENE ENTORNO DE TESTING

Esto me sorprendió.

```
phpunittests
```

Eso es MUY bueno.

---
