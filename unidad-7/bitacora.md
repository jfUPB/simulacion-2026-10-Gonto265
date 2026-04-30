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

Palabra elegida: Cohete

Mi intención es significar gráficamente la Palabra Cohete, ya que al ponerla en Mayúsculas y en vertical, La letra E puede convertirse en los propulsores de un cohete real, la o en el ventanal y La otra E en alerones.

La idea es que un cohete se encuentre se encuentre flotando en el espacio en gravedad 0 y que el usuario pueda controlar la velocidad del cohete por medio de su voz.

**Referencias**

<img width="735" height="1089" alt="space!🔭🪐☄️" src="https://github.com/user-attachments/assets/69896d49-8768-4485-b735-4e0a106948c7" />

<img width="736" height="920" alt="descarga (5)" src="https://github.com/user-attachments/assets/217c6f32-70d8-4017-9fce-e5e4ccea4e3f" />

<img width="735" height="490" alt="descarga (6)" src="https://github.com/user-attachments/assets/779dfc70-722d-4664-a19c-5928b4c14fcb" />

**Bocetos**

<img width="621" height="180" alt="1" src="https://github.com/user-attachments/assets/6988d5a7-4545-4122-b838-2ea8e78a28b3" />

<img width="219" height="650" alt="2" src="https://github.com/user-attachments/assets/68787001-8f85-4254-89da-68a5e508c576" />

<img width="389" height="708" alt="3" src="https://github.com/user-attachments/assets/5a8ebbb7-74b5-42e0-97de-6a093bfd8a13" />

<img width="1317" height="823" alt="image" src="https://github.com/user-attachments/assets/91887984-3a59-4398-a1ef-2b9807ce660e" />

<img width="1261" height="798" alt="image" src="https://github.com/user-attachments/assets/6551db9e-3678-4f1d-8833-fb1cad8cc396" />

**Mapa de Decisiones**

tipografía en mayúsculas y disposición vertical de la palabra “COHETE”: construcción de una silueta reconocible de cohete a partir de la palabra;

estiramiento de la C en la parte superior: generación de una punta aerodinámica que sugiere dirección y avance;

transformación de la O con una línea horizontal: representación de un ventanal que refuerza la lectura objetual del cohete;

uso de las dos E como elementos estructurales: la E inferior funciona como propulsores y la E media como alerones, conectando forma tipográfica con partes mecánicas;

deformación controlada de letras: adaptación de la tipografía para que pierda rigidez textual y gane lectura como objeto físico;

integración de cuerpos compuestos en Matter.js: construcción del cohete como un solo cuerpo con múltiples formas que respetan la silueta de las letras;

colisiones con límites del canvas: refuerzo de la sensación de objeto físico existente en un espacio, no solo representación gráfica;

ausencia de gravedad (gravedad cercana a cero): simulación de flotación espacial coherente con la idea de cohete en el espacio;

aplicación de fuerzas según amplitud de audio: traducción directa de la voz en aceleración, vinculando sonido con propulsión;

generación de partículas en los propulsores: visualización del empuje mediante fuego que aparece únicamente cuando hay sonido;

intensidad del fuego proporcional al volumen: correspondencia semántica entre fuerza sonora y potencia del motor;

fondo azul oscuro con estrellas: construcción de atmósfera espacial y sensación de profundidad;

animación inicial de rotación y transformación de la palabra: transición de palabra legible a objeto funcional, mostrando el proceso semántico;

zoom out posterior a la transformación: cambio de escala que posiciona la pieza como escena espacial interactiva;

interacción por micrófono (voz): uso del cuerpo del usuario como controlador performativo, alineado con la idea de propulsión;

**Mapa de interpretación**

inicio en silencio: el cohete permanece flotando sin impulso, con movimiento mínimo generado por inercia o pequeñas colisiones;

activación por voz suave: el cohete comienza a desplazarse lentamente, generando una combustión leve en los propulsores;

incremento de volumen: aumento progresivo de la velocidad y aparición de fuego más intenso, evidenciando mayor empuje;

picos de sonido (gritos o golpes): aceleraciones bruscas que pueden provocar choques contra los límites del espacio;

modulación de la voz: control fino de la trayectoria, permitiendo dirigir el movimiento mediante variaciones de intensidad;

silencio repentino: corte inmediato de la propulsión, dejando al cohete desplazarse por inercia;

uso del espacio del canvas: interacción con los bordes como límites físicos que rebotan el cohete, generando cambios de dirección;

exploración performativa: el usuario experimenta con ritmos, intensidades y pausas para “pilotear” el cohete;

lectura simbólica en vivo: la voz se interpreta como combustible o energía vital del cohete;

construcción de narrativa: la interacción puede percibirse como despegue, navegación o pérdida de control dependiendo del uso del sonido;

variación de energía en el tiempo: la pieza permite momentos de calma (flotación) y momentos de tensión (aceleración y choque);

relación cuerpo-sistema: el usuario no presiona botones, sino que usa su voz como extensión directa del comportamiento del objeto;

interpretación abierta: aunque el sistema responde físicamente, el significado se construye en la experiencia performativa del usuario.

**Uso de IA**
Inicialmente se plantea visualmente, interactividad y tecnicamente, luego se le dan las especificaciones de diseño por con el prompt de la imagen a continuación.

<img width="1866" height="948" alt="image" src="https://github.com/user-attachments/assets/3661368e-edd1-4082-9961-ccd00fc56d9c" />

A partir de esto y depués de 30 prompts, se dan correcciones y ajustes hasta quedar exactamente a lo propuesto.

**Código Fuente**

```js
const { Engine, World, Bodies, Body } = Matter;
let engine, world, rocketBody;
let walls = [];

let state = "START"; // START, IDLE, ROTATING, MORPHING, ZOOMING, FLIGHT
let timer = 0;
let morph = 0;
let globalRotation = 0; 
let camScale = 1.0;
let targetZoom = 0.35; 

let mic, volSmooth = 0;
let stars = [];
let particles = [];

function setup() {
  createCanvas(windowWidth, windowHeight);
  engine = Engine.create();
  world = engine.world;
  world.gravity.y = 0; 

  mic = new p5.AudioIn();
  mic.start();
}

function initExperience() {
  resizeCanvas(windowWidth, windowHeight);
  
  stars = [];
  let starArea = 4000; 
  for (let i = 0; i < 1000; i++) {
    stars.push({ x: random(-starArea, starArea), y: random(-starArea, starArea), s: random(1, 3), o: random(80, 200) });
  }

  rocketBody = Bodies.rectangle(0, 0, 450, 80, {
    frictionAir: 0.05,
    restitution: 0.8,
    density: 0.001
  });

  updateBoundaries();
  state = "IDLE";
}

function updateBoundaries() {
  World.remove(world, walls);
  let t = 1000; 
  let vW = (width / targetZoom) / 2;
  let vH = (height / targetZoom) / 2;
  walls = [
    Bodies.rectangle(0, -vH - t/2, vW * 2, t, { isStatic: true }),
    Bodies.rectangle(0, vH + t/2, vW * 2, t, { isStatic: true }),
    Bodies.rectangle(-vW - t/2, 0, t, vH * 2, { isStatic: true }),
    Bodies.rectangle(vW + t/2, 0, t, vH * 2, { isStatic: true })
  ];
  World.add(world, walls);
}

function mousePressed() {
  if (state === "START") {
    fullscreen(true);
    userStartAudio();
  }
}

function windowResized() {
  if (state === "START") setTimeout(initExperience, 150);
  else {
    resizeCanvas(windowWidth, windowHeight);
    updateBoundaries();
  }
}

function draw() {
  background(0); 
  if (state === "START") return;

  background(2, 4, 10);
  
  // Audio-reactividad: Suavizamos la entrada para una física fluida
  let rawVol = mic.getLevel();
  volSmooth = lerp(volSmooth, rawVol, 0.2); 

  updateSequence();

  push();
  translate(width/2, height/2);
  scale(camScale);
  
  drawStars();
  handleParticles(); 

  if (state === "FLIGHT") {
    applyPhysics();
    push();
    translate(rocketBody.position.x, rocketBody.position.y);
    rotate(rocketBody.angle); 
    drawRocketDesign();
    pop();
  } else {
    rotate(globalRotation);
    drawRocketDesign();
  }
  pop();

  Engine.update(engine);
}

function updateSequence() {
  if (state === "IDLE") {
    timer++;
    if (timer > 40) state = "ROTATING";
  }
  if (state === "ROTATING") {
    globalRotation = lerp(globalRotation, HALF_PI, 0.04);
    if (abs(globalRotation - HALF_PI) < 0.01) { globalRotation = HALF_PI; state = "MORPHING"; }
  }
  if (state === "MORPHING") {
    morph = lerp(morph, 1, 0.02);
    if (morph > 0.99) state = "ZOOMING";
  }
  if (state === "ZOOMING") {
    camScale = lerp(camScale, targetZoom, 0.02); 
    if (abs(camScale - targetZoom) < 0.01) {
      state = "FLIGHT";
      World.add(world, rocketBody);
      Body.setAngle(rocketBody, HALF_PI); 
    }
  }
}

function drawRocketDesign() {
  let letters = ["C", "O", "H", "E", "T", "E"];
  let spacing = 75; 
  let cGap = lerp(0, 65, morph); 
  
  textAlign(CENTER, CENTER);
  textStyle(BOLD);
  textSize(95);
  textFont('Arial');

  for (let i = 0; i < letters.length; i++) {
    let xPos = (i - 2.5) * spacing;
    if (i === 0) xPos -= cGap; 

    push();
    translate(xPos, 0);
    fill(255);
    noStroke();

    if (letters[i] === "C") {
      scale(lerp(1, 3.2, morph), 1);
      text("C", 0, 0);
    } 
    else if (letters[i] === "O") {
      text("O", 0, 0);
      if (morph > 0.5) {
        stroke(255); strokeWeight(6);
        line(20, 20, -20, -20);
      }
    } 
    else if (letters[i] === "E" && i === 3) {
      scale(1, lerp(1, 3.2, morph));
      text("E", 0, 0);
    } 
    else if (letters[i] === "E" && i === 5) {
      scale(lerp(1, 1.6, morph), 1.2);
      text("E", 0, 0);
      
      // DISPARO DE FUEGO REACTIVO
      if (state === "FLIGHT") {
        if (volSmooth > 0.01 || keyIsDown(32) || keyIsDown(UP_ARROW)) {
            // Si es por teclado, simulamos un volumen medio-alto (0.2)
            let currentIntensity = keyIsDown(32) || keyIsDown(UP_ARROW) ? 0.25 : volSmooth;
            spawnFire(currentIntensity);
        }
      }
    } 
    else { text(letters[i], 0, 0); }
    pop();
  }
}

function applyPhysics() {
  // ACELERACIÓN POR SONIDO
  if (volSmooth > 0.01 || keyIsDown(32) || keyIsDown(UP_ARROW)) {
    // Mapeamos el volumen a una fuerza física (0.01 a 0.2 es el rango normal de voz)
    let thrustPower = keyIsDown(32) || keyIsDown(UP_ARROW) ? 0.4 : map(volSmooth, 0.01, 0.3, 0.05, 1.2);
    
    let angle = rocketBody.angle + PI; 
    Body.applyForce(rocketBody, rocketBody.position, {
      x: cos(angle) * thrustPower,
      y: sin(angle) * thrustPower
    });
  }
  
  if (keyIsDown(LEFT_ARROW)) Body.setAngularVelocity(rocketBody, -0.05);
  if (keyIsDown(RIGHT_ARROW)) Body.setAngularVelocity(rocketBody, 0.05);
}

function spawnFire(intensity) {
  let baseDist = 205; 
  let engineOffsets = [-20, 0, 20]; 
  
  // A más intensidad, más partículas por frame
  let particleCount = map(intensity, 0.01, 0.4, 1, 4);

  engineOffsets.forEach(off => {
    for (let i = 0; i < particleCount; i++) {
      let fireAngle = rocketBody.angle; 
      let fX = rocketBody.position.x + cos(fireAngle) * baseDist + cos(rocketBody.angle + HALF_PI) * off;
      let fY = rocketBody.position.y + sin(fireAngle) * baseDist + sin(rocketBody.angle + HALF_PI) * off;
      
      particles.push(new Particle(fX, fY, fireAngle, intensity, rocketBody.velocity));
    }
  });
}

class Particle {
  constructor(x, y, a, intensity, v) {
    this.pos = createVector(x, y);
    // La velocidad de la partícula depende de la intensidad del sonido
    let speed = map(intensity, 0.01, 0.4, 10, 40);
    this.vel = p5.Vector.fromAngle(a + random(-0.1, 0.1)).mult(speed);
    this.vel.add(createVector(v.x, v.y).mult(0.5)); 
    
    this.life = 255;
    this.intensity = intensity;
    // Partículas más grandes con más sonido
    this.size = map(intensity, 0.01, 0.4, 10, 45);
  }
  
  update() { 
    this.pos.add(this.vel); 
    this.life -= 20; 
  }
  
  display() {
    noStroke();
    // COLOR SEMÁNTICO: 
    // Silencio -> Naranja/Rojo
    // Grito -> Blanco/Cian (Calor extremo)
    let colorA = color(255, 100, 0); // Naranja base
    let colorB = color(150, 255, 255); // Cian/Blanco calor
    
    let t = constrain(map(this.intensity, 0.05, 0.3, 0, 1), 0, 1);
    let baseCol = lerpColor(colorA, colorB, t);
    
    fill(red(baseCol), green(baseCol), blue(baseCol), this.life);
    ellipse(this.pos.x, this.pos.y, this.size);
  }
}

function handleParticles() {
  for (let i = particles.length - 1; i >= 0; i--) {
    particles[i].update();
    particles[i].display();
    if (particles[i].life <= 0) particles.splice(i, 1);
  }
}

function drawStars() {
  noStroke();
  stars.forEach(s => { fill(255, s.o); ellipse(s.x, s.y, s.s); });
}
```

**Enlace al sketch**

[CØHETE - Unidad 7 FGT Simulación](https://editor.p5js.org/felipegtupb/sketches/WR5kJUq2Q)

**Galería**

<img width="1919" height="1079" alt="Captura de pantalla 2026-04-30 042208" src="https://github.com/user-attachments/assets/ec3ae519-cf81-41bc-8978-7df1a3363d49" />

<img width="1919" height="1079" alt="Captura de pantalla 2026-04-30 042223" src="https://github.com/user-attachments/assets/de249283-2816-45cd-ab41-f21e2c46519a" />

<img width="1919" height="1079" alt="Captura de pantalla 2026-04-30 042308" src="https://github.com/user-attachments/assets/ac8fe7b5-ea85-4cb9-bbfa-c9643f53f794" />


## Bitácora de reflexión
