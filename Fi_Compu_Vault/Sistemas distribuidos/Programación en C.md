

# **Windows Subsystem for Linux 2** o Subsistema de Windows para Linux 2

Es una herramienta de _Microsoft_ que te permite ejecutar un entorno Linux completo directamente dentro de Windows, sin necesidad de configurar un arranque dual (_dual-boot_) ni recurrir a máquinas virtuales tradicionales pesadas.

A diferencia de la primera versión de WSL, que traducía los comandos de Linux a Windows, WSL2 incluye un **kernel de Linux real y nativo** optimizado por Microsoft. Este se ejecuta en segundo plano a través de una arquitectura de virtualización extremadamente ligera.

```Bash
PS C:\Users\rojor\OneDrive\Escritorio> wsl
rojor@Redgnar055:/mnt/c/Users/rojor/OneDrive/Escritorio$ cd ~/
rojor@Redgnar055:~$ pwd
/home/rojor
rojor@Redgnar055:~$
```

Los comandos `ps` y `ps -fea` se utilizan en Linux (y dentro de WSL2) para **ver los procesos que se están ejecutando en el sistema** en un momento determinado. Funcionan de forma similar al "Administrador de tareas" de Windows, pero desde la línea de comandos.

```Bash
rojor@Redgnar055:~$ ps
    PID TTY          TIME CMD
    289 pts/0    00:00:00 bash
   1131 pts/0    00:00:00 ps
rojor@Redgnar055:~$ ps -fea
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 16:41 ?        00:00:00 /sbin/init
root           2       1  0 16:41 hvc0     00:00:00 /init
root           6       2  0 16:41 hvc0     00:00:00 plan9 --control-socket 7 --lo
...
```

#### ps

- **Sesión limpia:** Solo tienes abierta una única terminal.
- El proceso `bash` (PID 289) es la consola donde estás escribiendo.
- El proceso `ps` (PID 1131) apareció solo por una fracción de segundo para tomar esta foto de tus procesos actuales y luego se cerró.
- **`pts/0`** indica que ambos procesos comparten la misma terminal virtual (la pestaña que tienes abierta).

#### ps -fea

Muestra las entrañas de cómo arranca Linux en Windows. Los puntos clave que se interpretan aquí son:

- **Systemd activado (Muy importante):** El proceso con **PID 1** (el primer proceso y el padre de todos) es `/sbin/init`. En las versiones modernas de WSL2, esto significa que tu distribución tiene habilitado el soporte nativo para `systemd`, permitiéndote usar comandos como `systemctl`.
- **Arquitectura de WSL2:** Los procesos `/init` (PID 2) y `plan9` (PID 6) son las herramientas internas de Microsoft que permiten que Windows se comunique con Linux, compartan archivos y manejen la red de forma invisible.

---

#### Opciones estilo BSD (Sin guion)

Son las más populares entre desarrolladores para monitorear el rendimiento en tiempo real:

- **`aux`**: Es la alternativa más común a `-fea`. Muestra todos los procesos del sistema (`a` y `x`), pero añade información crítica como el **uso exacto de CPU y Memoria (RAM)** de cada proceso, además del usuario que lo corre (`u`).
	
- **`lax`**: Muestra información técnica detallada de manera muy rápida porque **no traduce los números de usuario a nombres** (ahorra tiempo de CPU). Incluye detalles de prioridad del sistema (`NI` y `PRI`).

#### Opciones estilo UNIX/POSIX (Con guion)

Ideales para automatizar tareas, hacer scripts o buscar datos muy específicos:

- **`-u [usuario]`**: Filtra la lista para mostrar **únicamente los procesos de un usuario específico**. (Ejemplo: `ps -u rojor`).
	
- **`-C [nombre]`**: Busca procesos filtrando **exactamente por el nombre del comando** o programa. (Ejemplo: `ps -C bash`).
	
- **`-p [PID]`**: Muestra información **únicamente de los IDs de procesos específicos** que le indiques. (Ejemplo: `ps -p 289`).
	
- **`-o [columnas]`**: Te permite **personalizar por completo qué columnas quieres ver** y ocultar el resto. Es excelente para scripts. (Ejemplo: `ps -eo pid,user,cmd` solo mostrará el ID, el usuario y el comando).

---

## Código 1

el objetivo es observar cómo `fork()` crea un nuevo proceso y cómo el valor que devuelve permite distinguir entre el **proceso padre** y el **proceso hijo**. También se debe comprobar que la misma lógica puede expresarse mediante `switch`.

```C
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(void)
{
    int pid = 0;

    pid = fork();

    if (pid == 0)
    {
        printf("Código a ejecutar en el proceso hijo\n");
        exit(0);
    }
    else
    {
        printf("Código a ejecutar en el proceso padre\n");
        exit(0);
    }
}
```

Salida: 

```C
Codigo a ejecutar en el proceso padre
Codigo a ejecutar en el proceso hijo
```

**Librerías usadas:**

- **`<stdio.h>` (Standard Input/Output):** Se usa para **entrada y salida de datos**. Permite mostrar texto en pantalla (con `printf`) y leer lo que escribe el usuario (con `scanf`).
	
- **`<stdlib.h>` (Standard Library):** Se usa para **gestión de memoria y control del sistema**. Permite reservar memoria dinámica (con `malloc`/`free`), convertir texto a números (con `atoi`) o generar números aleatorios (con `rand`).
	
- **`<unistd.h>` (POSIX Operating System API):** Se usa para **interactuar directamente con el sistema operativo (como WSL2/Linux)**. Permite pausar el programa (con `sleep`), manejar procesos (con `fork`/`exec`) y trabajar con archivos a bajo nivel.

#### Función fork()

Se usa en sistemas basados en Unix/Linux (como WSL2) para crear un nuevo proceso clonando el proceso actual. El proceso original se llama **padre** y el nuevo proceso se llama **hijo**.

A partir del momento en que se ejecuta `fork()`, el sistema operativo duplica el programa y **ambos procesos corren al mismo tiempo (en paralelo)**, ejecutando exactamente la misma línea de código que sigue.

```C
int pid = 0; 
pid = fork();
```

Este bloque **crea el proceso hijo y guarda una "llave" (un identificador) en la variable `pid`** para que el programa pueda saber si es el padre o el hijo.

Aunque ambos procesos ejecutan la misma variable `pid`, **el valor que recibe cada uno es diferente**, y así es como se diferencian:

1. **En el proceso Hijo:** `fork()` devuelve exactamente **`0`**. Si `pid == 0`, el programa sabe que es el hijo.
2. **En el proceso Padre:** `fork()` devuelve el **PID (ID de proceso) real del hijo** (un número mayor a 0, como `1132`). Si `pid > 0`, el programa sabe que es el padre.

La función **`exit(0)`** se usa para terminar la ejecución del proceso actual de forma inmediata y reportar al sistema operativo que el programa finalizó correctamente.

#### Programa utilizando switch

```C
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(void)
{
    int pid = 0;

    pid = fork();

    switch (pid)
    {
        case 0:
            printf("Código a ejecutar en el proceso hijo\n");
            exit(0);

        case -1:
            printf("Error al crear el proceso\n");
            exit(1);

        default:
            printf("Código a ejecutar en el proceso padre\n");
            exit(0);
    }

    return 0;
}
```

Salida: 

```C
Codigo a ejecutar en el proceso padre
Codigo a ejecutar en el proceso hijo
```


## Código 2

> [!Note] Ejercicio
> Programe una aplicación que cree un proceso hijo a partir de un proceso padre, el hijo creado a su vez creará tres procesos hijos más. A su vez cada uno de los tres procesos creará dos procesos más. Cada uno de los procesos creados imprimirá en la pantalla el pid de su padre si se trata de un hijo terminal o los pid’s de sus hijos creados si se trata de un proceso padre.

```C
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/wait.h>

int main(void){

    pid_t pid;
    pid_t hijos[3];

    /* El proceso padre crea un hijo */
    pid = fork();

    if (pid < 0){

        perror("Error al crear el proceso");
        exit(1);
    }

    /* Proceso hijo */
    if (pid == 0){

        printf("Proceso hijo: PID = %d\n", getpid());

        /* El hijo crea tres procesos */
        for (int i = 0; i < 3; i++){

            hijos[i] = fork();

            if (hijos[i] < 0){
                perror("Error al crear proceso");
                exit(1);
            }

            /* Cada uno de los tres hijos */
            if (hijos[i] == 0){
                pid_t nietos[2];
                
                /* Cada hijo crea dos procesos terminales */
                for (int j = 0; j < 2; j++){
                    nietos[j] = fork();

                    if (nietos[j] < 0){
                        perror("Error al crear proceso");
                        exit(1);
                    }

                    /* Proceso terminal */
                    if (nietos[j] == 0){
                        printf(
                            "Proceso terminal: PID = %d, PID de mi padre = %d\n",
                            getpid(),
                            getppid()
                        );
                        exit(0);
                    }
                }
  
                /* Este proceso creó dos hijos */
                printf(
                    "Proceso padre: PID = %d, hijos = %d, %d\n",
                    getpid(),
                    nietos[0],
                    nietos[1]
                );

                /* Esperar a que terminen sus dos hijos */
                waitpid(nietos[0], NULL, 0);
                waitpid(nietos[1], NULL, 0);

                exit(0);
            }
        }

        /* El primer hijo creó tres procesos */
        printf(
            "Proceso padre: PID = %d, hijos = %d, %d, %d\n",
            getpid(),
            hijos[0],
            hijos[1],
            hijos[2]
        );

        /* Esperar a que terminen los tres hijos */
        for (int i = 0; i < 3; i++){
            waitpid(hijos[i], NULL, 0);
        }
        exit(0);
    }

    /* Proceso padre original */
    printf(
        "Proceso padre original: PID = %d, hijo creado = %d\n",
        getpid(),
        pid);
    waitpid(pid, NULL, 0);

    return 0;
}
```

En total se crean **10 procesos nuevos**, además del proceso original:
- 1 proceso hijo creado por el padre original.
- Ese hijo crea 3 procesos.
- Cada uno de esos 3 procesos crea 2 procesos.
- 1+3+(3×2)=101 + 3 + (3\times2) = 10 procesos creados.

```C
    pid_t pid;
    pid_t hijos[3];
```

Esta sintaxis sirve para **declarar variables especializadas en almacenar IDs de procesos**, una de forma individual y la otra en un grupo o arreglo.

`pid_t` es un **tipo de datos especial en C** (definido en las librerías `<sys/types.h>` o `<unistd.h>`).

- Se creó específicamente para guardar **PIDs** (Process IDs). El sistema operativo lo usa en lugar de un `int` común para garantizar que el programa funcione correctamente en cualquier tipo de computadora o arquitectura, sin importar si es de 32 o 64 bits.

```C
    printf(
	    "Proceso padre original: PID = %d, hijo creado = %d\n",
		getpid(),
		pid);

    waitpid(pid, NULL, 0);
```

Este bloque de código se utiliza para rastrear el nacimiento de un proceso hijo y asegurar que el padre no termine su ejecución hasta que el hijo haya finalizado por completo.

- `getpid()`: Imprime el ID único que el sistema operativo (en este caso, WSL2/Linux) le asignó a este proceso padre.

- `waitpid`
	- Inmediatamente después de imprimir el mensaje, el padre llega a esta línea y **se congela por completo (entra en estado de espera)**.
	
	El comportamiento de sus tres parámetros funciona así:
	
	1. **`pid`**: Le dice al sistema operativo: _"Quédate congelado aquí hasta que el proceso con este ID específico (el hijo) muera"_.
	2. **`NULL`**: Significa que al padre no le interesa guardar el reporte de daños o código de error del hijo; solo le importa saber que ya terminó.
	3. **`0`**: Es una bandera de configuración que obliga al padre a esperar de forma **estricta y síncrona**. No avanzará a la siguiente línea de código bajo ninguna circunstancia hasta que el hijo deje de existir.

```C
if (pid < 0) { 
	perror("Error al crear el proceso"); 
	exit(1); 
}
```

Este bloque **es la forma correcta** de manejar errores al usar `fork()` en C.

- A diferencia de `printf`, la función `perror()` no solo imprime el texto (`"Error al crear el proceso"`), sino que automáticamente le añade dos puntos y el motivo exacto por el cual falló el sistema operativo (por ejemplo: `Error al crear el proceso: Resource temporarily unavailable`).

