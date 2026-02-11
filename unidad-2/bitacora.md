# Unidad 2

## Bitácora de proceso de aprendizaje

### Actividad 1

Mi referente favorito fue StarField de Jared S Tarbell, por la sencilla razón de que logra sumergir al espectador en un mundo alterno, no se siente estático, se siente real, orgánico y sin necesidad de twener colores ni efectos extraordinarios.

### Actividad 2

- ¿Cómo funciona la suma dos vectores en p5.js?

Para calcular la suma de dos vectores, se suman componente a componente de forma independiente.

- ¿Por qué esta línea position = position + velocity; no funciona?

esto es porque el signo más no esta sobrecargado con el sistema para realizar la suma entre dos objetos vectores.

### Actividad 3

- ¿Qué tuviste que hacer para hacer la conversión propuesta?

Para vectorizar el Ejemplo 0.2: A Random-Number Distribution, dentro del for del dibujo, en vez de calcular todo suelto, tengo que crear vectores; luego tengo que crear un arreglo de vectores que representen las posiciones base de cada barra; finalmente hay que usar el vector para dibujar sumando la posición base con el vector de crecimiento.

- Escribe el código que utilizaste para resolver el ejercicio.

```js
let randomCounts = [];
let bars = [];
let total = 20;

function setup() {
  createCanvas(640, 240);

  let w = width / total;

  for (let i = 0; i < total; i++) {
    randomCounts[i] = 0;
    bars.push(createVector(i * w, height));
  }
}

function draw() {
  background(255);

  let index = floor(random(randomCounts.length));
  randomCounts[index]++;

  let w = width / randomCounts.length;

  stroke(0);
  fill(127);

  for (let i = 0; i < bars.length; i++) {
    let base = bars[i];
    let growth = createVector(0, -randomCounts[i]);
    let top = p5.Vector.add(base, growth);

    rect(top.x, top.y, w - 1, randomCounts[i]);
  }
}
```

### Actividad 4

- ¿Qué resultado esperas obtener en el programa anterior?

Espero que se impriman en consola dos lines de texto donde se muestre cada valor de dos diferentes vectores , el primero como 6 9 0 y el segundo como 20 30 0 y de tercer linea un texto que dice Only Once.

- ¿Qué resultado obtuviste?

Similar a mi hipotesis, sin embargo al parecer a la hora de imprimir un vector tipo p5.vector y transformarlo con toString(), lo que se escribe es p5.Vector Object : [x, y, z], lo cual no pensé que fuese de esa forma.

- Recuerda los conceptos de paso por valor y paso por referencia en programación.

Paso por valor = la función recibe una fotocopia
Paso por referencia = la función recibe el original

- ¿Qué tipo de paso se está realizando en el código?

Se está realizando paso por referencia pues la función playingVector() logra sobreescribir los valores del vector original.

- ¿Qué aprendiste?

Aprendí que en el caso de necesitar que el paso de una referencia no se sobre escriba, se puede realizar la copia del elemento a pasar y se trabaja con el mismo.

### Actividad 5

- ¿Para qué sirve el método mag()? Nota que hay otro método llamado magSq(). ¿Cuál es la diferencia entre ambos? ¿Cuál es más eficiente?

`mag()` devuelve la longitud del vector, es decir, la distancia desde el origen (0,0) hasta el punto (x,y), `magSq()` devuelve lo mismo que mag() pero sin hacer la raíz cuadrada.

magSq() es más eficiente, porque la operación más costosa aquí es la raíz cuadrada (sqrt). Cuando trabajas con muchos vectores por frame (animaciones, partículas, físicas, interacciones), evitar esa raíz mejora el rendimiento.

- ¿Para qué sirve el método normalize()?

El método normalize() en p5.Vector sirve para convertir cualquier vector en un vector unitario (de longitud 1), sin cambiar su dirección.

- Te encuentras con un periodista en la calle y te pregunta ¿Para qué sirve el método dot()? ¿Qué le responderías en un frase?

El método dot() en p5.Vector calcula el producto punto (producto escalar) entre dos vectores.

- El método dot() tiene una versión estática y una de instancia. ¿Cuál es la diferencia entre ambas?

Ambos calculan exactamente el mismo producto punto. La diferencia no es matemática, sino cómo se llaman y desde dónde se usan.

- Ahora el mismo periodista curioso de antes te pregunta si le puedes dar una intuición geométrica acerca del producto cruz. Entonces te pregunta ¿Cuál es la interpretación geométrica del producto cruz de dos vectores? Tu respuesta debe incluir qué pasa con la orientación y la magnitud del vector resultante.

Geométricamengte, el vector resultante es, perpendicular al plano formado por los dos vectores originales. Si a y b están en el plano 2D (x, y), el resultado del cross apunta en el eje z. 

La dirección del vector resultante sigue la regla de la mano derecha. El orden importa, Cambiar el orden invierte la dirección.

La magnitud del vector resultante señala qué tan “abiertos” están los vectores entre sí. Geométricamente también indica el área del paralelogramo formado por los dos vectores. La magnitud del vector resultante es directamente proporcional a la magnitud del ángulo entre los vectores a ser operados.

- ¿Para que te puede servir el método dist()?

El método dist() en p5.Vector sirve para calcular la distancia real entre dos vectores (dos puntos en el plano), es decir, la distancia euclidiana entre sus posiciones.

Prodia usarlos para saber si dos partículas se tocan, medir cuánto falta para llegar a un punto, crear comportamientos tipo “seguir”, “huir”, “atracción” o detectar cercanía (colisiones, interacción).

- ¿Para qué sirven los métodos normalize() y limit()?

Estas controlan dos cosas distintas del movimiento, `normalize()` controla la dirección y `limit()` controla la velocidad máxima (magnitud)

### Actividad 6

El código que genera el resultado que te pedí.

```
let u = 0;
let speed = 0.01;
let dir = 1;

function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(200);
  
  let v0 = createVector(50, 50);
  let v1 = createVector(300, 0);
  let v2 = createVector(0, 300);

  u += speed * dir;
  if (u >= 1 || u <= 0) dir *= -1;

  let movingPoint = p5.Vector.lerp(v1, v2, u);

  drawArrow(v0, v1, "red");
  drawArrow(v0, v2, "blue");
  drawArrow(v0, movingPoint, "purple");
  drawArrow(p5.Vector.add(v0, v1), p5.Vector.sub(v2, v1), "green");
}

function drawArrow(base, vec, myColor) {
  push();
  stroke(myColor);
  strokeWeight(3);
  fill(myColor);
  translate(base.x, base.y);
  line(0, 0, vec.x, vec.y);
  rotate(vec.heading());
  let arrowSize = 7;
  translate(vec.mag() - arrowSize, 0);
  triangle(0, arrowSize / 2, 0, -arrowSize / 2, arrowSize, 0);
  pop();
}

```

¿Cómo funciona lerp() y lerpColor().

lerp(a, b, t) devuelve el valor que está a un porcentaje t entre a y b. En el caso lerpColor(), pasa lo mismo pero en valores de RGB.

¿Cómo se dibuja una flecha usando drawArrow()?

La función drawArrow(base, vec, color) dibuja una flecha a partir de un punto base y usando un vector como dirección y longitud.

### Actividad 7

- Cuál es el concepto del marco motion 101 y cómo se interpreta geométricamente.

El marco motion 101 relaciona los elementos que conforman las mecanicas de los elementos para implementarlos en los programas, esto a partir de los dictamenes de la Física mecánica, el cual establece que la posición final de un elemento se puede predecir a partir de la suma entre la posicion inicial y su velocidad multiplicado por el cambio de tiempo. Así mismo para determinar proxima velocidad se aplica de forma similar, pues esta determinada por la velocidad inicial sumada a la multiplicación entre la aceleridad y el cambio en el tiempo. Finalmente para hallar se usa la Ley de Newton que establece que la sumatoria de fuerzas aplicadas a un elemento es igual a la multiplicación entre su masa y aceleración.

- ¿Cómo se aplica motion 101 en el ejemplo?

Esto en el ejemplo se refleja en el momento en que se calculan las magnitude spor medio de estas formulas y se suman los vectores para dar un efecto de movimiento de aceleración constante.

### Actividad 8

- ¿Qué observaste cuando usas cada una de las aceleraciones propuestas?

Con aceleración constante se genera unmovimiento que se siente rigido y seco, con aceleración aleatoria, se vuelve impredecible la velocidad con que se moverá el elemento en cualquier momento así que lo hace tener un movieminto interesante y orgánico, y con aceleración hacia el mouse logra además de implementar un diseño interactivo, además permite predecir no solo visual sino manualmente el moviemiento del elemento.

## Bitácora de aplicación 

### Actividad 9

- Describe el concepto de tu obra generativa. Explica el concepto de tu obra generativa, qué regla aplicaste para la aceleración y por qué, si fue una decisión de diseño, o qué te evoca, si fue una exploración artística.

Mi obra esta pensada para revivir un sentimiento casi infantil en el que posees un juguete y eres capaz de transformar el canvas mientras juegas. Uso velocidad y aceleración, esto con la intención de darle una completa sensación realista y orgánica al movimiento del objeto. Fue inicialmente una idea de tener la sensación de tener un objeto amarrado con una cuerda, fué lo que primordialmente logré y las funcionalidades de color y rebote fueron saliendo en el proceso.

- El código de la aplicación.

```js
let points = [];
let segments = 15;
let segLength = 5;
let circler = 30;

let bgColor;
let fgColor;

function setup() {
  background(255);
  createCanvas(700, 600);

  bgColor = color(0);
  fgColor = color(255);

  for (let i = 0; i <= segments; i++) {
    points.push(new Point(width / 2, height / 2 + i * segLength));
  }
}

function draw() {
  noStroke();
  fill(red(bgColor), green(bgColor), blue(bgColor), 50);
     rect(0, 0, width, height);

  for (let p of points) {
    p.update();
  }

  constrainPoints();

  // Revisar rebote SOLO del último punto (el círculo)
  let last = points[points.length - 1];
  let bounced = last.constrainToCanvas(true);

  // Los demás puntos también se contienen, pero sin disparar color
  for (let i = 0; i < points.length - 1; i++) {
    points[i].constrainToCanvas(false);
  }

  if (bounced) {
    randomizeColors();
  }

  // dibujar cuerda
  stroke(fgColor);
  noFill();
  beginShape();
  for (let p of points) {
    vertex(p.pos.x, p.pos.y);
  }
  endShape();

  // círculo
  fill(fgColor);
  noStroke();
  circle(last.pos.x, last.pos.y, circler);
}

function randomizeColors() {
  bgColor = color(random(255), random(255), random(255));
  fgColor = color(random(255), random(255), random(255));
}

function constrainPoints() {
  // el primer punto está amarrado al mouse
  points[0].pos.set(mouseX, mouseY);

  for (let i = 0; i < 10; i++) {
    for (let j = 0; j < points.length - 1; j++) {
      let p1 = points[j];
      let p2 = points[j + 1];

      let diff = p5.Vector.sub(p2.pos, p1.pos);
      let d = diff.mag();
      let error = segLength - d;
      diff.normalize();
      diff.mult(error * 0.5);

      if (j != 0) p1.pos.sub(diff);
      p2.pos.add(diff);
    }

    points[0].pos.set(mouseX, mouseY);
  }
}

class Point {
  constructor(x, y) {
    this.pos = createVector(x, y);
    this.old = this.pos.copy();
    this.bounce = 0.9;
  }

  update() {
    let vel = p5.Vector.sub(this.pos, this.old);
    this.old = this.pos.copy();
    this.pos.add(vel);
    this.pos.add(0, 0.25); // gravedad
  }

  // detectColor = true solo para el último punto
  constrainToCanvas(detectColor = false) {
    let vel = p5.Vector.sub(this.pos, this.old);
    let bounced = false;

    if (this.pos.x > width) {
      this.pos.x = width;
      this.old.x = this.pos.x + vel.x * this.bounce;
      bounced = true;
    }

    if (this.pos.x < 0) {
      this.pos.x = 0;
      this.old.x = this.pos.x + vel.x * this.bounce;
      bounced = true;
    }

    if (this.pos.y > height) {
      this.pos.y = height;
      this.old.y = this.pos.y + vel.y * this.bounce;
      bounced = true;
    }

    if (this.pos.y < 0) {
      this.pos.y = 0;
      this.old.y = this.pos.y + vel.y * this.bounce;
      bounced = true;
    }

    return detectColor && bounced;
  }
}
```

- Un enlace al proyecto en el editor de p5.js.

(Actividad 9 - simulación FGT)[https://editor.p5js.org/felipegtupb/sketches/yT9P18D7b]

- Selecciona capturas de pantalla representativas de tu pieza de arte generativa.

<img width="881" height="758" alt="image" src="https://github.com/user-attachments/assets/65921e89-30f1-41da-b3f2-549d6be426ce" />
<img width="880" height="754" alt="image" src="https://github.com/user-attachments/assets/b7f2cc65-18a0-484c-a7d6-27be0be6cf92" />


## Bitácora de reflexión





