# Algoritmos de Clustering: Clustering Jerárquico



## Objetivos de aprendizaje

* Clustering Jerárquico y Dendrograma
* Métodos Divisivos y Aglomerativos
* Vínculos en el Clustering
* Pasos para realizar Clustering Jerárquico (Aglomerativo)
* Elección del Número de Clusters en Clustering Jerárquico

## Clustering Jerárquico y Dendrograma










<iframe width="560" height="315" src="https://www.youtube.com/embed/ijUMKMC4f9I" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>










### Clustering Jerárquico

La agrupación jerárquica implica la creación de clusters que tienen un orden predeterminado de arriba a abajo. Por ejemplo, todos los archivos y carpetas del disco duro están organizados en una jerarquía. Hay dos tipos de clustering jerárquico, el divisivo y el aglomerativo.





![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_ba5bd2749ceb449a90922f2984673106.png)






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