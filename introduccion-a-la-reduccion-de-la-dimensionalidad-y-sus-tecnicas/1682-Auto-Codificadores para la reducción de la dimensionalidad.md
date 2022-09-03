# Auto-Codificadores para la reducción de la dimensionalidad

## Objetivos de aprendizaje

* Introducción a los autocodificadores
* Componentes de los autocodificadores
* Ejemplo de reconstrucción de imágenes con reducción de dimensionalidad
* Aplicaciones de los autocodificadores

### Autocodificadores

Otro método popular de reducción de la dimensionalidad que da resultados espectaculares son los autocodificadores, un tipo de red neuronal artificial que pretende copiar sus entradas en sus salidas.

Su procedimiento comienza comprimiendo los datos originales en un código corto que ignora el ruido. Después, el algoritmo descomprime ese código para generar una imagen lo más parecida posible a la entrada original.

### Componentes de los autocodificadores

Un autocodificador se compone de dos partes :

1. **Codificador:** comprime la entrada en una representación de espacio latente.
2. **Decodificador:** reconstruye la entrada a partir de la representación del espacio latente.








![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_31821184c4704ca9984c38a85e5ec41f.png)

Las traducciones exactas de la imagen anterior se pueden encontrar a continuación:

---
Entrada / Salida
Código
Codificador
Decodificador
---






### Ejemplo de reconstrucción de imágenes con reducción de la dimensionalidad










![image.png](https://dphi-live.s3.amazonaws.com/media_uploads/image_65260c1901344a6f91756c6c79883704.png)

Las traducciones exactas de la imagen anterior se pueden encontrar a continuación:

---
Imágenes originales
Imágenes reconstruidas de un auto codificador
---







Puedes notar que las imágenes reconstruidas son un poco borrosas y no tan detalladas. Pero, siguen conservando la misma estructura.

### Aplicaciones de los autocodificadores

* Reducción de la dimensionalidad
* Compresión de imágenes
* Desenmascaramiento de imágenes
* Extracción de características
* Generación de imágenes
* Predicción de secuencia a secuencia
* Sistema de recomendación

### Autocodificador








<iframe width="560" height="315" src="https://www.youtube.com/embed/Rdpbnd0pCiI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>






### Recursos adicionales

Los autocodificadores implican el concepto de aprendizaje profundo. Así que asegúrate de que estás familiarizado con él antes de empezar con la implementación de Autoencoders. No vamos a profundizar en ello por el momento. Si quieres una introducción al Aprendizaje Profundo, considera revisar nuestro [Curso de Introducción al Aprendizaje Profundo](https://dphi.tech/courses/getting-started-with-deep-learning) ¡Es gratis!

[Implementación de Autoencoders en MNIST Dataset](https://pub.towardsai.net/autoencoders-for-dimensionality-reduction-6fb6553f392f)