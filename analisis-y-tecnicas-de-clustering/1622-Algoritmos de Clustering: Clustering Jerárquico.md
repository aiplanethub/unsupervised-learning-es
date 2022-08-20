# Algoritmos de Clustering: Clustering Jerárquico



## Objetivos de aprendizaje

* Clustering Jerárquico y Dendrograma
* Métodos Divisivos y Aglomerativos
* Vínculos en el Clustering
* Pasos para realizar Clustering Jerárquico (Aglomerativo)
* Elección del Número de Clusters en Clustering Jerárquico

## Clustering Jerárquico y Dendrograma










<iframe width="560" height="315" src="https://www.youtube.com/embed/ijUMKMC4f9I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>



[La versión traducida del vídeo en español puede encontrarse aquí](https://drive.google.com/file/d/1i5X6lTrctEpcmjZh6ATzmmDTryGxK3ij/view?usp=sharing)






### Clustering Jerárquico

La agrupación jerárquica implica la creación de clusters que tienen un orden predeterminado de arriba a abajo. Por ejemplo, todos los archivos y carpetas del disco duro están organizados en una jerarquía. Hay dos tipos de clustering jerárquico, el divisivo y el aglomerativo.





![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_ba5bd2749ceb449a90922f2984673106.png)

Las traducciones exactas de la imagen anterior se pueden encontrar a continuación:

---
Título: Clustering Jerárquico
Izquierda: Aglomerativo
Derecha: Divisivo
---





#### Método divisivo

El método de clustering jerárquico divisivo o top-down funciona comenzando con un cluster que contiene todo el conjunto de datos y luego partiendo el cluster en dos clusters menos similares.

Se procede recursivamente en cada cluster hasta que haya un cluster para cada observación.

Hay pruebas de que los algoritmos divisorios producen jerarquías más precisas que los algoritmos aglomerativos en algunas circunstancias, pero es conceptualmente más complejo.

#### Método aglomerativo

El método aglomerativo o de clustering ascendente comienza con cada observación como su propio cluster.

A continuación, calcula la similitud (por ejemplo, la distancia) entre cada uno de los clusters y une los dos clusters más similares.

Por último, repita los pasos 2 y 3 hasta que sólo quede un cluster.

## Enlaces en la agrupación (clustering)

Antes de realizar cualquier clustering, se requiere determinar la matriz de proximidad que contiene la distancia entre cada punto utilizando una función de distancia. Luego, la matriz se actualiza para mostrar la distancia entre cada cluster.

**En palabras sencillas, hay que definir lo que significa "proximidad "**.

La distancia en sí o la unidad de medida puede ser la distancia euclidiana o la de Manhattan.

Hay una variedad de métricas posibles para establecer cómo se mide la distancia entre cada cluster, pero enumeraremos aquí las 4 más populares: enlace-simple, enlace-completo, enlace-medio y enlace-centroide.

### Enlance-Simple

El enlace simple (vecino más cercano) es la distancia más corta entre un par de observaciones en dos clusters. Por ejemplo, la distancia entre los clusters "r" y "s" a la izquierda es igual a la longitud de la flecha entre sus dos puntos más cercanos.
![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_a1fceb9d09e94aba91958336dafd4a07.png)

A veces puede producir clusters en los que las observaciones de diferentes clusters están más cerca entre sí que las observaciones de sus propios clusters. Estos conglomerados pueden parecer dispersos.

### Enlace-Completo

El enlace completo (vecino más lejano) es cuando la distancia se mide entre el par más lejano de observaciones en dos conglomerados. Por ejemplo, la distancia entre los clusters "r" y "s" a la izquierda es igual a la longitud de la flecha entre sus dos puntos más lejanos.

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_7eb4e007791845a0ad243d08ce145dd0.png)

Este método suele producir clusters más cerrados que el de enlace simple, pero estos clusters cerrados pueden acabar muy juntos. Junto con el enlace medio, es una de las métricas de distancia más populares.

### Enlace-Medio

La vinculación media consiste en sumar la distancia entre cada par de observaciones en cada cluster y dividirla por el número de pares para obtener una distancia media entre clusteres. Por ejemplo, la distancia entre los clusters "r" y "s" a la izquierda es igual a la longitud media de cada flecha entre la conexión de los puntos de un cluster con el otro.




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_1b72f850849547f58c3e3fb85a265b8c.png)



Enlace-medio y enlace-completo son las dos métricas de distancia más populares en el clustering jerárquico.

### Enlace-Centroide

El enlace-centroide es la distancia entre los centroides de dos clusters.

Cuando los centroides se mueven con nuevas observaciones, es posible que los clusters más pequeños sean más similares al nuevo cluster más grande que a sus clusters individuales, causando una inversión en el dendrograma. Este problema no se plantea en los otros métodos de vinculación porque los clusters que se fusionan siempre serán más similares a sí mismos que al nuevo cluster más grande.

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_15eea9a4636844d68da9ee85e4bfa06d.png)

Las traducciones exactas de la imagen anterior se pueden encontrar a continuación:

---
Enlance Centroide
---


## Clustering Jerárquico








<iframe width="560" height="315" src="https://www.youtube.com/embed/7xHsRkOdVwo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[La versión traducida del vídeo en español puede encontrarse aquí](https://drive.google.com/file/d/1BEv6g_SHEquI100vgNNUtLcIM0XpdgiW/view?usp=sharing)






### Pasos para realizar el Clustering Jerárquico (Aglomerativo)

* Al principio, trate cada punto de datos como un cluster. Por lo tanto, el número de clusters al inicio será K, donde K es un número entero que representa el número de puntos de datos.






![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_4b33855f89fe4e328773a8e0dd9de344.png)





* Formar un cluster uniendo los dos puntos de datos más cercanos, lo que resulta en K-1 clusteres.
* Formar más clusters uniendo los dos clusters más cercanos dando como resultado K-2 clusters.
* Repita los tres pasos anteriores hasta que se forme un cluster grande.





![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_a1ea2b1f30ad4b0780651d5a7eadce5a.png)





* Una vez que se ha formado un solo cluster, se utilizan dendrogramas para dividir en múltiples clusteres dependiendo del problema.

### Elección del número de clusters en la agrupación jerárquica

* Para obtener el número de clusters para la agrupación jerárquica, hacemos uso de un concepto impresionante llamado Dendrograma.
* Un dendrograma es un diagrama en forma de árbol que registra las secuencias de fusiones o divisiones.
* Tomando un ejemplo de los siguientes puntos de datos:








![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_079f220dd8524e799c5b53253cb6268e.png)









* Los dendrogramas para nuestros puntos de datos tendrán un aspecto como el siguiente.










![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_b611725456dc4ac3baed069256fdd3bd.png)









* Podemos visualizar claramente los pasos de la agrupación jerárquica.
* A mayor distancia de las líneas verticales en el dendrograma, mayor es la distancia entre esos clusters.
* Una vez que se forma un gran cluster, se selecciona la distancia vertical más larga sin que pase ninguna línea horizontal y se traza una línea horizontal a través de ella. **El número de líneas verticales que pasa esta línea horizontal recién creada es igual al número de clusters**. Observe el siguiente gráfico:









![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_f1bdb576c3524f36b88d3e9fdbbdcb31.png)







* Aquí, el número de clusters = 2 ya que la línea roja pasa por 2 puntos.
* Básicamente, la línea horizontal es un umbral, que define la distancia mínima necesaria para ser un cluster independiente. Si trazamos una línea más abajo, el umbral requerido para ser un nuevo cluster disminuirá y se formarán más clusters como se puede ver en la imagen de abajo:









![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_bd1be0344ea44d59bd73426ba8bb57c2.png)



* La línea horizontal pasa por cuatro líneas verticales dando lugar a cuatro clusters: cluster de los puntos 6,7,8 y 10, cluster de los puntos 3,2,4 y 1, y los puntos 9 y 5 serán tratados como clusters de un solo punto.

### Notebooks

Introducción al Clustering Jerárquico: [https://dphi.tech/notebooks/4380](https://dphi.tech/notebooks/4380)

Tipos de Algoritmos de Clustering Jerárquico: [https://dphi.tech/notebooks/1324/gunnika/types-of-hierarc](https://dphi.tech/notebooks/1324/gunnika/types-of-hierarchical-clustering)[hical-clustering](https://dphi.tech/notebooks/1324/gunnika/types-of-hierarchical-clustering)