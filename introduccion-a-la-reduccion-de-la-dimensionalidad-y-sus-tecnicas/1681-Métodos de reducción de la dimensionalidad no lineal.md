# Métodos de reducción de la dimensionalidad no lineal

## Objetivos de aprendizaje

* Métodos no lineales de reducción de la dimensionalidad
* Kernel PCA
* Embedding de Vecinos Estocásticos distribuidos en t (t-SNE)
* Mapa auto-organizado (SOM)

### Métodos de reducción de la dimensionalidad no lineal

Los métodos de transformación no lineal, también conocidos como **métodos de aprendizaje de pliegues**, se utilizan cuando los datos no se encuentran en un subespacio lineal. Se basan en la **hipótesis del manifold** que dice que **en una estructura de alta dimensión, la información más relevante** **se concentra en un pequeño número de manifiestos de baja dimensión**.

Si un subespacio lineal es una hoja de papel plana, una hoja de papel enrollada es un ejemplo sencillo de colector no lineal. Informalmente, esto se denomina rollo suizo, un problema canónico en el campo de la reducción de la dimensionalidad no lineal.

Algunos métodos populares de aprendizaje de colectores son

1. **Escalado multidimensional (MDS) :** Una técnica utilizada para analizar la similitud o disimilitud de los datos como distancias en un espacio geométrico. Proyecta los datos a una dimensión inferior de forma que los puntos de datos que están cerca unos de otros (en términos de distancia euclidiana) en la dimensión superior también lo están en la dimensión inferior.
2. **Mapa de características isométricas (Isomap):** Proyecta los datos a una dimensión inferior preservando la distancia geodésica (en lugar de la distancia euclidiana como en el MDS). La distancia geodésica es la distancia más corta entre dos puntos de una curva.
3. **Incorporación localmente lineal (LLE):** Recupera la estructura global no lineal a partir de los ajustes lineales. Cada parche local de la variedad puede escribirse como una suma lineal y ponderada de sus vecinos si se dan suficientes datos.
4. 4. **Mapa de valores propios hessianos (HLLE):** Proyecta los datos a una dimensión inferior preservando la vecindad local como LLE pero utiliza el operador Hessiano (un operador matemático del que no necesitas preocuparte ahora) para lograr mejor este resultado y de ahí el nombre.
5. **Incorporación espectral (mapas propios laplacianos) : Utiliza técnicas espectrales para realizar la reducción de la dimensionalidad mediante la asignación de entradas cercanas a salidas cercanas. Preserva la localidad en lugar de la linealidad local.
6. **Incrustación estocástica de vecinos distribuida (t-SNE):** Calcula la probabilidad de que los pares de puntos de datos en el espacio de alta dimensión estén relacionados y luego elige una incrustación de baja dimensión que produzca una distribución similar.

Kernel PCA, Isomap y muchos más.

¿No ha entendido del todo las definiciones básicas?

No se preocupe, ahora explicaremos algunos de los métodos de reducción de la dimensionalidad no lineal más utilizados.

### Kernel PCA

Hemos leído sobre PCA hasta ahora. PCA es un método lineal. Es decir, sólo puede aplicarse a conjuntos de datos que son linealmente separables. Hace un excelente trabajo para los conjuntos de datos que son linealmente separables. Pero muchos datos del mundo real no son linealmente separables. Por lo tanto, si lo utilizamos en conjuntos de datos no lineales, podemos obtener un resultado que no sea la reducción óptima de la dimensionalidad.

El Kernel PCA  utiliza una función de núcleo para proyectar el conjunto de datos en un espacio de características de mayor dimensión, donde es linealmente separable. Es similar a la idea de las máquinas de vectores de apoyo.

Existen varios métodos de kernel como el lineal, el polinómico y el gaussiano.

### La "magia" de las altas dimensiones

* Dado un problema, ¿cómo sabemos qué clases de funciones son capaces de resolver ese problema?
* La teoría VC (Vapnik-Chervonenkis) nos dice que a menudo los mapeos que nos llevan a un espacio de mayor dimensión que la dimensión del espacio de entrada nos proporcionan un mayor poder de clasificación.
* Problema: Estas clases son linealmente inseparables en el espacio de entrada. (en 2 dimensiones)








![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_60f7da0f84ff4c0380ec1b7440fc61aa.png)












* Solución: Mapeo de alta dimensión. Podemos hacer el problema linealmente separable mediante un simple mapeo: (de 2 dim a 3 dim)








![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_a3691d792e334938aca67bce71073519.png)









### Kernel Trick

* El mapeo de alta dimensión puede aumentar seriamente el tiempo de computación.
* ¿Podemos evitar este problema y seguir obteniendo el beneficio de la alta dimensión?
* ¡Sí! Usando el truco del Kernel.

El truco del Kernel es básicamente un método para proyectar los datos originales en una dimensión superior sin sacrificar demasiado tiempo de cálculo. (Mapeo no lineal de características).

Algunos kernels populares son:

* Gaussiano
* Polinomio
* Tangente hiperbólica

### Kernel PCA

Pasando a la parte principal, ¿qué es el Kernel PCA?

El Kernel PCA extiende el análisis de componentes principales (PCA) convencional a un espacio de características de alta dimensión utilizando el "truco del kernel".

Con esto, usted puede extraer hasta n (número de muestras) componentes principales no lineales sin cálculos costosos.

### Implementación del Kernel PCA

A continuación puede ver un ejemplo de implementación de Kernel PCA. El kernel utilizado aquí es lineal, pero hay muchos kernels útiles que puedes probar.




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_eb3a3cc4fda54f5080bb812cfd6d3c85.png)




### Embedding de Vecinos Estocásticos distribuidos en t (t-SNE) 

Embedding de Vecinos Estocásticos distribuidos en t (t-SNE) es una técnica no lineal para la reducción de la dimensionalidad que es particularmente adecuada para la **visualización de conjuntos de datos de alta dimensión**. Se aplica ampliamente en el procesamiento de imágenes, la NLP, los datos genómicos y el procesamiento del habla.

Hasta hace poco, era la mejor técnica de reducción de la dimensionalidad del estado de la técnica. Ahora, ha sido sustituida por una técnica mejor y más rápida llamada **UMAP**.

El t-SNE básicamente disminuye la multidimensionalidad a dimensiones 2d o 3d de forma que pueda ser visualizada por los ojos humanos. El trabajo de análisis de datos se reducirá ya que puede revelar varios patrones en el conjunto de datos en 2d o 3d.

### Visualización de 784 dimensiones en 2d usando t-SNE




![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_5761cdb22ed54e529b9fd9950c4ce692.png)





### t-SNE Explicación detallada










<iframe width="560" height="315" src="https://www.youtube.com/embed/NEaUSP4YerM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>











### Implementación de t-SNE en Python

t-SNE está presente como un paquete en la biblioteca manifold de sklearn. Una implementación sencilla de t-SNE será algo parecido a lo que se muestra a continuación. Entraremos en los detalles de la implementación en el cuaderno.



![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_d5adf9fd19604da3a6155473acf006dc.png)



### t-SNE Fortalezas

* **Funciona bien para datos no lineales:** Es capaz de interpretar la compleja relación entre características y representar puntos de datos similares en alta dimensión para acercarse en baja dimensión.
* **Preserva la estructura local y global:** t-SNE es capaz de preservar la estructura local y global de los datos. Esto significa que los puntos que están cerca unos de otros en el conjunto de datos de alta dimensión, tenderán a estar cerca unos de otros en la dimensión baja.

### t-SNE Debilidad

***Reducción de la dimensionalidad para otros propósitos:** ex: BAD para la selección de características/extracción de características porque se basa en la distribución de probabilidad -> ¡sólo para la visualización!
* **Maldición de la dimensionalidad intrínseca (sensible a la dimensión intrínseca):** La dimensión intrínseca es el número de variables que se necesitan para generar una buena aproximación de la señal. El rendimiento es malo si los datos de alta dimensión tienen realmente una dimensión intrínseca alta.
* **No convexidad de la función de coste t-SNE:** hay que elegir varios parámetros de optimización.

### t-SNE Recursos

Aquí hay un artículo increíble que puede ir a través de entender t-SNE en detalle: [https://towardsdatascience.com/what-why-and-how-of-t-sne-1f](https://towardsdatascience.com/what-why-and-how-of-t-sne-1f78d13e224d) [78d13e224d](https://towardsdatascience.com/what-why-and-how-of-t-sne-1f78d13e224d)

### Mapa Auto-Organizado (SOM) o Mapa de Características Auto-Organizadas (SOFM)

Un mapa autoorganizado (SOM) es un tipo de red neuronal artificial (RNA) que se entrena utilizando el aprendizaje no supervisado para producir una **representación discretizada de baja dimensión (típicamente bidimensional) del espacio de entrada de las muestras de entrenamiento**, llamada **mapa**, y es por lo tanto un método para hacer la reducción de la dimensionalidad.

Los mapas autoorganizativos se diferencian de otras redes neuronales artificiales en que aplican el **aprendizaje competitivo** en contraposición al aprendizaje con corrección de errores (como la retropropagación con descenso de gradiente), y en que utilizan una función de vecindad para preservar las propiedades topológicas del espacio de entrada.

El SOM fue introducido por el profesor finlandés Teuvo Kohonen en la década de 1980, y a veces se denomina **mapa de Kohonen**.

El siguiente vídeo ofrece una intuición sencilla sobre los mapas autoorganizados, relacionando su funcionamiento con una serie de aplicaciones.

Siéntase libre de saltarse la parte 'Desglosando la fórmula de actualización del peso', se pone un poco matemático allí.





<iframe width="560" height="315" src="https://www.youtube.com/embed/g8O6e9C_CfY" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>






### Implementación de SOM en Python

Aunque se puede codificar SOM desde cero en Python, el paquete de elección para utilizar fácilmente los mapas autoorganizados en Python es minisom: [https://github.com/JustGlowing/minisom](https://github.com/JustGlowing/minisom)

Es una implementación minimalista, basada en Numpy, de los mapas autoorganizativos y es muy fácil de usar. Se puede instalar usando: `pip install minisom`



### Recursos para entender SOM en profundidad

* [Cómo funciona el algoritmo SOM (Self Organizing Maps)](https://youtu.be/H9H6s-x-0YE)
* [Tutorial de SOM](https://algobeans.com/2017/11/02/self-organizing-map/)

### Cuaderno de notas

[Implementación de varias técnicas de reducción de la dimensionalidad lineal y no lineal](https://dphi.tech/notebooks/1326/gunnika/comparison-of-various-dimensionality-reduction-techniques-in-python