# Unidad 4

## Bitácora de proceso de aprendizaje

### Actividad 2

- ¿Qué está pasando en esta simulación? ¿Cuál es la interacción?

muestra una barra con dos círculos en los extremos que gira alrededor de su centro. La animación ya rota sola porque `angle += 0.1` está en `draw()` y cada vez que presionas una tecla el ángulo aumenta, por lo cual, la figura rota un poco más.

- Nota que en cada frame se está trasladando el origen del sistema de coordenadas al centro de la pantalla. ¿Por qué crees que se hace esto? 

Por defecto en p5.js el origen (0,0) está en la esquina superior izquierda del canvas. Si rotáramos sin hacer `translate()` el objeto rotaría alrededor de esa esquina, no alrededor de su propio centro.

Con `translate(width/2, height/2)` movemos el origen al centro de la pantalla, lo que permite que la figura rote alrededor de su propio centro.

- Cuál es la relación entre el sistema de coordenadas y la función rotate().

El metodo `rotate(angle)` rota todo el sistema de coordenadas, no solo el objeto. Esto gira el eje X y Y, por lo cual las figuras se dibujan usando ese sistema transformado.

- Observa que al dibujar los elementos gráficos parece que se está dibujando en la posición (0, 0) del sistema de coordenadas. ¿Por qué crees que se hace esto? y ¿Por qué aunque en cada frame se hace lo mismo, los elementos gráficos rotan?

con `translate(width / 2, height / 2)` el origen del sistema de coordenadas se mueve al centro del canvas, (0,0) ya no es la esquina superior izquierda, ahora (0,0) es el centro de la pantalla.

Lo que pasa realmente es que en cada frame angle aumenta, `rotate(angle)` rota el sistema de coordenadas y luego se dibuja la línea y los círculos en ese sistema ya rotado.

- Identifica el marco motion 101. ¿Qué es lo que se está haciendo en este marco?

Se calcula aceleración (hacia el mouse), se actualiza velocidad con esa aceleración, se limita la velocidad, se actualiza posición y se dibuja el objeto orientado hacia su velocidad.

- ¿Qué hace la función heading()?

La función `heading()` devuelve el ángulo del vector respecto al eje X positivo. Calcula hacia dónde apunta el vector de velocidad y devuelve ese ángulo en radianes.

- ¿Qué hace la función push() y pop()? Realiza algunos experimentos para entender su funcionamiento.

Guardan y restauran el sistema de transformaciones. `push()` guarda el estado actual de posición del sistema de coordenadas, rotación, escala, estilos de dibujo, `pop()` restaura ese estado.

- ¿Qué hace rectMode(CENTER)? Realiza algunos experimentos para entender su funcionamiento.

Por defecto los rectángulos se dibujan desde la esquina superior izquierda. `rectMode(CENTER)` significa: (x,y) = centro del rectángulo. `rect(0,0,30,10)` dibuja el rectángulo centrado en el origen.

- ¿Cuál es la relación entre el ángulo de rotación y el vector de velocidad? Trata de dibujar en un papel el vector de velocidad y cómo se relaciona con el ángulo de rotación y la operación de traslación y rotación.

El objeto rota porque el ángulo del vector velocidad se usa directamente para la rotación.

### Actividad 3

- Ahora es momento de practicar los conceptos anterior. Crea una simulación de un vehículo que puedas conducir por la pantalla utilizando las teclas de flecha: la flecha izquierda acelera el vehículo hacia la izquierda, y la flecha derecha acelera hacia la derecha. El vehículo tendrá forma triangular y debe apuntar en la dirección en la que se está moviendo actualmente.

```js
let vehicle;

function setup() {
  createCanvas(640, 240);
  vehicle = new Vehicle();
}

function draw() {
  background(255);

  vehicle.update();
  vehicle.checkEdges();
  vehicle.display();
}

function keyPressed() {

  if (keyCode === LEFT_ARROW) {
    vehicle.acceleration = createVector(-0.2, 0);
  }

  if (keyCode === RIGHT_ARROW) {
    vehicle.acceleration = createVector(0.2, 0);
  }

}

function keyReleased() {
  vehicle.acceleration = createVector(0,0);
}

class Vehicle {

  constructor() {
    this.position = createVector(width/2, height/2);
    this.velocity = createVector(0,0);
    this.acceleration = createVector(0,0);
    this.topspeed = 5;
  }

  update() {

    // Motion 101
    this.velocity.add(this.acceleration);
    this.velocity.limit(this.topspeed);
    this.position.add(this.velocity);

  }

  display() {

    let angle = this.velocity.heading();

    push();
    translate(this.position.x, this.position.y);
    rotate(angle);

    stroke(0);
    fill(127);

    // vehículo triangular
    triangle(-15, -10, -15, 10, 15, 0);

    pop();

  }

  checkEdges() {

    if (this.position.x > width) {
      this.position.x = 0;
    } 
    else if (this.position.x < 0) {
      this.position.x = width;
    }

  }

}
```

### Actividad 4

- Identifica motion 101. ¿Qué modificación hay que hacer al motion 101 cuando se quiere agregar fuerzas acumulativas? Trata de recordar por qué es necesario hacer esta modificación.

El Motion 101 aparece dentro del método update() de la clase `Mover` con `this.velocity.add(this.acceleration)` y `this.position.add(this.velocity)`. 

Las fuerzas se acumulan en la aceleración `this.acceleration.add(f)`, después de actualizar la velocidad y posición, la aceleración se reinicia con `this.acceleration.mult(0)`. Si no se reinicia, las fuerzas se acumularían infinitamente.

- Identifica dónde está el Attractor en la simulación. Cambia el color de este.

Está en el centro, `this.position = createVector(width / 2, height / 2)`, y el color se controla en `display()`, lo cambio a rojo con `fill(255,0,0)`.

- Observa que el Attractor tiene dos atributos `this.dragging` y `this.rollover`. Estos atributos no se modifican en el código, pero permitirían mover el attractor con el mouse y cambiar su color cuando el mouse está sobre él. ¿Cómo podrías modificar el código para que esto funcione? considera las funciones que ofrece p5.js para interactuar con el mouse.

agrego en `draw()`:

```js
let d = dist(mouseX, mouseY, attractor.position.x, attractor.position.y);

if (d < attractor.mass) {
  attractor.rollover = true;
} else {
  attractor.rollover = false;
}
```

y las siguientes funciones:

```js
function mousePressed() {
  let d = dist(mouseX, mouseY, attractor.position.x, attractor.position.y);
  if (d < attractor.mass) {
    attractor.dragging = true;
  }
}

function mouseDragged() {
  if (attractor.dragging) {
    attractor.position.x = mouseX;
    attractor.position.y = mouseY;
  }
}

function mouseReleased() {
  attractor.dragging = false;
}
```

### Actividad 5

r es la distancia al origen y theta es el ángulo de rotación, `p5.Vector.fromAngle(theta,r)` convierte las coordenadas polares a cartesianas:

```js
x = r*cos(theta)
y = r*sin(theta)
```

Gracias a esto se puede dibujar un punto que gira y cambia su distancia al centro.

Luego aparece `let v = p5.Vector.fromAngle(theta)`. La función crea un vector unitario en la dirección del ángulo.

Eso significa que `v.x = cos(theta)` y `v.y = sin(theta)`, es decir que `radio = 1`.

Luego, El punto, mantiene una distancia constante r y cambia continuamente su ángulo. Esto produce un movimiento circular uniforme alrededor del centro.

### Actividad 6

```js
let amplitude = 80;
let angularVelocity = 0.05;
let phase = 0;

let theta = 0;

function setup() {
  createCanvas(640, 240);
}

function draw() {
  background(20);

  translate(width/2, height/2);

  for(let i = -5; i <= 5; i++){

    let localPhase = phase + i * 0.4;

    let x = amplitude * sin(theta + localPhase);
    let y = i * 20;

    noStroke();
    fill(255, 220, 100, 200);
    circle(x, y, 18);

    stroke(255, 120);
    line(0, y, x, y);
  }

  theta += angularVelocity;
}

function keyPressed(){

// amplitud
if(key === 'a'){ amplitude += 10; }
if(key === 'z'){ amplitude -= 10; }

// velocidad angular
if(key === 's'){ angularVelocity += 0.01; }
if(key === 'x'){ angularVelocity -= 0.01; }

// fase
if(key === 'd'){ phase += 0.2; }
if(key === 'c'){ phase -= 0.2; }

}
```

## Bitácora de aplicación 

- Describe el concepto de tu obra generativa. Recuerda que desde la unidad anterior añadimos la idea de narrativa a la obra generativa, para guiar algunas de las decisiones en la definición de reglas del sistema generativo. PERO OJO, no estamos contando una historia, estamos usando la narrativa como herramienta de diseño para la definición de reglas.

Este programa está inspirado en proyecto actual llamado Alpha Centauri, donde éste programa busca simular un creador y regente del universo.

```js
let particles = [];
let stars = [];
let t = 0;

class Particle {
  constructor(x, y) {
    this.pos = createVector(x, y);
    this.offset = random(1000);
    this.size = random(2,6);
    this.color = color(random(150,255), random(100,200), random(200,255));
  }

  update() {
    let amp = map(mouseY, 0, height, 20, 150);
    let freq = map(mouseX, 0, width, 0.01, 0.08);

    let wave = sin(t + this.offset) * amp;

    let nx = noise(this.offset, t) * width;
    let ny = height/2 + wave;

    this.pos.x = lerp(this.pos.x, nx, 0.02);
    this.pos.y = lerp(this.pos.y, ny, 0.05);
  }

  display() {
    noStroke();
    fill(this.color);
    ellipse(this.pos.x, this.pos.y, this.size);
  }
}

class Star {
  constructor() {
    this.x = random(width);
    this.y = random(height);
    this.size = random(1,3);
  }

  display() {
    fill(255);
    noStroke();
    ellipse(this.x, this.y, this.size);
  }
}

function setup() {
  createCanvas(windowWidth, windowHeight);

  // partículas cósmicas
  for (let i = 0; i < 120; i++) {
    particles.push(new Particle(random(width), random(height)));
  }

  // estrellas de fondo
  for (let i = 0; i < 300; i++) {
    stars.push(new Star());
  }
}

function draw() {

  // fondo con transparencia para efecto de movimiento
  background(5, 5, 20, 40);

  // dibujar estrellas
  for (let s of stars) {
    s.display();
  }

  // nebulosa suave
  noStroke();
  fill(120, 60, 200, 20);
  ellipse(width/2, height/2, 500);

  fill(50, 100, 255, 20);
  ellipse(mouseX, mouseY, 400);

  // partículas espaciales
  for (let p of particles) {
    p.update();
    p.display();
  }

  t += 0.03;
}

function mousePressed() {
  particles.push(new Particle(mouseX, mouseY));
}
```

[Alpha Centauri](https://editor.p5js.org/felipegtupb/sketches/S9lqQhmsM)

<img width="915" height="790" alt="image" src="https://github.com/user-attachments/assets/2b9859b3-0890-427a-94ba-3629703e8411" />

## Bitácora de reflexión



