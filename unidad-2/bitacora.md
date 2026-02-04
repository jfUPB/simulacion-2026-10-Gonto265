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

## Bitácora de aplicación 



## Bitácora de reflexión

