

## 1. Actualizar el sistema

```
sudo apt updatesudo apt upgrade -y
```

---

## 2. Instalar Apache

```
sudo apt install apache2 -y
```

Verificar:

```
sudo systemctl status apache2
```

Abrir en el navegador:

```
http://localhost
```

Deberías ver la página de bienvenida de Apache.

---

## 3. Instalar PHP

Instalar PHP y módulos comunes:

```Bash
sudo apt install php php-cli php-common php-mysql php-curl php-xml php-mbstring php-zip php-gd -y
```

Verificar:

```
php -v
```

---

## 4. Comprobar PHP en Apache

Crear un archivo:

```
sudo nano /var/www/html/info.php
```

Contenido:

```
<?phpphpinfo();?>
```

Guardar y abrir:

```
http://localhost/info.php
```

---

## 5. Instalar MySQL

```
sudo apt install mysql-server -y
```

Verificar:

```
sudo systemctl status mysql
```

---

## 6. Configurar MySQL

Ejecutar:

```Bash
sudo mysql_secure_installation
```

Seguir el asistente para:

- Configurar contraseña de root
- Eliminar usuarios anónimos
- Deshabilitar acceso remoto de root
- Eliminar base de datos de pruebas

---

## 7. Entrar a MySQL

```
sudo mysql
```

O:

```
mysql -u root -p
```

Mostrar bases de datos:

```
SHOW DATABASES;
```

---

## Crear una base de datos para practicar

Ejecuta:

```SQL
CREATE DATABASE curso_php;
```

Verifica:

```SQL
SHOW DATABASES;
```

Ahora debería aparecer:

```
curso_php
```


## Crear un usuario para tus proyectos

No es recomendable usar `root` para desarrollar aplicaciones.

Ejecuta:

```SQL
CREATE USER 'developer'@'localhost' IDENTIFIED BY 'Dev2026!';
```

Otorga permisos sobre la base de datos:

```SQL
GRANT ALL PRIVILEGES ON curso_php.* TO 'developer'@'localhost';
```

Aplica los cambios:

```SQL
FLUSH PRIVILEGES;
```

Verifica los usuarios:

```SQL
SELECT User, Host FROM mysql.user;
```

```Bash
mysql> SELECT User, Host FROM mysql.user;
+------------------+-----------+
| User             | Host      |
+------------------+-----------+
| debian-sys-maint | localhost |
| developer        | localhost |
| mysql.infoschema | localhost |
| mysql.session    | localhost |
| mysql.sys        | localhost |
| root             | localhost |
+------------------+-----------+
6 rows in set (0.00 sec)

mysql> 
```

## Salir de MySQL

```SQL
EXIT;
```

o

```SQL
QUIT;
```


## Probar el nuevo usuario

Desde la terminal:

```
mysql -u developer -p
```

Ingresa la contraseña:

```
Dev2026!
```

Una vez dentro:

```
USE curso_php;SHOW TABLES;
```

---
---

# Instalar Composer 

# 1. Actualizar repositorios

Ejecuta:

```
sudo apt update
```

---

# 2. Instalar dependencias necesarias

```
sudo apt install curl unzip git -y
```

Estas herramientas son utilizadas por Composer y por muchos proyectos PHP.

Verifica:

```
git --versioncurl --version
```

---

# 3. Descargar el instalador oficial de Composer

Ve a tu carpeta personal:

```
cd ~
```

Descarga Composer:

```
curl -sS https://getcomposer.org/installer -o composer-setup.php
```

Verifica que se descargó:

```
ls
```

Deberías ver:

```
composer-setup.php
```

---

# 4. Instalar Composer globalmente

Ejecuta:

```
sudo php composer-setup.php --install-dir=/usr/local/bin --filename=composer
```

Si todo sale bien verás algo parecido a:

```
All settings correct for using ComposerDownloading...Composer (version X.X.X) successfully installed to:/usr/local/bin/composer
```

---

# 5. Eliminar el instalador

Ya no lo necesitaremos:

```
rm composer-setup.php
```

---

# 6. Verificar la instalación

Ejecuta:

```
composer --version
```

Deberías obtener algo parecido a:

```
Composer version 2.x.xPHP version 8.3.6
```

Si aparece esa información, Composer quedó instalado correctamente.

---

# 7. Configuración recomendada para desarrollo

Configura un tiempo de espera más amplio:

```
composer config --global process-timeout 2000
```

Verifica dónde guarda Composer su configuración:

```
composer global config home
```

---

# 8. Crear una carpeta para tus proyectos

Te recomiendo esta estructura:

```
mkdir -p ~/Proyectos
```

Verifica:

```
ls ~
```

Deberías ver:

```
Proyectos
```

---

# 9. Verificar que todo el entorno está listo

Ejecuta:

```
php -vcomposer --versionmysql --version
```


