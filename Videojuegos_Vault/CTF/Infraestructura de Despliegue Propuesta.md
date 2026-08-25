
## Despliegue en Red Local (LAN)

Con el objetivo de garantizar la estabilidad, disponibilidad y rapidez del sistema durante la competencia, se propone implementar la plataforma dentro de una **Red de Área Local (LAN)**, evitando la dependencia de servicios externos o de una conexión a Internet.

La infraestructura estará conformada por un servidor local que alojará la aplicación web y una red local a la que se conectarán todos los equipos de los participantes.

La arquitectura propuesta se representa de la siguiente manera:

![[Diagrama sin título.drawio.png]]

Todos los participantes accederán al sistema utilizando un navegador web e ingresando la dirección asignada al servidor dentro de la red local, por ejemplo:

```
http://192.168.1.100:5000
```

No será necesario instalar software adicional en las computadoras de los participantes, ya que toda la interacción se realizará desde el navegador.

---

# Funcionamiento de la Infraestructura

Antes del inicio de la competencia se configurará una red local mediante un router o un switch, al cual estarán conectados:

- El servidor que ejecutará la aplicación web.
    
- Los equipos de todos los participantes.
    
- El equipo del administrador del evento.
    

Una vez conectados a la misma red, cada equipo podrá comunicarse directamente con el servidor utilizando su dirección IP local.

Toda la información permanecerá dentro de la red interna, sin salir hacia Internet.

Las solicitudes realizadas por los participantes, como el inicio de sesión, el envío de banderas, la consulta del ranking y la actualización de puntuaciones, serán procesadas directamente por el servidor local.

---

# Justificación de la Solución

La elección de una infraestructura basada en una red LAN responde principalmente a criterios de confiabilidad, rendimiento y seguridad.

## Independencia de Internet

El funcionamiento del sistema no dependerá de la disponibilidad del servicio de Internet.

En caso de presentarse una interrupción del proveedor de Internet durante el evento, la plataforma continuará operando con normalidad, ya que toda la comunicación ocurre dentro de la red local.

Esta característica reduce considerablemente el riesgo de interrupciones durante la competencia.

---

## Baja Latencia

Al encontrarse todos los dispositivos dentro de la misma red física, el tiempo de respuesta entre los participantes y el servidor será mínimo.

Esto permite que:

- La autenticación sea prácticamente inmediata.
    
- La validación de banderas ocurra en pocos milisegundos.
    
- El ranking se actualice en tiempo real.
    
- La experiencia de todos los participantes sea uniforme.
    

Esta baja latencia resulta especialmente importante debido al uso de comunicación en tiempo real mediante WebSockets.

---

## Mayor Estabilidad

La comunicación entre los clientes y el servidor no depende de infraestructura de terceros.

No intervienen:

- Servicios de alojamiento web.
    
- Plataformas de nube.
    
- Proveedores externos.
    
- Servicios gratuitos con limitaciones.
    

Al eliminar estos intermediarios se reduce significativamente la probabilidad de fallas ocasionadas por factores ajenos a la organización del evento.

---

## Mayor Seguridad

Toda la información permanecerá dentro de la red del evento.

Las credenciales de acceso, las respuestas correctas, las puntuaciones y la base de datos nunca abandonarán la infraestructura local.

Esto disminuye la superficie de exposición frente a ataques externos y facilita el control de acceso a la información sensible.

---

## Comunicación en Tiempo Real

El sistema utilizará **Flask-SocketIO** para mantener una comunicación permanente entre el servidor y los navegadores de los participantes.

Gracias a esta tecnología, cualquier cambio en la competencia podrá reflejarse inmediatamente en todas las pantallas conectadas.

Por ejemplo:

- Actualización automática del ranking.
    
- Incremento inmediato de la puntuación.
    
- Notificación de nuevas respuestas válidas.
    
- Sincronización de la información entre todos los participantes.
    

Este mecanismo elimina la necesidad de que los usuarios recarguen constantemente la página para conocer los cambios en la clasificación.

---

# Beneficios Operativos

La implementación mediante una red local proporciona ventajas importantes para la organización del evento:

- No requiere contratar servicios de hospedaje web.
    
- No genera costos asociados a infraestructura en la nube.
    
- Reduce la complejidad técnica durante el despliegue.
    
- Facilita la configuración y el mantenimiento del sistema.
    
- Permite un mayor control sobre toda la infraestructura utilizada durante la competencia.
    

Asimismo, al concentrar todos los servicios en un único servidor local, la supervisión y administración del sistema resulta más sencilla para el organizador.

---

# Consideraciones de Implementación

Se recomienda utilizar un equipo dedicado como servidor durante toda la competencia, el cual permanecerá encendido y conectado a la red local.

Este servidor será responsable de ejecutar:

- La aplicación desarrollada en Flask.
    
- El servicio de comunicación en tiempo real mediante Flask-SocketIO.
    
- La base de datos SQLite.
    
- El panel de administración del evento.
    

Por su parte, los participantes únicamente necesitarán un navegador web moderno y conexión a la red local para acceder a la plataforma.

Esta arquitectura es suficiente para soportar una competencia de aproximadamente 30 participantes simultáneos, ofreciendo un funcionamiento estable, tiempos de respuesta bajos y una administración centralizada de toda la información del evento.