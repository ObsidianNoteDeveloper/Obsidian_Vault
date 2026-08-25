# Archivo `Routes.php`

### Mapa de módulos reales

Si agrupamos las rutas por dominio de negocio obtenemos:

```
AUTENTICACIÓN
├── Login
├── Logout
├── Perfil
├── Datos personales
└── Cambio de contraseña

ADMINISTRACIÓN
├── Usuarios
├── Historial de acceso
├── Roles de áreas
└── Notificaciones

CATÁLOGO ARCHIVÍSTICO
└── Buscar Código

INVENTARIO GENERAL
├── Cargar
├── Consultar
├── Editar
├── Revisar nuevos
├── Revisar modificaciones
└── Generar inventario

OFICIOS
└── Generación 

PDFCONFIGURACIÓN
├── Cortes parciales
└── Control de versiones
```


### El módulo principal es Inventario General

Mira cuántas rutas tiene:

```
CargaInventarioGeneral
ConsultarInventarioGeneral
EditarRegistrosInventarioGeneral
RevisionInventarioGeneral
RevisarEdicionesInventario
GeneralGeneracionInventarioGeneral
InsertInventario
```

### Diagrama de flujo real del negocio

Según las rutas, el flujo parece ser:

```
RESPONSABLE
↓
Carga Inventario
↓
Guardar temporalmente
↓
Enviar a revisión
↓
REVISOR
↓
AceptaroDevolver
↓
Inventario definitivo
```

Pero además existe:

```
Inventario definitivo
↓
Solicitud de edición
↓
Revisión de edición
↓
Aprobada
↓
Actualizar inventario
```


