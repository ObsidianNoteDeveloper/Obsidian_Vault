# Math Quest 

Un juego de plataformas 2D donde el personaje debe responder preguntas matemáticas para avanzar y derrotar enemigos. Diseño retro-pixel con paleta vibrante.

**Mecánicas completas:**

- Personaje controlable con física (← → saltar)
- 3 niveles de dificultad progresiva en preguntas (básica → intermedia → avanzada)
- Enemigos con IA de patrulla que activan desafíos matemáticos
- Monedas coleccionables (+10 pts), quiz correcto (+50 pts), nivel completado (+100 pts)
- Sistema de 3 vidas con invencibilidad temporal
- Cámara con scroll lateral
- Pantalla inicio, fin (victoria/derrota), reinicio y menú

```
math-quest/
├── index.html          
├── css/
│   └── style.css       
└── js/
    ├── config.js       
    ├── questions.js    
    ├── levels.js       
    ├── physics.js      
    ├── renderer.js     
    ├── quiz.js         
    ├── game.js         
    └── main.js         
```


-  `config.js` - Constantes globales: física, colores, puntuación, dimensiones del canvas. Todo el juego las importa.
	
-  `questions.js` - Banco de 30 preguntas por nivel. Función `getQuestions(levelindex)`.
	
-  `levels.js` - Datos de los 3 niveles (plataformas, enemigos, monedas). Función `buildLevel()`
	
-  `physics.js`
	-  `rectsOverlap()` - detección AABB de colisiones entre rectángulos.
	-  `updatePlayer()` - aplica graveda, salto, fricción y resuelve colisiones con plataformas.
	-  `updateEnemy()` - patrulla sobre plataformas, rebota en sus bordes.
	
-  `render.js` 
	-  `drawBackgroud()` - gradiente de cielo, estrellas, nubes con paralaje.
	-  Objetos del mundo:
		-  `drawPlatform()`
		-  `drawCoin()`
		-  `drawFlag()`
		-  `drawEnemy()` 
	-  `drawPlayer()` - personaje pixel art con transformaciones de canvas.
	-  `drawFrame()` - orquesta un frame completo: llama todas las funciones en orden.
-  `quiz.js`
	Comunica el resultado (correcto/incorrecto) vía callback al módulo Game.
	-  `Quiz.open(enemy,qs,onResult)` - abre el overlay con la pregunta del enemigo tocado.
	-  `_checkAnswer()` - valida la opción elegida, muestra feedback visual.
-  `game.js`
	-  `init()` - reinicia el estado global (score, lives, level, player, nivel construido).
	-  `update()` - frame a frame: física, cámara, colisión monedas, colisión enemigos, bandera.
	-  `_startQuiz()` → delega a Quiz; `_loseLife()` → resta vida o gameover.
	-  `_nextLevel() / _endGame()` - transiciones de pantalla y fin del juego.
-  `main.js` - Bucle principal con `requestAnimationFrame`. Bindings de botones (inicio, retry, menú). Llama a `Game.update()` y `Renderer.drawFrame()` cada frame. 










