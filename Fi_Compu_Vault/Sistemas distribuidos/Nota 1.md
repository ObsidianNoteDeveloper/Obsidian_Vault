
# Sistemas Distribuidos

## Sistema Operativo

### 1.1 ¿Qué es un sistema operativo?

Un **sistema operativo (SO)** es el software encargado de administrar los recursos de una computadora y proporcionar servicios tanto a los programas como a los usuarios. Actúa como intermediario entre el hardware y las aplicaciones.

Una computadora moderna necesita ejecutar varias tareas aparentemente al mismo tiempo. Por ejemplo, puede estar reproduciendo música, ejecutando un navegador, descargando un archivo y respondiendo a las acciones del usuario. El sistema operativo se encarga de administrar estos recursos y coordinar los procesos necesarios.

Entre sus principales funciones se encuentran:

- **Gestión de procesos**
- **Planificación de procesos**
- **Gestión de memoria**
- **Gestión de concurrencia**
- **Gestión de entrada/salida (E/S)**
- **Gestión de archivos**
- **Gestión de dispositivos**
- **Seguridad y protección**
- **Gestión de redes**

---

# Procesos

## 2.1 Modelo del proceso

### Definición

Un **proceso** es una instancia de un programa que se encuentra en ejecución.

No debemos confundir **programa** con **proceso**:

> Un programa es un conjunto de instrucciones almacenadas, mientras que un proceso es ese programa cuando está siendo ejecutado.

Por ejemplo, tener `notepad.exe` almacenado en el disco corresponde al **programa**. Cuando abrimos el Bloc de notas, el sistema operativo crea un **proceso** asociado a ese programa.

Un proceso incluye, entre otras cosas:

- El código del programa.
- Los datos que está utilizando.
- El **contador de programa (PC)**.
- Los registros del procesador.
- La información de memoria.
- El estado actual del proceso.
- Recursos asignados.

Conceptualmente, cada proceso parece tener su propia CPU. En realidad, la CPU física va alternando rápidamente entre diferentes procesos, dando la impresión de que se ejecutan simultáneamente.

---

## 2.2 Características de un proceso

Un proceso puede describirse mediante diferentes elementos:

|Elemento|Descripción|
|---|---|
|**PID**|Identificador único del proceso.|
|**Estado**|Indica si está ejecutándose, listo, bloqueado, etc.|
|**Prioridad**|Determina su importancia para la planificación.|
|**Contador de programa**|Indica cuál es la siguiente instrucción que debe ejecutarse.|
|**Registros**|Contienen información temporal utilizada por la CPU.|
|**Punteros de memoria**|Permiten localizar diferentes regiones de memoria utilizadas por el proceso.|
|**Recursos**|Archivos, dispositivos y otros recursos asignados.|

### PID

El **PID (Process ID)** es un número utilizado por el sistema operativo para identificar un proceso.

Por ejemplo:

```
Proceso: navegador
PID: 3524
```

---

# Estados de un proceso

Durante su vida, un proceso puede pasar por diferentes estados.

Los estados básicos son:

```
             ┌──────────────┐
             │    Listo     │
             └──────┬───────┘
                    │
                    ▼
             ┌──────────────┐
             │  Ejecutando  │
             └───┬──────┬───┘
                 │      │
       espera E/S│      │termina
                 │      │
                 ▼      ▼
          ┌──────────┐  Fin
          │ Bloqueado│
          └────┬─────┘
               │
               │ E/S terminada
               ▼
             Listo
```

### Ejecutando

El proceso está utilizando actualmente la CPU.

### Listo

El proceso puede ejecutarse, pero está esperando que la CPU quede disponible.

### Bloqueado

El proceso no puede continuar porque está esperando algún evento, por ejemplo:

- Una operación de entrada/salida.
- La llegada de datos.
- Un recurso.
- Una señal de otro proceso.

---

# Creación de procesos

Un sistema operativo puede crear nuevos procesos por diferentes motivos.

### Razones para crear un proceso

1. **Nuevo proceso por lotes**
    - El sistema necesita ejecutar un trabajo programado.
2. **Sesión interactiva**
    - El usuario inicia una aplicación desde la terminal o interfaz gráfica.
3. **El sistema necesita proporcionar un servicio**
    - El propio sistema operativo crea procesos para realizar determinados servicios.
4. **Un proceso existente crea otro proceso**
    - Un proceso puede solicitar al sistema operativo la creación de otro proceso.

Cuando un proceso crea otro:

```
Proceso padre
     │
     │ crea
     ▼
Proceso hijo
```

El proceso que crea al nuevo proceso se denomina **padre**, mientras que el proceso creado se denomina **hijo**.

Los procesos padre e hijo pueden comunicarse y cooperar entre sí.

---

# fork()

En sistemas Unix/Linux, `fork()` es una llamada al sistema utilizada para **crear un nuevo proceso**.

Su comportamiento puede representarse así:

```
                 Proceso padre
                      │
                      │ fork()
                      ▼
              ┌───────────────┐
              │ Sistema       │
              │ operativo     │
              └───────┬───────┘
                      │
             ┌────────┴────────┐
             ▼                 ▼
       Proceso padre      Proceso hijo
       recibe PID        recibe 0
```

Una característica importante de `fork()` es que **la llamada retorna en ambos procesos**.

En el proceso hijo:

```
fork() == 0
```

En el proceso padre:

```
fork() > 0
```

El valor recibido por el padre corresponde al **PID del proceso hijo**.

### Ejemplo sencillo en C

```C
#include <stdio.h>
#include <unistd.h>

int main() {

    pid_t pid = fork();

    if (pid == 0) {
        printf("Soy el proceso hijo\n");
    }
    else {
        printf("Soy el proceso padre\n");
    }

    return 0;
}
```

El resultado puede ser:

```
Soy el proceso padre
Soy el proceso hijo
```

El orden exacto puede variar debido a la planificación del sistema operativo.

---

# Funciones relacionadas con procesos

Algunas funciones comunes en sistemas Unix/Linux son:

|Función|Función|
|---|---|
|`fork()`|Crea un nuevo proceso.|
|`getpid()`|Obtiene el PID del proceso actual.|
|`getppid()`|Obtiene el PID del proceso padre.|
|`wait()`|Permite esperar a que termine un proceso hijo.|
|`exit()`|Finaliza un proceso.|
|`exec()`|Sustituye el programa que está ejecutando un proceso por otro.|

Una combinación muy importante es:

```
fork()
  ↓
crea proceso
  ↓
exec()
  ↓
ejecuta otro programa
```

---

# Terminación de procesos

Un proceso puede terminar por diferentes razones.

### Razones para terminar un proceso

- **Finalización normal:** el programa terminó correctamente.
- **Error:** ocurre una condición que impide continuar.
- **Error fatal:** ocurre un problema grave durante la ejecución.
- **Límite excedido:** el proceso supera un límite de tiempo o recursos.
- **Falta de memoria:** no existe memoria suficiente para continuar.
- **Terminación por otro proceso:** otro proceso o el sistema operativo solicita su finalización.
- **Intervención del usuario:** por ejemplo, cuando se cierra una aplicación.

---

# Cola de procesos

Debido a que normalmente existen más procesos que CPUs disponibles, el sistema operativo necesita organizar los procesos.

Para esto utiliza **colas de procesos**.

Una representación sencilla sería:

```
                 CPU
                  ▲
                  │
          ┌───────┴───────┐
          │   Ejecutando  │
          └───────────────┘
                  ▲
                  │
        ┌─────────┴─────────┐
        │    Cola de listos │
        ├───────────────────┤
        │ Proceso A         │
        │ Proceso B         │
        │ Proceso C         │
        │ Proceso D         │
        └───────────────────┘
```

El **planificador (scheduler)** determina qué proceso de la cola debe recibir la CPU.

---

# Planificación de procesos

La **planificación** es el mecanismo mediante el cual el sistema operativo decide qué proceso debe utilizar la CPU.

Algunos algoritmos de planificación son:

- **FCFS (First Come, First Served)**
- **Round Robin**
- **Shortest Job First (SJF)**
- **Prioridades**
- **Multilevel Queue**

El objetivo es aprovechar eficientemente la CPU y proporcionar tiempos de respuesta adecuados.

---

# Concurrencia

La **concurrencia** ocurre cuando varios procesos o hilos avanzan durante un mismo periodo de tiempo, aunque no necesariamente estén ejecutándose exactamente al mismo instante.

En una CPU con un solo núcleo, el sistema operativo puede realizar:

```
Proceso A → Proceso B → Proceso A → Proceso C → Proceso B
```

mediante cambios rápidos de contexto.

En sistemas multinúcleo, algunos procesos pueden ejecutarse realmente de manera simultánea.

### Cambio de contexto

Cuando la CPU cambia de un proceso a otro, el sistema operativo debe guardar el estado del proceso actual y recuperar el estado del siguiente.

Este mecanismo se conoce como **cambio de contexto (context switch)**.

---

# Hilos

Un **hilo (thread)** es una unidad de ejecución dentro de un proceso.

Un proceso puede contener uno o varios hilos.

### Flujo único

Un programa puede tener un solo hilo:

```
Proceso
   │
   └── Hilo 1
```

### Flujo múltiple

También puede tener varios:

```
Proceso
   ├── Hilo 1
   ├── Hilo 2
   ├── Hilo 3
   └── Hilo 4
```

Esto se conoce como **multithreading**.

Los hilos de un mismo proceso comparten determinados recursos, especialmente el espacio de memoria del proceso, aunque cada hilo posee su propio contador de programa, registros y pila.

### Ventajas

- Permiten realizar varias tareas dentro de un proceso.
- Pueden mejorar el aprovechamiento de la CPU.
- Facilitan la creación de aplicaciones concurrentes.
- Permiten atender múltiples tareas o solicitudes.
- Son muy importantes en sistemas distribuidos y servidores.

> **Corrección importante de tus apuntes:** decir que "en los hilos el SO no asigna espacio de memoria ni tiempo de procesamiento" no es correcto. Los hilos **comparten el espacio de memoria del proceso**, pero el sistema operativo sí puede planificarlos y asignarles tiempo de CPU.

---

# Redes de computadoras

## 12.1 Definición

Una **red de computadoras** es un conjunto de computadoras y dispositivos interconectados capaces de intercambiar información y compartir recursos.

El objetivo principal de una red es permitir que:

- Los datos puedan compartirse.
- Los usuarios puedan comunicarse.
- Se compartan dispositivos.
- Se compartan servicios.
- Los recursos puedan utilizarse independientemente de su ubicación.

Por ejemplo:

```
Computadora A ──┐
                │
Computadora B ──┼── Red ── Servidor
                │
Computadora C ──┘
```

---

# Arquitectura computacional

Una computadora está formada por diferentes componentes fundamentales:

- **CPU:** unidad de procesamiento.
- **RAM:** memoria principal para almacenar temporalmente datos y programas en ejecución.
- **Memoria de instrucciones:** almacenamiento de programas e instrucciones.
- **Interconexiones:** buses que transportan información.
- **Entrada/Salida:** dispositivos como teclado, pantalla, discos, etc.
- **Fuente de alimentación.**

Los buses pueden transportar diferentes tipos de información:

- **Bus de datos**
- **Bus de direcciones**
- **Bus de control**

Podemos encontrar esta arquitectura en:

- PC.
- Servidores.
- Tablets.
- Teléfonos celulares.
- Microcomputadoras.
- Sistemas embebidos.

---

# Modelo OSI

El **modelo OSI (Open Systems Interconnection)** es un modelo conceptual que divide la comunicación de una red en **siete capas**.

|Capa|Nombre|Función principal|
|---|---|---|
|7|Aplicación|Servicios de red para las aplicaciones.|
|6|Presentación|Formato, codificación, compresión y cifrado de datos.|
|5|Sesión|Administración de sesiones entre aplicaciones.|
|4|Transporte|Comunicación extremo a extremo y control de transporte.|
|3|Red|Direccionamiento lógico y enrutamiento.|
|2|Enlace de datos|Tramas, direccionamiento físico y control del enlace.|
|1|Física|Transmisión de bits mediante el medio físico.|

### 1. Capa física

Se encarga de transmitir **bits** a través del medio físico.

Incluye aspectos como:

- Cables.
- Conectores.
- Señales eléctricas u ópticas.
- Características físicas de la transmisión.

### 2. Capa de enlace de datos

Organiza los bits en **tramas** y permite la comunicación entre dispositivos conectados directamente.

También puede encargarse de:

- Detección de errores.
- Control del acceso al medio.
- Direccionamiento físico, como MAC.

### 3. Capa de red

Se encarga de determinar cómo transportar paquetes desde un origen hasta un destino.

Aquí encontramos conceptos como:

- Direcciones IP.
- Enrutamiento.
- Routers.

### 4. Capa de transporte

Proporciona comunicación **extremo a extremo** entre aplicaciones.

Puede encargarse de:

- Segmentación.
- Control de flujo.
- Control de errores.
- Entrega confiable, dependiendo del protocolo.

Ejemplos:

- TCP.
- UDP.

### 5. Capa de sesión

Administra las sesiones de comunicación entre aplicaciones.

Puede encargarse de:

- Establecer sesiones.
- Mantenerlas.
- Sincronizarlas.
- Finalizarlas.

### 6. Capa de presentación

Se encarga de representar los datos de manera que puedan ser interpretados correctamente.

Puede involucrar:

- Codificación.
- Conversión de formatos.
- Compresión.
- Cifrado y descifrado.

### 7. Capa de aplicación

Es la capa más cercana al usuario y proporciona servicios de red a las aplicaciones.

Ejemplos:

- HTTP/HTTPS.
- FTP.
- DNS.
- SMTP.
- SSH.

---

# Sistemas distribuidos

## 15.1 Introducción

Las redes de computadoras son fundamentales para los sistemas distribuidos porque permiten que diferentes computadoras puedan comunicarse.

Una idea importante es:

> **Una red permite conectar computadoras; un sistema distribuido utiliza esas computadoras conectadas para trabajar coordinadamente.**

Por eso, las redes constituyen una de las bases de los sistemas distribuidos.

---

# Definición de sistema distribuido

Un **sistema distribuido** es una colección de computadoras independientes que trabajan juntas y que, desde el punto de vista del usuario, pueden aparentar funcionar como un único sistema.

De manera simplificada:

```
          Sistema distribuido
                  │
        ┌─────────┼─────────┐
        ▼         ▼         ▼
     PC 1       PC 2      PC 3
        │         │         │
        └─────────┼─────────┘
                  │
                 Red
```

Aunque existen varias computadoras físicamente independientes, el objetivo es que el usuario pueda utilizar los servicios sin tener que preocuparse necesariamente por dónde se encuentra cada recurso.

---

# Tecnologías que impulsaron los sistemas distribuidos

El desarrollo de los sistemas distribuidos fue favorecido especialmente por:

### Microprocesadores

Permitieron construir computadoras cada vez más pequeñas, económicas y potentes.

### Redes de área local

Permitieron conectar múltiples computadoras y facilitar el intercambio de información.

### Almacenamiento

El desarrollo de tecnologías de almacenamiento permitió manejar grandes cantidades de información y compartirla entre diferentes sistemas.

---

# Sistemas centralizados vs. distribuidos

Un **sistema centralizado** concentra el procesamiento y los recursos principales en una computadora o sistema central.

```
          Usuarios
             │
             ▼
       ┌────────────┐
       │ Computadora│
       │   central  │
       └────────────┘
```

En cambio, un sistema distribuido utiliza diferentes computadoras:

```
       ┌────────┐
       │ PC 1   │
       └───┬────┘
           │
       ┌───▼────┐
       │  Red   │
       └───┬────┘
       ┌───┼────┐
       ▼   ▼    ▼
     PC 2  PC 3 Servidor
```

---

# Ventajas de los sistemas distribuidos frente a los centralizados

### Economía

Los sistemas distribuidos pueden utilizar múltiples computadoras relativamente económicas en lugar de depender de una computadora central de alto costo.

Esto puede proporcionar una mejor relación **precio/rendimiento**.

### Mayor velocidad de cómputo

Varias computadoras pueden colaborar para resolver un problema, permitiendo obtener mayor capacidad de procesamiento.

### Distribución de aplicaciones

Los componentes de una aplicación pueden encontrarse en diferentes computadoras.

Por ejemplo:

```
Cliente
   │
   ▼
Servidor web
   │
   ▼
Servidor de aplicación
   │
   ▼
Servidor de base de datos
```

### Confiabilidad

Un sistema distribuido puede ofrecer **tolerancia a fallos parciales**.

Esto significa que la falla de una computadora no necesariamente provoca la caída completa del sistema.

### Crecimiento proporcional

Un sistema distribuido puede crecer agregando nuevos recursos o computadoras cuando aumenta la demanda.

Esto se conoce como **escalabilidad**.

---

# Ventajas frente a computadoras aisladas

### Datos compartidos

Diferentes usuarios y computadoras pueden acceder a información común.

Por ejemplo:

```
PC 1 ──┐
PC 2 ──┼── Base de datos
PC 3 ──┘
```

Esto permite trabajar con información compartida y manejar problemas de concurrencia.

### Dispositivos compartidos

Se pueden compartir recursos como:

- Impresoras.
- Plotters.
- Almacenamiento.
- Cámaras.
- Servidores.

### Comunicación

Las computadoras conectadas pueden intercambiar información.

Ejemplos:

- Correo electrónico.
- Mensajería.
- Videoconferencias.
- SSH.
- Servicios web.

### Balanceo de carga

La carga de trabajo puede distribuirse entre diferentes computadoras.

Por ejemplo:

```
             Clientes
                 │
                 ▼
          Balanceador
          de carga
          /    |    \
         ▼     ▼     ▼
      Serv.1 Serv.2 Serv.3
```

Si un servidor tiene demasiadas solicitudes, otras pueden atenderlas.

---

# Desventajas y retos de los sistemas distribuidos

Los sistemas distribuidos también presentan problemas que hacen que su diseño sea más complejo.

### Complejidad del software

Es necesario desarrollar software capaz de coordinar diferentes computadoras y procesos.

### Fallos parciales

En un sistema centralizado puede fallar una máquina y detener todo el sistema. En uno distribuido pueden fallar solamente algunos componentes.

Esto genera preguntas como:

> ¿Cómo sabe el sistema que una computadora dejó de funcionar?

### Comunicación por red

La comunicación entre máquinas puede sufrir:

- Retrasos.
- Pérdida de paquetes.
- Interrupciones.
- Congestión.
- Fallos de conexión.

### Sincronización

Diferentes computadoras pueden ejecutar operaciones al mismo tiempo, por lo que es necesario coordinar sus acciones.

### Consistencia de datos

Cuando varias computadoras trabajan con los mismos datos, se debe garantizar que no existan inconsistencias.

### Seguridad

Existen más puntos de entrada y comunicación, por lo que proteger el sistema puede ser más complicado.

---

# Seguridad en sistemas

La seguridad es una función importante de los sistemas operativos y adquiere todavía mayor importancia en sistemas distribuidos.

Podemos distinguir dos grandes escenarios:

## Seguridad dentro de la computadora

Algunos mecanismos son:

- Contraseñas.
- Usuarios.
- Permisos.
- Control de acceso.
- Protección de memoria.
- Protección de archivos.
- Aislamiento de procesos.

Por ejemplo, un usuario puede tener permisos para:

```
Leer       ✓
Escribir   ✓
Ejecutar   ✗
```

Esto evita que cualquier usuario pueda modificar o ejecutar recursos sin autorización.

## Seguridad en la red

Cuando las computadoras están conectadas, se necesitan mecanismos adicionales:

- Firewalls.
- Filtrado de tráfico.
- Autenticación.
- Cifrado.
- Control de acceso.
- Sistemas de detección y prevención de intrusiones.

### Firewall

Un **firewall** controla el tráfico de red de acuerdo con determinadas reglas.

Por ejemplo:

```
Internet
   │
   ▼
Firewall
   │
   ▼
Red interna
```

En Linux, una herramienta tradicional para configurar reglas de filtrado es **iptables**.

---

# Idea general de la materia

Todos estos temas están relacionados:

```
              SISTEMAS DISTRIBUIDOS
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
      Sistemas       Redes       Seguridad
      operativos       │            │
          │            │            │
          ▼            ▼            ▼
      Procesos      Modelo OSI    Firewall
      Hilos         TCP/IP        Permisos
      Memoria       IP            Cifrado
      Concurrencia  Ethernet      Autenticación
          │            │            │
          └────────────┼────────────┘
                       ▼
                Comunicación
                 entre nodos
                       │
                       ▼
              Sistema distribuido
```

La conexión fundamental es que **un sistema distribuido necesita computadoras capaces de ejecutar procesos, una red que permita su comunicación y mecanismos de coordinación y seguridad que permitan que todos esos componentes trabajen conjuntamente**.

### Conceptos que conviene tener muy claros

|Concepto|Idea clave|
|---|---|
|**Programa**|Conjunto de instrucciones almacenadas.|
|**Proceso**|Programa en ejecución.|
|**PID**|Identificador de un proceso.|
|**Hilo**|Flujo de ejecución dentro de un proceso.|
|**Concurrencia**|Varias tareas progresando durante un mismo periodo.|
|**`fork()`**|Crea un proceso hijo en Unix/Linux.|
|**Planificador**|Decide qué proceso obtiene CPU.|
|**Red**|Permite la comunicación entre dispositivos.|
|**OSI**|Modelo de 7 capas para comprender la comunicación de red.|
|**Sistema distribuido**|Varias computadoras independientes que cooperan y se presentan como un sistema.|
|**Tolerancia a fallos**|Capacidad de continuar funcionando ante fallos parciales.|
|**Escalabilidad**|Capacidad de crecer agregando recursos.|
|**Balanceo de carga**|Distribución de trabajo entre diferentes recursos.|

**Nota importante para tus apuntes:** corregí y organicé varias cosas que estaban mezcladas, especialmente **procesos vs. hilos**, **concurrencia**, **OSI**, y la relación entre **redes y sistemas distribuidos**. También eliminé la frase _“Sin redes, existirían los sistemas distribuidos”_, porque conceptualmente debería ser al contrario: **las redes son una infraestructura fundamental que permite construir sistemas distribuidos**.

