# Unidad 6

## Bitácora de proceso de aprendizaje

### Actividad 01

Punto: Selección de referentes

Se seleccionaron dos piezas del artista generativo Tyler Hobbs: Flow Field Lines y Fidenza.

Punto: Decisiones visuales (composición, densidad, dirección, color, ritmo, repetición y variación)

En Flow Field Lines, la composición es homogénea, con líneas distribuidas sin jerarquía central. La densidad es alta pero controlada, la dirección fluye en curvas suaves y el color se mantiene en una paleta limitada. El ritmo es constante y orgánico, y la repetición de líneas se equilibra con variaciones en su trayectoria.

En Fidenza, la composición es más fragmentada, con formas que se expanden en bloques. La densidad varía, la dirección es menos uniforme, el color tiene mayor contraste y el ritmo alterna entre zonas calmadas y dinámicas. La repetición estructural se combina con variaciones formales.

Punto: ¿Por qué son potentes estas decisiones?

Son potentes porque equilibran control y complejidad emergente, logrando sistemas coherentes que no se vuelven predecibles. Mantienen tensión visual sin perder unidad.

Punto: Hipótesis del sistema

Es probable que usen flow fields generados con ruido, donde agentes siguen direcciones locales y parámetros como velocidad, curvatura y separación determinan el resultado.

### Actividad 02

Punto: ¿Qué es un agente autónomo?

Es una entidad que percibe su entorno y toma decisiones propias para moverse, en lugar de reaccionar únicamente a fuerzas externas.

Punto: ¿Qué es una steering force?

Es una fuerza que representa una decisión de movimiento, como acercarse a un objetivo o evitar otros agentes.

Punto: Diferencia con fuerzas externas

Las fuerzas externas, como la gravedad, actúan de forma pasiva. Las steering forces son internas y responden a una intención de comportamiento.

Punto: ¿Por qué es útil para diseño visual?

Permite diseñar comportamiento en lugar de solo movimiento, creando sistemas más expresivos y adaptativos en el tiempo.

### Actividad 03

Punto: ¿Cómo está construido el campo de flujo?

Se construye como una grilla donde cada celda contiene un vector de dirección.

Punto: ¿Qué representa cada celda o vector?

Cada vector indica hacia dónde debe moverse un agente en esa posición.

Punto: ¿Cómo consulta un agente el campo?

El agente usa su posición para identificar su celda y obtener el vector correspondiente.

Punto: ¿Cómo se convierte en decisión de movimiento?

El vector se transforma en una steering force que ajusta su velocidad y dirección.

Punto: Parámetros importantes

Los principales son resolución del campo, velocidad máxima, fuerza máxima y cantidad de agentes.

Punto: Modificación y efecto

Al aumentar la resolución, el movimiento se vuelve más detallado y orgánico, generando mayor complejidad visual.

Punto: Tipo de movimiento

Produce un movimiento continuo y fluido.

Punto: Sensaciones visuales

Sugiere calma, fluidez y naturalidad.

Punto: Relación con música

Funciona bien con música ambiental o introspectiva.

### Actividad 04

Punto: Explicación de separación, alineación y cohesión

La separación evita que los agentes se amontonen, la alineación hace que compartan dirección y la cohesión mantiene el grupo unido.

Punto: Parámetros del sistema

Incluyen el radio de percepción y el peso de cada regla.

Punto: Modificación y efecto

Al aumentar la separación, el sistema se vuelve más disperso y caótico.

Punto: Comportamiento emergente

El comportamiento puede volverse disperso, inestable y dinámico.

Punto: Atmósfera visual

Genera una sensación viva, activa y en constante cambio.

Punto: Relación con música

Funciona mejor con música rítmica o energética.

### Actividad 05

Punto: Comparación general

Los flow fields producen movimiento fluido con mayor control visual y menor emergencia. El flocking genera movimiento colectivo con alta emergencia pero menos control directo.

Punto: Tipo de movimiento

Flow fields son continuos; flocking es reactivo y colectivo.

Punto: Nivel de control y emergencia

Flow fields tienen más control; flocking más comportamiento emergente.

Punto: Sensación o atmósfera

Flow fields son calmados y orgánicos; flocking es dinámico y caótico.

Punto: Relación con música

Flow fields funcionan con música suave; flocking con música intensa o rítmica.

Punto: Ventajas y limitaciones

Flow fields permiten precisión estética pero menos interacción. Flocking ofrece riqueza emergente pero menos control fino.

Punto: Aplicación según emoción musical

Para música contemplativa o melancólica usaría flow fields por su fluidez. Para música agresiva o eufórica usaría flocking por su energía y comportamiento colectivo.

## Bitácora de aplicación 

**Concepto visual**

El nombre del producto será BROOK

La idea principal de esta obra es el juego de palabras el cual crea una relación entre la imagen y la semántica de la palabra "BROOK", esta al ser traducida significa "quebrada", y puede ser aludida de dos formas, como el ente fluvial hídrico y como algo roto o desequilibrado de forma repentina.

Quiero lograr una sensación de contradicción, satisfactoria e incluso adictiva, tanto emocional como visual, al involucrar al usuario a una serie de estímulos explosivos pero armónicos, repetitivamente y dando ciertos descansos.

**Relación entre la visual y la canción**

La relación que va a tener con la canción es la significación del color según la intensidad de tono y volumen de la canción. Además el comportamiento y densidad de las visuales será significadas por el usuario para evidenciar esa sensación emocional dentro de la experiencia.

La interacción busca que se realicen modificaciones al Flow field de manera que el usuario decida en que estado se encuentra el flujo de partículas. Dentro de las posibilidades está subir y bajar la velocidad de los agentes, ajustar la uniformidad del movimiento de los agentes.

**Referencias**

<img width="736" height="1313" alt="Blue Cosmic Wave" src="https://github.com/user-attachments/assets/7290d7df-df05-4288-bb02-1175cb15f073" />

<img width="673" height="1200" alt="descarga (3)" src="https://github.com/user-attachments/assets/1b60dccb-75f2-490c-82f3-fe65dd04a4b2" />

<img width="562" height="1000" alt="MuchaTseBle" src="https://github.com/user-attachments/assets/49a59b12-8134-4dd7-b44e-7fe284449190" />

**Mapa de desiciones**

Opacidad de rosas: Proporcional a intensidad de las frecuencias altas.

Opacidad de naranjas: Proporcional a intensidad de las frecuencias medias.

Opacidad de azules: Proporcional a intensidad de las frecuencias bajas.

Densidad de agentes: Proporcional a la intensidad del sonido.

**Mapa de interpretación**

Posición Mouse X: Proporcional a lumminosidad de los agentes.

Posición Mouse Y: Proporcional a Tamaño de los agentes.

Sonido: Controla valores valores de los agentes.

**Uso de algoritmo**

Uso Flow Fields porque lo prinicipal que quiero obtener es algo parecido a una quebrada, como su nombre lo indica.

**Uso explícito de IA como materializador**

Use IA para determinar thresh holds y funciones que apoyaran y complementaran mi diseño, con los siguientes prompts:

```md
ayudame a mejorar este prompt para un programa de experiencias interactivas:

El nombre del producto será BROOK

La idea principal de esta obra es el juego de palabras el cual crea una relación entre la imagen y la semántica de la palabra "BROOK", esta al ser traducida significa "quebrada", y puede ser aludida de dos formas, como el ente fluvial hídrico y como algo roto o desequilibrado de forma repentina.

Quiero lograr una sensación de contradicción, satisfactoria e incluso adictiva, tanto emocional como visual, al involucrar al usuario a una serie de estímulos explosivos pero armónicos, repetitivamente y dando ciertos descansos.

Te dejo también algunos referentes visuales, están de forma vertical pero la idea es que sea de forma horizontal.

Ahora técnicamente hablando, se necesita una forma de analizar sonido en tiempo real, lo que tengo en mente quiero separarlo en diferentes capas, especificaciones de movimiento, de color, de interacción, de forma y de sonido. 

En cuanto a las de movimiento, por supuesto que va a ser un flow field con ruido Perlin. quisiera que la intensidad o volumen del sonido modifiquen la densidad de agentes en pantalla, para esto es necesario que se pueda configurar el "caudal" de los agentes en pantalla y que estos al salir de ella, desaparezcan y no haya ninguna fuga de memoria, de esta forma el programa debe ser capaz de detectar en tiempo real el nivel de intensidad del volumen y que este sea directamente proporcional al "caudal" de agentes. 

En cuanto a las especificaciones de color, quisiera que los agentes mantengan el mismo tono durante su recorrido, sin embargo, quiero que la opacidad de estos sea directamente proporcional con la intensidad del sonido, también quisiera establecer dos establecer dos casos extremos quiero que el color sea una escala entre estos casos, donde esté establecida según las altas, bajas y medias frecuencias del sonido, quiero que el valor rojo sea directamente proporcional con la intensidad de las altas, el valor verde sea directamente proporcional con la intensidad de los bajos y el valor azul sea directamente proporcional con la intensidad de las medias, esto es para que no hay colores sólidos sino variaciones de color interesantes y afines a la música en tiempo real. 

En cuanto a la interacción, quiero que el usuario sea capaz de ajustar el tamaño y dar glow a los agentes con inputs independientes y además pueda cambiar entre semillas para el flow field de dos formas, entonces: ajuste de tamaño, posición de mouse respecto al eje y en el canvas, ajuste de luminosidad (glow), posición de mouse respecto al eje x en el canvas, para las semillas del flow field, quiero que si el usuario presiona la tecla J, la semilla cambie una sola vez de forma aleatoria y permanece en ella, y si presiona la tecla K, las semillas cambien continuamente con frecuencia moderada y asi darle un movimiento impredecible y natural. 

En cuanto a la forma de los agentes, quiero que se vean como puntos luminosos que además van dejando rastro, sin que esto genere fugas de memoria, nada se debe ver sólido.

En cuanto al sonido, necesito que me indiques el espacio y como instalar una canción de mi elección, dejo a tu propio criterio la herramienta y lógica para análisis del sonido.

No adiciones textos en pantalla ni layouts, solo la experiencia.
```

```md
quiero realizar cambios nuevos en algunos aspectos, sin afectar la esencia naturaleza visual ni técnica del programa logrado, estos son los cambios, ayudame a mejraer el prompt:

vamos a configurar ahora el programa en su forma de mostrar el color, de tal forma que existan 3 clases diferentes, un tercio de los agentes van mostrar color verde y su opacidad va ser ajustada directamente proporcional a la intensidad de las frecuencias bajas, otro tercio de los agentes van a mostrar color rojo y su opacidad va ser ajustada directamente proporcional a la intensidad de las frecuencias altas, finalmente el otro tercio de los agentes van a mostrar color azul y su opacidad va ser ajustada directamente proporcional a la intensidad de las frecuencias medias, siempre teniendo en cuenta el caudal de agentes como fue configurado previamente y ajustandolo según tu criterio para mayor optimización y atractivo visual.
```

## Bitácora de reflexión
