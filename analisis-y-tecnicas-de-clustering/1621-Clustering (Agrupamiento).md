# Clustering

## Objetivos de aprendizaje

* Un Caso de Uso
* ¿Qué es el Clustering?
* Aplicaciones de Clustering
* Visión general de las Técnicas de Clustering

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

El análisis de clústeres o clustering es la tarea de agrupar un conjunto de objetos de tal manera que los objetos del mismo grupo (llamado clúster) sean más similares (en algún sentido) entre sí que los de otros grupos (clústeres).

**Los objetos en nuestro caso de uso son clientes.**

## Clustering

El clustering puede considerarse el problema de aprendizaje no supervisado más importante. Se trata de encontrar una estructura en una colección de datos sin etiquetar.

Una definición general de clustering podría ser "**el proceso de organizar objetos en grupos cuyos miembros son similares de alguna manera**". Un cluster es, por tanto, una colección de objetos que son "similares" entre sí y son "disímiles" a los objetos que pertenecen a otros clusters.

Nota: El clustering es sólo un tipo de Algoritmo de Aprendizaje No Supervisado. Existen muchos más.

![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_9c0e30f5eb5649b2b172c1ae926d986e.png)

---

---


## Aplicaciones del Clustering

El clustering se utiliza en casi todos los campos.

## El clustering ayuda a los vendedores a mejorar su base de clientes y a trabajar en las áreas objetivo. Ayuda a agrupar a las personas (según diferentes criterios como la voluntad, el poder adquisitivo, etc.) basándose en su similitud en muchos aspectos, relacionados con el producto considerado.
* El clustering ayuda a identificar grupos de viviendas en función de su valor, tipo y ubicación geográfica.
* El clustering se utiliza para estudiar los terremotos. Basándose en las zonas afectadas por un terremoto en una región, el clustering puede ayudar a analizar el próximo lugar probable donde puede producirse un terremoto.

Hay muchas más aplicaciones del clustering, como la agrupación de documentos y el análisis de redes sociales. Estas aplicaciones son relevantes en casi todos los sectores, por lo que el clustering es una habilidad valiosa para los profesionales que trabajan con datos en cualquier campo.

A continuación se ofrece una lista detallada de aplicaciones. Tómese su tiempo para explorarla: [https://en.wikipedia.org/wiki/Cluster\_analysis#Applications](https://en.wikipedia.org/wiki/Cluster\_analysis#Applications)

## Visión general de las Técnicas de Clustering

Puede realizar la agrupación utilizando muchos enfoques diferentes, tantos, de hecho, que hay categorías enteras de algoritmos de agrupación. Cada una de estas categorías tiene sus propios puntos fuertes y débiles. Esto significa que ciertos algoritmos de clustering resultarán en asignaciones de cluster más naturales dependiendo de los datos de entrada.

La selección de un algoritmo de clustering apropiado para su conjunto de datos es a menudo difícil debido al número de opciones disponibles. Algunos factores importantes que afectan a esta decisión son

* las características de los clusters,
* características del conjunto de datos,
* número de valores atípicos,
* número de objetos de datos.

## Visión general de las Técnicas de Clustering

Explorará cómo estos factores ayudan a determinar qué enfoque es el más apropiado, examinando algunas categorías/subcategorías populares de algoritmos de clustering:

* Clustering Particionado
* Clustering Jerárquico
* Clustering basado en la Densidad