
# Sistema distribuido para el análisis de eventos de red

## 1. Planteamiento del problema

En una red de computadoras se generan constantemente diferentes eventos, como solicitudes DNS, conexiones TCP, solicitudes HTTP, conexiones a puertos y errores de conexión.

El análisis de estos eventos puede requerir procesar una gran cantidad de información de manera simultánea. Realizar todas estas tareas dentro de un único proceso puede limitar la capacidad de procesamiento y dificultar la organización del sistema.

Por ello, se propone desarrollar un sistema distribuido capaz de **generar, transmitir, procesar y analizar eventos de red mediante diferentes procesos independientes que trabajen de manera concurrente**.

El proyecto utilizará eventos de red simulados, por lo que no será necesario trabajar inicialmente con tráfico de una red real.

## 2. Objetivo

Desarrollar un sistema distribuido que permita generar y procesar eventos de red simulados mediante múltiples procesos independientes, utilizando mecanismos de comunicación y sincronización para coordinar las diferentes etapas del procesamiento.

## 3. Funcionamiento general

El sistema estará compuesto por diferentes procesos, donde cada uno tendrá una función específica:

```text
Generador de eventos
        │
        ▼
   Procesador
        │
        ▼
 ┌──────┴──────┐
 ▼             ▼
Analizador 1  Analizador 2
 │             │
 └──────┬──────┘
        ▼
 Generador de alertas
```

El **generador de eventos** producirá información simulada relacionada con actividades de red.

El **procesador** recibirá los eventos y se encargará de distribuirlos entre los procesos analizadores.

Los **analizadores** procesarán los eventos de manera concurrente y buscarán determinadas condiciones o patrones previamente establecidos.

Finalmente, el **generador de alertas** recibirá los resultados y mostrará los eventos que cumplan con las condiciones definidas.

## 4. Comunicación entre procesos

Para la comunicación entre los diferentes componentes se utilizarán mecanismos de comunicación entre procesos.

La primera implementación utilizará:

- `pipe`
    
- Procesos mediante `fork()`
    
- Señales
    
- `select()` o `poll()`
    

Posteriormente, el sistema podrá evolucionar hacia una arquitectura cliente-servidor utilizando **sockets TCP** para permitir la comunicación entre procesos que se encuentren en diferentes equipos.

## 5. Conceptos de Sistemas Distribuidos

El proyecto permitirá aplicar los siguientes conceptos:

|Concepto|Aplicación|
|---|---|
|**Procesos**|Cada componente funcionará como un proceso independiente.|
|**Concurrencia**|Los analizadores podrán procesar eventos simultáneamente.|
|**Comunicación entre procesos**|Los procesos intercambiarán información mediante `pipe` y posteriormente sockets.|
|**Sincronización**|Los procesos deberán coordinar el envío y recepción de eventos.|
|**Paso de mensajes**|Los eventos serán enviados entre los diferentes procesos.|
|**Cliente-servidor**|En una segunda etapa, los sensores podrán enviar eventos a un servidor.|
|**Paralelismo**|Diferentes eventos podrán procesarse simultáneamente.|
|**Tolerancia a fallos**|Se podrá analizar el comportamiento del sistema cuando uno de los procesos deje de funcionar.|
|**Escalabilidad**|Se podrán agregar nuevos procesos analizadores al sistema.|

## 6. Tecnologías

La primera versión del proyecto se desarrollará utilizando:

```text
C
Linux
fork()
pipe()
select()
poll()
señales
```

Para una segunda etapa se podrán incorporar:

```text
Sockets TCP
Arquitectura cliente-servidor
```

## 7. Resultado esperado

Al finalizar el proyecto se espera contar con un sistema funcional capaz de generar eventos de red simulados y distribuirlos entre diferentes procesos para su procesamiento concurrente.

El sistema deberá demostrar la comunicación y coordinación entre los procesos, así como el procesamiento simultáneo de los eventos.

De esta manera, el proyecto permitirá aplicar de forma práctica conceptos fundamentales de **Sistemas Distribuidos**, particularmente procesos, comunicación, concurrencia, sincronización, paso de mensajes y arquitectura cliente-servidor.




---
---

Java + Redes + Linux + SQL + HTTP + Seguridad

**Java aplicado a sistemas**

```
Java
 ↓
Maven
 ↓
JUnit
 ↓
JDBC
 ↓
PostgreSQL
 ↓
Sockets
 ↓
HTTP
 ↓
REST
```

Perfil buscado: Java Backend Developer con conocimientos de redes, Linux y seguridad.