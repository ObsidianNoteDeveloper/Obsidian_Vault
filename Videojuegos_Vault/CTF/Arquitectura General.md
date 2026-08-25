
### Arrancar un servidor local

Probar el proyecto en VS Code: 

```Bash
python3 -m http.server 8000
```

### Borrar los datos del sitio

En Chrome/Chromium también puedes ir a:

`F12` → `Application` → `Local Storage` → `http://localhost:8000`

y eliminar: `pilares_ctf_state`

Después recargas la página.

---

## Arquitectura general

Arquitectura basada en el patrón **MVC (Modelo - Vista - Controlador)**, adaptada para Flask

```Text
CTF-Web/
│
├── app.py                  # Punto de entrada de la aplicación
├── config.py               # Configuración general
├── requirements.txt
├── README.md
│
├── database/
│   ├── ctf.db              # Base de datos SQLite
│   └── schema.sql          # Script de creación de tablas
│
├── controllers/
│   ├── auth_controller.py
│   ├── flag_controller.py
│   ├── ranking_controller.py
│   ├── admin_controller.py
│   └── socket_controller.py
│
├── models/
│   ├── database.py
│   ├── user.py
│   ├── flag.py
│   ├── score.py
│   └── submission.py
│
├── templates/
│   ├── login.html
│   ├── dashboard.html
│   ├── admin.html
│   └── base.html
│
├── static/
│   │
│   ├── css/
│   │     style.css
│   │
│   ├── js/
│   │     login.js
│   │     dashboard.js
│   │     socket.js
│   │     admin.js
│   │
│   └── img/
│         logo.png
│
├── routes/
│   ├── auth_routes.py
│   ├── flag_routes.py
│   ├── ranking_routes.py
│   └── admin_routes.py
│
├── services/
│   ├── auth_service.py
│   ├── flag_service.py
│   ├── ranking_service.py
│   └── socket_service.py
│
├── utils/
│   ├── security.py
│   ├── validators.py
│   └── helpers.py
│
└── instance/
    └── secret_key.txt
```


