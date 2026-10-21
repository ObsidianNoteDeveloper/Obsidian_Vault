Subsistema de Windows para Linux (WSL)

## Configuración inicial de WSL 2 y herramientas de C/C++ en Ubuntu

#### Comprobar el estado de WSL

El comando `wsl --status` muestra información sobre la configuración general del Subsistema de Windows para Linux (WSL).

```BASH
PS C:\Users\rojor> wsl --status
Distribución predeterminada: Ubuntu-24.04
Versión predeterminada: 2
```

#### Iniciar Ubuntu desde PowerShell

La opción `-d` significa distribution (distribución). Permite indicar qué distribución de Linux quieres iniciar.

```BASH
PS C:\Users\rojor> wsl -d Ubuntu-24.04
rojor@Redgnar055:/mnt/c/Users/rojor$
```

La ruta `/mnt/c/Users/rojor` permite entender una de las características más útiles de WSL: Linux puede acceder a los archivos de Windows.

#### Cambiar al directorio personal de Linux

El comando `cd` (change directory) permite cambiar de directorio. El símbolo `~` representa el directorio personal del usuario actual.

`pwd` significa print working directory y muestra la ruta absoluta del directorio de trabajo actual.

```BASH
rojor@Redgnar055:/mnt/c/Users/rojor$ cd ~/
rojor@Redgnar055:~$ pwd
/home/rojor
```

Por lo tanto, al ejecutar `cd ~/`, pase de estar en la carpeta de Windows montada en `/mnt/c/Users/rojor` al directorio personal del usuario de Ubuntu.

> [!Note]
> Esta distinción es importante: `/home/rojor` pertenece al entorno Linux, mientras que `/mnt/c/Users/rojor` corresponde a archivos almacenados en la unidad C: de Windows

#### Lista de archivos y directorios 

`ls` (list) muestra los archivos y directorios visibles que existen en la ubicación actual.

Linux también utiliza archivos ocultos, cuyos nombres suelen comenzar con un punto.

```BASH
rojor@Redgnar055:~$ ls
Documentos
```

Las opciones `-l` y `-a` modifican la información que muestra `ls`:

- `-l`: presenta un listado detallado, con permisos, propietario, grupo, tamaño y fecha.
    
- `-a`: incluye los archivos ocultos, incluso los nombres especiales `.` y `..`.

```BASH
rojor@Redgnar055:~$ ls -la
total 44
drwxr-x--- 6 rojor rojor 4096 Sep 25 13:59 .
drwxr-xr-x 3 root  root  4096 Sep 20 20:04 ..
-rw------- 1 rojor rojor 1735 Sep 30 22:39 .bash_history
-rw-r--r-- 1 rojor rojor  220 Sep 20 20:04 .bash_logout
-rw-r--r-- 1 rojor rojor 3771 Sep 20 20:04 .bashrc
drwx------ 3 rojor rojor 4096 Sep 25 13:21 .cache
drwxr-xr-x 3 rojor rojor 4096 Sep 25 13:59 .dotnet
-rw-rw-r-- 1 rojor rojor    0 Oct 16 08:26 .motd_shown
-rw-r--r-- 1 rojor rojor  807 Sep 20 20:04 .profile
-rw-r--r-- 1 rojor rojor    0 Sep 20 20:18 .sudo_as_admin_successful
drwxr-xr-x 5 rojor rojor 4096 Sep 25 13:21 .vscode-server
-rw-r--r-- 1 rojor rojor  183 Sep 25 13:21 .wget-hsts
drwxr-xr-x 3 rojor rojor 4096 Sep 25 11:52 Documentos
```



```BASH
rojor@Redgnar055:~/Documentos$ cd Programacion/
rojor@Redgnar055:~/Documentos/Programacion$ ls
C  SisDistribuidos
rojor@Redgnar055:~/Documentos/Programacion$ ls C
holaMundo  holaMundo.c
rojor@Redgnar055:~/Documentos/Programacion$ gcc --version
gcc (Ubuntu 13.3.0-6ubuntu2~24.04.1) 13.3.0
Copyright (C) 2023 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

rojor@Redgnar055:~/Documentos/Programacion$ g++ --version
g++ (Ubuntu 13.3.0-6ubuntu2~24.04.1) 13.3.0
Copyright (C) 2023 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

rojor@Redgnar055:~/Documentos/Programacion$ gdb --version
GNU gdb (Ubuntu 15.1-1ubuntu1~24.04.1) 15.1
Copyright (C) 2024 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
rojor@Redgnar055:~/Documentos/Programacion$
```


