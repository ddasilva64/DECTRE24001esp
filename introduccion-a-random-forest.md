# Introducción a random forest

<details>

<summary>Índice de contenidos</summary>

* ***¿Qué son los random forest o bosques aleatorios?***  
    * ***Ensemble Method (métodos de conjunto)***
        * ***Tipos de Ensemble Methods***
            * ***Embolsado***
* ***Ventajas sobre otros algoritmos de ML***
* ***Desventajas***
* ***Algunas aplicaciones***
* ***¿Cómo funcionan los random forest?***
* ***¿Cuándo utilizar random forest?***
  
</details>

## ¿Qué son los random forest o bosques aleatorios?

***[<span style="font-family:Verdana; font-size:0.95em;color:red">*Random forest*</span>][r000]*** es un algoritmo de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">ML</span>][r005]*** popular que pertenece a la familia de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*algoritmos ensemble*</span>][r006]***. El aprendizaje ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*ensemble*</span>][r006]*** es una técnica en la que se utilizan múltiples modelos para resolver un único problema y se combinan sus resultados para producir una solución más precisa y estable.

El algoritmo ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*random forest*</span>][r000]*** es una extensión del algoritmo de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r004]***, que es una herramienta sencilla y potente para problemas de **clasificación y regresión**. Un ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r004]*** es una estructura de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r004]*** similar a un diagrama de flujo, donde cada **nodo** interno representa una característica o atributo, cada **rama** representa una decisión o **regla**, y cada **nodo** hoja representa una etiqueta de **clase** o un valor de salida.

![Random forest][i000] 

La idea principal detrás de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*random forest*</span>][r000]*** es *crear múltiples ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** y luego agregar sus resultados tomando el **voto mayoritario** o el **valor promedio***. Este enfoque puede ***reducir la varianza y el sesgo*** del modelo y mejorar la generalización y robustez de las predicciones.  

![Varianza y sesgo en los random forest 001][i001]

![Varianza y sesgo en los random forest 002][i002]

Los humanos establecemos atajos para llegar a conclusiones sin tener que recorrer todos los pasos del razonamiento. Esos pasos los establecemos a partir de nuestra experiencia o la de otras personas. Aunque la experiencia y el conocimiento nos permiten llegar más rápido a conclusiones, si no tenemos claro que debemos tener un pensamiento autocrítico, muy a menudo llegamos conclusiones en las cuales juzgamos a los demás por características externas como su aspecto, mientras que nos juzgamos a nosotros mismos por aspectos internos. Este tipo de razonamiento erróneo es genéricamente conocido como ***sesgo***. Muy habitualmente establecen los sistemas de prejuicios basados en raza, sexo, religión, edad, pertenencia al grupo, etc.  
***En ML el sesgo es ruido***. Al entrenar un modelo de ***ML***, este podría llegar a aprender características (features), las cuales en el futuro no sean representativas en la verdadera población de casos, que verá el modelo en producción. Debemos:  
* ***Cuestionar los datos***, usando nuestro ***pensamiento crítico*** al realizar correlaciones y consultando a otros analistas, para ver si ellos observan lo mismo que nosotros.  
* ***Establecer las variables y categorías del mundo real***, que existen y que afectan el desempeño del modelo. Los usuarios deben conocer el alcance de las categorías que son válidas para el sistema.  

***Ninguna aplicación ML puede estar libre del 100% de sesgo***. ***Reducir sesgo es un equilibrio entre la cantidad y la diversidad de los datos*** o la mayor complejidad del modelo (varianza, complejidad del modelo).  

***Técnicas para la reducción del sesgo en ML***:  

1. ***Balancear las categorías de datos***.  
Si al observar los datos detectamos que ***tenemos una limitada cantidad datos de entrenamiento y que existe un porcentaje pequeño de una categoría*** (por ejemplo mujeres o personas con piel oscura), podemos generar ***oversampling*** o ***undersampling*** sobre la categoría minoritaria.
***El oversampling permite aumentar registros de la clase minoritaria, para equilibrarla con la mayoritaria***, es decir, crea nuevos datos sínteticos.  
***El undersampling permite eliminar registros de la categoría mayoritaria, para equilibrarla con la clase minoritaria***.  

2. ***La correlación no implica causalidad***.
Imaginemos que los días que el baño no funciona tenemos más reuniones en la oficina, podríamos llegar a la conclusión de que para tener más reuniones debemos romper el baño.  

3. ***Eliminar outliers***.  
Siempre hay datos que se salen de la gráfica, lo normal es eliminarlos del modelo.  

La ***codificación de variables categóricas*** es una tarea fundamental en el análisis de datos y el ***ML***. Las ***variables categóricas representan atributos discretos*** que no se pueden interpretar como valores numéricos directos. Al codificar estas variables de manera adecuada, podemos transformarlas en formatos numéricos comprensibles ***para los algoritmos de modelado***. Existen las siguientes técnicas:  

1. ***Codificación one-hot***: Transformación esencial que crea ***variables binarias para cada categoría***, indicando su ***presencia o ausencia***.  

2. ***Codificación ordinal***: Asignación de ***valores ordinales a las categorías***, teniendo en cuenta el ***orden jerárquico de las mismas***.  

3. ***Codificación de enteros***: Asignación de ***valores enteros a cada categoría***.  

4. ***Codificación de frecuencia***: Asignación de ***valores en función de la frecuencia a cada categoría***.  

Una de las características clave de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*random forest*</span>][r000]*** es el uso de subconjuntos aleatorios de los datos y de las características predictivas para entrenar cada ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r004]***. Esta técnica puede aumentar la diversidad e independencia de los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles</span>][r004]*** y evitar el **sobreajuste** y la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*correlación*</span>][r009]***. 

*Desafortunadamente, los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** tienden a **sobreajustarse** muy rápidamente. Esto significa que el algoritmo se acostumbra demasiado a los datos de entrenamiento y los aprende de memoria. Como resultado, funciona muy mal con datos nuevos e invisibles.*

En ***[<span style="font-family:Verdana; font-size:0.95em;color:red">ML</span>][r005]***, el objetivo siempre es entrenar un algoritmo que aprenda ciertas capacidades de un conjunto de datos de entrenamiento y luego pueda aplicarlas a nuevos datos. Por esta razón, los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** rara vez se utilizan hoy en día, y en su lugar se recurre a ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*random forest*</span>][r000]*** muy similares. Esto es posible gracias al llamado ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*ensemble method*</span>][r006]***.  

### Ensemble Method (métodos de conjunto)

Los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*ensemble methods*</span>][r006]*** son una técnica de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">ML</span>][r005]*** que combinan varios modelos base para producir un modelo predictivo óptimo. Para comprender mejor esta definición, retrocedamos un paso hacia el objetivo final del ***[<span style="font-family:Verdana; font-size:0.95em;color:red">ML</span>][r005]*** y la construcción de modelos. 

Un ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r004]*** determina el valor predictivo en función de una serie de preguntas y condiciones.  

A la hora de realizar ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]***, hay varios factores que debemos tener en cuenta: ¿Sobre qué características tomamos nuestras decisiones? ¿Cuál es el umbral para clasificar cada pregunta en una respuesta de sí o no?.  

¡Aquí es donde los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*métodos ensemble*</span>][r006]*** resultan útiles!. En lugar de simplemente confiar en un ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r004]*** y esperar haber tomado la decisión correcta en cada división, los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*métodos de conjunto*</span>][r006]*** nos permiten tomar una muestra de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** en cuenta, calcular qué características usar o qué preguntas hacer en cada división y tomar una decisión final basada en los resultados agregados de los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** muestreados.  

Llamamos **aprendizaje ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*ensamblado*</span>][r006]***** a la combinación de modelos de aprendizaje simple para crear nuevos modelos combinados que mejoran los resultados.

Hay dos maneras de hacer la combinación:

1. **En paralelo**: Se divide el conjunto de datos de entrenamiento de manera aleatoria y se entrenan modelos simples. La salida se combina mediante una media de los resultados de los modelos simples (average en caso de valores continuos) o seleccionando el resultado más frecuente o la moda estadística (más votos) para valores discretos. Esta combinación se denomina ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*bagging*</span>][r008]***.  

    Dentro de esta categoría se engloba el método de *****[<span style="font-family:Verdana; font-size:0.95em;color:red">*random forest*</span>][r000]*****. En este caso, los modelos simples son ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** y los principales **parámetros** a configurar son: ****número estimadores*** (número de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles</span>][r004]*** del *****[<span style="font-family:Verdana; font-size:0.95em;color:red">*bosque*</span>][r000]*****) y los propios de los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** (**máxima profundidad** del ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r004]*** y ***mínimo número de muestras por hoja***)*.

2. **En serie**: Dentro de esta categoría se incluyen los modelos **XGboost o Gradient Boosted Trees**. Son uno de los modelos más utilizados actualmente porque obtiene muy buenos resultados. Se utilizó por primera vez en un hackaton o concurso para resolver un problema de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">ML</span>][r005]*** donde consiguió métricas sorprendentes.

    Se basa en un método que se denomina **boosting** o empuje que persigue mejorar los resultados de modelo más simples utilizando la técnica de *descenso por gradiente para optimizar el error*.

    *En un momento t, se asignan pesos a los resultados del modelo en función de la salida en el momento t-1. Las salidas correctas tienen un peso menor y las incorrectas un peso mayor. El objetivo es analizar el modelo peor, aprender de sus atributos y ***[<span style="font-family:Verdana; font-size:0.95em;color:red">parámetros</span>][r003]*** y utilizar estos aprendizajes para construir un modelo mejor*.

    Se pueden usar para resolver problemas de **regresión** y **clasificación** y el número de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">parámetros</span>][r003]*** a configurar es relevante.

![Paralelo y secuencial][i003]


#### ***Tipos de Ensemble Methods***

1. *****[<span style="font-family:Verdana; font-size:0.95em;color:red">*Bagging*</span>][r008]*** (o Bootstrap AGGregatING)**. ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*Bagging*</span>][r008]*** recibe su nombre porque combina **Bootstrapping** y **Aggregation** para formar un *****[<span style="font-family:Verdana; font-size:0.95em;color:red">métodos de conjunto</span>][r002]*****. Dada una muestra de datos, se extraen varias submuestras arrancadas. Se forma un ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r004]*** en cada una de las submuestras arrancadas. Después de que se haya formado cada ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r004]*** de submuestra, se utiliza un algoritmo para agregar los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** y formar el predictor más eficiente.  

2. **Modelos de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*random forest*</span>][r000]*****. Los **modelos de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">random forest</span>][r000]***** pueden considerarse como ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*bagging*</span>][r008]***, con un ligero ajuste. Al decidir dónde dividir y cómo tomar decisiones, los *****[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** BAGGed** tienen todas las funciones para elegir. Por lo tanto, aunque las muestras de arranque pueden ser ligeramente diferentes, los datos se dividirán en gran medida en las mismas características en cada modelo. Por el contrario, los modelos de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*random forest*</span>][r000]*** deciden dónde dividirse en función de una selección aleatoria de características. En lugar de dividirse en características similares en cada **nodo**, los modelos de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*random forest*</span>][r000]*** implementan un nivel de diferenciación porque cada ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r004]*** se dividirá en función de diferentes características. Este nivel de diferenciación proporciona un conjunto mayor para agregar, por lo que produce un predictor más preciso.  

![Random forest y bagging][i004]

El objetivo de cualquier problema de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">ML</span>][r005]*** es encontrar un modelo único que prediga mejor el resultado deseado. En lugar de crear un modelo y esperar que este modelo sea el mejor predictor o el más preciso que podamos hacer, *los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">métodos de conjunto</span>][r002]*** toman en cuenta una gran cantidad de modelos y promedian esos modelos para producir un modelo final*. Es importante señalar que los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** no son la única forma de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">métodos de conjunto</span>][r002]***, solo los más populares y relevantes en la DS actual.

##### ***Embolsado***

Para que el ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*bosque aletorio*</span>][r000]*** produzca buenos resultados, debemos asegurarnos de que los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** individuales no estén ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*correlacionados*</span>][r009]*** entre sí. Usamos lo que se llama **embolsado**. Es un método dentro de los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*algoritmos ensemble*</span>][r006]*** que garantiza que diferentes modelos se entrenen en diferentes subconjuntos del conjunto de datos.

![Variables correlacionadas][i005]

Los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** son muy sensibles a sus datos de entrenamiento. Un pequeño cambio en los datos ya puede conducir a una estructura de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r004]*** significativamente diferente. Aprovechamos esta propiedad al **embolsar**. Por lo tanto, cada ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r004]*** dentro del ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*bosque*</span>][r000]*** se entrena en una muestra del conjunto de datos de entrenamiento, lo que evita que los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles</span>][r004]*** se ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*correlacionen*</span>][r009]*** entre sí.

Cada ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r004]*** aún se entrena en un conjunto de datos de entrenamiento con la longitud del conjunto de datos original, aunque se haya tomado una muestra. Esto se hace reemplazando los valores faltantes. Supongamos que nuestro conjunto de datos original es la lista [1,2,3,4,5,6] con una longitud de seis. Una posible muestra de esto es [1,2,4,6], que extendemos por el 2 y el 6 para que nuevamente obtengamos una lista de longitud seis: [1,2,2,4,6,6]. *El **embolsado** es el proceso de tomar una muestra del conjunto de datos y “aumentarla” con elementos de la muestra para volver al tamaño original*.

## Ventajas sobre otros algoritmos de ML

* Alta precisión y rendimiento, especialmente para conjuntos de datos grandes y complejos.  

* Baja  **varianza y sobreajuste**, gracias a la combinación de múltiples modelos.  

* Alta estabilidad, gracias al uso de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]***.  

* Alta versatilidad y aplicabilidad, gracias al soporte tanto para tareas de **clasificación** como de **regresión**.  

* Decisiones reproducibles.

* Buena capacidad de selección automática de características.  

* Fácil ajuste y optimización del modelo.  

* Baja necesidad de cómputo, comparado con otros modelos de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">ML</span>][r005]***.

> Fuente: [<span style="font-family:Verdana; font-size:0.95em;color:red">*Random forest*</span>][r000]  

## Desventajas

* Alto costo computacional y de memoria, especialmente para conjuntos de datos grandes y complejos.  

* Alta dependencia y ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*correlación*</span>][r009]***, especialmente para conjuntos de datos pequeños y similares.  

* Baja transparencia a la hora de entender y explicar el modelo.  

> Fuente: [<span style="font-family:Verdana; font-size:0.95em;color:red">*Random forest*</span>][r000]  

## Algunas aplicaciones

* Diagnóstico y pronóstico médico.  

* Calificación de créditos y detección de fraude.  

* Evaluar la solvencia de un cliente bancario.

* Predecir los precios de las acciones.

* Predecir las preferencias de los consumidores en función del historial de compras.

* Reconocimiento de imágenes y voz.  

* Procesamiento del lenguaje natural y análisis de sentimiento.  

* Pronóstico del clima y del tiempo.  

* Modelado de energía y medio ambiente.  

* Análisis social y de redes.  

> Fuente: [<span style="font-family:Verdana; font-size:0.95em;color:red">*Random forest*</span>][r000]  

## ¿Cómo funcionan los random forest?

***[<span style="font-family:Verdana; font-size:0.95em;color:red">*Random forest*</span>][r000]*** consta de una gran cantidad de estos ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]***, que funcionan juntos como un conjunto. Cada ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r004]*** individual hace una predicción, como un resultado de **clasificación**, y el bosque usa el resultado respaldado por la mayoría de los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** como la predicción de todo el conjunto. ¿Por qué los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** múltiples son mucho mejores que uno solo?

El secreto detrás del ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*Random forest*</span>][r000]*** es el llamado ***principio de la sabiduría de las multitudes***. La idea básica es que la decisión de muchos siempre es mejor que la decisión de un solo individuo o un solo ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r004]***. Este concepto fue reconocido por primera vez en la estimación de un conjunto continuo.

En 1906, se mostró un buey a un total de 800 personas en una feria. Se les pidió que estimaran cuánto pesaba este buey antes de pesarlo. Resultó que la mediana de las 800 estimaciones estaba solo un 1% alejada del peso real del buey. Ninguna estimación había estado tan cerca de ser correcta. Así que la multitud en su conjunto había estimado mejor que cualquier otra persona.

Esto se puede aplicar exactamente de la misma manera al ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*Random forest*</span>][r000]***. Una gran cantidad de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r004]*** y su predicción agregada siempre superarán a un solo ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r004]***.

> Fuente: [<span style="font-family:Verdana; font-size:0.95em;color:red">*Introducción al algoritmo random forest*</span>][r001]

## ¿Cuándo utilizar random forest?

Aunque los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*Random forest*</span>][r000]*** son una alternativa a considerar en muchos casos de uso, también hay situaciones en las que no son adecuados.

*Los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*Random forest*</span>][r000]*** deben usarse principalmente para tareas de **clasificación** donde todas las **clases** con algunos ejemplos están presentes en el conjunto de datos de entrenamiento*. Sin embargo, no son adecuados para predecir nuevas **clases** o valores, como los conocemos por **regresiones lineales** o redes neuronales, por ejemplo.

*Aunque entrenar ***[<span style="font-family:Verdana; font-size:0.95em;color:red">*Random forest*</span>][r000]*** es relativamente rápido, una sola **clasificación** lleva un tiempo relativamente largo*. Entonces, si tiene un caso de uso en el que se deben realizar predicciones en tiempo real, otros algoritmos pueden ser más adecuados.

*Si el conjunto de datos de entrenamiento está poblado de manera muy desigual, lo que significa que algunas **clases** tienen muy pocos registros. Las muestras en el proceso de **embolsado** sufren esto, lo que a su vez tiene un impacto negativo en el rendimiento del modelo*.

> Fuente: [<span style="font-family:Verdana; font-size:0.95em;color:red">*Introducción al algoritmo random forest*</span>][r001]

## Resumen 

***¿Qué es un árbol de decisión?***  

Un ***árbol de decisión*** es un método para crear y visualizar modelos y algoritmos predictivos. Comenzando desde arriba (***raíz***), responde preguntas que lo llevan a las siguientes (***nodos***). Finalmente, llega al final que proporciona su respuesta (***hojas***).

Son fáciles de entender y muy efectivos. El objetivo de un ***árbol de decisión*** es dividir una población de datos en segmentos más pequeños.

Etapas de la predicción:

1. Entrenar el modelo; aquí es donde ***se construye, prueba y optimiza el árbol*** utilizando una colección de datos existente.  

2. Se utiliza el modelo para ***predecir un resultado desconocido***.  

Tipos de ***árboles de decisión***:  

* ***Árbol de regresión*** para predecir datos cuantitativos continuos. Por ejemplo, para predecir los ingresos de una persona se requiere un ***árbol de regresión***, ya que los datos que se intenta predecir caen a lo largo de un continuo. 

* ***Árbol de clasificación*** para predecir datos cualitativos. Un ejemplo sería un árbol que predice el diagnóstico médico de una persona en función de diversos síntomas; hay un número finito de valores o categorías objetivo. 

No se puede concluir simplemente concluir que si la información que se intenta predecir es un número, siempre se trata de un ***árbol de regresión***. El código postal es un buen ejemplo. A pesar de ser un número, en realidad es una medida cualitativa porque los códigos postales no se calculan; representan categorías.

***Términos clave***  

Es importante tener en cuenta que se utilizan varios términos para describir estos conceptos. También se indicarán los términos alternativos, en caso de que los encuentre en un contexto diferente.  

![Términos clave][i006]

En la tabla anterior, la columna Z es el ***indicador objetivo (target indicator)***; la información que predice el modelo. Todo el modelado se basa en estos puntos de datos. Términos alternativos son: ***clase, variable prevista, variable objetivo***.

Los datos de las columnas A, B, C, etc. se denominan ***indicadores (indicators)***. Los ***indicadores*** son los puntos de datos que se utilizan para hacer predicciones. Términos alternativos son: ***característica, dimensión, variable***.

En su conjunto, la colección total de indicadores forma un ***vector indicador (vector indicator)***. Términos alternativos son: ***vector de medición, vector de características, conjunto de datos***.

Las filas 1, 2 y 3 representan ***átomos (atoms)***. Cada fila contiene puntos de datos relacionados con una entidad singular; En nuestros análisis, normalmente se trata de una persona o producto individual. Términos alternativos son: ***instancias, ejemplos, puntos de datos***.

En los ***árboles de decisión (decision trees)*** en el análisis predictivo se muestra la ***raíz del árbol*** arriba y las ***ramas (branches)*** hacia abajo.

Cada división en la ***rama (branch)***, donde dividimos el grupo grande en grupos progresivamente más pequeños planteando un escenario de uno u otro, se denomina ***nodo (node)***. El ***nodo terminal (terminal node)*** a se llama ***hoja (leaf)***.  

***Metodología***

Construir un modelo predictivo implica primero ***entrenar el modelo (model training) y construir el árbol*** usando datos conocidos y verificando su precisión y confiabilidad ***usando el modelo en datos de prueba*** que se habían reservado para predecir los resultados de la prueba conocidos.  

En el siguiente diagrama, el modelo se construye inicialmente utilizando datos de 6 meses (el sexto mes es el ***indicador objetivo*** y los cinco meses anteriores se utilizan para ***entrenar el modelo*** que predecirá el resultado del sexto mes). Se ***evalúa la precisión del modelo*** y se ***optimiza*** utilizando los datos del mes anterior para predecir el resultado conocido de hoy (un valor conocido). Finalmente, ***el modelo se puede utilizar para predecir resultados en el futuro***.  

![Metodología][i007] 

***Una vez que el árbol ha sido probado y optimizado, se puede utilizar para predecir resultados futuros o desconocidos***.

***Desarrollo***   

Cuando construimos un ***árbol de decisión***, comenzamos desde la ***raíz***, que incluye la ***población total de átomos***. A medida que ***avanzamos hacia abajo en el árbol***, el objetivo es ***dividir la población total en subconjuntos cada vez más pequeños de átomos en cada nodo***; de ahí la descripción popular de “divide y vencerás”. ***Cada subconjunto debe ser lo más distinto posible en términos del indicador objetivo***. Por ejemplo, si buscamos clientes de alto y bajo riesgo, querremos dividir cada ***nodo*** en dos subconjuntos; uno con clientes en su mayoría de alto riesgo y el otro con clientes en su mayoría de bajo riesgo.

Este ***objetivo se logra iterando cada indicador en relación con el indicador objetivo y luego eligiendo el indicador que mejor divide los datos en dos nodos más pequeños***. ***A medida que el programa recorre cada par de indicador-objetivo, calcula el coeficiente de Gini***, que es un cálculo matemático que ***se utiliza para determinar el mejor indicador a utilizar para esa división en particular***. El ***coeficiente de Gini*** es una puntuación entre 0 y 1, siendo 1 la mejor división y 0 la peor. El programa elige el indicador que tiene el ***coeficiente de Gini*** más alto para dividir el nodo, ***luego pasa al siguiente nodo y repite el proceso***.

En la siguiente ilustración, el gráfico de la izquierda, muestra el indicador 1 en términos del ***indicador objetivo***, no es una división óptima. Hay cantidades casi iguales de clientes de alto y bajo riesgo a cada lado de la línea dividida. Sin embargo, el gráfico de la derecha muestra un muy buen indicador; la línea divide con mucha precisión a los clientes de alto y bajo riesgo.  

![Coeficiente de Gini][i008]  

***Cómo calcular una puntuación predictiva***  

Una vez que el programa haya terminado de construir el ***árbol***, se pueden calcular puntuaciones predictivas. ***La puntuación predictiva es un porcentaje del indicador objetivo en el nodo hoja del modelo entrenado***.  

En el siguiente ejemplo, hay 20 clientes de alto riesgo y 80 clientes de bajo riesgo en la ***hoja*** del extremo izquierdo. Se diría que cualquier ***átomo*** que termine en la ***hoja*** izquierda tiene un 20% de posibilidades de ser un cliente de alto riesgo. De no ser por la ***hoja*** de la derecha, un cliente tendría un 75% de posibilidades de ser un cliente de alto riesgo. Esto demuestra que un modelo puede predecir si ciertos ***átomos*** tienen una mayor propensión a un ***indicador objetivo***. ***No es 100% precisa, sin embargo, es mucho más precisa que una suposición aleatoria, ¡lo cual es suficiente para marcar una gran diferencia!***.   

***Se deja al lector reflexionar sobre el valor de la experiencia y su relación (altísma con la construcción de sesgos humanos) y como, por poco que ayude un árbol de decisión, es mejor que la experiencia humana***.  

![Ejemplo clientes alto y bajo riesgo][i009]  

***Optimizando el modelo. Cómo reducir el sesgo***  

Existe un ***problema potencial importante al trabajar con árboles de decisión: la creación de un árbol demasiado complejo***. Con los ***árboles de decisión***, la simplicidad es la clave para reducir el ***sesgo (bias) o ruido***. Si un ***árbol*** crece demasiado, deja de ser útil.  

La siguiente imagen ilustra este punto con un ejemplo muy simplificado. Como se puede ver, el modelo divide los datos de tal manera que las ***hojas*** inferiores solo tienen una persona cada una. Lo único que hace este ***árbol*** es mostrar la información de la tabla de una forma nueva. ***No añade ninguna información adicional; solo reafirma los datos***. También se notará que el ***árbol*** es bastante impreciso; si se agregan los datos de Sally a la mezcla, se verá que predice que el valor de su vivienda es mucho más caro del que realmente tiene. ***El árbol no ha permitido circunstancias novedosas fuera de los datos de entrenamiento***. Esto se conoce como ***sobreajuste (sobreaprendizaje o overfiting)***.  

![Overfiting][i010]  

El desafío, entonces, es crear un ***árbol*** que sea ***lo suficientemente específico como para permitir conocimientos prácticos, pero que no sea complejo hasta el punto de que no brinde información nueva ni permita posibilidades que no estaban expresamente establecidas en los datos***. Este problema ***se alivia mediante*** un proceso conocido como ***poda (pruning)***.

La idea es ***construir un árbol muy complejo y luego eliminar suficientes niveles de complejidad hasta que sea lo más simple posible, pero aún con la máxima precisión en la predicción del indicador objetivo***. Esto se hace empleando una técnica simple: ***reservar una parte de los datos de entrenamiento para usarlos como datos de validación***. Dado que ***estos datos no se utilizaron para entrenar el modelo, mostrarán si el árbol de decisión ha aprendido en exceso los datos de entrenamiento. Si la precisión predictiva (también conocida como elevación) con los datos de prueba es baja, el tamaño del árbol se reduce y el proceso se repite hasta que el árbol alcanza el punto óptimo entre alta precisión y baja complejidad***.

***Optimizando el modelo. Cómo sacarlo del parque***  

Ya ha sabemos cómo se construyen los ***árboles de decisión*** para garantizar la ***precisión*** de los resultados y, al mismo tiempo, evitar el ***sobreajuste***. Pero, ¿cómo llevan los científicos de datos un modelo predictivo al siguiente nivel?. Usan múltiples modelos. ***Cuando se combinan varios modelos en un solo megamodelo, se lo denomina modelo de conjunto (ensamble model)***. El uso de ***un conjunto de modelos predictivos puede mejorar el rendimiento de un solo modelo entre un 5% y un 30%***. ¡Eso es enorme!. Hay algunas formas de crear un conjunto, pero ***los dos métodos más comunes*** son: ***embolsado (bagging) y bosques aleatorios (random forest)***.

***Bagging*** es una versión abreviada del término "agregación de arranque". En este método, ***los datos de entrenamiento se dividen en subconjuntos de datos más pequeños y, dentro de los subconjuntos, algunos átomos se duplican o eliminan aleatoriamente***. Esto garantiza que ***ningún átomo afecte desproporcionadamente a los resultados finales***. Se crea un ***árbol de decisión para cada subconjunto y se combinan los resultados de cada árbol. Al combinar estos árboles en un modelo conjunto, se superan las deficiencias de cualquier árbol individual***.

Los ***random forest*** están estrechamente relacionados con el ***bagging***, pero agregan un elemento adicional: ***en lugar de solo aleatorizar los átomos en los distintos subconjuntos de datos, también duplica o elimina indicadores aleatoriamente. Si un determinado indicador tiene fallas o muestra una correlación falsa con el indicador objetivo, esto se supera por el hecho de que el indicador defectuoso no está presente en ciertos árboles o tiene una importancia reducida en otros***.  

***Conclusión***  

Los ***árboles de decisión*** son una ***herramienta poderosa*** para los científicos de datos, pero deben manejarse con cuidado. Aunque muchas de las tareas repetitivas se logran mediante el uso de programas (de ahí el término aprendizaje automático), todos los aspectos del proceso deben ser orquestados y supervisados ​​por un científico de datos experimentado para crear el modelo más preciso. Pero al final el trabajo vale la pena cuando un ***modelo preciso conduce a conocimientos prácticos***.

> Fuente: [<span style="font-family:Verdana; font-size:0.95em;color:red">*Árboles de decisión: descripción general*</span>][r010]

## Listado de referencias externas

* Random forest (InteractiveChaos)  

[r000]: https://interactivechaos.com/es/wiki/random-forest "referencia a random forest en InteractiveChaos"

* Introducción al algoritmo Random Forest (Medium)  

[r001]: https://tutegomeze.medium.com/introducci%C3%B3n-al-algoritmo-random-forest-54577e93458b "referencia a introducción al algoritmo random forest en Medium"

* Ensemble methods in Machine Learning: What are they and why use them?  

[r002]: https://towardsdatascience.com/ensemble-methods-in-machine-learning-what-are-they-and-why-use-them-68ec3f9fef5f "referencia a Ensemble methods in Machine Learning: What are they and why use them?"

* El superpoder de los hiperparámetros  

[r003]: https://impulsatek.com/8-el-superpoder-de-los-hiperparametros/ "referencia a el superpoder de los hiperparámetros"

* Árboles de decisión (Wikipedia)  

[r004]: https://es.wikipedia.org/wiki/%C3%81rbol_de_decisi%C3%B3n "referencia a árboles de decisión en Wikipedia"

* Machine Learning (Wikipedia)  

[r005]: https://es.wikipedia.org/wiki/Aprendizaje_autom%C3%A1tico "referencia a Machine Learning en Wikipedia"

* Guía definitiva a las técnicas de Ensemble (Medium)  

[r006]: https://es.wikipedia.org/wiki/Aprendizaje_autom%C3%A1tico "referencia a Guía definitiva a las técnicas de Ensemble en Medium"

* Covarianza y Correlación (Medium)  

[r007]: https://medium.com/@nicolasarrioja/covarianza-y-correlaci%C3%B3n-7f16e59445b4 "referencia a Covarianza y Correlación en Medium"

* Bagging

[r008]: https://rubenfcasal.github.io/aprendizaje_estadistico/bagging.html "referencia a Bagging"

* Correlación (Wikipedia)

[r009]: https://es.wikipedia.org/wiki/Correlaci%C3%B3n "referencia a correlación en Wikipedia"

* Árboles de decisión: descripción general

[r010]: https://www.aunalytics.com/decision-trees-an-overview/ "referencia a árboles de decisión: descripción general"

## Listado de imágenes

* Random forest  

[i000]: https://i.imgur.com/GRDmMqH.png "Random forest"

* Varianza y sesgo en los random forest 001  

[i001]: https://i.imgur.com/6beWzpG.png "Varianza y sesgo en los random forest 001"

* Varianza y sesgo en los random forest 002  

[i002]: https://i.imgur.com/qCJ5MSD.png "Varianza y sesgo en los random forest 002"

* Paralelo y secuencial  

[i003]: https://i.imgur.com/jaNkAxe.png "Paralelo y secuencial"

* Random forest y bagging  

[i004]: https://i.imgur.com/Zbhpl6W.png "Random forest y bagging"

* Variables correlacionadas 

[i005]: https://i.imgur.com/meVitNX.png "Variables correlacionadas"

* Términos clave 

[i006]: https://i.imgur.com/dGsgWWF.png "Términos clave"

* Metodología 

[i007]: https://i.imgur.com/vnSY6oQ.png "Metodología"

* Coeficiente de Gini 

[i008]: https://i.imgur.com/r554rnz.png "Coeficiente de Gini"

* Ejemplo clientes alto y bajo riesgo 

[i009]: https://i.imgur.com/Qg1oImA.png "Ejemplo clientes alto y bajo riesgo"

* Overfiting 

[i010]: https://i.imgur.com/ASbN3Bt.png "Overfiting"