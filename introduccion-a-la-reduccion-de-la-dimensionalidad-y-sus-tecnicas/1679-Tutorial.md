# Reducción de la dimensionalidad

## Objetivos de aprendizaje

* Importancia y selección de características
* Extracción de características
* Maldición de la dimensión
* Reducción de la Dimensionalidad
* Beneficios de la reducción de la dimensionalidad
* Métodos de reducción de la dimensionalidad

### Problema y solución

**Problema:** Se acabaron los días en los que tenías 5 variables para ajustar tu regresión lineal: Los conjuntos de datos modernos contienen más variables/características entre las que elegir. Un conjunto de datos con 50 o más características -> más de 1 millón de observaciones.

**Solución:**
Reducción de la dimensionalidad mediante la selección y extracción de características.

### Importancia de las características y selección de las mismas

**La importancia de las características** se refiere a las técnicas que asignan una puntuación a las características de entrada en función de su utilidad para predecir una variable objetivo.

**La selección de características** es el proceso en el que se seleccionan automática o manualmente las características que más contribuyen a la variable objetivo.

En resumen, las puntuaciones de importancia de las características se utilizan para realizar la selección de características.

Supongamos que estamos trabajando en la Clasificación de Iris. Primero crearemos un modelo de referencia utilizando la Regresión Logística. Ahora, queremos probar la Selección de Características y tratar de mejorar el rendimiento de nuestro modelo. Al trazar las puntuaciones de importancia de las características, obtenemos el siguiente gráfico:



(https://dphi-live.s3.amazonaws.com/media_uploads/image_c942a0f832534bc88e9399fea517ddef.png)



* Las puntuaciones de importancia de las características nos indican que la anchura y la longitud de los pétalos son las dos características más importantes. El resto tiene una puntuación de importancia mucho menor.
* Seleccionaremos estas dos características transformando nuestro conjunto de datos para que sólo contenga estas dos características.
* Entrenaremos nuestro modelo en este conjunto de datos transformado.
* Finalmente, compararemos las métricas de evaluación de nuestro modelo inicial de Regresión Logística con este nuevo modelo.

### Extracción de características

**La extracción de características** es un proceso de reducción de características. A diferencia de la selección de características, que clasifica los atributos existentes según su importancia, la extracción de características **transforma realmente las características**.

La diferencia clave entre la selección y la extracción de características es que la selección de características mantiene un subconjunto de las características originales, mientras que la extracción de características crea otras nuevas.

La extracción de rasgos es el nombre que reciben los métodos que **seleccionan y/o combinan variables en rasgos**, reduciendo de forma efectiva la cantidad de datos que deben procesarse, sin dejar de describir de forma precisa y completa el conjunto de datos original.

### Extracción y selección de características






![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_40c45ead07c9428b9dba41f49aa14708.png)






**Selección de características** - Selección de los atributos más relevantes.

**Extracción de características** - Combinación de atributos en un nuevo conjunto reducido de características.

### Visualización del espacio de alta dimensión







<iframe width="560" height="315" src="https://www.youtube.com/embed/wvsE8jm1GzE" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>








### Maldición de la dimensión

Es posible que ya conozcas varios métodos de optimización y pienses ¿qué necesidad hay de reducir nuestros datos mediante la selección o extracción de características si podemos simplemente optimizar?

Hay algo que se conoce como "La Maldición de la dimensión". En el aprendizaje automático,
"dimensionalidad" = número de características (es decir, variables de entrada) en su conjunto de datos.






(https://dphi-live.s3.amazonaws.com/media_uploads/image_9a9cb3ade0a943a2a7f82019949afa96.png)








Cuando el número de características es muy grande en relación con el número de observaciones (filas) del conjunto de datos, algunos algoritmos tienen dificultades para entrenar modelos eficaces. Esto se llama la **Maldición de la dimensión**.

### Analogía de la Maldición de la dimensión

Supongamos que tienes una línea recta de 100 metros de largo y que se te cae una moneda en algún lugar de ella. No sería muy difícil de encontrar. Caminas a lo largo de la línea y tardas dos minutos.

Ahora digamos que tienes un cuadrado de 100 yardas a cada lado y dejas caer un centavo en algún lugar del mismo. Sería bastante difícil, como buscar a través de dos campos de fútbol pegados. Podría llevar días.

Ahora un cubo de 100 yardas de ancho. Eso es como buscar en un edificio de 30 pisos del tamaño de un estadio de fútbol. Ugh.

**La dificultad de buscar a través del espacio se vuelve mucho más difícil a medida que tienes más dimensiones.**

### Maldición de la dimensión

La maldición de la dimensión se refiere a todos los problemas que surgen al trabajar con datos en las dimensiones superiores, que no existían en las dimensiones inferiores.






![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_2f70eb33799c477a9b363fd2cb3be348.png)







A medida que aumenta el número de características, el modelo se vuelve más complejo. Cuanto mayor sea el número de características, mayores serán las posibilidades de sobreajuste. Un modelo de aprendizaje automático que se entrena con un gran número de características, se vuelve cada vez más dependiente de los datos con los que se entrenó y, a su vez, se sobreajusta, lo que da lugar a un mal rendimiento en datos reales, anulando el propósito del modelo.



### Reducción de la dimensionalidad

En el aprendizaje automático, podemos tener demasiados factores sobre los que se realiza la clasificación final. Estos factores se conocen como variables.

Cuanto mayor sea el número de características, más difícil será visualizar el conjunto de entrenamiento y trabajar con él. A veces, la mayoría de estas características están correlacionadas y, por tanto, son redundantes.

Aquí es donde entran en juego los algoritmos de reducción de la dimensionalidad.

### Beneficios de la reducción de la dimensionalidad

* **Reduce el sobreajuste:** Menos datos redundantes significa menos oportunidades de tomar decisiones basadas en el ruido (datos irrelevantes).
* **Mejora el rendimiento del modelo:** Menos datos engañosos significa que el rendimiento de nuestro modelo mejora.
* **Reduce el tiempo de entrenamiento:** Menos datos significa que los algoritmos se entrenan más rápido.
* **Utiliza datos no etiquetados:** La mayoría de las técnicas de extracción de características son no supervisadas. Usted puede entrenar su autoencoder o ajustar su PCA (Análisis de componentes principales) en datos no etiquetados. Esto puede ser útil si usted tiene una gran cantidad de datos sin etiquetar y el etiquetado es lento y costoso.
* **Mejor visualización:** Reducir las dimensiones de los datos a 2D o 3D puede permitirnos trazarlos y visualizarlos con precisión. Así se pueden observar los patrones con mayor claridad.

### Métodos de reducción de la dimensionalidad

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_ed8c08cc062f453d9e9556f97ae4c5b0.png)

Los diversos métodos utilizados para la reducción de la dimensionalidad incluyen, pero no se limitan a:

1. Análisis de componentes principales (PCA)
2. Análisis de componentes independientes (ICA)
3. Análisis factorial
4. Análisis discriminante lineal (LDA)
5. Análisis discriminante generalizado (GDA)

La reducción de la dimensionalidad puede ser lineal o no lineal, dependiendo del método utilizado. A continuación exploraremos en detalle algunos de los métodos de reducción de la dimensionalidad.