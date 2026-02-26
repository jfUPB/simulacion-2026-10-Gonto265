# Unidad 3

## Bitácora de proceso de aprendizaje

### Actividad 1

Inicialmente, ví a la IA como simplemente una herramienta que podria resolver muchos problemas contemporaneos, nunca habia reflexionado el que esos problemas fuesen en realidad incomodidades desarrolladas de forma capitalista, y de alguna forma estoy de acuerdo con que el uso de deliberadamente mediocre de la herramienta es destructivo a largo plazo, aun asi desde mi perspectiva como estudiante e individuo de mi generación considero que es una pieza clave para el desarrollo humano y tecnológico, aun asi se necesita saber cual es ese limite donde perjudica el uso de IA.

### Actividad 2

La forma en que esta lectura me abre la mente es que en realidad muchos de los componentes de nuestros programas podrian no siempre ser arbitrarios, podriamos scarle mayor partido a cada uno de elos si tratamos de modificarlos y significarlos de forma creativa, Definitivamente lo que me parece más intersesante es el hecho de que nos podemos inventar nuestras propias fuerzas, a pesar de que esté basado en fundamentos tan teóricos.

### Actividad 3

[**Fricción**](https://editor.p5js.org/felipegtupb/sketches/0lZpjUMeA)

[**Dinamica de fluidos**](https://editor.p5js.org/felipegtupb/sketches/IrLAudgiR)

[**Atracción gravitacional**](https://editor.p5js.org/felipegtupb/sketches/s4TlrZG24)

## Bitácora de aplicación 

La obra representa dinámicas migratorias en un territorio abstracto.

Los agentes representan individuos en desplazamiento, hay:

Zonas de atracción (oportunidad, estabilidad).

Zonas de repulsión (conflicto, exclusión).

Zonas densas (fricción social o burocrática).

La historia no está escrita:
emerge de las trayectorias.

El usuario no observa el fenómeno, lo altera.

```js
let agents = [];
let attractors = [];
let repellers = [];
let fluidOn = false;

function setup() {
  createCanvas(900, 600);
}

function draw() {
  background(10);

  // Spawn continuo
  if (frameCount % 20 === 0) {
    agents.push(new Agent(random(width), random(-50, 0)));
  }

  for (let a of agents) {

    let gravity = createVector(0, 0.1);
    a.applyForce(gravity);

    for (let att of attractors) {
      a.applyForce(att.attract(a));
      att.show();
    }

    for (let rep of repellers) {
      a.applyForce(rep.repel(a));
      rep.show();
    }

    if (fluidOn && a.position.y > height / 2) {
      a.applyDrag(0.05);
    }
    
    socialAttraction(agents);

    a.update();
    a.show();
  }

  if (fluidOn) {
    fill(0, 80, 150, 80);
    rect(0, 0, width, height);
  }


}

class Agent {

  constructor(x, y) {
    this.position = createVector(x, y);
    this.velocity = createVector(random(-1, 1), 0);
    this.acceleration = createVector(0, 0);
    this.mass = random(0.8, 1.5);
    this.size = 6;
  }

  applyForce(force) {
    let f = p5.Vector.div(force, this.mass);
    this.acceleration.add(f);
  }

  applyDrag(c) {
    let drag = this.velocity.copy();
    drag.mult(-1);
    drag.normalize();
    drag.mult(c * this.velocity.mag());
    this.applyForce(drag);
  }

  update() {
  this.velocity.add(this.acceleration);

  this.velocity.limit(15);

  this.position.add(this.velocity);
  this.acceleration.mult(0);
}

  show() {
    fill(random(255),random(255),random(255), 180);
    noStroke();
    circle(this.position.x, this.position.y, this.size);
  }
}

class Attractor {

  constructor(x, y) {
    this.position = createVector(x, y);
    this.power = 50;
  }

  attract(agent) {
    let force = p5.Vector.sub(this.position, agent.position);
    let d = constrain(force.mag(), 20, 200);
    force.normalize();
    force.mult(this.power / d);
    return force;
  }

  show() {
    fill(0, 255, 0);
    circle(this.position.x, this.position.y, 5);
  }
}

class Repeller {

  constructor(x, y) {
    this.position = createVector(x, y);
    this.power = 100;
  }

  repel(agent) {
    let force = p5.Vector.sub(agent.position, this.position);
    let d = constrain(force.mag(), 20, 200);
    force.normalize();
    force.mult(this.power / d);
    return force;
  }

  show() {
    fill(255, 0, 0);
    circle(this.position.x, this.position.y, 5);
  }
}

function mousePressed() {

  if (mouseButton === LEFT) {
    attractors.push(new Attractor(mouseX, mouseY));
  }

  if (mouseButton === RIGHT) {
    repellers.push(new Repeller(mouseX, mouseY));
  }
}

function keyPressed() {
  if (key === 'd' || key === 'D') {
    fluidOn = !fluidOn;
  }
}

function socialAttraction(particles) {

  let perceptionRadius = 60;

  for (let i = 0; i < particles.length; i++) {

    for (let j = i + 1; j < particles.length; j++) {

      let p1 = particles[i];
      let p2 = particles[j];

      let dir = p5.Vector.sub(p2.position, p1.position);
      let d = dir.mag();

      if (d > 5 && d < perceptionRadius) {

        dir.normalize();

        let strength = 0.03 * (1 - d / perceptionRadius);

        let force = dir.copy().mult(strength);

        p1.applyForce(force);
        p2.applyForce(force.copy().mult(-1)); 
        // fuerza opuesta para equilibrio
      }
    }
  }
}
```

[Actividad 4 - simulación FGT](https://editor.p5js.org/felipegtupb/sketches/_rxCK8KMB)

<img width="914" height="673" alt="image" src="https://github.com/user-attachments/assets/f55b2c5a-76f6-4a95-8a95-a3c877dc60d5" />

<img width="902" height="668" alt="image" src="https://github.com/user-attachments/assets/a961c3ca-5610-449c-9d73-427d4bea6cc6" />

## Bitácora de reflexión

- Explica detalladamente en tu bitácora ¿Qué es el marco de movimiento motion 101 y cómo se relacionan: fuerza, aceleración, velocidad y posición?

El marco de movimiento 101 es la forma básica en que se puede simular el movimiento de las masas, esto a partir de los distintos elementos que componen la fisica mecanica, como la velocidad, la aceleración, la posición, y las fuerzas. La forma en que estas se relacionan estos es que son derivados  o componentos de cada uno, es decir, la velocidad es derivada de  la posición, la aceleración es la suma de las fuerzas dividida por la masa, etc.

- Vas a analizar este video sobre el artista Alexander Calder. Selecciona una de sus obras y luego crea una obra generativa inspirada en la obra de Calder que seleccionaste y el marco de movimiento motion 101 con fuerzas que trabajamos en esta unidad.

[Actividad 5 - simulación FGT](https://editor.p5js.org/felipegtupb/sketches/vKx08CHzT)

```js
let nodes = [];
let num = 12;

function setup() {
  createCanvas(900, 600);

  for (let i = 0; i < num; i++) {
    nodes.push(new Node(
      random(width * 0.2, width * 0.8),
      random(height * 0.3, height * 0.7)
    ));
  }
}

function draw() {
  background(245);

  // Dibujar conexiones tipo estructura móvil
  drawConnections();

  for (let n of nodes) {
    n.applyForce(createVector(0, 0.03)); // gravedad más suave
    n.springToAnchor();                 // fuerza elástica equilibrada
    n.applyDrag(0.02);                  // fricción del aire
    n.update();
    n.show();
  }
}

function drawConnections() {
  stroke(0);
  strokeWeight(2);
  noFill();

  beginShape();
  for (let n of nodes) {
    curveVertex(n.position.x, n.position.y);
  }
  endShape();
}

class Node {

  constructor(x, y) {
    this.position = createVector(x, y);
    this.velocity = createVector(random(-0.5, 0.5), random(-0.5, 0.5));
    this.acceleration = createVector(0, 0);
    this.mass = random(1, 3);
    this.size = random(50, 110);

    // Anchor cercano para evitar que suban al techo
    this.anchor = createVector(
      x + random(-120, 120),
      y + random(-80, 80)
    );

    // Color fijo (no cambia cada frame)
    this.col = random([
      color(220, 40, 40),   // rojo
      color(30, 70, 200),   // azul
      color(240, 220, 50)   // amarillo
    ]);
  }

  applyForce(force) {
    let f = p5.Vector.div(force, this.mass);
    this.acceleration.add(f);
  }

  applyDrag(c) {
    let drag = this.velocity.copy();
    drag.mult(-1);
    drag.normalize();
    drag.mult(c * this.velocity.magSq());
    this.applyForce(drag);
  }

  springToAnchor() {
    let force = p5.Vector.sub(this.anchor, this.position);
    let k = 0.02; // constante elástica más fuerte
    force.mult(k);
    this.applyForce(force);
  }

  update() {
    this.velocity.add(this.acceleration);
    this.velocity.limit(3); // límite de velocidad estable
    this.position.add(this.velocity);
    this.acceleration.mult(0);
  }

  show() {
    noStroke();
    fill(this.col);
    ellipse(this.position.x, this.position.y, this.size);
  }
}

function mousePressed() {
  // Interacción: el usuario altera el equilibrio
  for (let n of nodes) {
    let force = p5.Vector.sub(createVector(mouseX, mouseY), n.position);
    force.setMag(300);
    n.applyForce(force);
  }
}
```

<img width="915" height="672" alt="image" src="https://github.com/user-attachments/assets/d906cffa-46df-45c5-b82d-00f1286f9019" />
