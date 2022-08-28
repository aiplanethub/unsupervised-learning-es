# Métodos de reducción de la dimensionalidad lineal

### Objetivos de aprendizaje

* Métodos de reducción de la dimensionalidad lineal
* Análisis de componentes principales (PCA)
* Análisis de Componentes Independientes (ICA)

### Métodos de reducción de la dimensionalidad lineal

Los métodos de reducción de la dimensionalidad más comunes y conocidos son los que aplican transformaciones lineales, como:

1. **PCA (Análisis de Componentes Principales):** Popularmente utilizado para la reducción de la dimensionalidad en datos continuos, PCA rota y proyecta los datos a lo largo de la dirección de la varianza creciente. Las características con la máxima varianza son los componentes principales.
2. **Análisis factorial:** una técnica que se utiliza para reducir un gran número de variables a un número menor de factores. Los valores de los datos observados se expresan como funciones de una serie de posibles causas para encontrar cuáles son las más importantes. Se supone que las observaciones son causadas por una transformación lineal de factores latentes de menor dimensión y se les añade ruido gaussiano.
3. **LDA (Análisis Discriminante Lineal) :** proyecta los datos de forma que se maximice la separabilidad de las clases. Los ejemplos de la misma clase se colocan muy juntos por la proyección. Los ejemplos de clases diferentes se colocan lejos por la proyección.
4. **Análisis de componentes independientes:** transforma el conjunto de datos en columnas de componentes independientes. La separación ciega de fuentes y el "problema del cóctel" son otros de sus nombres.

Algunos otros métodos de reducción de la dimensionalidad lineal son el análisis de correlaciones canónicas, los factores de autocorrelación máxima, el análisis de componentes independientes incompletos, el aprendizaje de la métrica de la distancia, etc.

Esto muestra el inmenso alcance de ampliar su aprendizaje aún más allá de este contenido.

¿No ha entendido del todo las definiciones básicas?

No se preocupe, ahora elaboraremos algunos de los métodos de reducción de la dimensionalidad lineal más utilizados.

### Introducción al Análisis de Componentes Principales (PCA)

El análisis de componentes principales (PCA) es una de las técnicas de reducción de la dimensión lineal más populares. A veces, se utiliza solo y otras veces como solución de partida para otros métodos de reducción de la dimensión.

El PCA es un método basado en la proyección que suele utilizarse para reducir la dimensionalidad de grandes conjuntos de datos, transformando un gran conjunto de variables en otro más pequeño que siga conteniendo la mayor parte de la información del conjunto grande.

La reducción del número de variables de un conjunto de datos se produce, naturalmente, a expensas de la precisión, pero el truco de la reducción de la dimensionalidad consiste en cambiar un poco de precisión por simplicidad. Porque los conjuntos de datos más pequeños son más fáciles de explorar y visualizar y hacen que el análisis de los datos sea mucho más fácil y rápido para los algoritmos de aprendizaje automático sin variables extrañas que procesar.

En resumen, la idea del PCA es sencilla: reducir el número de variables de un conjunto de datos, conservando la mayor cantidad de información posible.

Algunas aplicaciones del mundo real de PCA son el procesamiento de imágenes, el sistema de recomendación de películas, la optimización de la asignación de energía en varios canales de comunicación.

### Intuición del PCA

Supongamos que desea diferenciar entre diferentes alimentos en función de su contenido nutricional. ¿Qué variable será una buena elección para diferenciar los alimentos?

Si eliges una variable que varía mucho de un alimento a otro, por ejemplo el nivel de sodio, podrás aislarlos correctamente. Su trabajo será mucho más difícil si la variable elegida es casi la misma en la mayoría de los alimentos, por ejemplo, la vitamina E.

¿Qué pasa si los datos no tienen una variable que segregue los alimentos adecuadamente? Podemos crear una variable artificial mediante una combinación lineal de las variables originales como

art_var1 = 2$\times$org_var1 - 3$\times$org_var2 + 5$\times$org_var3

Esto es lo que hace esencialmente el PCA, encuentra las mejores combinaciones lineales de las variables originales para que la varianza o dispersión a lo largo de la nueva variable sea máxima.

### ¿Cuándo se debe utilizar el PCA?

1. ¿Quiere reducir el número de variables, pero no es capaz de identificar las variables para eliminarlas completamente de la consideración?
2. ¿Quiere asegurarse de que sus variables son independientes entre sí?
3. ¿Se siente cómodo haciendo que sus variables independientes sean menos interpretables?

Si ha respondido "sí" a las tres preguntas, entonces el PCA es un buen método a utilizar. Si ha respondido "no" a la pregunta 3, **no debería utilizar** el PCA.

Algunos casos de uso más particulares para PCA incluyen:

* Cuando las características latentes son las que determinan los patrones en los datos.
* Para la reducción de la dimensionalidad.
* Para visualizar datos de alta dimensión.
* Para reducir el ruido.
* Como paso de preprocesamiento para mejorar el rendimiento de otros algoritmos.

### ¿Cómo funciona el PCA?

He aquí un breve resumen no técnico del funcionamiento de PCA:

* Vamos a calcular una matriz que resume cómo nuestras variables se relacionan entre sí.
* A continuación, desglosaremos esta matriz en dos componentes separados: dirección y magnitud. Así podremos entender las "direcciones" de nuestros datos y su "magnitud" (o lo "importante" que es cada dirección).





![Imagen.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_afbb10f76eda4fd39c7874faadee4275.png)







* La figura muestra las dos direcciones principales de estos datos: la "dirección roja" y la "dirección verde".
* En este caso, la "dirección roja" es la más importante. ¿Puedes entender por qué? (Pista: ¿Cómo sería el ajuste de una línea de mejor ajuste a estos datos?)
* Transformaremos nuestros datos originales para alinearlos con estas direcciones importantes (que son combinaciones de nuestras variables originales). La figura siguiente tiene los mismos datos exactos que la anterior, pero transformados de modo que los ejes x e y son ahora la "dirección roja" y la "dirección verde". ¿Qué aspecto tendría aquí la línea de mejor ajuste?
* Las direcciones roja y verde de las que hablamos son los **componentes principales**, ¡de ahí el nombre!









![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_334ce53f787b42858fa423c1bfcb408c.png)










* Mientras que el ejemplo visual aquí es bidimensional (y por lo tanto tenemos dos "direcciones"), piensa en un caso en el que nuestros datos tienen más dimensiones.
* Al identificar qué "direcciones" son más "importantes", podemos comprimir o proyectar nuestros datos en un espacio más pequeño eliminando las "direcciones" que son las "menos importantes".
* Al proyectar nuestros datos en un espacio más pequeño, estamos reduciendo la dimensionalidad de nuestro espacio de características... pero como hemos transformado nuestros datos en estas diferentes "direcciones", ¡nos hemos asegurado de mantener todas las variables originales en nuestro modelo!






![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_806be7012994455aa50e3efbce0161f0.png)





Observe dos cosas en el gráfico anterior:

1. Los dos gráficos muestran exactamente los mismos datos, pero el gráfico de la derecha refleja los datos originales transformados de manera que nuestros ejes son ahora los componentes principales.
2. En ambos gráficos, los componentes principales son perpendiculares entre sí. De hecho, **cada componente principal será SIEMPRE ortogonal (también conocido como término matemático oficial para perpendicular) a cualquier otro componente principal.**

Si desea profundizar en el funcionamiento de PCA, puede ver el siguiente vídeo en 2X.

Implica algunos términos técnicos, pero todos los términos se explican en detalle y es una buena práctica para estar familiarizado con el funcionamiento interno del algoritmo que está implementando.

Si no desea entrar en los detalles a partir de ahora, no dude en saltárselo :)

### Paso a Paso PCA







<iframe width="560" height="315" src="https://www.youtube.com/embed/FgakZw6K1QQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>







### Necesidad de estandarización

El objetivo de este paso es normalizar el rango de las variables continuas iniciales para que cada una de ellas contribuya por igual al análisis.

Más concretamente, la razón por la que es crítico realizar la estandarización antes del PCA, es que este último es bastante sensible respecto a las varianzas de las variables iniciales. Es decir, si hay grandes diferencias entre los rangos de las variables iniciales, aquellas variables con rangos más grandes dominarán sobre las que tienen rangos pequeños (Por ejemplo, una variable que oscila entre 0 y 100 dominará sobre una variable que oscila entre 0 y 1), lo que conducirá a resultados sesgados. Por lo tanto, la transformación de los datos a escalas comparables puede evitar este problema.

### Implementación de PCA de Scikit-Learn







![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_2e61a49fd0984eacb403094b2f64a000.png)







### Deficiencias de PCA

* Si el número de variables es grande, se hace difícil interpretar los componentes principales.
* El PCA es más adecuado cuando las variables tienen una relación lineal entre ellas.
* Además, PCA es susceptible a los grandes valores atípicos.

### Conclusión

El PCA es un método antiguo y ha sido bien investigado. Hay muchas extensiones del PCA básico que abordan sus deficiencias, como el PCA robusto, el PCA de núcleo y el PCA incremental.


### Análisis de componentes independientes (ICA)

El ICA es un método de reducción de la dimensionalidad similar al PCA en el sentido de que toma un conjunto de características y produce un conjunto diferente que es útil de alguna manera.

Pero mientras que PCA trata de maximizar la varianza, ICA asume que las características son mezclas de fuentes independientes y trata de aislar estas fuentes independientes que se mezclan en el conjunto de datos.

La motivación de ICA sería **tomar el conjunto original de características e intentar identificar aquellas que contribuyen de forma independiente al conjunto de datos**, es decir, las que tienen menos correlación con las demás características. De este modo, **se aíslan los componentes más importantes.** Este problema se denomina **Aislamiento de fuentes ciegas**.













<iframe width="560" height="315" src="https://www.youtube.com/embed/2WY7wCghSVI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>












<iframe width="560" height="315" src="https://www.youtube.com/embed/wIlrddNbXDo" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>










### Implementación de ICA en Scikit learn





![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_bd68e36e4d124bc2b739a46c63bc66ad.png)






### Aplicaciones de ICA

Una aplicación interesante de ICA es el análisis de datos electroencefalográficos (datos del cerebro). ICA es una herramienta importante en el análisis de neuroimágenes, fMRI y EEG que ayuda a separar las señales normales de las anormales.

A continuación se muestra un ejemplo de las lecturas de 14 canales de un EEG que duró 4,5 segundos y los componentes independientes extraídos del conjunto de datos.










![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_79b4f20815fc46fa88473fb2ea6f0d89.png)









### Inconvenientes de ICA

ICA no puede descubrir las relaciones no lineales del conjunto de datos. ICA no nos dice nada sobre el orden de los componentes independientes o cuántos de ellos son relevantes.

### PCA vs ICA

* PCA elimina las correlaciones, pero no la dependencia de orden superior.
* ICA elimina las correlaciones y la dependencia de orden superior.
* PCA: algunos componentes son más importantes que otros (valores propios).
* ICA: todos los componentes tienen la **misma importancia.**
* PCA: los vectores son ortogonales.
* ICA: los vectores son **no ortogonales**.


![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_134f377882234a4384aacc8b7eec097a.png)