# Unidad 1

## Bitácora de proceso de aprendizaje

### Actividad 1

- Piensa y describe en una sola frase y en tus propias palabras cómo la aleatoriedad influye en el arte generativo.

Pienso que el papel que cumple la aleaatoriedad en el arte generativo es el de permitir al desarrollador y/o artista, intanciar, de forma indeterminada pero controlada, el producto de un sistema o algorritmo que es propiamente creada y maneja un estilo y significado memorable.

### Actividad 2

Realiza el siguiente experimento y reporta los resultados en tu bitácora:

- Modifica el código del ejemplo Example 0.1: A Traditional Random Walk.

```js
let randomCounts = [];
let total = 20;

function setup() {
  createCanvas(640, 240);
  for (let i = 0; i < total; i++) {
    randomCounts[i] = 0;
  }
}

function draw() {
  background(random(225),random(225),random(225));
  const index = floor(random(total));
  randomCounts[index]++;

  // Draw a rectangle to graph results
  stroke(random(225),random(225),random(225));
  strokeWeight(2);
  fill(random(225),random(225),random(225));
  const w = width / randomCounts.length;

  for (let x = 0; x < randomCounts.length; x++) {
    rect(x * w, height - randomCounts[x], w - 1, randomCounts[x]);
  }
}
```

- Antes de ejecutar el código, escribe en tu bitácora qué esperas que suceda.

Lo que espero que suceda es que haya un suceción de colores, del fondo, columnas y sus contornos, que cambie rapida y amenamente.

- Ejecuta el código y escribe en tu bitácora qué sucedió realmente.

Definitivamente hubo una sucesión de colores aleatorios, sin embargo, no fue nada ameno, pues el cambio de color era directo y a favor de la velocidad de iteración de draw().

- Ocurrió lo que esperabas? ¿Por qué crees que sí o por qué crees que no?

No realmente, porsupuesto que el programa cumplia la función de elegir colores para fonod  y objetos de forma aleatoria de forma périodica, sin embargo faltó amenidad en el proceso, pues no tuve en cuenta la velocidad de iteración de `draw()`, por lo que los colores de el fondo y los objetos cambiaba de color a gran velocidad que hasta llegaba a molestar a la vista, para arreglar esto es posible agregar la función `frameRate(6)` en `setup()` con la finalidad de desacelerar la velocidad con que cambia los colores, esto afecta además la velocidad con que van creciendo las columnas.

### Actividad 3

- En tus propias palabras cuál es la diferencia entre una distribución uniforme y una no uniforme de números aleatorios.

La diferencia sería los parametros, mientras que no uniforme no cuenta con parametros, la uniforme si cuenta con paraametros para su distribución, en este caso de media y desviación estandar.

- Modifica el código de la caminata aleatoria para que utilice una distribución no uniforme, favoreciendo el movimiento hacia la derecha.

```js
// The Nature of Code
// Daniel Shiffman
// http://natureofcode.com

let walker;

function setup() {
  createCanvas(640, 240);
  walker = new Walker();
  background(255);
}

function draw() {
  walker.step();
  walker.show();
}

class Walker {
  constructor() {
    this.x = width / 2;
    this.y = height / 2;
  }

  show() {
    stroke(0);
    point(this.x, this.y);
  }

  step() {
// se cambia random(4) por randomGaussian(0) para favorecer x++:
    const choice = floor(randomGaussian(0,1));
    if (choice == 0) {
      this.x++;
    } else if (choice == 1) {
      this.x--;
    } else if (choice == 2) {
      this.y++;
    } else {
      this.y--;
    }
  }
}
```

### Actividad 4

Una vez has entendido el concepto de distribución normal, vas a pensar en una nueva manera de visualizarlo.

- Crea un nuevo sketch en p5.js que represente una distribución normal.
- Copia el código en tu bitácora.
- Coloca en enlace a tu sketch en p5.js en tu bitácora.
- Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.

[Actividad 4 - Simulación FGT](https://editor.p5js.org/felipegtupb/sketches/DvRkkfW_f)

<img width="496" height="497" alt="image" src="https://github.com/user-attachments/assets/7b69cb9c-26de-4d38-ad40-2c1b336facfb" />

```
function setup() {
  createCanvas(400, 400);
  background(220);
}

function draw() {
  frameRate(10)
  let x = randomGaussian(250,60)
  let y = randomGaussian(250,60)
  let r = random(225)
  let g = random(225)
  let b = random(225)
  let a = random(225)
  
  noStroke()
  fill(r,g,b,a)
  circle(x,200,10)
  circle(200,x,10)
  circle(x,x,10)
  circle(x,-x+400,10)
}
```

### Actividad 5

Ahora vas a:

- Crea un nuevo sketch en p5.js donde modifiques uno de los ejemplos anteriores y adiciones de Lévy flight.
- Explica por qué usaste esta técnica y qué resultados esperabas obtener.

Usé esta técnica usé para que la diferenciación de las probabilidades sea aún más evidente además de dar una visualización más lineal de las mismas. Lo que esperaba fué exactamente lo que resultó, una barra que cambia su largo en el eje x según los valores que ofrece Lévy Flight, que además cambia su color según el lado del umbral (200) esté.

- Copia el código en tu bitácora.

```js
function setup() {
  createCanvas(400, 400);
}

function draw() {
  frameRate(6);
  background(220);
  rect(0, 200 - 35, acceptreject(), 70);
}

function acceptreject() {
  while (true) {
    r1 = random(400);
    probability = r1;
    r2 = random(400);

    if (r1 > 200) {
      fill(0, 0, 225);
    } else {
      fill(225, 0, 0);
    }

    if (r2 < probability) {
      return r1;
    }
  }
}
```

- Coloca en enlace a tu sketch en p5.js en tu bitácora.

[Actividad 5 - Simulación FGT](https://editor.p5js.org/felipegtupb/sketches/BQm6dtnQ_)

- Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.

<img width="253" height="250" alt="image" src="https://github.com/user-attachments/assets/8938191e-28d3-4a04-bc2b-32685d3e82ee" />
<img width="249" height="250" alt="image" src="https://github.com/user-attachments/assets/19cd26db-1699-4e21-8ad6-885d55a6fa13" />

### Actividad 6

Una vez has entendido el concepto de ruido Perlin, vas a pensar en una nueva manera de visualizarlo.

- Crea un nuevo sketch en p5.js donde los visualices.
- Explica el concepto qué resultados esberabas obtener.

Espero obtener variedad de figuras, que puedan identificarse como insectos voladores, de diferentes tamaños y tonalidades de amarillo volando por el canvas de forma aleatoria según el patrón Perlin Noise para un movimiento orgánico.

- Copia el código en tu bitácora.

```js
let walkers = [];
let total = 40;

function setup() {
  createCanvas(640, 240);

  for (let i = 0; i < total; i++) {
    walkers.push(new Walker());
  }
}

function draw() {
  background(200);

  for (let w of walkers) {
    w.step();
    w.show();
  }
}

class Walker {
  constructor() {
    this.colorsillo = random(255);
    this.tx = random(1000);
    this.ty = random(1000);
    this.velocidad = random(0.005, 0.02);
    this.tamanoygeneral = random(5, 8);
    this.tamanorectx = random(10, 15);
  }

  step() {
    this.x = map(noise(this.tx), 0, 1, 0, width);
    this.y = map(noise(this.ty), 0, 1, 0, height);

    this.tx += this.velocidad;
    this.ty += this.velocidad;
  }

  show() {
    noStroke();
    fill(127);
    circle(this.x + 10, this.y, this.tamanoygeneral);
    circle(this.x + 3, this.y, this.tamanoygeneral);
    fill(this.colorsillo, this.colorsillo, 0);
    rect(this.x, this.y, this.tamanorectx, this.tamanoygeneral - 3);
  }
}

```

- Coloca en enlace a tu sketch en p5.js en tu bitácora.

[Actividad 6 (Candelillas y moscas) - simulación FGT](https://editor.p5js.org/felipegtupb/sketches/ZXTDVDOj1)

- Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.

<img width="795" height="296" alt="image" src="https://github.com/user-attachments/assets/f69f2597-5199-41e1-80a0-74be6992c311" />

## Bitácora de aplicación 

### Actividad 7

**Creación de obra generativa**

Vas a crear una obra generativa interactiva en tiempo real utilizando los conceptos de aleatoriedad que has aprendido en esta unidad.
Tu obra debe:

- Usar al menos tres conceptos estudiados en esta unidad COMBINADOS de manera creativa y coherente.
- Tu obra de ser interactiva y generativa en tiempo real. Puedes usar el mouse, el teclado o cualquier otro sensor de entrada para interactuar con la obra.

Reporta en tu bitácora lo siguiente:

- Un texto donde expliques el concepto de obra generativa.

Quiero que mi pantalla por defecto cambie sus colores de forma lenta y orgánica para lo que usaré el ruido perlin, además ajustaré algunos inputs de teclado para añadir figuras, con la particularidad de que mientras mantenga el input, el click del mouse, empezará una rafaga de un tipo de forma determinado en el que el tamaño y color sean aleatorios según ruido Perlin y el Levy Flight.

- Copia el código en tu bitácora.

```
let colorManager;
let fgManager;
let trailLayer;
let figures = [];

function setup() {
  createCanvas(700, 590);

  colorManager = new RandomColorRampGenerator();
  trailLayer = createGraphics(width, height);
  trailLayer.colorMode(RGB, 255);
  trailLayer.noStroke();
}

function draw() {
  colorManager.colorChange();

  background(colorManager.r, colorManager.g, colorManager.b);
  image(trailLayer, 0, 0);

  if (mouseIsPressed && frameCount % 5 === 0) {
    figures.push(new FigureGenerator(trailLayer));
  }

  for (let f of figures) {
    f.update();
    f.draw();
  }
}

function LevyFlight() {
  let r = random(1);
  let step;
  if (r < 0.05) {
    step = random(0, 200);
  } else {
    step = random(0, 50);
  }
  return step;
}

class RandomColorRampGenerator {
  constructor() {
    this.tr = random(1000);
    this.tg = random(1000);
    this.tb = random(1000);
  }

  colorChange() {
    this.r = Math.floor(map(noise(this.tr), 0, 1, 0, 255));
    this.g = Math.floor(map(noise(this.tg), 0, 1, 0, 255));
    this.b = Math.floor(map(noise(this.tb), 0, 1, 0, 255));
    this.tr += 0.04;
    this.tg += 0.04;
    this.tb += 0.04;
    return {
      r: this.r,
      g: this.g,
      b: this.b,
    };
  }
}

class FigureGenerator {
  constructor(pg) {
    this.pg = pg;
    this.colore = new RandomColorRampGenerator();
    this.colore.colorChange();

    this.figure = floor(random(1, 4));
    this.size = LevyFlight();

    this.x = mouseX;
    this.y = mouseY;
  }

  update() {
    this.colore.colorChange();
  }

  draw() {
    this.pg.fill(this.colore.r, this.colore.g, this.colore.b, 120);

    if (this.figure === 1) {
      this.pg.square(this.x, this.y, this.size);
    } else if (this.figure === 2) {
      this.pg.circle(this.x, this.y, this.size);
    } else {
      this.pg.triangle(
        this.x,
        this.y,
        this.x + this.size,
        this.y,
        this.x + this.size / 2,
        this.y - this.size
      );
    }
  }
}

```

- Coloca en enlace a tu sketch en p5.js en tu bitácora.

(Actividad 7 - simulación FGT)[https://editor.p5js.org/felipegtupb/sketches/qVhVKGaEv]

- Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.

<img width="435.5" height="368" alt="image" src="https://github.com/user-attachments/assets/b56b99a4-cbb5-4338-995a-6de3f4822155" />
<img width="435.5" height="368" alt="image" src="https://github.com/user-attachments/assets/ce688c3f-8245-4a0e-adee-d5781e67dd2d" />

## Bitácora de reflexión









