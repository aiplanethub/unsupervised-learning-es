# Algoritmos de clustering: K-Medias

## Objetivos de aprendizaje

* ¿Qué es el Clustering de K-Medias?
* ¿Cómo funciona?
* Elección del número de clusters para K-Medias:
  * Método del codo
  * Método de la silueta
* Pros y contras de K-Medias



## K-Medias Clustering

El clustering de K-Medias es uno de los algoritmos de aprendizaje automático no supervisado más sencillos y populares. Incluso se puede decir que es _el_ algoritmo de clustering más popular.

Es intuitivo, fácil de implementar y rápido.

K = número de clusters/grupos en los que se quieren dividir los datos.




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_5d627b3744404f83a4980a968370929c.png)

Las traducciones exactas de la imagen anterior se pueden encontrar a continuación:

---
Figura 1: antes de aplicar K-Medias Clustering
Figura 2: después de aplicar K-Medias Clustering
---




## ¿Cómo funciona?

K-Medias es un modelo no supervisado, por lo que los datos no están etiquetados. Pero el modelo asigna matemáticamente cada punto de datos a un cluster.

Aquí tenemos algunos datos bidimensionales sin etiquetar que se ven como abajo. Todos los puntos son del mismo color (verde), es decir, no están segregados en clusters por el momento.



![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_7c14e8c0aa13414e91c91facfa0a2169.png)



**PASO 0: Decidir el número de clusters (K)**

Al inicializar el modelo, debemos decidir previamente el número de conglomerados. Tener que hacer esto por adelantado es un inconveniente del modelo.

Para este ejemplo, vamos a elegir k=2 (es decir, 2 clusters).

**PASO 1:** Cree aleatoriamente los centroides o puntos que se supone que son los centros de los clusters (representados por el color púrpura). Tenga en cuenta que no es necesario que estén en los centros inicialmente, pueden ser colocados en cualquier lugar.



![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_04a522026b0d48fb84898eb9374f0c80.png)



**Paso 2:** Cada punto de datos se asigna al centroide más cercano:





![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_2d3cb58dfccf4b97be06bb07ac1cded9.png)




Inicialmente, nuestros clusters tienen el siguiente aspecto (mira cómo los datos se dividen en clusters rojos y amarillos):





![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_7ad31e408a6743e980d1ac1473618c32.png)





**PASO 3:** Los centroides se mueven a la ubicación de la media de los puntos de su cluster:




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_ff63f02a97b14657b9431ee1e31ec899.png)




**PASO 4:** Repetir la asignación de cada punto al centroide más cercano.




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_e52ca48df4084fd6b7f23fce3251b4d8.png)




Lo que nos da los clusters según nuestra segunda iteración.





![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_496388f4c15e4e1babc12401cdc26f40.png)





**PASO 5:** Repetir este proceso hasta que los clusters dejen de moverse.

Es decir, cuando 2 veces consecutivas se obtienen los mismos clusters, no es necesario repetir los pasos.

¿Ya está?

Sí. Excepto que podemos acabar con unos resultados bastante pobres si las ubicaciones iniciales de los centroides no son óptimas.

Así que repetimos todo este proceso varias veces, y aceptamos el resultado con la menor variación acumulada entre clusters.

## Resumen



![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_b6ed76aace934b0485b9614f5c6a54d9.png)

Las traducciones exactas de la imagen anterior se pueden encontrar a continuación:

---
Para k = 2, Se escogen k objetos como cluster inicial
Asignar cada punto a un centro similar
Identificar el centroide de cada cluster
Reasignar los puntos (basados en la distancia mínima)
Identificar los nuevos centroides de cada cluster
Reasignar
---







<iframe width="560" height="315" src="https://www.youtube.com/embed/IJt62uaZR-M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>










## K-Medias Clustering






<iframe width="560" height="315" src="https://www.youtube.com/embed/EItlUEPCIzM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>










## ¡Debe probar!

Este sitio web le permitirá visualizar la agrupación de K-Medias por su cuenta. En un momento dado, observarás que el centroide ha dejado de moverse y los clusters siguen siendo los mismos. Es entonces cuando sabes que el algoritmo ha convergido y te ha dado los clusters finales.

Le sugiero encarecidamente que pase algún tiempo con esta herramienta: [Visualizing k-means Clustering/](https://www.naftaliharris.com/blog/visualizing-k-means-clustering/)





![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_0bea076aeb984af2b0d20b6bd7866f3a.png)

Las traducciones exactas de la imagen anterior se pueden encontrar a continuación:

---
Reiniciar
Agregar Centroide
Reasignar puntos
---







## Elegir el número de clusters para K-medias

Una de las tareas más difíciles de este algoritmo de clustering es elegir los valores correctos de k.

Si eliges los valores de k al azar, puede ser correcto o incorrecto. Si elige el valor incorrecto, afectará directamente al rendimiento de su modelo. Así que hay dos métodos por los cuales usted puede seleccionar el valor correcto de k.

1. Método del codo.
2. Método de la silueta.

Ahora, vamos a entender ambos conceptos uno por uno en detalle.


### Método del codo

El método del codo es uno de los más conocidos para seleccionar el valor correcto de k y aumentar el rendimiento del modelo. También es un poco ingenuo en su enfoque.

Es un método empírico para encontrar el mejor valor de k. Recoge un rango de valores y toma el mejor entre ellos. Calcula la suma del cuadrado de los puntos y calcula la distancia media.

¿Por qué se llama método del "codo"? Porque el gráfico trazado en este caso se parece a un codo. El valor de k que cae en la parte de la articulación es lo que consideramos el valor óptimo.








![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_d61becc396be4407b5a789010c58e37b.png)










![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_17e6e45c8c234a46b4f1657ae4887a0b.png)






Como la gráfica empieza a enderezarse casi en 3, 3 es el valor óptimo de k según el método del codo.

### Problemas con el método del codo

Por desgracia, no siempre tenemos datos tan claramente agrupados. Esto significa que el codo puede no ser claro y nítido.



![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_00077dc8d6c0496ca9a485320945828e.png)



Para el conjunto de datos A, el codo es claro en k = 3. Sin embargo, esta elección es ambigua para el conjunto de datos B. Podríamos elegir que k sea 3 o 4.

En este caso ambiguo, podemos utilizar el método de la silueta.

### Método de la silueta

El método de la silueta es algo diferente. Al igual que el método del codo, también toma un rango de valores de k y dibuja el gráfico de la silueta. Calcula el coeficiente de silueta de cada punto.

Una mayor puntuación del coeficiente de silueta se relaciona con un modelo con clusters mejor definidos.

Por ejemplo, en el primer gráfico, se puede ver que el cian tiene una puntuación de coeficiente de silueta más alta. También es el más segregado (mejor definido) que los otros dos clusters, el negro y el amarillo.






![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_3b180f4c2e4d4613ba712a3ce7c81064.png)




El valor de la silueta mide la similitud de un punto con su propio cluster (cohesión) en comparación con otros clusteres (separación).

* El rango del valor de la silueta está entre +1 y -1.
* Un valor alto es deseable e indica que el punto está situado en el cluster correcto.
* Si muchos puntos tienen un valor de Silueta negativo, puede indicar que hemos creado demasiados o muy pocos clusters.

Ya hemos mencionado que una Puntuación de Silueta alta es deseable. **La puntuación de la silueta alcanza su máximo global en el punto óptimo k.** Esto debería aparecer idealmente como un peak en el gráfico del valor de la silueta frente a k.

Aquí hay un gráfico de este tipo:







![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_5522fc93c8c3455ab80ba0b628b6a2ea.png)







Hay un peak claro en k = 3. Por lo tanto, es óptimo.

### Nota

El método del codo es más bien una regla de decisión, mientras que la silueta es una métrica utilizada para la validación durante la agrupación. Por lo tanto, se puede utilizar en combinación con el método del codo.

Por lo tanto, el Método del Codo y el Método de la Silueta no son alternativas entre sí para encontrar el K óptimo. Más bien son herramientas que deben utilizarse conjuntamente para tomar una decisión más segura.

### Aplicación de los métodos del codo y de la silueta

[Determinación de la K óptima para K-Medias](https://medium.com/analytics-vidhya/how-to-determine-the-optimal-k-for-k-means-708505d204eb)

Este artículo explica en detalle tanto el método Elbow como la puntuación Silhouette.

## Pros y contras de K-Medias

### Pros:

* Fácil de interpretar
* Relativamente rápido
* Escalable para grandes conjuntos de datos
* Capaz de elegir las posiciones de los centroides iniciales de una manera inteligente que acelera la convergencia
* Garantiza la convergencia

### Contras:

* El número de clusters debe ser predeterminado. El algoritmo K-Medias no es capaz de adivinar cuántos clusters existen en los datos. Determinar el número de clusters puede ser una tarea difícil.
* Sólo puede trazar límites lineales. Si hay una estructura no lineal que separa los grupos en los datos, k-medias no será una buena opción.
* Se ralentiza a medida que aumenta el número de muestras porque en cada paso, el algoritmo k-means accede a todos los puntos de datos y calcula las distancias.
* Sensible a los valores atípicos

## Notebook

Implementación de K-Medias Clustering:

[https://dphi.tech/notebooks/1325/gunnika/implementing-kmeans-clustering-algorithm](https://dphi.tech/notebooks/1325/gunnika/implementing-kmeans-clustering-algorithm)