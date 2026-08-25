
Notas en el contexto del desarrollo de videojuegos y específicamente desde la perspectiva que suelen adoptar libros como _Desarrollo de Videojuegos: Arquitectura del Motor_, donde el enfoque está más orientado a la ingeniería de software, la arquitectura de motores y las tecnologías utilizadas en la industria.

En este primer capitulo se estudian los aspectos esenciales del **diseño de un motor de videojuegos,** así como las técnicas básicas de programación y **patrones de diseño**


### Índice general 

1. Introducción
	1.1. El desarrollo de videojuegos 
	1.2. Arquitectura del motor. Visión general

2. Herramientas de Desarrollo
	2.1. Introducción
	2.2. Compilación, enlazado y depuración
	2.3 Gestión de proyectos y documentación 

3. C++. Aspectos Esenciales
	3.1. Utilidades básicas
	3.2. Clases
	3.3. Herencia y polimorfismo
	3.4. Plantillas
	3.5. Manejo de excepciones

4. Patrones de Diseño
	4.1. Introducción
	4.2. Patrones de creación
	4.3. Patrones estructurales 
	4.4. Patrones de comportamiento

5. La Biblioteca STL
	5.1. Visión general de STL
	5.2. STL y el desarrollo de videojuegos
	5.3. Secuencias
	5.4. Contenedores asociativos 
	5.5. Adaptadores de secuencia

6. Sistemas del Motor de Bajo Nivel
	6.1. Subsistema de arranque y parada
	6.2. Contenedores
	6.3. Subsistema de gestión de cadenas
	6.4. Configuración del motor

7. El Bucle de Juego
	7.1. El Bucle de renderizado
	7.2. El bucle de juego
	7.3. Arquitecturas típicas del bucle de juego
	7.4. Gestión de estado de juego con Ogre3D
	7.5. Definición de estados concretos

8. Importador de Datos de Intercambio
	8.1. Formatos de intercambio
	8.2. Creación de un importador 

9. Recursos y el sistema de archivos
	9.1. Gestión básica de recursos
	9.2. Gestión de recursos con Ogre3D
	9.3. Gestión básica del sonido
	9.4. El sistema de archivos 

10. Hilos y Concurrencia
	10.1. Fundamentos básicos 
	10.2. La biblioteca de hilos de ICE
	10.3. Multi-threading en Ogre3D
	10.4. Caso de estudio. Procesamiento en segundo plano mediante hilos

---
---

# 1. Introducción
## 1.1. El desarrollo de videojuegos 

shaders programables

motores de juego (game engines)
	Quake
	Unreal

middlewares

Motores de renderizado
	Ogre 3D

tasa de frames o imágenes por segundo, típicamente 30 ó 60

Ingenieros:
	**Programadores del núcleo** del juego
	**Programadores de herramientas** 



Artistas:
	Artista de concepto
	Modeladores
	Artistas de texturizado
	Artistas de iluminación 
	Animadores
	Actores de captura de movimiento 
	Diseñadores de sonido
	Otros actores

renderizado en tiempo real

frame rate

deadline

agentes (agents)

NPCs

Motor de Juego
	arquitectura orientada a la reutilización
	mods
	shooters o shoot’em all
	data-driven architecture
	hard-coded logic

Géneros de juegos
	first-person shooters (FPS)
		binary space partitioning (BSP) trees
		occlusion culling
		código fuente de Quake, Quake II y Quake III
		Unreal
	juegos en tercera persona
	juegos de lucha
		stamina
		scroll lateral
		sistema de timing
		shaders
		bump mapping
	conducción
		simuladores
		arcade
	estrategia
		en tiempo real 
		por turnos

		- perspectiva isométrica
 
	MMOG (Massively Multiplayer Online Game).

Una de las más populares, y que se utilizará en el presente curso, es OGRE 3D9.









## 1.2. Arquitectura del motor. Visión general

  
  <u>pag - 31</u>

# 2. Herramientas de Desarrollo

  

2.1. Introducción

  

2.2. Compilación, enlazado y depuración

  

2.3 Gestión de proyectos y documentación 

  
  

# 3. C++. Aspectos Esenciales

  

3.1. Utilidades básicas

  

3.2. Clases

  

3.3. Herencia y polimorfismo

  

3.4. Plantillas

  

3.5. Manejo de excepciones

  
  

# 4. Patrones de Diseño

  

4.1. Introducción

  

4.2. Patrones de creación

  

4.3. Patrones estructurales 

  

4.4. Patrones de comportamiento

  
  

# 5. La Biblioteca STL

  

5.1. Visión general de STL

  

5.2. STL y el desarrollo de videojuegos

  

5.3. Secuencias

  

5.4. Contenedores asociativos 

  

5.5. Adaptadores de secuencia

  
  

# 6. Sistemas del Motor de Bajo Nivel

  

6.1. Subsistema de arranque y parada

  

6.2. Contenedores

  

6.3. Subsistema de gestión de cadenas

  

6.4. Configuración del motor

  
  

# 7. El Bucle de Juego

  

7.1. El Bucle de renderizado

  

7.2. El bucle de juego

  

7.3. Arquitecturas típicas del bucle de juego

  

7.4. Gestión de estado de juego con Ogre3D

  

7.5. Definición de estados concretos

  
  

# 8. Importador de Datos de Intercambio

  

8.1. Formatos de intercambio

  

8.2. Creación de un importador 

  
  

# 9. Recursos y el sistema de archivos

  

9.1. Gestión básica de recursos

  

9.2. Gestión de recursos con Ogre3D

  

9.3. Gestión básica del sonido

  

9.4. El sistema de archivos 

  
  

# 10. Hilos y Concurrencia

  

10.1. Fundamentos básicos 

  

10.2. La biblioteca de hilos de ICE

  

10.3. Multi-threading en Ogre3D

  

10.4. Caso de estudio. Procesamiento en segundo plano mediante hilos

















