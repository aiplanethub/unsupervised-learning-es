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




## ¿Cómo funciona?

K-Medias es un modelo no supervisado, por lo que los datos no están etiquetados. Pero el modelo asigna matemáticamente cada punto de datos a un cluster.

Aquí tenemos algunos datos bidimensionales sin etiquetar que se ven como abajo. Todos los puntos son del mismo color (verde), es decir, no están segregados en clusters por el momento.



(https://dphi-live.s3.amazonaws.com/media_uploads/image_7c14e8c0aa13414e91c91facfa0a2169.png)



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









<iframe width="560" height="315" src="https://www.youtube.com/embed/IJt62uaZR-M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>










## K-Medias Clustering






<iframe width="560" height="315" src="https://www.youtube.com/embed/EItlUEPCIzM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>










## ¡Debe probar!

Este sitio web le permitirá visualizar la agrupación de K-Medias por su cuenta. En un momento dado, observarás que el centroide ha dejado de moverse y los clusters siguen siendo los mismos. Es entonces cuando sabes que el algoritmo ha convergido y te ha dado los clusters finales.

Le sugiero encarecidamente que pase algún tiempo con esta herramienta: [Visualizing k-means Clustering/](https://www.naftaliharris.com/blog/visualizing-k-means-clustering/)





![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_0bea076aeb984af2b0d20b6bd7866f3a.png)







## Elegir el número de clusters para K-medias

Una de las tareas más difíciles de este algoritmo de clustering es elegir los valores correctos de k.

Si eliges los valores de k al azar, puede ser correcto o incorrecto. Si elige el valor incorrecto, afectará directamente al rendimiento de su modelo. Así que hay dos métodos por los cuales usted puede seleccionar el valor correcto de k.

1. Método del codo.
2. Método de la silueta.

Ahora, vamos a entender ambos conceptos uno por uno en detalle.