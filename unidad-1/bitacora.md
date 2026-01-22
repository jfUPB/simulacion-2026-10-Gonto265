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



- Copia el código en tu bitácora.



- Coloca en enlace a tu sketch en p5.js en tu bitácora.

[Actividad 5 - Simulación FGT](https://editor.p5js.org/felipegtupb/sketches/BQm6dtnQ_)

- Selecciona una captura de pantalla de tu sketch y colócala en tu bitácora.

<img width="253" height="250" alt="image" src="https://github.com/user-attachments/assets/8938191e-28d3-4a04-bc2b-32685d3e82ee" />
<img width="249" height="250" alt="image" src="https://github.com/user-attachments/assets/19cd26db-1699-4e21-8ad6-885d55a6fa13" />

## Bitácora de aplicación 



## Bitácora de reflexión



