
# Scratch CTF

Un **Scratch CTF (Capture The Flag)** es un evento educativo basado en desafíos interactivos donde los participantes desarrollan habilidades de pensamiento computacional y programación mediante la exploración de videojuegos creados en Scratch. A lo largo de diferentes niveles, los jugadores deben encontrar banderas ocultas, corregir bloques de código, resolver acertijos, identificar errores de lógica y superar retos de programación para avanzar hasta completar la misión. Cada desafío representa un problema que pone a prueba la creatividad, el razonamiento y la capacidad de resolver problemas de forma divertida y práctica.


# ¿Qué hace diferente a un Scratch CTF?

En un CTF tradicional los participantes buscan vulnerabilidades o descifran información.

En un **Scratch CTF** los jugadores pueden enfrentarse a retos como:

- Encontrar una bandera escondida dentro del escenario.
- Corregir bloques de Scratch que contienen errores.
- Completar partes faltantes de un programa.
- Resolver acertijos matemáticos.
- Programar el movimiento correcto de un personaje.
- Descubrir por qué un juego no funciona.
- Encontrar variables ocultas.
- Resolver laberintos.
- Abrir puertas mediante secuencias lógicas.
- Encontrar mensajes cifrados.
- Completar minijuegos.
- Resolver rompecabezas de programación.

<div style="text-align: center;">  
<img src="ScratchHolmes.png" width="250">  
</div>

---

# Formato y búsqueda de banderas

Las banderas (flags) utilizadas durante el **Scratch CTF** tendrán un formato estandarizado que permitirá a los participantes identificarlas fácilmente y validar que la respuesta encontrada corresponde al reto.

El formato general de las banderas será:

`PiLARES{...}`

Dentro de las llaves se incluirá un identificador correspondiente al reto y la respuesta obtenida por el participante. Por ejemplo:

`PiLARES{BT_-15}`


## Ejemplo de búsqueda de una bandera 

Para el desarrollo del CTF se habilitará un sitio web que contendrá múltiples videojuegos desarrollados en **Scratch**. Cada juego representará múltiples retos que los participantes deberán analizar para localizar algunas banderas.

<div style="text-align: center;">  
<img src="Pasted image 20260813164307.png" width="750">  
</div>

En la parte inferior de cada juego se incluirá un icono de **Scratch**. Al seleccionar dicho icono, el participante será redirigido a la página oficial de Scratch donde se encuentra publicado el proyecto.

<div style="text-align: center;">  
<img src="Pasted image 20260813164528.png" width="550">  
</div>

Una vez dentro del proyecto, el participante deberá seleccionar la opción **“Ver adentro”**. Esto permitirá visualizar todos los bloques de programación utilizados para desarrollar el videojuego y analizar su funcionamiento en busca de las banderas correspondientes.

Los retos estarán clasificados en dos modalidades principales:

- **Retos de lógica**
- **Retos de acertijos**

### Tipo: Lógica 

En este tipo de reto, el participante deberá analizar el código de un videojuego para identificar errores, comportamientos inesperados o instrucciones que no corresponden con la lógica esperada del programa.

Por ejemplo, la siguiente imagen muestra parte del código utilizado para controlar el movimiento del jugador rojo:

<div style="text-align: center;">  
<img src="BarraRojaCTF 1.png" width="250">  
</div>

Dentro del código existe un error lógico en uno de los bloques de movimiento. El participante deberá analizar las instrucciones y determinar cuál es el valor incorrecto.

En este caso, el valor `15` deberá sustituirse por `-15`.

Una vez identificado y corregido el error, el participante deberá introducir la respuesta utilizando el formato de bandera establecido para el reto:

<div style="text-align: center;">  
<img src="Pasted image 20260806181844.png" width="250">  
</div>


Por lo tanto, la bandera correspondiente a este reto será:

`PiLARES{BT_-15}`

### Tipo: acertijo

En los retos de tipo acertijo, la bandera estará relacionada con una pregunta, pista o enigma colocado dentro del escenario del videojuego o en alguno de sus **Sprites**.

El participante deberá explorar el proyecto y analizar los elementos disponibles para localizar el acertijo y determinar su respuesta.

Por ejemplo, dentro de un escenario o Sprite se podrá encontrar un acertijo como el siguiente:

<div style="text-align: center;">  
<img src="Pasted image 20260806182904.png" width="550">  
</div>

Una vez resuelto el acertijo, el participante deberá introducir la respuesta respetando el formato establecido para la bandera.

Si la respuesta correcta al acertijo fuera `Sprite`, la bandera correspondiente sería:

`PiLARES{BT_Sprite}`

#### Banderas validas:

Las banderas deberán respetar estrictamente el formato establecido para cada reto. El participante **no deberá modificar la estructura de la bandera**, sino únicamente sustituir los puntos suspensivos (`...`) por la respuesta obtenida.

Formato de bandera: `PiLARES{BT_..}`

Ejemplos de banderas válidas:

`PiLARES{BT_-15}`

`PiLARES{BT_Sprite}`

Ejemplos de banderas no válidas:

`PiLARES{-15}`

`{BT_Sprite}`

De esta manera, el formato permite identificar fácilmente las banderas y facilita su validación dentro del sistema del CTF.

---
## Propuesta General

Se propone el desarrollo de una aplicación web que permita administrar y evaluar en tiempo real una competencia de tipo **Capture The Flag (CTF)**, en la que los participantes deberán ingresar respuestas (banderas) para obtener puntos conforme resuelvan los diferentes retos planteados.

El sistema estará diseñado para soportar aproximadamente **30 participantes conectados de manera simultánea**, manteniendo un marcador actualizado en tiempo real y garantizando la integridad de la información almacenada.

---

# Objetivo

Desarrollar una plataforma web que permita:

- Autenticar a cada participante mediante usuario y contraseña.
    
- Validar automáticamente las respuestas ingresadas.
	
- Asignar puntuaciones de acuerdo con la dificultad de cada reto.
    
- Mostrar un ranking actualizado en tiempo real.
    
- Impedir que un mismo usuario obtenga puntos más de una vez por la misma respuesta.
    
- Centralizar toda la administración del sistema para que únicamente el organizador tenga acceso a la información sensible.
    
---

# Flujo General del Sistema

## 1. Autenticación

Al ingresar al sitio web, el usuario visualizará una pantalla de inicio de sesión.

Cada participante deberá autenticarse mediante:

- Usuario
    
- Contraseña
    

Las credenciales serán previamente registradas por el administrador.

Como punto de partida, se contempla un total aproximado de **30 usuarios**.

Una vez autenticado correctamente, el participante tendrá acceso al sistema.

<div style="text-align: center;">  
<img src="Pasted image 20260813155833.png" width="300">  
</div>

---

## 2. Pantalla Principal

Después del inicio de sesión, el usuario visualizará una interfaz compuesta por dos áreas principales.

<div style="text-align: center;">  
<img src="Pasted image 20260813160411.png" width="700">  
</div>

### Ranking de participantes

En la parte superior se mostrará un marcador general con:

- Nombre del usuario
    
- Puntuación acumulada
    

Inicialmente se visualizarán los **10 participantes con mayor puntuación**, ordenados de forma descendente.

Si existen más participantes, la lista permitirá desplazarse mediante un **scroll vertical** para consultar la clasificación completa.

El ranking deberá actualizarse automáticamente conforme los participantes obtengan nuevos puntos.

<div style="text-align: center;">  
<img src="Pasted image 20260813160948.png" width="400">  
</div>

---

### Captura de banderas

Se encontrará un formulario muy sencillo compuesto por:

- Un único campo de texto
    
- Botón para enviar la respuesta
    
El participante ingresará la bandera obtenida durante la competencia.

Al enviarla, el sistema realizará una validación inmediata.

<div style="text-align: center;">  
<img src="Pasted image 20260813161935.png" width="350">  
</div>

---

# Validación de Respuestas

Cada respuesta será comparada contra un banco de respuestas previamente definido.

Existen dos posibles escenarios:

## Respuesta correcta

Si la bandera existe:

- El campo de texto cambiará temporalmente a color verde.
    
- Se mostrará un mensaje indicando que la respuesta fue válida.
    
- Se sumarán automáticamente los puntos correspondientes.
    
- El ranking se actualizará para todos los participantes.
    
<div style="text-align: center;">  
<img src="Pasted image 20260813160612.png" width="300">  
</div>

---

## Respuesta incorrecta

Si la bandera no existe:

- El campo cambiará a color rojo.
    
- Se notificará que la respuesta es incorrecta.
    
- No se otorgarán puntos.

<div style="text-align: center;">  
<img src="Pasted image 20260813162340.png" width="350">  
</div>

El usuario podrá seguir intentando hasta ingresar una respuesta válida.

---

# Clasificación de Retos

Las banderas estarán agrupadas por nivel de dificultad.

|Dificultad|Puntaje|
|---|---|
|Fácil|+10 puntos|
|Media|+15 puntos|
|Difícil|+20 puntos|

Cada bandera pertenecerá únicamente a una categoría.

---

# Restricciones del Sistema

Para garantizar la integridad de la competencia, deberán implementarse las siguientes reglas.

## Una bandera solo cuenta una vez por usuario

Si un participante intenta registrar nuevamente una bandera que ya había enviado anteriormente:

- No obtendrá puntos adicionales.
    
- El sistema notificará que dicha bandera ya fue registrada previamente.

<div style="text-align: center;">  
<img src="Pasted image 20260813161141.png" width="350">  
</div>

Sin embargo, otros participantes sí podrán obtener los puntos correspondientes al encontrar esa misma bandera.

---

## Validación individual

Cada participante tendrá un historial interno de las banderas ya capturadas.

Este historial evitará duplicidad de puntuaciones.

---

# Ranking en Tiempo Real

Uno de los objetivos principales es que todos los participantes puedan observar el desarrollo de la competencia.

Por ello, el ranking deberá actualizarse automáticamente conforme cambien las puntuaciones.

No será necesario que los usuarios recarguen la página manualmente.

Cada modificación de puntos deberá reflejarse en todos los navegadores conectados.

---

# Administración del Sistema

El sistema contará con un área administrativa exclusiva para el organizador.

Desde esta sección será posible administrar información crítica como:

- Usuarios registrados.
    
- Contraseñas.
    
- Banco de respuestas (banderas).
    
- Puntajes de cada bandera.
    
- Historial de respuestas enviadas.
    
- Puntuaciones de los participantes.
    

Esta información no deberá ser accesible para los participantes.

---

# Almacenamiento de la Información

## Base de Datos

Permitiría almacenar de forma estructurada:

- Usuarios.
    
- Contraseñas cifradas.
    
- Banderas.
    
- Categorías.
    
- Puntajes.
    
- Historial de respuestas.
    
- Ranking.
    

Ventajas:

- Mayor seguridad.
    
- Mejor rendimiento.
    
- Soporta múltiples conexiones simultáneas.
    
- Evita problemas de concurrencia.
    
- Facilita futuras ampliaciones del sistema.
    

---

# Requisitos Funcionales

El sistema deberá permitir:

- Inicio de sesión mediante usuario y contraseña.
    
- Administración de aproximadamente 30 participantes.
    
- Validación automática de banderas.
    
- Clasificación por dificultad.
    
- Asignación automática de puntos.
    
- Prevención de respuestas duplicadas por usuario.
    
- Ranking actualizado en tiempo real.
    
- Visualización de la clasificación completa mediante desplazamiento.
    
- Protección de la información sensible del sistema.
    
- Acceso exclusivo del administrador a la configuración del evento.
    

---

# Requisitos No Funcionales

- Interfaz sencilla e intuitiva.
    
- Baja latencia durante la validación de respuestas.
    
- Soporte para al menos 30 usuarios concurrentes.
    
- Comunicación en tiempo real entre servidor y clientes.
    
- Almacenamiento seguro de contraseñas mediante cifrado.
    
- Respaldo de la información del evento.
    
- Facilidad para agregar nuevas banderas y nuevos participantes en futuras competencias.
    

---

# Arquitectura Propuesta

Se propone desarrollar el sistema bajo una arquitectura cliente-servidor.

**Frontend**

- HTML5
    
- CSS3
    
- JavaScript
    

**Backend**

- Python con Flask
    

**Comunicación en tiempo real**

- Flask-SocketIO (WebSockets)
    

**Base de datos**

- SQLite para pruebas iniciales.
    
- PostgreSQL o MySQL para la versión definitiva.
    


---

# Beneficios Esperados

La implementación de este sistema permitirá:

- Automatizar completamente el proceso de validación de respuestas.
    
- Eliminar el conteo manual de puntuaciones.
    
- Mantener un ranking actualizado en tiempo real.
    
- Reducir errores humanos durante la competencia.
    
- Centralizar toda la administración del evento.
    
- Incrementar la transparencia y competitividad mediante un marcador visible para todos los participantes.
    
- Facilitar la organización de futuras ediciones del CTF reutilizando la misma plataforma con mínimas modificaciones.





