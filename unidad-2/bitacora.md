# Unidad 2

## Bitácora de proceso de aprendizaje

### Actividad 3

- ¿Qué tuviste que hacer para hacer la conversión propuesta?

Para vectorizar el Ejemplo 0.2: 

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

## Bitácora de aplicación 



## Bitácora de reflexión
