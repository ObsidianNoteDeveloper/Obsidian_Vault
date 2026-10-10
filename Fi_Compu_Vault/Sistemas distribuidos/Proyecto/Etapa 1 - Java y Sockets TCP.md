
La idea es avanzar como lo haría en un proyecto de ingeniería de software: 
- Primero estudiar los fundamentos
- Después practicarás las herramientas
- Y finalmente implementar un prototipo que servirá como base para las siguientes etapas.

# Fundamentos de comunicación en red

## Arquitectura cliente-servidor

El cliente inicia una solicitud y el servidor espera conexiones para atenderlas. En el proyecto, los clientes representan dispositivos que generan eventos y el servidor central los recibe.

![](clienteServidor.png)

## Dirección IP y puerto

La IP identifica una interfaz de red y el puerto identifica un punto de comunicación de una aplicación. Por ejemplo, `127.0.0.1:5000` indica el puerto 5000 del equipo local.

![](ModelTCP.png)

## TCP

Es un protocolo de transporte orientado a conexión que proporciona un flujo de bytes ordenado y confiable. Gestiona retransmisiones y entrega de datos, pero tu aplicación debe definir cómo separar e interpretar sus mensajes.

![](TCP.png)

> [!Important]
> TCP no envía automáticamente objetos ni mensajes completos. Envía un flujo de bytes. En nuestro primer ejercicio utilizaremos mensajes de texto terminados en un salto de línea (`\n`), que el cliente y el servidor interpretarán como el final de cada mensaje.

# Fundamentos de Java 

| **Tema**                 | **Qué debo saber**                                 | **Cómo lo aplicare**                                |
| ------------------------ | -------------------------------------------------- | --------------------------------------------------- |
| Clases y objetos         | Crear clases, instanciar objetos y llamar métodos. | Separar el servidor y el cliente.                   |
| Método `main`            | Punto de entrada de una aplicación Java.           | Ejecutar cada programa.                             |
| Variables y tipos        | `String`, `int`, `boolean`.                        | Representar mensajes y puertos.                     |
| Parámetros y retorno     | Pasar argumentos y devolver resultados.            | Enviar datos entre métodos.                         |
| `try-catch`              | Capturar excepciones.                              | Controlar fallos de conexión.                       |
| `try-with-resources`     | Cerrar automáticamente recursos.                   | Liberar sockets y flujos.                           |
| Entrada/salida           | Lectores y escritores de datos.                    | Recibir y enviar mensajes.                          |
| Paquetes e importaciones | `package` e `import`.                              | Organizar las clases y usar las bibliotecas de red. |
