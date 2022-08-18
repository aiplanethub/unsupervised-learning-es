# Clustering

## Objetivos de aprendizaje

* Un Caso de Uso
* ¿Qué es el Clustering?
* Aplicaciones de Clustering
* Visión General de las Técnicas de Clustering

## Clustering - Un Caso de Uso

Supongamos que iniciamos un negocio para vender algunos servicios a la gente.

El negocio va bien y en pocos meses tenemos unos 10.000 clientes en nuestra base de datos. Queremos mantener nuestros clientes y también aumentar nuestros ingresos por cliente. Así que planeamos ofrecer una oferta a los clientes de nuestra base de datos. Tenemos dos opciones:

* Ofrecer la misma oferta a todos los clientes
* Preparar ofertas específicas para cada cliente






![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_56ba252a7b914536b589dba99cd07055.png)




La primera opción es sencilla.

La oferta "10% de descuento en todos los servicios" sería suficiente. Sin embargo, es menos eficiente y menos rentable que los acuerdos específicos con los clientes.

Además, es probable que las ofertas específicas para un cliente sean más atractivas para los clientes.

* Algunos clientes prefieren un descuento en un solo artículo, mientras que otros prefieren una oferta de "compre uno y llévese otro gratis".
* Algunos clientes compran el servicio A los fines de semana, mientras que otros lo compran los lunes por la mañana.

Podemos enumerar muchas más opciones diferentes en función del tamaño del negocio y del número de clientes.

Decidimos preparar ofertas específicas para cada cliente.

El siguiente paso es decidir qué tipo de ofertas vamos a ofrecer. No podemos crear una oferta diferente para cada cliente. Eso no es posible.

**Una opción inteligente podría ser detectar a los clientes con intereses o comportamientos de compra similares y agruparlos.** Los criterios de agrupación pueden ser las preferencias de los clientes, los gustos, los intereses, las combinaciones de servicios al cliente, etc.

Es extremadamente difícil agrupar a los clientes manualmente. Entonces pedimos ayuda al aprendizaje automático (Machine Learning). La tarea de agrupar clientes similares se llama **clusterización**.

## Clustering - Divide y Vencerás

Una definición más formal de Wikipedia:

El análisis de clusteres o clustering es la tarea de agrupar un conjunto de objetos de tal manera que los objetos del mismo grupo (llamado cluster) sean más similares (en algún sentido) entre sí que los de otros grupos (clusteres).

**Los objetos en nuestro caso de uso son clientes.**

## Clustering

El clustering puede considerarse el problema de aprendizaje no supervisado más importante. Se trata de encontrar una estructura en una colección de datos sin etiquetar.

Una definición general de clustering podría ser "**el proceso de organizar objetos en grupos cuyos miembros son similares de alguna manera**". Un cluster es, por tanto, una colección de objetos que son "similares" entre sí y son "disímiles" a los objetos que pertenecen a otros clusters.

Nota: El clustering es sólo un tipo de Algoritmo de Aprendizaje No Supervisado. Existen muchos más.

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_9c0e30f5eb5649b2b172c1ae926d986e.png)

Las traducciones exactas de la imagen anterior se pueden encontrar a continuación:

---
Los datos son agrupados en 4 clusters
---


## Aplicaciones del Clustering

El clustering se utiliza en casi todos los campos.

* El clustering ayuda a los vendedores a mejorar su base de clientes y a trabajar en las áreas objetivo. Ayuda a agrupar a las personas (según diferentes criterios como la voluntad, el poder adquisitivo, etc.) basándose en su similitud en muchos aspectos, relacionados con el producto considerado.
* El clustering ayuda a identificar grupos de viviendas en función de su valor, tipo y ubicación geográfica.
* El clustering se utiliza para estudiar los terremotos. Basándose en las zonas afectadas por un terremoto en una región, el clustering puede ayudar a analizar el próximo lugar probable donde puede producirse un terremoto.

Hay muchas más aplicaciones del clustering, como la agrupación de documentos y el análisis de redes sociales. Estas aplicaciones son relevantes en casi todos los sectores, por lo que el clustering es una habilidad valiosa para los profesionales que trabajan con datos en cualquier campo.

A continuación se ofrece una lista detallada de aplicaciones. Tómese su tiempo para explorarla: [https://es.wikipedia.org/wiki/An%C3%A1lisis_de_grupos](https://es.wikipedia.org/wiki/An%C3%A1lisis_de_grupos)

## Visión General de las Técnicas de Clustering

Puede realizar la agrupación utilizando muchos enfoques diferentes, tantos, de hecho, que hay categorías enteras de algoritmos de agrupación. Cada una de estas categorías tiene sus propios puntos fuertes y débiles. Esto significa que ciertos algoritmos de clustering resultarán en asignaciones de cluster más naturales dependiendo de los datos de entrada.

La selección de un algoritmo de clustering apropiado para su conjunto de datos es a menudo difícil debido al número de opciones disponibles. Algunos factores importantes que afectan a esta decisión son

* las características de los clusters,
* características del conjunto de datos,
* número de valores atípicos,
* número de objetos de datos.

## Visión General de las Técnicas de Clustering

Explorará cómo estos factores ayudan a determinar qué enfoque es el más apropiado, examinando algunas categorías/subcategorías populares de algoritmos de clustering:

* Clustering Particional
* Clustering Jerárquico
* Clustering basado en la Densidad



### Clustering Particional

La agrupación parcial divide los objetos de datos en grupos que no se solapan. En otras palabras, **ningún objeto puede ser miembro de más de un cluster, y cada cluster debe tener al menos un objeto.**

Estas técnicas **requieren que el usuario especifique el número de clusters**, indicado por la variable **k**. Muchos algoritmos de clustering particional funcionan mediante un proceso iterativo para asignar subconjuntos de puntos de datos en k clusters. Dos ejemplos de algoritmos de clustering particional son **k-medias** y **k-medoids**.

Estos algoritmos son ambos **no deterministas**, lo que significa que podrían producir resultados diferentes en dos ejecuciones separadas, incluso si las ejecuciones se basan en la misma entrada.

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_d32e83c668fd461fa34082c3654dceff.png)

Las traducciones exactas de la imagen anterior se pueden encontrar a continuación:

---
Puntos originales
Clustering Particional
---

Los métodos de clustering particional tienen varios puntos fuertes:

* Funcionan bien cuando los **clusters tienen forma esférica**.
* Son **escalables** con respecto a la complejidad del algoritmo.

También tienen varios puntos débiles:

* No son **adecuados para grupos con formas complejas y diferentes tamaños**.
* Se **descomponen** cuando se utilizan con **conglomerados de diferentes** **densidades**.

### Clustering Jerárquico

El clustering jerárquico determina la asignación de clusters construyendo una jerarquía. Esto se implementa mediante un enfoque ascendente o descendente:

* **El clustering aglomerativo** es el enfoque ascendente. Combina los dos puntos que son más similares hasta que todos los puntos se han fusionado en un solo cluster.
* **La agrupación divisiva** es el enfoque descendente. Comienza con todos los puntos como un cluster y divide los clusteres menos similares en cada paso hasta que sólo quedan puntos de datos individuales.




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_8dc5829bd0e44986b17e9abb434dabd7.png)


Las traducciones exactas de la imagen anterior se pueden encontrar a continuación:

---
Clustering Jerárquico Agromerativo
Clustering Jerárquico Divisivo
---



Estos métodos producen una jerarquía de puntos basada en un árbol llamada **dendrograma**. Al igual que en el clustering particional, en el clustering jerárquico el **número de clusters (k) suele estar predeterminado por el usuario**. Los clusters se asignan cortando el dendrograma a una profundidad determinada que da lugar a k grupos de dendrogramas más pequeños.

A diferencia de muchas técnicas de clustering particional, el clustering jerárquico es un **proceso determinista**, lo que significa que las asignaciones de cluster no cambiarán cuando se ejecute un algoritmo dos veces con los mismos datos de entrada.

Los puntos fuertes de los métodos de clustering jerárquico son los siguientes:

* Suelen **revelar los detalles más finos sobre las relaciones** entre los objetos de datos.
* Proporcionan un **dendrograma interpretable**.

Los puntos débiles de los métodos de clustering jerárquico son los siguientes:

* Son **caros en términos de computación** con respecto a la complejidad del algoritmo.
* Son sensibles al **ruido** y a los **objetos**.

### Clustering basado en la densidad

El clustering basado en la densidad determina la asignación de clusters **basada en la densidad de los puntos de datos en una región**. Los clusters se asignan donde hay altas densidades de puntos de datos separados por regiones de baja densidad.

A diferencia de las otras categorías de clustering, este enfoque **no requiere que el usuario especifique el número de clusters** . En su lugar, hay un **parámetro basado en la distancia que actúa como un umbral ajustable**. Este umbral determina lo cerca que deben estar los puntos para ser considerados miembros de un cluster.

Algunos ejemplos de algoritmos de clustering basados en la densidad son Agrupamiento Espacial basado en Densidad de Aplicaciones con Ruido, o **DBSCAN**, y Puntos de Orden para Identificar la Estructura de la Agrupación , o **OPTICS**.

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_999099067d7e47169e2617a4bd512264.png)

Las traducciones exactas de la imagen anterior se pueden encontrar a continuación:

---
Clustering basado en la densidad
Cluster de forma esférica
Cluster de forma arbitraria
---
Los puntos fuertes de los métodos de clustering basados en la densidad son los siguientes:

* Sobresalen en la identificación de clusters de **formas no esféricas**.
* Son **resistentes a los valores atípicos**.

Los puntos débiles de los métodos de clustering basados en la densidad son los siguientes:

* No son adecuados para agrupar en **espacios de alta dimensión**.
* Tienen problemas para identificar clusters de **densidades variables**.

### Tipos de Algoritmos de Clustering



![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_3e26676b26394673a5ad37f7315a4fe9.png)

### Tipos de Algoritmos de Clustering - una categorización alternativa

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_eb8b3b2bafdc494c8fe5f457af68e6f5.png)