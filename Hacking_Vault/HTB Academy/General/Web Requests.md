Fundamental | Tier 0


# HTTP Fundamentals 
---
Section 1 / 8
## Protocolo de Transferencia de Hipertexto (HTTP)

El término `hipertexto` se refiere a texto que contiene enlaces a otros recursos y texto que los lectores pueden interpretar fácilmente. El puerto por defecto para la comunicación HTTP es el puerto `80`.

Introducimos un `Nombre de Dominio Completamente Calificado` (`FQDN` - Fully Qualified Domain Name) como un `Localizador Uniforme de Recursos` (`URL` - Uniform Resource Locator) para llegar al sitio web deseado, como [www.hackthebox.com](http://www.hackthebox.com/).

## URL

```
http://admin:password@inlanefreight.com:80/dashboard.php?login=true#status
```

| **Componente**           | **Ejemplo**          | **Descripción**                                                                                                                                                                                                 |
| ------------------------ | -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Esquema`                | `http://` `https://` | Se utiliza para identificar el protocolo al que accede el cliente y termina con dos puntos y una doble barra (`://`)                                                                                            |
| `Información de Usuario` | `admin:password@`    | Este es un componente opcional que contiene las credenciales (separadas por dos puntos `:`) utilizadas para autenticarse en el host, y está separado del host con un signo de arroba (`@`)                      |
| `Host`                   | `inlanefreight.com`  | El host indica la ubicación del recurso. Puede ser un nombre de host o una dirección IP                                                                                                                         |
| `Puerto`                 | `:80`                | El `Puerto` está separado del `Host` por dos puntos (`:`). Si no se especifica ningún puerto, los esquemas `http` usan por defecto el puerto `80` y los `https` el puerto `443`                                 |
| `Ruta`                   | `/dashboard.php`     | Apunta al recurso al que se está accediendo, que puede ser un archivo o una carpeta. Si no se especifica ninguna ruta, el servidor devuelve el índice por defecto (p. ej., `index.html`).                       |
| `Cadena de Consulta`     | `?login=true`        | La cadena de consulta comienza con un signo de interrogación (`?`), y consiste en un parámetro (p. ej., `login`) y un valor (p. ej., `true`). Múltiples parámetros pueden ser separados por un ampersand (`&`). |
| `Fragmentos`             | `#status`            | Los fragmentos son procesados por los navegadores en el lado del cliente para localizar secciones dentro del recurso principal (p. ej., un encabezado o una sección en la página).                              |
Los campos obligatorios principales son el esquema y el host.

La primera vez que un usuario introduce la URL (`inlanefreight.com`) en el navegador, este envía una petición a un servidor DNS (Sistema de Nombres de Dominio) para resolver el dominio y obtener su IP.

## cURL

**cURL** (client URL) es una herramienta de línea de comandos y una biblioteca que soporta principalmente HTTP junto con muchos otros protocolos.

Ejemplo:
```Bash
curl -s -O http://info.cern.ch/
```

`-s` (`--silent`)
Ejecuta `curl` en **modo silencioso**.
- No muestra la barra de progreso.
- No muestra mensajes informativos o de estado.
- Solo imprime la salida (o guarda el archivo, dependiendo de las otras opciones).

`-O` (`--remote-name`)
Le dice a `curl` que **guarde el archivo usando el mismo nombre que tiene en el servidor**.

Podemos usar la bandera `-h` para ver qué otras opciones podemos usar con cURL.

---
Section 2 / 8

# Protocolo Seguro de Transferencia de Hipertexto

Aunque los datos transferidos a través del protocolo HTTPS pueden estar cifrados, la petición aún podría revelar la URL visitada si contactó a un servidor DNS de texto plano. Por esta razón, se recomienda utilizar servidores DNS cifrados (p. ej., 8.8.8.8 o 1.1.1.1), o utilizar un servicio de VPN para asegurar que todo el tráfico esté correctamente cifrado.

Para omitir la verificación del certificado con cURL, podemos usar la bandera `-k`:

```Shell
`Redgnar155@htb[/htb]$ curl -k https://www.inlanefreight.com
 
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head> 
...SNIP...`
```

---
Section 3 / 8

# Peticiones y Respuestas HTTP

|**Campo**|**Ejemplo**|**Descripción**|
|---|---|---|
|`Method`|`GET`|El método o verbo HTTP, que especifica el tipo de acción a realizar.|
|`Path`|`/users/login.html`|La ruta al recurso al que se está accediendo. Este campo también puede tener como sufijo una cadena de consulta (query string) (p. ej., `?username=user`).|
|`Version`|`HTTP/1.1`|El tercer y último campo se utiliza para denotar la versión de HTTP.|

La bandera `-v` significa verbose (en español, “detallado” o “verboso”). En informática, salida verbosa = el programa muestra mucha más información de la que normalmente imprimiría.

Por ejemplo:
Sin -v, curl normalmente solo muestra el cuerpo de la respuesta (el HTML de la página).

Con -v, además muestra en stderr (la salida de diagnóstico):

- La resolución DNS (a qué IP se conectó).
- La dirección y puerto de destino (80 o 443).
- El proceso de conexión TCP.
- La negociación TLS/SSL (si usas HTTPS).
- Las cabeceras HTTP enviadas por el cliente.
- Las cabeceras HTTP recibidas del servidor.
- Mensajes de redirecciones, reutilización de conexiones, errores, etc.

El flag `-vvv` muestra una salida aún más detallada.

---
Section 4 / 8

# Cabeceras HTTP

Podemos dividir las cabeceras en las siguientes categorías:

1. `Cabeceras Generales`
2. `Cabeceras de Entidad`
3. `Cabeceras de Solicitud`
4. `Cabeceras de Respuesta`
5. `Cabeceras de Seguridad`

---

### Cabeceras Generales

Las [cabeceras generales](https://www.w3.org/Protocols/rfc2616/rfc2616-sec4.html) se utilizan tanto en las solicitudes como en las respuestas HTTP. Son contextuales y se usan para `describir el mensaje en lugar de su contenido`.

### Cabeceras de Entidad

Al igual que las cabeceras generales, las [cabeceras de entidad](https://www.w3.org/Protocols/rfc2616/rfc2616-sec7.html) pueden ser `comunes tanto a la solicitud como a la respuesta`. Estas cabeceras se utilizan para `describir el contenido` (entidad) transferido por un mensaje. Se suelen encontrar en las respuestas y en las solicitudes POST o PUT.

### Cabeceras de Solicitud

El cliente envía [cabeceras de solicitud](https://tools.ietf.org/html/rfc2616) en una transacción HTTP. Estas cabeceras se `utilizan en una solicitud HTTP y no se relacionan con el contenido` del mensaje. 

### Cabeceras de Respuesta

Las [cabeceras de respuesta](https://tools.ietf.org/html/rfc7231#section-7) pueden `utilizarse en una respuesta HTTP y no se relacionan con el contenido`. Ciertas cabeceras de respuesta como `Age`, `Location` y `Server` se utilizan para proporcionar más contexto sobre la respuesta.

### Cabeceras de Seguridad

Finalmente, tenemos las [cabeceras de seguridad](https://owasp.org/www-project-secure-headers/). Con el aumento de la variedad de navegadores y de ataques basados en la web, fue necesario definir ciertas cabeceras que mejoraran la seguridad. Las cabeceras de seguridad HTTP son `una clase de cabeceras de respuesta utilizadas para especificar ciertas reglas y políticas` que debe seguir el navegador al acceder al sitio web.

---

## DevTools del navegador

Finalmente, veamos cómo podemos previsualizar las cabeceras HTTP usando las herramientas de desarrollador del navegador (DevTools). Tal y como hicimos en la sección anterior, podemos ir a la pestaña `Network` para ver las diferentes solicitudes hechas por la página. Podemos hacer clic en cualquiera de las solicitudes para ver sus detalles

---
Section 5 / 8

# Métodos y códigos HTTP

A continuación se presentan algunos de los métodos más utilizados:

|**Método**|**Descripción**|
|---|---|
|`GET`|Solicita un recurso específico. Se pueden pasar datos adicionales al servidor a través de cadenas de consulta en la URL (p. ej., `?param=value`).|
|`POST`|Envía datos al servidor. Puede manejar múltiples tipos de entrada, como texto, PDF y otras formas de datos binarios. Estos datos se añaden en el cuerpo de la solicitud (request body) presente después de las cabeceras. El método `POST` se utiliza comúnmente al enviar información (p. ej., formularios/inicios de sesión) o al subir datos a un sitio web, como imágenes o documentos.|
|`HEAD`|Solicita las cabeceras que se devolverían si se hiciera una solicitud `GET` al servidor. No devuelve el cuerpo de la solicitud y normalmente se realiza para comprobar la longitud de la respuesta antes de descargar recursos.|
|`PUT`|Crea nuevos recursos en el servidor. Permitir este método sin los controles adecuados puede llevar a la subida de recursos maliciosos.|
|`DELETE`|Elimina un recurso existente en el servidor web. Si no se protege adecuadamente, puede provocar una Denegación de Servicio (DoS) al eliminar archivos críticos en el servidor web.|
|`OPTIONS`|Devuelve información sobre el servidor, como los métodos que acepta.|
|`PATCH`|Aplica modificaciones parciales al recurso en la ubicación especificada.|

> [!Note] Nota
> La mayoría de las aplicaciones web modernas se basan principalmente en los métodos `GET` y `POST`. Sin embargo, cualquier aplicación web que utilice API REST también se basa en `PUT` y `DELETE`, que se utilizan para actualizar y eliminar datos en el punto final de la API (API endpoint), respectivamente.


Los códigos de estado HTTP se utilizan para comunicar al cliente el estado de su solicitud. Un servidor HTTP puede devolver cinco clases de códigos de estado:

|**Clase**|**Descripción**|
|---|---|
|`1xx`|Proporciona información y no afecta al procesamiento de la solicitud.|
|`2xx`|Se devuelve cuando una solicitud tiene éxito.|
|`3xx`|Se devuelve cuando el servidor redirige al cliente.|
|`4xx`|Indica solicitudes incorrectas `por parte del cliente`. Por ejemplo, solicitar un recurso que no existe o solicitar un formato incorrecto.|
|`5xx`|Se devuelve cuando hay algún problema `con el propio servidor HTTP`.|

A continuación se presentan algunos de los ejemplos más comunes de cada una de las clases de códigos de estado HTTP anteriores:

|**Código**|**Descripción**|
|---|---|
|`200 OK`|Se devuelve en una solicitud exitosa y el cuerpo de la respuesta suele contener el recurso solicitado.|
|`302 Found`|Redirige al cliente a otra URL. Por ejemplo, redirigir al usuario a su panel de control (dashboard) después de un inicio de sesión exitoso.|
|`400 Bad Request`|Se devuelve al encontrar solicitudes mal formadas, como solicitudes sin terminadores de línea.|
|`403 Forbidden`|Indica que el cliente no tiene el acceso adecuado al recurso. También se puede devolver cuando el servidor detecta una entrada maliciosa por parte del usuario.|
|`404 Not Found`|Se devuelve cuando el cliente solicita un recurso que no existe en el servidor.|
|`500 Internal Server Error`|Se devuelve cuando el servidor no puede procesar la solicitud.|

---
Section 6 / 8

# GET

Cada vez que visitamos una URL, nuestros navegadores realizan por defecto una petición GET para obtener los recursos remotos alojados en esa URL. Una vez que el navegador recibe la página inicial que está solicitando, puede enviar otras peticiones utilizando varios métodos HTTP.


Intentemos acceder a la página con cURL y añadiremos `-i` para ver las cabeceras de respuesta (response headers):

```Bash
Redgnar155@htb[/htb]$ curl -i http://<SERVER_IP>:<PORT>/
```

Para proporcionar las credenciales a través de cURL, podemos usar el flag `-u`, de la siguiente manera:

```Bash
Redgnar155@htb[/htb]$ curl -u admin:admin http://<SERVER_IP>:<PORT>/
```

Hay otro método con el que podemos proporcionar las credenciales de `autenticación básica HTTP`, que es directamente a través de la URL como (`username:password@URL`):

```Bash
Redgnar155@htb[/htb]$ curl http://admin:admin@<SERVER_IP>:<PORT>/
```

El método **GET** es uno de los métodos HTTP más utilizados para **solicitar información a un servidor**. Su característica principal es que los datos que se envían viajan en la **URL**, como parámetros de consulta (_query parameters_), por lo que no modifica información en el servidor; únicamente la solicita.

La lección principal es que una petición **GET** puede reproducirse fácilmente con `curl`. Como pentester, es una habilidad fundamental porque puedes **imitar exactamente las solicitudes que hace un navegador**, modificar sus parámetros y observar cómo responde el servidor, todo sin necesidad de utilizar la interfaz web. Esto convierte a `curl` en una herramienta muy útil para analizar y probar aplicaciones web durante la fase de reconocimiento y validación de funcionalidades.

---
Section 7 / 8

# Post

Este comando de `curl` es muy común en pruebas de aplicaciones web porque simula el envío de un formulario de inicio de sesión. Como pentester, cada bandera tiene un propósito específico.

```Bash
curl -X POST -d 'username=admin&password=admin' http://154.57.164.82:31469 -i
```

|Bandera|Significado|¿Para qué la usa un pentester?|
|---|---|---|
|`-X POST`|Especifica el método HTTP que utilizará la petición.|Permite probar endpoints que aceptan distintos métodos (`GET`, `POST`, `PUT`, `DELETE`, `OPTIONS`, etc.) y verificar cómo responde la aplicación.|
|`-d`|Envía datos en el cuerpo (_body_) de la petición. Al usar `-d`, `curl` también añade automáticamente la cabecera `Content-Type: application/x-www-form-urlencoded`.|Se utiliza para enviar formularios, credenciales, parámetros de búsqueda o cualquier dato que normalmente introduciría un usuario en una página web.|
|`-i`|Muestra las cabeceras HTTP de la respuesta junto con el cuerpo.|Permite analizar el código de estado (`200`, `302`, `403`, etc.), cookies (`Set-Cookie`), redirecciones (`Location`) y otras cabeceras importantes.|

---

## Analizando el comando

### `-X POST`

Le indica al servidor que la petición utilizará el método **POST**.

Sin esta bandera, `curl` utiliza **GET** por defecto. Aunque hay un detalle importante: cuando usas `-d`, `curl` cambia automáticamente el método a **POST**, por lo que en este caso `-X POST` es **redundante**.

Estos dos comandos son equivalentes:

```Bash
curl -d 'username=admin&password=admin' http://IP
```

```Bash
curl -X POST -d 'username=admin&password=admin' http://IP
```

Muchos pentesters escriben `-X POST` por claridad, para que quede explícito el método utilizado.

---

### `-d`

La opción `-d` significa **data**.

Los datos se envían en el cuerpo de la petición con formato de formulario:

```
username=admin&password=admin
```

El servidor recibe algo equivalente a:

```HTTP
POST / HTTP/1.1
Host: 154.57.164.82:31469
Content-Type: application/x-www-form-urlencoded

username=admin&password=admin
```

Como pentester, esta opción es fundamental para:

- Enviar credenciales.
- Probar formularios de login.
- Modificar parámetros ocultos.
- Automatizar pruebas de autenticación.
- Verificar cómo responde la aplicación a diferentes entradas.

Por ejemplo, puedes cambiar fácilmente un valor:

```Bash
curl -d 'username=admin&password=test123' http://IP
```

o probar parámetros inesperados:

```Bash
curl -d 'username=admin&password=admin&role=admin' http://IP
```

---

### `-i`

Normalmente `curl` solo muestra el contenido de la respuesta:

```
Welcome admin
```

Con `-i`, también verás las cabeceras HTTP:

```HTTP
HTTP/1.1 302 Found
Location: /dashboard
Set-Cookie: PHPSESSID=abc123
Content-Type: text/html
```

Como pentester, esto te permite identificar:

- Si el inicio de sesión fue exitoso (`302 Found` con redirección al panel).
- Si el servidor creó una sesión (`Set-Cookie`).
- Si hubo un error (`403 Forbidden`, `401 Unauthorized`).
- Si existen cabeceras de seguridad o información del servidor.

---

# ¿Qué está haciendo este comando?

El comando simula que un usuario envía un formulario de autenticación.

1. Envía una petición **POST**.
2. Coloca las credenciales `admin/admin` en el cuerpo de la petición.
3. Espera la respuesta del servidor.
4. Muestra tanto las cabeceras como el contenido de la respuesta.

Es exactamente lo que haría un navegador al pulsar el botón **"Iniciar sesión"** en un formulario tradicional.

---

# Como pentester, ¿cuándo usarías cada bandera?

|Situación|Bandera|
|---|---|
|Cambiar el método HTTP|`-X`|
|Enviar datos de un formulario|`-d`|
|Ver cabeceras de la respuesta|`-i`|
|Ver el proceso completo de la comunicación (petición y respuesta)|`-v`|
|Autenticación HTTP Basic|`-u usuario:contraseña`|
|Añadir cabeceras personalizadas|`-H`|
|Seguir redirecciones|`-L`|
|Guardar cookies|`-c cookies.txt`|
|Reutilizar cookies|`-b cookies.txt`|

## Recomendación práctica

Cuando analices una aplicación web con `curl`, intenta seguir este flujo:

1. **Reproduce la petición** observada en las herramientas de desarrollador del navegador.
2. **Usa `-v`** si necesitas ver cómo se envía la petición y cómo responde el servidor.
3. **Usa `-i`** para inspeccionar rápidamente las cabeceras de la respuesta.
4. **Modifica solo un parámetro a la vez** (por ejemplo, el nombre de usuario o una cabecera). Así podrás atribuir cualquier cambio en la respuesta a una única modificación, una práctica esencial para realizar pruebas de forma ordenada y sacar conclusiones fiables.

---


La información importante es:

```HTTP
POST /search.php
Content-Type: application/json
Cookie: PHPSESSID=k3iavnnrp55a7nd2u6mdr9hrsg
```

Y el ejemplo de HTB te dice que el cuerpo debe tener este formato:

```JSON
{"search":"london"}
```

Por lo tanto, para buscar la bandera, tu comando quedaría así:

```Bash
curl -X POST \
-d '{"search":"flag"}' \
-b 'PHPSESSID=k3iavnnrp55a7nd2u6mdr9hrsg' \
-H 'Content-Type: application/json' \
http://154.57.164.82:31469/search.php
```

### ¿Qué hace cada parte?

- `-X POST`: utiliza el método **POST**.
- `-d '{"search":"flag"}'`: envía un objeto JSON con el término de búsqueda.
- `-b 'PHPSESSID=...'`: envía la cookie de sesión para que el servidor reconozca tu sesión autenticada.
- `-H 'Content-Type: application/json'`: indica al servidor que el cuerpo de la petición está en formato JSON.
- `http://154.57.164.82:31469/search.php`: endpoint que procesa la búsqueda.

---

## ¿Por qué ahora se usa `-b` y no `-u`?

En el laboratorio anterior la autenticación era **HTTP Basic**, por eso utilizabas:

```Bash
-u admin:admin
```

En este laboratorio, después de iniciar sesión, el servidor creó una **sesión PHP** y te entregó una cookie:

```
PHPSESSID=k3iavnnrp55a7nd2u6mdr9hrsg
```

Esa cookie es la que identifica que ya estás autenticado, por lo que debes enviarla en cada petición mediante `-b`.

---

### Un consejo como pentester

Cuando copies una petición desde las DevTools, identifica siempre estos cuatro elementos antes de construir el comando con `curl`:

|Elemento|En tu captura|Opción de `curl`|
|---|---|---|
|Método HTTP|`POST`|`-X POST`|
|Cuerpo de la petición|`{"search":"..."}`|`-d`|
|Tipo de contenido|`Content-Type: application/json`|`-H 'Content-Type: application/json'`|
|Autenticación/Sesión|`PHPSESSID=...`|`-b 'PHPSESSID=...'`|

Si sigues esa metodología, podrás convertir casi cualquier petición del navegador en un comando de `curl` de forma sistemática.

---
Section 8 / 8

# API CRUD

### Leer

```Bash
Redgnar155@htb[/htb]$ curl http://<SERVER_IP>:<PORT>/api.php/city/london [{"city_name":"London","country_name":"(UK)"}]
```

```Bash
Redgnar155@htb[/htb]$ curl -s http://<SERVER_IP>:<PORT>/api.php/city/london | jq

[
  {
    "city_name": "London",
    "country_name": "(UK)"
  }
]
```

### Crear

```Bash
Redgnar155@htb[/htb]$ curl -X POST http://<SERVER_IP>:<PORT>/api.php/city/ -d '{"city_name":"HTB_City", "country_name":"HTB"}' -H 'Content-Type: application/json'
```

### Actualizar

```Bash
Redgnar155@htb[/htb]$ curl -X PUT http://<SERVER_IP>:<PORT>/api.php/city/london -d '{"city_name":"New_HTB_City", "country_name":"HTB"}' -H 'Content-Type: application/json'
```

### Eliminar

```Bash
Redgnar155@htb[/htb]$ curl -X DELETE http://<SERVER_IP>:<PORT>/api.php/city/New_HTB_City
```

