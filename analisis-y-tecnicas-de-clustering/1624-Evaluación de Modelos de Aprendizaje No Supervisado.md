# Evaluación de modelos de aprendizaje no supervisado

## Objetivos de aprendizaje

* Evaluación de modelos
* Técnicas de Validación Externa
* Técnicas de Validación Interna

## Evaluación de modelos

Cuando se habla de validar o evaluar un modelo de aprendizaje automático, es importante saber que las técnicas de validación empleadas no sólo ayudan a medir el rendimiento, sino que también contribuyen en gran medida a entender el modelo a un nivel más profundo. Esta es la razón por la que se dedica una cantidad significativa de tiempo al proceso de validación de resultados y evaluación del modelo mientras se construye un modelo de aprendizaje automático.

La validación de resultados es un paso muy crucial, ya que garantiza que nuestro modelo da buenos resultados no sólo en los datos de entrenamiento, sino, lo que es más importante, también en los datos reales o de prueba.

## ¿En qué se diferencia la evaluación del aprendizaje supervisado?

En el caso del aprendizaje supervisado, la evaluación se realiza sobre todo midiendo las métricas de rendimiento como la exactitud, la precisión, exhaustividad, el AUC, etc. en el conjunto de entrenamiento y en los conjuntos de espera. Estas métricas de rendimiento ayudan a decidir la viabilidad del modelo. A continuación, podemos ajustar los hiperparámetros y repetir el mismo proceso hasta conseguir el rendimiento deseado.

Sin embargo, en el caso del aprendizaje no supervisado, el proceso no es muy sencillo, ya que no tenemos la verdad de base (las etiquetas). En ausencia de etiquetas, es muy difícil identificar cómo se pueden validar los resultados.

Por lo tanto, es en general difícil evaluar la calidad de un algoritmo no supervisado debido a la ausencia de una métrica de bondad explícita como la que se utiliza en el aprendizaje supervisado.

### Conocimiento del dominio existente

Supongamos que tenemos el problema de **agrupar diferentes canciones en Spotify en función de los géneros, para crear diferentes listas de reproducción**. Una vez realizado nuestro trabajo, ¿cómo sabemos que es lo suficientemente bueno?

Podemos verificar los resultados de nuestro ejercicio de agrupación a través del conocimiento que tenemos de los datos (por ejemplo, sabiendo que el género A y el género B de la música son similares, por lo que si esos grupos se encuentran cerca, debería ser correcto).

Pero, ¿y si no tenemos ese conocimiento previo de nuestros datos? ¿Y si los datos ni siquiera están etiquetados (como ocurre en muchos casos de clustering de la vida real)? Incluso si lo están, ¿qué ocurre si esas etiquetas carecen inicialmente de sentido para nosotros? Hay muchos artistas de los que nunca hemos oído hablar, y si intentamos agrupar miles de canciones, es claramente inviable verificar manualmente cada grupo. En estos casos, necesitamos algún tipo de medida matemática para saber si nuestra agrupación ha tenido éxito.

### Ejemplo

Volviendo a nuestro objetivo de crear clusters en base a los géneros para las listas de reproducción de Spotify. Hasta ahora hemos aprendido varios algoritmos de clustering, así que podemos probar cada uno de ellos para crear clusters.

Digamos que implementamos 4 algoritmos

Algo 1: Clustering aglomerativo jerárquico con enlace ward

Algo 2: Clustering aglomerativo jerárquico con enlace completo

Algo 3: Clustering aglomerativo jerárquico con enlace medio

Algo 4: Clustering K-Medias

Ahora, necesitamos saber cuál es el que mejor funciona con nuestros datos.

### Técnicas de evaluación

Hay dos clases de técnicas estadísticas para validar los resultados del aprendizaje de clusters. Estas son:

1. Validación externa
2. Validación interna

### **Validación externa**

**Métrica en la que se requieren etiquetas originales para evaluar los clusters.**  
Este tipo de validación se puede llevar a cabo si se dispone de etiquetas de cluster verdaderas.  
En este enfoque tendremos un conjunto de clusters S = {C1, C2, C3,..., Cn } que han sido generados como resultado de algún algoritmo de clustering. Tendremos otro conjunto de clusters P = {D1, D2, D3,..., Dm} que representan las verdaderas etiquetas de los clusters sobre los mismos datos. La idea es medir la similitud estadística entre los dos conjuntos. Un conjunto de clusters se considera bueno si es muy similar al conjunto de clusters verdadero.  
Para medir la similitud entre S y P, etiquetamos cada par de registros de los datos como Positivo si los pares pertenecen al mismo cluster en P, si no, Negativo. También se realiza un ejercicio similar para S. A continuación, calculamos una matriz de confusión entre las etiquetas de los pares de S y P que puede utilizarse para medir la similitud.

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_5a93044bd07d4bc8b31359d0abf18cbc.png)

Las traducciones exactas de la imagen anterior se pueden encontrar a continuación:

---
Eje X: Etiquetas para P
Eje Y: Etiquetas para S

* TP: Número de pares de registros que están en el mismo cluster, tanto para S como para P.
* FP: Número de pares de registros que están en el mismo cluster en S pero no en P.
* FN: Número de pares de registros que están en el mismo cluster en P pero no en S.
* TN: Número de pares de registros que no están en el mismo cluster en S y en P.

Sobre los 4 indicadores anteriores, podemos calcular diferentes métricas para obtener una estimación de la similitud entre S (etiquetas de cluster generadas por el método no supervisado) y P (verdaderas etiquetas de cluster). Algunos ejemplos de métricas que pueden utilizarse son Precisión, Exhaustividad y Valor F.



### Representación matricial

Podemos representar nuestros resultados en una matriz, mostrando qué porcentaje de las canciones de cada lista de reproducción han acabado en cada cluster.  
Si la agrupación hubiera sido perfecta, esperaríamos que cada fila y cada columna de la matriz contuvieran exactamente una entrada del 100% (no es necesario que esté en una diagonal, por supuesto, ya que la asignación del nombre del cluster es arbitraria).

### Representación matricial para Algo 1


![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_d8397bbf1b0f4e8a937902ac731aba4f.png)





En enlace 'ward' por defecto, que trata de minimizar la varianza dentro de los clusters, ha hecho un buen trabajo con los cuatro géneros, aunque hay algunas fugas en el cluster B, es decir, en la 2ª columna, hay entradas en múltiples clusters y no sólo en uno.

### Representación matricial para Algo 2




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_8455459d6f2a4cd6b1e26251644e6304.png)




Está claro que el enlace completo no ha funcionado bien. Ha colocado gran parte del conjunto de datos en el cluster A. El cluster C consta de una sola canción de rap.

### Representación matricial para Algo 3




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_8b6c851c200c42f795c7d75b1cbc9d64.png)





En enlace-medio tiene problemas similares a el enlace-completo. Muchos puntos de datos se han colocado en un solo cluster, con dos clusters que consisten en una sola canción.

### Representación matricial para Algo 4




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_1cc54508511c425ea9b3c0dca075443e.png)





Al igual que con el algoritmo análisis jerárquico de cluster (HAC) que utiliza el enlace 'ward', la agrupación K-Medias ha hecho un buen trabajo en la mayoría de los algoritmos, con algunas canciones de jazz y rap que se 'confunden' con el K-Pop.

### Representación matricial

Aunque estas matrices son buenas para "echar un vistazo" a nuestros resultados, están lejos de ser matemáticamente rigurosas. Consideremos algunas métricas que nos ayuden a asignar un número a la calidad de nuestros clusters.

### Índice de Rand ajustado

El Índice de Rand ajustado intenta expresar qué proporción de las asignaciones de clusters son "correctas". Calcula una medida de similitud entre dos métodos de clustering diferentes considerando todos los pares de muestras, y contando los pares que se asignan en los mismos o diferentes clusters predichos, contra las verdaderas etiquetas de los clusters, ajustando el azar.

Esto (así como las otras métricas que consideraremos) puede ser evaluado usando Scikit-Learn.

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_a3a7a0b860e340449a9c496337b2a808.png)

El índice de Rand ajustado está delimitado entre -1 y 1. Más cerca de 1 es bueno, mientras que más cerca de -1 es malo.



![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_a26709e8ba144f6fb07d41b84551e31a.png)



Vemos que K-Medias y Enlace Ward tienen una puntuación alta. Es lo que esperábamos, basándonos en las matrices que hemos observado anteriormente.

### Puntuación de Fowlkes Mallows

La puntuación de Fowlkes Mallow es similar al índice de Rand ajustado, en la medida en que indica el grado en que las asignaciones de clusters son "correctas".

En concreto, calcula la media geométrica (tipo especial de media en la que se multiplican los números y luego se saca una raíz cuadrada (para dos números)) entre la precisión y la recuperación. Está delimitada entre 0 y 1, y los valores más altos son mejores.


![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_dddc7808500d41f28f00c4f3bfbfdefe.png)


![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_7edf7f85006f4fe5ad32c5720a29ac2e.png)


Tenemos clasificaciones similares a las del Índice de Rand ajustado, lo que era de esperar, dado que son dos métodos para intentar responder a la misma pregunta.

### Más técnicas de validación externa

Otras técnicas de validación externa son las siguientes

* Similitud de Jaccard
* Información mutua

### Inconvenientes de la validación externa

La validación empresarial/de usuario, como su nombre indica, requiere entradas externas a los datos.

La idea es generar clusters sobre la base de los conocimientos de los expertos en la materia y luego evaluar la similitud entre los dos conjuntos de clusters, es decir, los clusters generados por ML y los clusters generados como resultado de las entradas humanas.

Sin embargo, en la mayoría de los casos, estos conocimientos no están fácilmente disponibles. Además, este enfoque no es muy escalable. Por ello, en la práctica, se suele omitir la validación externa.

### Validación interna

**Métricas en las que no se requieren etiquetas originales para evaluar los clusters.**

### ¿Por qué la validación interna?

Dado que tratar con datos no etiquetados es uno de los principales casos de uso del aprendizaje no supervisado, necesitamos algunas otras métricas que evalúen los resultados de la agrupación sin necesidad de referirse a las etiquetas "verdaderas".

### ¿Cómo la validación interna?

La mayor parte de la literatura relacionada con la validación interna para el aprendizaje de clusters gira en torno a los siguientes dos tipos de métricas

1. La cohesión dentro de cada cluster
2. Separación entre los distintos clusters

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_dc913cc422014386a53562806dc172b7.png)

### Intuición

Supongamos que tenemos los siguientes resultados de 3 análisis de clustering distintos.










![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_a25889fa4ee64bd4ae2a770ee310cdac.png)









![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_88f1bfeca0ec45cc887cb0c01bb125fa.png)








![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_3849a2bbeb694f28ab655922514dd9ba.png)






Evidentemente, cuanto más "apretados" podamos hacer nuestros clusters, mejor. ¿Existe alguna forma de dar un número a esta idea de "estrechez"?

### Métrica de validación interna

En la práctica, en lugar de tratar con dos métricas, existen varias medidas que combinan la cohesión y el acoplamiento en una sola medida. Algunos ejemplos de estas medidas son

* Coeficiente de silueta
* Coeficiente Calisnki-Harabasz
* Índice de Dunn
* Puntuación de Xie-Beni
* Índice de Hartigan

### Puntuación de silueta

La puntuación de silueta intenta describir la similitud de un punto de datos con otros puntos de datos de su cluster, en relación con los puntos de datos que no están en su cluster (esto se agrega a todos los puntos de datos para obtener la puntuación de un cluster global). En otras palabras, piensa en lo "distintos" que son los clusters en el espacio; de hecho, se podría utilizar cualquier medida de "distancia" para calcular la puntuación.

Está limitada entre -1 y 1. Más cerca de -1 sugiere una agrupación incorrecta, mientras que más cerca de +1 muestra que cada cluster es muy denso.

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_d1709b643653495e9096653106f0f16c.png)


![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_a72eca486f4b44c69cd346598f0a233d.png)



Vemos que ninguno de los clusters tiene puntuaciones de silueta muy altas. Curiosamente, vemos que los clusters de vinculación media tienen las puntuaciones más altas. Recuerde, sin embargo, que este algoritmo produjo dos clusters que contenían cada uno un solo punto de datos, lo cual es poco probable que sea un resultado deseable en una situación del mundo real (¡una lección de que a menudo no se puede confiar en una sola métrica para tomar decisiones sobre la calidad de un algoritmo!)

### Índice Calinski Harabaz

El índice de Calinski Harabaz es la relación entre la varianza de un punto de datos comparado con los puntos de otros clusters, frente a la varianza comparada con los puntos de su cluster.

Como queremos que esta primera parte sea alta y la segunda baja, es deseable un **índice CH alto**. A diferencia de otras métricas que hemos visto, esta puntuación no está acotada.

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_61a9a0324af64134824dffe94ac0acc8.png)

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_e98f806808f84eebab77911acd038197.png)

Aquí vemos que nuestros algoritmos K-Medias y Enlace Ward obtienen una alta puntuación. Los algoritmos de enlace Completo y Medio son castigados por tener uno o dos clusters grandes, que tendrán un nivel más alto de intravarianza.

### Exploración adicional

Es posible que quiera explorar una técnica llamada "Validación de muestras gemelas".

Debería utilizarse en combinación con la validación interna y puede resultar muy útil en el caso de datos de series temporales en los que queremos asegurarnos de que nuestros resultados siguen siendo los mismos a lo largo del tiempo. (Si quiere aprender más sobre el análisis de series temporales, consulte nuestro [Curso de introducción al análisis de series temporales](https://dphi.tech/courses/introduction-to-time-series-analysis).

### Conclusión

Así que esto nos lleva al final de esta unidad.

Esto fue escrito con el único propósito de cubrir las métricas de evaluación de modelos de aprendizaje automático más importantes y más comúnmente usadas y traer algo de claridad hacia el significado de estas métricas de evaluación. Espero que esto te haya ayudado de alguna manera y te haya motivado a elegir la métrica correcta para tu caso de uso con el fin de evaluar lo bueno que es el modelo de aprendizaje automático que has construido.