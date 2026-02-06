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
### Actividad 7

- Cuál es el concepto del marco motion 101 y cómo se interpreta geométricamente.

El marco motion 101 relaciona los elementos que conforman las mecanicas de los elementos para implementarlos en los programas, esto a partir de los dictamenes de la Física mecánica, el cual establece que la posición final de un elemento se puede predecir a partir de la suma entre la posicion inicial y su velocidad multiplicado por el cambio de tiempo. Así mismo para determinar proxima velocidad se aplica de forma similar, pues esta determinada por la velocidad inicial sumada a la multiplicación entre la aceleridad y el cambio en el tiempo. Finalmente para hallar se usa la Ley de Newton que establece que la sumatoria de fuerzas aplicadas a un elemento es igual a la multiplicación entre su masa y aceleración.

- ¿Cómo se aplica motion 101 en el ejemplo?

Esto en el ejemplo se refleja en el momento en que se calculan las magnitude spor medio de estas formulas y se suman los vectores para dar un efecto de movimiento de aceleración constante.

## Bitácora de aplicación 



## Bitácora de reflexión


