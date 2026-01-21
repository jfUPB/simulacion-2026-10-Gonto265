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



## Bitácora de aplicación 



## Bitácora de reflexión
