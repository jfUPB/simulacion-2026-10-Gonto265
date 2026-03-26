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


## Bitácora de reflexión
