
## CodeIgniter 4

### Estructura inicial

```
sigafi-clon/
│
├── app/
│   ├── Controllers/
│   │   ├── LoginController.php
│   │   ├── HomeController.php
│   │   └── CodeSearchController.php
│   │
│   ├── Models/
│   │
│   ├── Views/
│   │   ├── templates/
│   │   │   ├── header.php
│   │   │   ├── menu.php
│   │   │   └── footer.php
│   │   │
│   │   ├── login.php
│   │   ├── home.php
│   │   └── code_search.php
│   │
│   └── Config/
│       └── Routes.php
│
├── public/
│   ├── css/
│   ├── js/
│   └── images/
│
└── writable/
```

---

# Objetivo real de la Fase 1

NO hacer lógica.

NO hacer base de datos.

NO hacer AJAX.

Solo replicar:

```
Login
↓
Inicio
↓
Menú superior
```

Y que puedas navegar entre:

```
Inicio
Buscar Código
Inventario General
Oficios
Perfil
```

---

# Qué debe funcionar

### Login falso

```
Usuario: admin
Contraseña: admin
```

Botón:

```
Ingresar
```

Redirige a:

```
/inicio
```

---

### Home

Navbar superior:

```
Inicio
Buscar Código
Inventario General
Oficios
Perfil
```

Sin funcionalidad.

Solo navegación.

---

### Buscar Código

Página vacía con:

```
Año
Sección
Serie
Subserie

[Buscar]
```

---

### Inventario General

Tres pestañas:

```
Cargar
Consultar
Modificar
```

Vacías.

---

### Oficios

Formulario vacío.

---

### Perfil

Formulario vacío.

---

### Tecnologías para esta fase

#### Backend

```
PHP 8.2+
CodeIgniter 4
```

#### Frontend

```
Bootstrap 5
JavaScript Vanilla
```

NO usaría todavía:

❌ jQuery

❌ Tabulator

❌ Toastr

❌ AJAX

❌ MySQL

