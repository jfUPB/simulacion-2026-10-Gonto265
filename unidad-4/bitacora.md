# Unidad 4

## Bitácora de proceso de aprendizaje

### Actividad 2

- ¿Qué está pasando en esta simulación? ¿Cuál es la interacción?

muestra una barra con dos círculos en los extremos que gira alrededor de su centro. La animación ya rota sola porque `angle += 0.1` está en `draw()` y cada vez que presionas una tecla el ángulo aumenta, por lo cual, la figura rota un poco más.

- Nota que en cada frame se está trasladando el origen del sistema de coordenadas al centro de la pantalla. ¿Por qué crees que se hace esto? 

Por defecto en p5.js el origen (0,0) está en la esquina superior izquierda del canvas. Si rotáramos sin hacer `translate()` el objeto rotaría alrededor de esa esquina, no alrededor de su propio centro.

Con `translate(width/2, height/2)` movemos el origen al centro de la pantalla, lo que permite que la figura rote alrededor de su propio centro.

- Cuál es la relación entre el sistema de coordenadas y la función rotate().

El metodo `rotate(angle)` rota todo el sistema de coordenadas, no solo el objeto. Esto gira el eje X y Y, por lo cual las figuras se dibujan usando ese sistema transformado.

- Observa que al dibujar los elementos gráficos parece que se está dibujando en la posición (0, 0) del sistema de coordenadas. ¿Por qué crees que se hace esto? y ¿Por qué aunque en cada frame se hace lo mismo, los elementos gráficos rotan?

con `translate(width / 2, height / 2)` el origen del sistema de coordenadas se mueve al centro del canvas, (0,0) ya no es la esquina superior izquierda, ahora (0,0) es el centro de la pantalla.

Lo que pasa realmente es que en cada frame angle aumenta, `rotate(angle)` rota el sistema de coordenadas y luego se dibuja la línea y los círculos en ese sistema ya rotado.

- Identifica el marco motion 101. ¿Qué es lo que se está haciendo en este marco?

Se calcula aceleración (hacia el mouse), se actualiza velocidad con esa aceleración, se limita la velocidad, se actualiza posición y se dibuja el objeto orientado hacia su velocidad.

- ¿Qué hace la función heading()?

La función `heading()` devuelve el ángulo del vector respecto al eje X positivo. Calcula hacia dónde apunta el vector de velocidad y devuelve ese ángulo en radianes.

- ¿Qué hace la función push() y pop()? Realiza algunos experimentos para entender su funcionamiento.

Guardan y restauran el sistema de transformaciones. `push()` guarda el estado actual de posición del sistema de coordenadas, rotación, escala, estilos de dibujo, `pop()` restaura ese estado.

- ¿Qué hace rectMode(CENTER)? Realiza algunos experimentos para entender su funcionamiento.



- ¿Cuál es la relación entre el ángulo de rotación y el vector de velocidad? Trata de dibujar en un papel el vector de velocidad y cómo se relaciona con el ángulo de rotación y la operación de traslación y rotación.



## Bitácora de aplicación 



## Bitácora de reflexión
