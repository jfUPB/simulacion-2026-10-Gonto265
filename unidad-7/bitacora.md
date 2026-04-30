# Unidad 7

## Bitácora de proceso de aprendizaje

### Actividad 1

- Analiza 3 o 4 ejemplos de Ji Lee.

El trabajo de Clock me parece dlos mejores pues, utiliza muy ingeniosamente lo forma en que de forma mas minimalista es representado un reloj, esto a partir de dos lineas, el horario mas corto que el minutero, y un simple círculo alrededor, cuanto el reloj marca las 3:00 los indicadores se ubican perpendicularmente dormando así su semejanza con la letra L, y además el circulo asemejandose a la letra O.

Luego está el trabajo con Moon, donde Aprovechando que la tierra y la luna son dos astros circulares, una de las O de la misma palabra actúaa como satelite natural de la otra.

Finalmente está el trabajo con Capitalism, donde la semejanza de la letra i con la figura minimalista de un usario o individuo se arovecha para ser escalado de forma exagerada mientras que los demás caracteres se derrumban, para así hacer alusión al Monopolio y la desigualdad social.

- Explica cómo la manipulación tipográfica refuerza el significado.

Esto funciona puesto que somos seres visuales, por lo que esta manipulación permite relacionar la palabara con una persepción visual más realista del concepto.

- Propón 2 o 3 palabras propias y esboza cómo podrían representarse visualmente.

La palabra Huevo, puede ser modificada de tal forma que la O tome forma de huevo y luego se rompa de forma que simule el nacimiento de La misma palabra.

La palabra ojo es la más común y sencillla pues se puede hacer un parpadeo de de una de las O.

La palabra Paño puede ser configurada de forma que la virgulilla pasa por toda la palabra hasta dejarla reluciente.

- Indica cuál de esas palabras te interesa más y por qué.

La verdad la de Paño, siento que la vigulilla es un concepto menos usado y más versátil además.

### Actividad 02

Preguntas:

- Explica con tus palabras qué hace cada uno de esos conceptos.
- Replica al menos dos experimentos básicos integrando Matter.js con p5.js.
- Incluye código y capturas o enlaces.
- Describe qué tipo de comportamiento físico te interesa explorar en tu palabra.

En esta actividad comprendí que Engine es el motor que calcula toda la simulación física, es decir, donde ocurren las reglas del movimiento. World es el espacio donde existen los objetos y donde se agregan todos los elementos físicos. Bodies son los objetos individuales (como cajas o círculos) que tienen propiedades como masa, fricción o rebote. Constraint permite conectar cuerpos entre sí, como si fueran unidos por cuerdas o resortes, mientras que MouseConstraint permite interactuar con los objetos usando el mouse, arrastrándolos dentro del entorno.

Realicé dos experimentos básicos. En el primero, creé varias cajas que caen por gravedad y rebotan contra el suelo, lo que me permitió entender cómo funciona la simulación básica. En el segundo, conecté dos cuerpos con un Constraint, generando un efecto similar a un péndulo o sistema elástico.

```js
let engine, world, box;

function setup() {
  createCanvas(400, 400);
  engine = Matter.Engine.create();
  world = engine.world;

  box = Matter.Bodies.rectangle(200, 100, 50, 50);
  ground = Matter.Bodies.rectangle(200, 380, 400, 20, { isStatic: true });

  Matter.World.add(world, [box, ground]);
}

function draw() {
  background(220);
  Matter.Engine.update(engine);

  rectMode(CENTER);
  rect(box.position.x, box.position.y, 50, 50);
}
```

El comportamiento físico que más me interesa explorar es la inestabilidad o deformación, ya que puede aportar significado emocional a una palabra, por ejemplo haciendo que las letras colapsen, vibren o se desintegren según ciertas condiciones.

### Actividad 03

Preguntas:

- Realiza al menos dos experimentos simples de audio-reactividad.
- Explica qué dato estás leyendo del audio.
- Explica qué comportamiento visual o físico activa ese dato.
- Describe qué tipo de respuesta sonora te serviría más para tu palabra y por qué.

En esta actividad experimenté con la lectura de audio usando p5.js. En el primer experimento utilicé la amplitud del sonido para modificar el tamaño de una figura en pantalla. El dato leído fue el nivel de volumen en tiempo real, y este hacía que un círculo creciera o disminuyera dependiendo de la intensidad del sonido. En el segundo experimento trabajé con un análisis de frecuencias (FFT), donde diferentes bandas de frecuencia controlaban distintos elementos visuales, como el movimiento o la cantidad de objetos.

```js
let song, amplitude;

function preload() {
  song = loadSound('audio.mp3');
}

function setup() {
  createCanvas(400, 400);
  amplitude = new p5.Amplitude();
  song.play();
}

function draw() {
  background(0);
  let level = amplitude.getLevel();
  let size = map(level, 0, 1, 50, 200);

  fill(255);
  ellipse(width/2, height/2, size);
}
```

El dato principal que utilicé fue la amplitud, que representa la energía general del sonido. Este dato activaba cambios visuales directos, como escalado o movimiento. También exploré frecuencias para generar respuestas más específicas.

En mi opinión, considero que la mejor respuesta sonora sería una combinación entre amplitud y eventos puntuales de la frecuencia, ya que esto permitiría generar cambios tanto continuos como explosivos, reforzando mejor el significado dependiendo de la intención semántica.

### Actividad 4

Preguntas:

- Muestra una prueba inicial.
- Explica qué parte de la palabra construiste.
- Explica qué propiedad física manipulaste.
- Explica qué aspecto del audio afecta qué comportamiento.
- Evalúa qué funcionó y qué no para el significado que quieres construir.

En esta actividad realicé una prueba inicial donde tomé una palabra y separé sus letras en formas individuales para convertirlas en cuerpos físicos dentro de Matter.js. Trabajé principalmente con una parte de la palabra, no con su totalidad, para enfocarme en entender el comportamiento.

Manipulé propiedades como la gravedad y la restitución (rebote), haciendo que las letras reaccionaran de forma dinámica dentro del espacio. Además, integré el audio utilizando la amplitud para modificar la fuerza aplicada a las letras, generando movimientos más intensos cuando el sonido aumentaba.

El audio afectaba directamente el comportamiento físico: a mayor volumen, mayor movimiento o inestabilidad en las letras. Esto generaba una relación clara entre sonido y forma.

En la evaluación, funcionó bien la conexión entre audio y movimiento, ya que lograba una sensación de vida en la palabra. Sin embargo, no funcionó del todo la claridad semántica, porque el exceso de movimiento hacía que la palabra se volviera difícil de leer. Esto indica que debo equilibrar mejor la legibilidad con la expresividad para que el significado no se pierda.


## Bitácora de aplicación 



## Bitácora de reflexión
