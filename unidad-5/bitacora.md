# Unidad 5
## Bitácora de proceso de aprendizaje

### Actividad 01

- *¿Qué propiedades tiene cada partícula? Clasifícalas: ¿Cuáles definen su estado físico? ¿Cuáles su estado vital?*

Cada partícula tiene propiedades como posición, velocidad y aceleración, que definen su estado físico porque determinan cómo se mueve en el espacio. También tiene una propiedad llamada lifespan que representa su estado vital, ya que indica cuánto tiempo le queda antes de desaparecer.

- *¿Qué condición determina que una partícula “muere”? ¿Es una muerte instantánea o gradual?*

Una partícula muere cuando su valor de lifespan llega a cero o es menor. No es una muerte instantánea, sino gradual, porque el lifespan disminuye poco a poco en cada frame.

- *¿Cómo se actualiza la partícula en cada frame? Identifica el patrón motion 101 dentro de la partícula.*

En cada frame, la partícula sigue el patrón motion 101: primero se suma la aceleración a la velocidad, luego la velocidad a la posición, después se reinicia la aceleración y finalmente se reduce el lifespan.

- *¿Quién crea las partículas? ¿En qué momento?*

Las partículas son creadas desde el sketch principal, generalmente en cada frame dentro de la función draw.

- *¿Quién decide cuándo eliminar una partícula del array?*

El sketch principal es quien revisa si una partícula está muerta y decide eliminarla del array.

- *¿Por qué se recorre el array en orden inverso para eliminar? ¿Qué pasaría si no se hiciera así?*

Se recorre en orden inverso para evitar errores al eliminar elementos, ya que al borrar uno cambian los índices. Si no se hiciera así, podrían saltarse partículas o producirse fallos en la ejecución.

- *Si no eliminaras nunca las partículas, ¿Qué pasaría con la memoria y el rendimiento?*

El número de partículas crecería sin límite, lo que aumentaría el consumo de memoria y disminuiría el rendimiento hasta afectar el frame rate.

- *¿Qué elementos visuales usa para representar una partícula?*

Se representa normalmente con una figura simple como un círculo.

- *¿Cómo se conecta el “tiempo de vida” con la apariencia visual?*

El lifespan se relaciona con la transparencia del objeto, haciendo que la partícula se desvanezca visualmente con el tiempo.

- *Si quisieras cambiar la representación visual, ¿Qué cambiarías y qué NO cambiarías?*

Solo cambiaría el método de visualización (display), sin modificar la lógica de movimiento, estructura ni el sistema de vida.

---

### Actividad 02

- *¿Qué responsabilidades que antes estaban en draw() ahora están dentro de la clase Emitter?*

En este caso, la creación, actualización y eliminación de partículas se trasladan desde draw() hacia la clase Emitter, centralizando la lógica del sistema.

- *¿Cuál es la ventaja de encapsular la lógica de emisión en una clase separada?*

Permite organizar mejor el código, hacerlo más reutilizable y facilitar la creación de múltiples sistemas independientes.

- *¿Quién crea los emitters? ¿Quién crea las partículas dentro de cada emitter?*

El sketch principal crea los emitters, mientras que cada emitter es responsable de crear sus propias partículas.

- *Dibuja un diagrama que muestre la jerarquía*

Existe una jerarquía en la que el sketch contiene un conjunto de emitters, y cada emitter contiene un conjunto de partículas, formando dos niveles de colección.

- *Describe este ejemplo sin mencionar herramientas específicas*

Un sistema está compuesto por emisores que generan entidades con estado y ciclo de vida. Estas entidades evolucionan en el tiempo siguiendo reglas de movimiento y desaparecen cuando su energía se agota. La organización es jerárquica y cada nivel gestiona al siguiente.

---

### Actividad 03

- *¿Qué tienen en común las subclases de partículas? ¿Qué tienen de diferente?*

Todas las subclases comparten la misma lógica de movimiento y ciclo de vida, pero se diferencian en la forma en que se representan visualmente o en pequeños comportamientos específicos.

- *¿Por qué es importante que el Emitter no necesite saber qué tipo específico de partícula está gestionando?*

Porque permite tratar todas las partículas de forma uniforme, facilitando la extensión del sistema sin modificar su estructura interna.

- *Si quisieras agregar un tercer tipo de partícula, ¿Qué tendrías que crear y qué NO modificarías?*

Solo sería necesario crear una nueva subclase de partícula, sin modificar el emitter ni la lógica general del sistema.

- *Compara con Example 4.2*

La lógica del emitter no cambia porque en 4.2 no existía como clase. La lógica de muerte se mantiene igual. Lo que cambia es la capa de especialización, añadiendo diversidad en los tipos de partículas.

---

### Actividad 04

- *En Example 4.6, ¿Dónde se define la gravedad? ¿Quién la aplica? ¿Es global o local?*

La gravedad se define fuera de las partículas y se aplica desde el sistema a cada una de ellas, por lo que es una fuerza global.

- *En Example 4.7, ¿Qué diferencia hay entre la gravedad y la fuerza del repeller?*

La gravedad es constante y global, mientras que el repeller es un objeto que genera una fuerza variable dependiendo de la distancia, siendo una interacción local.

- *¿Qué principio físico se está modelando?*

Se modela un comportamiento similar a la ley del inverso del cuadrado, donde la fuerza depende de la distancia entre dos objetos.

- *¿Cambió la clase Particle entre 4.6 y 4.7? ¿Qué implica esto?*

No cambia, lo que demuestra que las fuerzas externas pueden modificarse sin alterar la estructura interna de la partícula.

- *Tabla comparativa*

En 4.2 las partículas las crea el sketch, no hay emitter, ni herencia ni fuerzas externas ni interacción. En 4.4 los emitters crean partículas y aparece la estructura jerárquica. En 4.5 se introduce herencia sin cambiar la lógica base. En 4.6 se agregan fuerzas externas globales. En 4.7 se añade interacción mediante fuerzas dependientes de la distancia, manteniendo el mismo sistema base.

- *Modificación quirúrgica*

Se modificó únicamente la visualización cambiando la forma de las partículas en el método display. No fue necesario alterar la estructura, las fuerzas ni la lógica de vida. Esto es posible porque el sistema está organizado en capas independientes, permitiendo cambios locales sin afectar el resto del programa.

## Bitácora de aplicación 

```js
/**
 * UNIDAD 5: Sistema de Partículas
 * Proyecto: "Así de efímeras son las ideas"
 * 
 * Concepto: Luces difuminadas que nacen brillantes y mueren grises.
 * La intervención humana (clic) las expande y las hace trascender.
 */

let sistema;
let bgPulse = 0; // Intensidad del brillo de fondo
let colorPulso;

function setup() {
  createCanvas(windowWidth, windowHeight);
  sistema = new SistemaDeIdeas();
  colorPulso = color(0, 100, 200); // Azul para el pulso
  noCursor(); // Ocultamos el cursor para usar una luz propia
}

function draw() {
  // Fondo oscuro con reacción al pulso
  let r = map(bgPulse, 0, 255, 10, 20);
  let g = map(bgPulse, 0, 255, 15, 40);
  let b = map(bgPulse, 0, 255, 25, 80);
  background(r, g, b);
  
  if (bgPulse > 0) bgPulse -= 2; // Desvanecimiento suave del pulso

  // Generar una nueva idea cada cierto tiempo (movimiento limpio)
  if (frameCount % 45 == 0) {
    sistema.addIdea(random(width), random(height));
  }

  sistema.run();
  
  // Guía visual para el usuario (un pequeño resplandor en el mouse)
  drawMouseGlow();
}

function mousePressed() {
  sistema.checkClick(mouseX, mouseY);
}

// --- CLASE EMISORA ---
class SistemaDeIdeas {
  constructor() {
    this.ideas = [];
  }

  addIdea(x, y) {
    this.ideas.push(new Idea(x, y));
  }

  run() {
    for (let i = this.ideas.length - 1; i >= 0; i--) {
      let id = this.ideas[i];
      id.update();
      id.display();

      if (id.isDead()) {
        if (id.enriquecida) bgPulse = 180; // Activa el pulso de fondo
        this.ideas.splice(i, 1);
      }
    }
  }

  checkClick(mx, my) {
    for (let id of this.ideas) {
      let d = dist(mx, my, id.pos.x, id.pos.y);
      if (d < 60 && !id.enriquecida) {
        id.enriquecer(); // Transforma la idea al hacer clic
      }
    }
  }
}

// --- CLASE PARTÍCULA ---
class Idea {
  constructor(x, y) {
    this.pos = createVector(x, y);
    // Movimiento suave y limpio
    this.vel = createVector(random(-0.5, 0.5), random(-0.5, 0.5));
    this.lifespan = 255;
    this.baseSize = random(40, 70);
    this.currentSize = this.baseSize;
    
    this.enriquecida = false;
    
    // Colores iniciales
    this.cInicio = color(255, 230, 100); // Amarillo brillante
    this.cFinal = color(100, 100, 100);  // Gris
    this.cTrascendente = color(150, 230, 255); // Azul claro
  }

  update() {
    this.pos.add(this.vel);
    this.lifespan -= 0.8; // Desgaste lento

    if (!this.enriquecida) {
      // Comportamiento normal: se encoge y se vuelve gris
      this.currentSize = map(this.lifespan, 255, 0, this.baseSize, 5);
    } else {
      // Comportamiento enriquecido: crece
      this.currentSize += 0.5;
      this.lifespan -= 1.2; // Muere un poco más rápido al ser tan intensa
    }
  }

  enriquecer() {
    this.enriquecida = true;
    this.vel.mult(0.2); // Se vuelve más pausada y contemplativa
  }

  isDead() {
    return this.lifespan < 0;
  }

  display() {
    push();
    noStroke();
    
    let col;
    if (!this.enriquecida) {
      // Mezcla de amarillo a gris según la vida
      let amt = map(this.lifespan, 255, 0, 0, 1);
      col = lerpColor(this.cInicio, this.cFinal, amt);
    } else {
      col = this.cTrascendente;
    }

    // Dibujo de la "Luz Difuminada" (capas de resplandor)
    for (let i = 4; i > 0; i--) {
      let p = i * 10;
      let alpha = map(i, 4, 0, 0, this.lifespan / (this.enriquecida ? 1 : 2));
      fill(red(col), green(col), blue(col), alpha);
      ellipse(this.pos.x, this.pos.y, this.currentSize + p);
    }
    
    // Núcleo más brillante
    fill(red(col), green(col), blue(col), this.lifespan);
    ellipse(this.pos.x, this.pos.y, this.currentSize * 0.3);
    pop();
  }
}

function drawMouseGlow() {
  noStroke();
  for(let i = 10; i > 0; i--) {
    fill(255, 10 - i);
    ellipse(mouseX, mouseY, i * 5);
  }
}
```

## Bitácora de reflexión
