# Introducción a árboles de decisión

<details>

<summary>Índice de contenidos</summary>

* ***¿Qué son los árboles de decisión?***   
  * ***Terminología*** 
  * ***Reglas***  
  * ***Algoritmos***  
    * ***Conceptos***  
    * ***Utilización***  
* ***Pasos para implementar árboles de decisión***  
  * ***1) Recopilación y preparación de datos***  
  * ***2) Selección de características***  
  * ***3) Entrenamiento del modelo***  
  * ***4) Validación del modelo***  
  * ***5) Ajuste y optimización del modelo***  
  * ***6) Implementación y despliegue***  
  * ***7) Adicionalmente***  
    * ***7.1) Seleccionar el algoritmo adecuado***  
    * ***7.2) Considerar la interpretabilidad del modelo***  
    * ***7.3) Realizar una validación exhaustiva***
    * ***7.4) Evaluar la estabilidad del modelo***  
  * ***Matriz de confusión***
    * ***Métricas***
      * ***Accuracy (exactitud)***  
      * ***Precision (precisión)***  
      * ***Bias, ó inaccuracy (sesgo)***    
      * ***Recall o sensitivity (sensibilidad)***  
      * ***Especificity (especificidad)***  
      * ***Relación entre recall (sensibilidad) y especificity (especificidad)***
      * ***Mediciones de la precisión de una prueba***
        * ***Tasa de falsos positivos (TFP)***  
        * ***Tasa de falsos negativos (TFN o tasa de error)***  
        * ***Tasa de verdadero positivos (TVP o sensibilidad)***  
        * ***Tasa de verdaderos negativos (TVN o especificidad)***  
        * ***F1 Score***  
      * ***Resumen***
    * ***Consejos generales sobre la matriz de confusión y sus métricas***  
    * ***Balanceo de clases***  
    * ***Hiperparámetros***  
* ***¿Cómo funcionan los árboles de decisión?***  
  * ***Ventajas***  
  * ***Desventajas***  
  * ***¿Cuándo usar árboles de decisión?***  
  

</details>

## ¿Qué son los árboles de decisión?  

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Árbol de decisión</span>][r000]***: ***Modelo de [<span style="font-family:Verdana; font-size:0.95em;color:red">ML</span>][r001] [<span style="font-family:Verdana; font-size:0.95em;color:red">supervisado</span>][r002]*** para ***[<span style="font-family:Verdana; font-size:0.95em;color:red">clasificación</span>][r005] y [<span style="font-family:Verdana; font-size:0.95em;color:red">regresión</span>][r005]***. *Muy extendidos por su  simplicidad, facilidad de interpretación y aplicaciones diversas*.  

![Aprendizaje supervisado][i001]  

![Regresión vs clasificación 001][i002]  

![Regresión vs clasificación 002][i003]  

![Regresión vs clasificación 003][i004]  

Las primeras versiones de los *[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]* fueron propuestas por [<span style="font-family:Verdana; font-size:0.95em;color:red">*Leo Breiman*</span>][r003] en la década de 1980.  

![Leo Breiman][i000]    

> Fuente: [<span style="font-family:Verdana; font-size:0.95em;color:red">*Decision Trees y Random Forest*</span>][r004]   

### Terminología

* **Nodo**: El momento en el que se ha de tomar una decisión de entre varias posibles, lo que va haciendo que a medida que aumenta el número de **nodos** aumente el número de posibles finales a los que puede llegar. Esto hace que un ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]*** con muchos **nodos** sea complicado de dibujar a mano y de analizar debido a la existencia de numerosos caminos que se pueden seguir. Dicho de otro modo, *un **nodo** es una pregunta sobre los datos*.  

![Nodo][i005]  

* **Nodo raíz**: Es el primer **nodo** del ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]*** y no tiene un **nodo padre**. Representa el conjunto de datos completo y es el punto de partida para la construcción del **árbol**.  

![Nodo raíz][i006]    

* **Rama**: Es una conexión entre dos **nodos** del **árbol** que representa una opción posible para un atributo determinado.  

![Rama][i007]  

* **Nodo de decisión**: Es un **nodo** interno del **árbol** que representa una característica del conjunto de datos y tiene al menos dos **ramas** que indican las posibles opciones para esa característica.  

![Nodo de decisión][i008]   

* **División**: Es la separación de un conjunto de datos en subconjuntos más pequeños y homogéneos en función de un atributo determinado. Cada división genera un nuevo **nodo** y una nueva **rama** en el **árbol**.  

![División][i009]    

* **Nodo padre**: Es el **nodo** inmediatamente anterior a un **nodo** específico en el **árbol**. Un **nodo** puede tener varios **nodos hijos**, pero solo tiene un **nodo padre**.  

![Nodo padre][i010]    

* **Nodo hijo**: Es un **nodo** inmediatamente posterior a un **nodo** específico en el **árbol**. Un **nodo** puede tener varios **nodos hijos**, pero solo tiene un **nodo padre**.  

![Nodo hijo][i011]    

* **Nodo hoja**: Es un **nodo** terminal del **árbol** que no tiene más **ramas** y representa una **etiqueta de clase** o una predicción para el conjunto de datos de entrada.  

![Nodo hoja][i012]    

* **Overfitting (sobreajuste)**: Se produce cuando *los datos de formación son pocos o contienen incoherencias*.  

![Overfitting][i013] 

* **Pruning (poda)**: Es un proceso de eliminación de **nodos** innecesarios del **árbol** para evitar el **overfitting** (**sobreajuste**) del modelo y mejorar su capacidad de generalización. La **poda** se realiza después de construir el **árbol** y puede ser *prepruning o postpruning*. Es decir, se *elimina una **rama** de un **nodo** transformándolo en una **hoja***. Una metáfora sería intentar avanzar a un camión sin poderlo ver (podemos tener problemas).  

![Pruning][i014] 

* **Vectores** (de números): La solución final a la que se llega en función de las diversas posibilidades que se tienen, dan las utilidades en esa solución.  

![Vectores][i015]  

* **Flechas**: Uniones entre un **nodo** y otro **nodo** y representan cada acción distinta.  

![Flechas][i016]   

* **Etiquetas**: Se encuentran en cada **nodo** y cada **flecha** y dan nombre a cada acción.

![Etiquetas][i017]   

* **Clase**: Un ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]*** es una representación simple para **clasificar** ejemplos. Para esta sección, supongamos que todas las características de entrada tienen dominios discretos finitos y que hay una única característica objetivo llamada "**clasificación**". Cada elemento del dominio de la **clasificación** se denomina **clase**.  

![Clase][i018]  

* **Costo**: 
    * **Costo de medición**: Para determinar el *valor de una determinada propiedad (atributo)* exhibida por el objeto.
    * **Costo de clasificación errónea**: Al *decidir que el objeto pertenece a la clase X cuando su clase real es Y*.  

* **Validación cruzada**: Es el proceso de *construir un ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]*** con la mayoría de los datos y posteriormente usar la parte restante de los datos para probar la precisión del **[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]***.  

![Validación cruzada][i019] 

* **Outliers**: Valores atípicos de la muestra.  

![Outliers][i020]   

El modelo aprende de los datos, generando reglas de tipo *if-else*. Cada **rama** del **árbol** es una respuesta a un **nodo**. El proceso continúa hasta que se llega a una **hoja** del **árbol**, la cual representa la predicción final (**vectores**).  

* ***Tipos de variables en Estadística***

* **Variables cualitativas**: Son características de un individuo u objeto, que ***se pueden expresar con palabras***. Algunos ejemplos son: el color de ojos, el color del cabello, el género, el estado civil o la marca de un producto. 

* **Variables cuantitativas**: Son aquellas características de un objeto o individuo que ***se pueden escribir en números***. Por ejemplo: edad, ingresos, peso, altura, presión, humedad o cantidad de hermanos.  

  * **Variables discretas**: Son aquellas que ***no aceptan un valor entre dos números consecutivos***. Si tienes los datos 1, 2, 3, 10, 11 y 15, entre el 1 y 2 no puede aparecer el 1.48, porque del 1 salta directamente al 2. Generalmente, las variables discretas son resultado de un conteo y no permiten los números decimales. Por ejemplo: número de pacientes, número de alumnos, número de motos por modelo.  

  * **Variables continuas**: Son aquellas que ***pueden tomar cualquier valor entre dos intervalos o números***. Por ejemplo, si necesitas escribir la estatura de un grupo de basquetbolistas, seguramente, no podrás utilizar los números 1 y 2, pero si las variables 1.78, 1.65, 1.45, porque la altura suele expresarse de esa manera.
  
### Reglas

1) *Al comienzo del juego hay un **nodo** inicial que no es apuntado por ninguna **flecha***, es el único **nodo** del juego con esta característica.  

2) El *resto de los **nodos** del juego son apuntados por una única **flecha***.  

3) De lo anterior se deduce que *hay un único camino para llegar del **nodo** inicial a cada uno de los **nodos** del juego*. Las decisiones son excluyentes y no hay marcha atrás. Opción 1->opción 2->opción 3->Resultado Final X  

### Algoritmos  

  * ***[<span style="font-family:Verdana; font-size:0.95em;color:red">ID3</span>][r008] (Iterative Dichotomiser 3)***: A [<span style="font-family:Verdana; font-size:0.95em;color:red">Ross Quinlan</span>][r009] se le atribuye el desarrollo de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">ID3</span>][r008]***. Este algoritmo aprovecha la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** y la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Ganancia de la información</span>][r012]*** como **métricas** para evaluar las divisiones de candidatos.   

    * **Algoritmo**:  
  
      1) Calcular la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** para todas las **clases**.  

      2) Seleccionar el mejor **atributo** basado en la reducción de la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]***.  

      3) *Iterar hasta que todos los objetos sean clasificados*.  

  * ***[<span style="font-family:Verdana; font-size:0.95em;color:red">C4.5</span>][r010]***: Este algoritmo se considera una iteración posterior de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">ID3</span>][r008]***, que también fue desarrollado por [<span style="font-family:Verdana; font-size:0.95em;color:red">Ross Quinlan</span>][r009]. Puede utilizar la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Ganancia de la información</span>][r012]*** o las proporciones de la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Ganancia de la información</span>][r012]*** para evaluar los puntos de división dentro de los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]***.  

    * **Algoritmo**:  

      1) En cada **nodo** del ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r000]***, ***[<span style="font-family:Verdana; font-size:0.95em;color:red">C4.5</span>][r010]*** elige un **atributo** de los datos que más eficazmente dividen el conjunto de muestras en subconjuntos enriquecidos en una **clase** u otra.  

      2) Su criterio es el normalizado para la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Ganancia de la información</span>][r012]*** (diferencia de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]***) que resulta en la elección de un atributo para dividir los datos.  

      3) El atributo con la mayor ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Ganancia de la información</span>][r012]*** normalizada se elige como parámetro de decisión.  

      4) El algoritmo ***[<span style="font-family:Verdana; font-size:0.95em;color:red">C4.5</span>][r010]*** divide recursivamente en sublistas más pequeñas.  

  * ***[<span style="font-family:Verdana; font-size:0.95em;color:red">CART (*Classification And Regression* Trees)</span>][r015]***: Fue introducido por [<span style="font-family:Verdana; font-size:0.95em;color:red">*Leo Breiman*</span>][r003]. Generalmente utiliza la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">impureza de Gini</span>][r018]***, la cual ***mide la frecuencia con la que se clasifica incorrectamente un atributo elegido al azar***, con lo que *se identifica el atributo ideal para la división*, es decir, *un valor más bajo es más ideal*.   

    * **Algoritmo**:  

      1. Para crear la **raíz del ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r000]*****, es decir la primera partición, se toman todas las características y, para cada una de ellas, se definen todos los posibles umbrales a que haya lugar. Cada umbral será simplemente el punto intermedio entre dos valores consecutivos de cada característica.  

      2. Para cada uno de estos umbrales se calcula la partición (**nodo** izquierdo y **nodo** derecho) y para cada **nodo hijo** se calcula el ***[<span style="font-family:Verdana; font-size:0.95em;color:red">índice de Gini</span>][r018]***. Con estos **nodos hijos** se calcula la función de **costo del nodo padre**, que es el promedio ponderado de los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">índices de Gini</span>][r018]*** de sus hijos.  

      3. Se toma el umbral (o **nodo padre** resultante) que tenga la función de **costo** con el menor valor posible, indicando que la partición obtenida es la más homogénea de todas las analizadas.  

      4. Una vez se haya realizado esta partición, se repite el mismo procedimiento de forma iterativa para los **nodos** resultantes, exceptuando los que sean **nodos hoja**.

#### Conceptos

  * ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Entropía de la información</span>][r007]***: La cantidad de información promedio que contienen los símbolos usados. ***Los símbolos con menor probabilidad son los que aportan mayor información***; por ejemplo, si se considera como sistema de símbolos a las palabras en un texto, palabras frecuentes como «que», «el», «a» aportan poca información, mientras que palabras menos frecuentes como «corren», «niño», «perro» aportan más información. Si de un texto dado borramos un «que», seguramente no afectará a la comprensión y se sobreentenderá, no siendo así si borramos la palabra «niño» del mismo texto original. Cuando todos los símbolos son igualmente probables (distribución de probabilidad plana), todos aportan información relevante y la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** es máxima. La ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** puede ser considerada como una medida de la incertidumbre y de la información necesaria para, en cualquier proceso, poder acotar, reducir o eliminar la incertidumbre. Es decir, ***cuanto mayor sea la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]***, mayor será la impureza y la mezcla de clases en el conjunto de datos***.  

  ![Entropía de la información][i021]  

  * *Definición formal*  

    Supongamos que un evento (variable aleatoria) tiene un *grado de indeterminación inicial igual a 𝑘* (i.e. existen 𝑘 estados posibles) y supongamos *todos los estados equiprobables*. Entonces *la probabilidad de que se dé una de esas combinaciones será $p=\frac{1}{k}$*. Luego podemos representar la expresión $𝑐_𝑖$ como:  

      $$
      \begin{align*}  
      c_i &= log_2(k)\\  
          &= log_2[\frac{1}{(\frac{1}{k})}]\\  
          &= log_2(\frac{1}{p})\\ 
          &= log_2(1)-log_2(p)\\  
          &= 0-log_2(p)\\  
          &= -log_2(p) 
      \end{align*}
      $$

    Si ahora *cada uno de los 𝑘 estados tiene una probabilidad $𝑝_𝑖$, entonces la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** vendrá dada por la suma ponderada de la cantidad de información*:  

      $$
      \begin{align*}
      H &= -p_1log_2(p_1)-p_2log_2(p_2)-...-p_klog_2(p_k)\\  
        &= -\sum_{i=1}^{k}p_ilog_2(p_i)
      \end{align*}
      $$  

    Por lo tanto, la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** de un mensaje 𝑋, denotado por 𝐻(𝑋), **es el valor medio ponderado de la cantidad de información de los diversos estados del mensaje**:  

      $$
      \begin{align*}
      H(X) &= -\sum_{i}p(x_i)log_2p(x_i)\\  
           &= \sum_{i}p(x_i)log_2p(\frac{1}{p(x_i)})  
      \end{align*}
      $$  

    que **representa una medida de la incertidumbre (impureza) media acerca de una variable aleatoria y por tanto de la cantidad de información**.

    Es decir,  

      Entropía(S) $=-p(+)log_2(p(+))-p(-)log_2(p(-))$  

    donde  

    * $p_i$ es la proporción de ejemplos en la clase i en el conjunto de datos S.  
    * p(+) son éxitos.
    * p(-) son fracasos.

  * ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Índice (o impureza) de Gini</span>][r018]***: Mide la frecuencia con la que se clasifica incorrectamente un atributo elegido al azar. Cuando se evalúa usando ***la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">impureza de Gini</span>][r018]***, un valor más bajo es ideal***. Es decir, ***al igual que con la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]***, cuanto menor sea la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">impureza de Gini</span>][r018]***, mayor será la pureza del conjunto de datos***.  
  
  * ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Ganancia de la información</span>][r012]***: Representa la diferencia de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** antes y después de una división en un atributo determinado. *El atributo con la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Ganancia de la información</span>][r012]*** más alta producirá la mejor división*, ya que hace el mejor trabajo al clasificar los datos de entrenamiento de acuerdo con su clasificación de destino. Es decir, ***nos interesan valores más altos de la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Ganancia</span>][r012]******.

    **Ejemplos**:  

    * **La ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** de un mensaje M de longitud 1 carácter que utiliza el conjunto de caracteres ASCII, suponiendo una equiprobabilidad en los 256 caracteres ASCII, será:**  

      $$
      \begin{align*}
      H(M) &=-\sum_{i}^{256}\frac{1}{256}log_2\frac{1}{256}\\  
           &=(-\frac{256}{256})log_2(\frac{1}{256})\\  
           &=-1(log_2(1)-log_2(256))\\  
           &=0+log_2(256)\\   
           &=log_2(256)\\  
           &=8\\  
      \end{align*}
      $$  

    * **Supongamos que el número de estados de un mensaje es igual a 3, $M_1$, $M_2$ y $M_3$ donde la probabilidad de $M_1$ es 50%, la de $M_2$ 25% y la de $M_3$ 25%. Por tanto, la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** es:**  

      $$
      \begin{align*}
      H(M)&=\frac{1}{2}log_2(2)+\frac{1}{4}log_2(4)+\frac{1}{4}log_2(4)\\  
          &=\frac{1}{2}·1+\frac{1}{4}·2+\frac{1}{4}·2\\  
          &=\frac{1}{2}+\frac{1}{2}+\frac{1}{2}\\  
          &=\frac{3}{2}\\  
          &=1,5 
      \end{align*}
      $$ 

    * **Tenemos un conjunto de estudiantes, en el que vamos a considerar las siguientes características:** 

    ![Ejemplo estudiantes][i022] 

    * El conjunto total es de 30 estudiantes  
    * Consideramos 3 variables: Género (hombre/mujer), Clase (IX/X) y Altura (5,5pies=1,68m).  
    * Del conjunto total 15 estudiantes juegan al cricket en su tiempo libre
    * *Debemos crear un modelo para predecir quien jugará al cricket*  
    * Segregar estudiantes basados en todos los valores de las 3 variables e identificar aquella variable que crea los conjuntos más homogéneos de estudiantes y que a su vez son heterogéneos entre ellos.  

    Obtenemos los siguientes resultados experimentales:  

    * 10 estudiantes son mujeres y 20 son hombres    
    * 14 estudiantes son de la clase IX y 16 son de la clase X  
    * 12 estudiantes miden < 1,68m y 18 miden $\ge$ 1,68m

    Consideramos dos categorías en cada clase, éxito y fracaso, con la fórmula:  

    Entropía(S) $=-p(+)log_2(p(+))-p(-)log_2(p(-))=>$ éxitos y fracasos  

    * Un 20% de las mujeres juegan al cricket, el complemento (jueguen o no) es del 80%.  
    * Un 65% de los hombres juegan al cricket, el complemento (jueguen o no) es del 35%.   
    * Un 43% de los/as alumnos/as de la clase IX juegan al cricket, el complemento (jueguen o no) es del 57%.  
    * Un 56% de los/as alumnos/as de la clase X juegan al cricket, el complemento (jueguen o no) es del 44%.   
    * Un 42% de los/as alumnos/as que miden < 1,68m juegan al cricket, el complemento (jueguen o no) es del 58%.  
    * Un 56% de los/as alumnos/as que miden $\ge$ 1,68m juegan al cricket, el complemento (jueguen o no) es del 44%.   

  Cáculo del ***[<span style="font-family:Verdana; font-size:0.95em;color:red">índice de Gini</span>][r018]*** para los subnodos usando la fórmula de la suma de los cuadrados de probabilidad para éxito y fracaso $(p^2 + q^2)$. Es decir, calculamos ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Gini</span>][r018]*** para la división usando puntuación ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Gini</span>][r018]*** y ponderado para cada nodo de la división.  

  | Género   | Clase    | Altura |
  | :------- | :------- | :----- |
  | Mujer $=>(0,2)^2+(0,8)^2= 0,68$ | IX $=>(0,43)^2+(0,57)^2= 0,51$ | <1,68 $=>(0,42)^2+(0,58)^2= 0,52$ |
  | Hombre $=>(0,65)^2+(0,35)^2= 0,55$ | X $=>(0,56)^2+(0,44)^2= 0,51$ | $\ge1,68=>(0,56)^2+(0,44)^2= 0,50$ |
  | Ponderado $\frac{10}{30}·0.68+\frac{20}{30}·0,55=$ **0,59** | Ponderado $\frac{14}{30}·0.51+\frac{16}{30}·0,51=$ 0,51 | Ponderado $\frac{12}{30}·0.52+\frac{18}{30}·0,50=$ 0,51 |

  **Como el valor más alto es el del género, este será el nodo raíz.** Recordemos que en el algoritmo ***[<span style="font-family:Verdana; font-size:0.95em;color:red">CART</span>][r015]***, para determinar la raíz, se toman todas las características y, para cada una de ellas, se definen todos los posibles umbrales a que haya lugar. Cada umbral será simplemente el punto intermedio entre dos valores consecutivos de cada característica.  

  Además, para calcular el umbral se puede utilizar la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">ganancia</span>][r012]***, eso quiere decir que para comenzar a dividir, escogemos la impureza más baja, es decir, la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">ganancia</span>][r012]*** mayor. Si eligiésemos el ***[<span style="font-family:Verdana; font-size:0.95em;color:red">índice de Gini</span>][r018]***, se cogería el valor más bajo (idéntico razonamiento sería para la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]***).  

  Lo anterior quiere decir que, en un ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]***, cuanto más arriba (hacia la raíz), menor ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** y cuanto más abajo (hacia las hojas), mayor ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** se tiene. Este modo de trabajar permite, para evitar el **overfitting**, **podar** en ramas donde es mayor la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** y mantener ramas en las cuales es menor.

  Calculando la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]***.

  | Género   | Clase    | Altura |
  | :------- | :------- | :----- |
  | Mujer $=>-(\frac{2}{10}log_2(\frac{2}{10}))-(\frac{8}{10}log_2(\frac{8}{10}))= 0,72$| IX $=>-(\frac{6}{14}log_2(\frac{6}{14}))-(\frac{8}{14}log_2(\frac{8}{14}))= 0,99$|$<1,68=>-(\frac{5}{12}log_2(\frac{5}{12}))-(\frac{7}{12}log_2(\frac{7}{12}))= 0,98$|
  | Hombre $=>-(\frac{13}{20}log_2(\frac{13}{20}))-(\frac{7}{20}log_2(\frac{7}{20}))= 0,93$|X $=>-(\frac{9}{16}log_2(\frac{9}{16}))-(\frac{7}{16}log_2(\frac{7}{16}))= 0,99$|$\ge1,68=>-(\frac{10}{18}log_2(\frac{10}{18}))-(\frac{8}{18}log_2(\frac{8}{18}))= 1,55$|
  | Ponderado $=>(\frac{10}{30}·0,72)+(\frac{20}{30}·0,93)=$ **0,83**|Ponderado $=>(\frac{14}{30}·0,99)+(\frac{16}{30}·0,99)=$ 0,99|Ponderado $=>(\frac{12}{30}·0,98)+(\frac{18}{30}·1,55)=$ 1.32|

  Por complemento a 1 con la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]***, podemos calcular la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">ganancia</span>][r012]***.

  | Género   | Clase    | Altura |
  | :------- | :------- | :----- |
  | 1-0.83=**0.17**|1-0.99=0.01|1-1.32=-0.32|

  ***Tal como habíamos supuesto, todo cuadra***, es decir, que ***la menor impureza la tiene el género***.

  Este método no solo se aplicaría al **nodo** raíz, sino que se aplicaría recursivamente en todo el  ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r000]***.

***Nota***: ***Tanto la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** como la ***[<span style="font-family:Verdana; font-size:0.95em;color:red">impureza de Gini</span>][r018]*** son medidas de lo homogéneo o puro es un conjunto de datos en términos de las clases que contiene***. La elección entre ***usar ***[<span style="font-family:Verdana; font-size:0.95em;color:red">entropía</span>][r007]*** o ***[<span style="font-family:Verdana; font-size:0.95em;color:red">impureza de Gini</span>][r018]*** a menudo depende del contexto y del conjunto de datos específico, pero en la práctica, ambas métricas suelen llevar a resultados similares en términos de construcción de  ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]******.

![Entropía, Mínimo error e Índice Gini][i023]

#### Utilización

Estos modelos se utilizan comúnmente en tareas de **clasificación**, como la *detección de spam* en el correo electrónico o la **clasificación** de clientes en grupos de *segmentación de mercado*. También se utilizan en tareas de **regresión**, como la *predicción de precios de bienes raíces*.

***Ejemplo*** 

Supongamos que queremos *decidir si comprar o no un coche usado*. El ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]*** podría ser el siguiente:

* ¿El coche tiene menos de 5 años?  
    * Sí: ¿El coche tiene menos de 50.000 km?  
        * Sí: Comprar el coche.  
        * No: No comprar el coche.  
    * No: ¿El coche tiene menos de 80.000 km?  
        * Sí: Comprar el coche.  
        * No: No comprar el coche.  

Este **árbol** tiene dos **nodos**, con cada **nodo** representando una pregunta y cada **rama** representando una posible respuesta. En función de las respuestas a las preguntas, se llega a una **hoja**, la cual *indica si se debe comprar o no el coche usado*.

## Pasos para implementar árboles de decisión  

### ***1) Recopilación y preparación de datos***  

* Recolectar los *datos relevantes* para el proyecto.  
* Realizar una *limpieza y preprocesamiento de los datos*, como, por ejemplo, *eliminar **outliers*** (valores atípicos) y *manejar datos faltantes*.  
* *Dividir los datos en conjuntos de entrenamiento y prueba (**validación cruzada**)* para *evaluar el rendimiento del modelo*.  

### ***2) Selección de características***  

* *Identificar las características más relevantes* para el modelo.  
* Utilizar *técnicas de selección de características*, como la correlación y la importancia de las variables.  

### ***3) Entrenamiento del modelo***  

* Utilizar un *algoritmo* de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]***, como el ***[<span style="font-family:Verdana; font-size:0.95em;color:red">CART</span>][r015]*** o el ***[<span style="font-family:Verdana; font-size:0.95em;color:red">C4.5</span>][r010]***, *para entrenar el modelo*.  
* Asegurarse de *ajustar los **hiperparámetros*** del algoritmo *para obtener el mejor rendimiento*.  

### ***4) Validación del modelo***  

* Evaluar el *rendimiento del modelo utilizando **métricas*** como **la precisión, la exhaustividad y el valor F**.  
* Utilizar *técnicas de validación cruzada*, como la **validación cruzada k-fold**, *para obtener una estimación más precisa del rendimiento del modelo*.  

### ***5) Ajuste y optimización del modelo***  

* *Si el rendimiento del modelo no es satisfactorio, realizar ajustes en los parámetros del modelo o probar diferentes algoritmos* de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]***.  
* Utilizar *técnicas de optimización*, como la **poda**, *para mejorar la generalización del modelo*.  

### ***6) Implementación y despliegue***  

* *Una vez que el modelo ha sido entrenado y validado, se puede implementar en un entorno de producción*.  
* *Integrar el modelo en una aplicación o sistema existente para utilizarlo en la toma de decisiones*.  

### ***7) Adicionalmente***  

#### ***7.1) Seleccionar el algoritmo adecuado***

Existen diferentes tipos de algoritmos de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]***, como ***[<span style="font-family:Verdana; font-size:0.95em;color:red">CART</span>][r015], [<span style="font-family:Verdana; font-size:0.95em;color:red">C4.5</span>][r010] y Random Forest***. Es importante *seleccionar el algoritmo adecuado según las características y los requisitos del proyecto*.  

#### ***7.2) Considerar la interpretabilidad del modelo*** 

Los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** *son modelos fácilmente interpretables*, lo que significa que se puede entender cómo se toman las decisiones. Esto puede ser especialmente útil en proyectos que requieren explicabilidad, como pueda ser el sector financiero.  

#### ***7.3) Realizar una validación exhaustiva***

Es importante *realizar diferentes pruebas y validaciones del modelo para garantizar que esté funcionando correctamente*. Además de las ***métricas** de rendimiento*, se pueden utilizar técnicas como la **matriz de confusión** y la **curva ROC** para evaluar el rendimiento del modelo en diferentes escenarios.  

#### ***7.4) Evaluar la estabilidad del modelo***

Algunos ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** *pueden ser sensibles a cambios pequeños en los datos de entrada, lo que puede afectar el rendimiento del modelo*. Es importante *evaluar la estabilidad del modelo y realizar pruebas con diferentes conjuntos de datos para asegurarse de que sea robusto*.

> Fuente: [<span style="font-family:Verdana; font-size:0.95em;color:red">*Guía completa sobre algoritmos de árboles de decisión en España*</span>][r011] 

### Matriz de confusión

En el campo del ML una **matriz de confusión** es una herramienta que permite visualizar el desempeño de un algoritmo  de **aprendizaje supervisado**. *Cada columna de la matriz representa el número de predicciones de cada **clase***, mientras que cada *fila representa a las instancias en la **clase** real*, o sea, en términos prácticos nos ***permite ver qué tipos de aciertos y errores está teniendo nuestro modelo*** a la hora de pasar por el proceso de aprendizaje con los datos.

Resultados posibles:

* ***Verdadero positivo (VP)***: El valor real es positivo y  la prueba predijo tambien que era positivo.  
En el área de la salud: ***El paciente tiene la enfermedad y el test es positivo***.  
* ***Verdadero negativo (VN)***: El valor real  es negativo y la prueba predijo tambien que el resultado era negativo.  
En el área de la salud: ***El paciente no tiene la enfermedad y el test es negativo***.  
* ***Falso negativo (FN)***: El valor real es positivo, y la prueba predijo  que el resultado es negativo. Esto es lo que en Estadística se conoce como ***error tipo II***.  
En el área de la salud: ***El paciente tiene la enfermedad pero el resultado del test es negativo***.  
* ***Falso positivo (FP)***: El valor real es negativo, y la prueba predijo  que el resultado es positivo. Esto es lo que en Estadística se conoce como ***error tipo I***.  
En el área de la salud: ***El paciente no tiene la enfermedad pero el resultado del test es positivo***.

A partir de estas 4 opciones  surgen las ***métricas** de la **matriz de confusión***:  Por una parte la **accuracy (exactitud)** y la **precision (precisión)** y por otra la **recall (sensibilidad)** y la **especificity (especificidad)**.  

![Matriz de confusión][i024]  

#### Métricas

##### ***Accuracy (exactitud)***  

Se refiere a ***lo cerca que está el resultado de una medición del valor verdadero***. En términos estadísticos, la exactitud está relacionada con el **bias (sesgo)** de una estimación. Se representa como la proporción de resultados verdaderos dividido entre el número total de casos examinados. En forma práctica, ***la exactitud es la cantidad de predicciones acertadas***.

Accurancy $=\frac{VP+VN}{VP+FP+FN+VN}$  

![Accuracy][i025]

##### ***Precision (precisión)***  

Se refiere a la ***dispersión del conjunto de valores obtenidos a partir de mediciones repetidas de una magnitud. Cuanto menor es la dispersión mayor la precisión***. Se representa por la proporción de verdaderos positivos dividido entre todos los resultados positivos. En forma práctica, ***la precisión es el porcentaje predicciones positivas acertadas***.

Precision $=\frac{Resultados\_positivos}{Total\_resultados\_positivos}=\frac{VP}{VP+FP}$  

![Precision][i026]

##### ***Bias, ó inaccuracy (sesgo)***

***Es la diferencia entre el valor medio y el verdadero valor de la magnitud medida***. El **sesgo (bias)** pertenece al concepto de **exactitud**.  

##### ***Recall o sensitivity (sensibilidad)***  

También se conoce como **Tasa de verdaderos positivos (true positive rate o TP)**. En forma práctica, ***la sensibilidad es el porcentaje de casos positivos que fueron correctamente identificados***.

Sensitivity $=\frac{VP}{VP+FN}$

***En el área de la salud***:  $=\frac{Verdaderos\_positivos}{Total\_enfermos}$, es dicir, es ***la capacidad de de poder detectar correctamente la enfermedad entre los enfermos***.  

![Recall][i027]

##### ***Especificity (especificidad)***  

También conocida como la **Tasa de verdaderos negativos, (true negative rate o TN)**. En forma práctica, ***la Especificidad es el porcentaje de casos negativos que fueron correctamente identificados***. Expresa como de bien puede el modelo detectar esa **clase**.

Especificity $=\frac{VN}{VN+FP}$  

***En el área de la salud***:  $=\frac{Verdaderos\_negativos}{Total\_sanos}$, es dicir, es ***la capacidad de poder identificar los casos de pacientes sanos entre todos los sanos***.  

![Especificity][i028]  

##### ***Relación entre recall (sensibilidad) y especificity (especificidad)***  

La **sensibilidad** y la **especificidad** son dos valores que nos *indican la capacidad de nuestro estimador para discriminar los casos positivos, de los negativos*. La **sensibilidad** se representa como la *fracción de verdaderos positivos*, mientras que la **especificidad**, es la *fracción de verdaderos negativos*.

![Métricas de la matriz de confusión][i033] 

##### ***Mediciones de la precisión de una prueba***  

Al calcular las relaciones entre estos valores, podemos medir cuantitativamente la **precisión de nuestras pruebas**.  

###### ***Tasa de falsos positivos (TFP)***

La **tasa de falsos positivos o TFP** es la probabilidad de que se produzca una ***falsa alarma***, es decir, que se dé un resultado positivo cuando el valor verdadero sea negativo. 

En el área de la salud: Imaginemos que *diagnostiquemos como enfermo a una persona sana*, está calro que ***no es un error muy grave (es una falsa alarma)***, porque un segundo diagnóstico, probablemente lo identifique como sano. 

TFP $=\frac{Falsos\_positivos}{Total\_negativos}=\frac{FP}{FP+VN}$ 
donde  
FP = **número de falsos positivos**
VN = **número de verdaderos negativos**
FP+VN=**número total de casos negativos**

![Tasa de falsos positivos][i029]

###### ***Tasa de falsos negativos (TFN o tasa de error)***

La **tasa de falsos negativos (TFN o tasa de error)**, es la ***probabilidad de que la prueba pase por alto un verdadero positivo***. 

En el área de la salud: Imaginemos que *diagnostiquemos como sano a una persona enferma*, está calro que ***es un error muy grave***, porque no habrá un segundo diagnóstico para una persona enferma. En el caso de una persona con cáncer, probablemente la condenemos a muerte. 

TFN $=\frac{Falsos\_negativos}{Total\_positivos}=\frac{FN}{FN+VP}$
donde  
FN = **número de falsos negativos**
VP = **número de verdaderos positivos**
FN+VP=**número total de casos positivos**  

![Tasa de falsos negativos][i032]

###### ***Tasa de verdadero positivos (TVP o sensibilidad)***

La **tasa de verdadero positivos (TVP) es la sensibilidad** y ***es la probabilidad de que un resultado positivo real dé positivo***. Dicho de otro modo, la **sensibilidad** de nuestro modelo.  

###### ***Tasa de verdaderos negativos (TVN o especificidad)***

La **tasa de verdaderos negativos (TVN) es la especificidad** y ***es la probabilidad de que un resultado negativo real dé un resultado negativo***. Dicho de otro modo, lo **específico** de nuestro modelo.  

  * El **valor predictivo positivo (VP+)** ***es la probabilidad de que, si ha obtenido un resultado positivo en la prueba, realmente sea cierto***.  
  VP+$=\frac{Positivos\_reales}{Total\_positivos\_en\_pruebas}=\frac{VP}{VP+FP}$
  En el área de la salud: La probabilidad de tener la enfermedad si el resultado de la prueba diagnóstica es positivo.

  * El **valor predictivo negativo (VP-)**, por el contrario ***es la probabilidad de que, si ha obtenido un resultado negativo en la prueba, en realidad sea falso***.  
  VP-$=\frac{Negativos\_reales}{Total\_negativos\_en\_pruebas}=\frac{VN}{VN+FN}$
  En el área de la salud: La probabilidad de no tener la enfermedad si el resultado de la prueba diagnóstica es negativo.
  
  * Los **valores predictivos (positivo y negativo)** miden la eficacia real de una prueba diagnóstica. Son probabilidades del resultado, es decir, dan la probabilidad de padecer o no una enfermedad una vez conocido el resultado de la prueba diagnóstica. Se trata de valores post-test y dependen de la prevalencia de una enfermedad, es decir, en el área de la salud, el porcentaje de una población que está afectada por esa determinada patología.

###### ***F1 Score***  

Esta es otra métrica muy empleada porque nos ***resume la precisión y sensibilidad en una sola métrica***. Por ello ***es de gran utilidad cuando la distribución de las clases es desigual***, lo que acostumbra a ser bastante común.  

bullshit

  $$
  \begin{align*}
  F1 Score &=\frac{2}{Precisión^{-1}+Sensibilidad^{-1}}\\  
    &=\frac{2·Precisión·Sensibilidad}{Precisión+Sensibilidad}\\
    &=\frac{2·(\frac{VP}{VP+FP}·\frac{VP}{VP+FN})}{\frac{VP}{VP+FP}+\frac{VP}{VP+FN}}\\
    &=\frac{2VP}{2VP+FP+FN}\\
  \end{align*}
  $$  

![F1 Score][i030]

##### ***Resumen***  
 
Podemos obtener cuatro casos posibles para cada **clase**:  

1. ***Alta precisión y alta sensibilidad***: El ***modelo*** de ML escogido ***maneja perfectamente esa **clase*****.  
2. ***Alta precisión y baja sensibilidad***: El ***modelo*** de ML escogido ***no detecta la **clase** muy bien, pero cuando lo hace es altamente confiable***.  
3. ***Baja precisión y alta sensibilidad***: El ***modelo*** de ML escogido ***detecta bien la **clase**, pero también incluye muestras de la otra **clase*****.  
4. ***Baja precisión y baja sensibilidad***: El ***modelo*** de ML escogido ***no logra clasificar la **clase** correctamente***.

Cuando tenemos un ***“dataset”  con desequilibrio, suele ocurrir que obtenemos un alto valor de **precisión** en la **clase** mayoritaria y un bajo **recall** en la **clase** minoritaria***.  Esta circunstancia es particularmente ****frecuente* y por ello tenemos que recurrir al **balanceo de clases*****.  

![Resumen de métricas][i031]

#### ***Consejos generales sobre la matriz de confusión y sus métricas***  

1) La **precisión** es un gran valor estadístico, pero *es útil únicamente cuando se tienen “datasets” simétricos* (la cantidad de casos de la clase 1 y de las clase 2 tienen magnitudes similares).

2) El **indicador F1 Score** de la **matriz de confusión** *es útil si se  tiene una distribución de clases desigual*, ***por ejemplo cuando el número de pacientes con una condición es del 15% y el otro es 85%, lo que en el campo de la salud es bastante común***.

3) Debemos elegir mayor **precisión** *para conocer qué tan seguro estamos de los verdaderos positivos*, mientras que la ***sensibilidad o  “Recall”** nos servirá para saber si no estamos perdiendo positivos*.  

4) Las **Falsas Alarmas**, como por ejemplo, *si creemos que es mejor en nuestro caso tener falsos positivos que falsos negativos, debemos utilizar una sensibilidad alta (Recall), cuando la aparición de falsos negativos nos resulta inaceptable pero no nos importa tener falsos positivos adicionales (falsas alarmas).*  
***Ejemplo***: ***Preferimos que algunas personas sanas sean etiquetadas como diabéticas en lugar de dejar a una persona diabética etiquetada como sana***.

5) Debemos elegir **precisión** *si queremos estar más seguros de nuestros verdaderos positivos, por ejemplo, correos electrónicos no deseados.*  
***Ejemplo***: ***Se prefiere tener algunos correos electrónicos “no deseados” en su bandeja de entrada en lugar de tener correos electrónicos “reales” en su bandeja de SPAM***.

6) Debemos elegir **alta Especificidad**, *si deseamos identificar los verdaderos negativos, o lo que es igual cuando no deseamos falsos positivos.*   
***Ejemplo***: ***Se está llevando a cabo una prueba de drogas en la que todas las personas que dan positivo irán a la cárcel de inmediato, la idea es que ninguna persona “libre de drogas” vaya a la cárcel***. Los falsos positivos aquí son intolerables.

> Fuente: [<span style="font-family:Verdana; font-size:0.95em;color:red">*La matriz de confusión y sus métricas*</span>][r014]

#### ***Balanceo de clases***

***Clases desbalanceadas en modelos de ML (Imbalanced data)***  

Cuando utilizamos modelos de ML para fines de **clasificación**, corremos el riesgo de encontrarnos con **clases desbalanceadas (imbalanced data)** . Por ejemplo cuando tenemos que etiquetar  «spam» o «no spam» ó entre múltiples categorías (Medicamento 1, 2 o 3) *es frecuente encontrar que en nuestro conjunto de datos de entrenamiento contamos con que alguna de las **clases** de la muestra es una **clase** «minoritaria» es decir, de la cual tenemos muy pocos casos*. Esto provoca un desbalanceo en los datos que utilizaremos para el entrenamiento de nuestra máquina. Además el problema es que al final de cuentas, *nuestro algoritmo será muy bueno detectando las **clases** mayoritarias, pero muy malo detctando las minoritarias, lo que nos puede acarrerar muchos errores tipo 1, (Falsos Positivos)*.  

Un caso muy evidente es en el área de Salud en donde solemos encontrar conjuntos de datos con miles de registros con pacientes «negativos» y unos pocos casos positivos es decir, que padecen la enfermedad que queremos clasificar.

Otros ejemplos suelen ser los de detección de fraude en las tarjetas de crédito, donde tenemos muchas muestras de clientes «honestos» y pocos casos etiquetados como fraudulentos.

***¿Cómo nos afectan las **Clases** desbalanceadas en modelos de Machine Learning?***  

Por lo general nos afecta en su proceso de “generalización de la información” (aplicar el conocimiento a casos nuevos) y perjudicando a las **clases** minoritarias. Esto suena bastante razonable: si a una red neuronal le damos 990 de fotos de gatitos y sólo 10 de perros, no podemos pretender que logre diferenciar una clase de otra. Lo más probable que la red se limite a responder siempre «tu foto es un gato» puesto que así tuvo un acierto del 99% en su fase de entrenamiento.  

***Estrategias para el manejo de **Clases**  Desbalanceadas***  

* ***Ajuste de Parámetros del modelo***  
Consiste en ajustar **parametros** ó **metricas** del propio algoritmo para intentar *equilibrar a la **clase** minoritaria, penalizando a la **clase** mayoritaria durante el entrenamiento.*  
Ejemplos: Ajuste de peso en **árboles**, también en **logistic regression** tenemos el **parámetro class_weight= «balanced»**.  

* ***Modificar el Dataset***  
Por ejemplo, podemos *eliminar muestras de la **clase** mayoritaria para reducirlo e intentar equilibrar la situación. Tiene de «peligroso» que podemos prescindir de muestras importantes, que brindan información y por lo tanto empeorar el modelo.* Entonces para seleccionar qué muestras eliminar, deberíamos seguir algún criterio. *También podríamos agregar nuevas filas con los mismos valores de las clases minoritarias.* Pero esto no sirve demasiado y *podemos llevar al modelo a caer en **overfitting**.*

* ***Muestras artificiales***  
Primero *podemos intentar crear muestras sintéticas (no idénticas) utilizando diversos algoritmos que intentan seguir la tendencia del grupo minoritario.* Según el método, podemos mejorar los resultados. *Lo peligroso de crear muestras sintéticas es que podemos alterar la distribución «natural» de esa **clase** y confundir al modelo en su clasificación.*

* ***Balanced Ensemble Methods***  
Utilizar las ventajas de hacer **ensamble de métodos**, es decir, *entrenar diversos modelos y entre todos obtener el resultado final (por ejemplo «votando»), pero se asegura de tomar muestras de entrenamiento equilibradas.*  

***Conclusiones***  

*Es muy frecuente encontrarnos ***clases desbalanceadas*** en modelos de ML, de hecho, lo más raro sería encontrar datasets bien equilibrados.*

Una pregunta frecuente es *«¿Que hacer cuando tengo pocas muestras de una **clase**?*». La primera respuesta y la de sentido común es *«Salir a la calle y conseguir más muestras!»* pero la realidad es que no siempre es posible conseguir más datos de las **clases** minoritarias (como por ejemplo en Casos de Salud).

Como resultado la **Matriz de Confusión** es un útil instrumento para medir si las métricas pueden ser engañosas. *Si miramos a nuestros aciertos únicamente, puede que pensemos que tenemos un buen clasificador, cuando realmente está fallando.*

> Fuente: [<span style="font-family:Verdana; font-size:0.95em;color:red">*Clases desbalanceadas en modelos de Machine Learning*</span>][r016] 

#### ***Hiperparámetros***

Los modelos de ML ya no son modelos lineales. Utilizan **“hiperparámetros”** para mejorar el rendimiento de los algoritmos, realizar selección de variables de entrada (regularización), evitar el **sobreajuste** y optimizar el procesamiento.  

Los **hiperparámetros** no están en los datos de entrenamiento y no se conocen a priori. Una mejor selección de sus valores se hace mediante un proceso de ajuste de parámetros o tuning en función de resultados de validación.  

Los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** son flujogramas que mapean las posibles salidas del objetivo que buscamos en función de una serie de elecciones o datos de entrada relacionados.  

Por lo general, un ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]*** comienza con un solo **nodo** o **nodo raíz**, que se ramifica según preguntas que nos hacemos sobre los atributos de entrada (**nodos internos**). El ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r000]*** se va formando de acuerdo a los resultados de dichas preguntas hasta los **últimos nodos (hojas)** que son los que incluyen la **clasificación**, etiqueta o número buscado.  

Es un algoritmo **supervisado** y los principales **hiperparámetros** de este tipo de modelo son:
1. **La profundidad máxima del ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r000]*****: El número de saltos, cortes o test sobre atributos.
2. **El mínimo número de muestras por hoja** o nodo final

Los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** son fáciles de construir y de interpretar y de escalar sin embargo, son bastante inexactos, funcionan bien con los valores con los que se han entrenado pero no tanto con nuevos valores (alta varianza).  

> Fuente: [<span style="font-family:Verdana; font-size:0.95em;color:red">*El superpoder de los hiperparámetros*</span>][r017]

## ¿Cómo funcionan los árboles de decisión?

Los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** son un tipo de modelo de **aprendizaje supervisado** que se utilizan para **clasificar o predecir valores numéricos**. Toman un conjunto de datos de entrada, lo dividen en subconjuntos basados en diferentes atributos y, finalmente, hacen una predicción sobre el valor de salida.

Por ejemplo, consideremos el siguiente conjunto de datos que describe varios productos que se venden en una tienda en línea:  

|Producto | Precio | Descuento | En Oferta |
| ------- | -----: | --------: | --------- |  
| A | 10 | 0.05 | Sí |
| B | 20 | 0.10 | No |
| C | 30 | 0.20 | Sí |
| D | 15 | 0.15 | Sí |
| E | 25 | 0.10 | No |

En este caso, queremos construir un ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]*** que nos permita **predecir si un producto estará en oferta o no, en función de sus características**.

Comenzamos por construir el **nodo raíz**, que representa el conjunto completo de datos. A continuación, seleccionamos un atributo para dividir el conjunto de datos. En este caso, podríamos elegir el atributo **"Precio"** como nuestra primera división.

Supongamos que elegimos un umbral de 20€ para el precio, lo que significa que cualquier producto con un precio mayor a 20€ se considerará "caro" y cualquier producto con un precio menor o igual a 20€ se considerará "barato". La primera división del ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r000]*** quedaría así:

````
                     Precio <= 20
                    /            \
         Sí (Producto Barato)  No (Producto Caro) 
````

El ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]*** tiene dos ramas: una **rama** para los productos baratos y otra para los productos caros. La **rama** para los productos baratos conduce a un **nodo hoja** que indica que el producto A está en oferta. La **rama** para los productos caros conduce a otro **nodo de decisión**, que utiliza el descuento para decidir si el producto está en oferta o no.

Supongamos que elegimos un umbral de descuento del 15%. Entonces, el ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]*** completo quedaría así:

````
                     Precio <= 20
                    /            \
         Sí (Producto Barato)  No (Producto Caro) 
                  /                       \
      (Descuento <= 3%)              (Descuento <= 15%)
      /            \                  /                \
Sí (Sin oferta)  No (En oferta)    Sí (Sin oferta)  No (En oferta) 
```` 
Este ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r000]*** nos permite predecir si un producto está en oferta o no, en función de su precio y de su descuento.

### ***Ventajas***

* **Algoritmo de caja blanca**: los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** son considerados algoritmos de **caja blanca**, lo que significa que son modelos fácilmente interpretables y comprensibles por los humanos.

* **Resultados fáciles de interpretar y entender**: los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** son modelos fáciles de interpretar y entender, ya que cada paso en el proceso de toma de decisiones se representa explícitamente. Esto permite que los expertos del dominio puedan validar el modelo y dar sugerencias para mejorarlo.

* **Las combinaciones de los mismos pueden dar resultados muy certeros**: los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** individuales pueden ser limitados en términos de precisión de predicción. Sin embargo, una técnica que se utiliza para mejorar la precisión de los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** es la combinación de varios ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles</span>][r000]*** en un conjunto, como en el caso de **Random Forest**. Esto se conoce como **ensamblaje de modelos** y puede proporcionar una mayor precisión en las predicciones.

### ***Desventajas***

* **Tendencia al overfitting**: Los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** tienen una tendencia natural al **overfitting**, lo que significa que pueden ajustarse demasiado a los datos de entrenamiento y no generalizar bien para nuevos datos. Esto se puede prevenir mediante técnicas de **poda** o regularización.

* **Influencia de los outliers**: Los **outliers** pueden tener una influencia significativa en la creación de los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]***, ya que pueden **sesgar** la partición de los datos. Una solución a esto es utilizar técnicas de preprocesamiento de datos para tratar con los **outliers** antes de crear el ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r000]***.

* *****[<span style="font-family:Verdana; font-size:0.95em;color:red">Árboles</span>][r000]*** demasiado complejos pueden no adaptarse bien a los nuevos datos**: Si se crean ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** demasiado complejos, pueden adaptarse demasiado a los datos de entrenamiento y no generalizar bien para nuevos datos. Esto se puede prevenir mediante técnicas de **pruning** o regularización para simplificar el ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r000]***.

* **Posibilidad de crear ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles</span>][r000]*** sesgados si una clase es más numerosa**: si una **clase** es significativamente más numerosa que las demás **clases**, el ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol de decisión</span>][r000]*** puede estar sesgado hacia esa **clase** mayoritaria y no prestar suficiente atención a las otras **clases**. Esto se puede prevenir mediante técnicas de **balanceo de clases**, como el muestreo estratificado o el aumento de datos.

### ***¿Cuándo usar árboles de decisión?***  

* **Sencillo y fácil de entender**: Los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** son una técnica sencilla y fácil de interpretar. Por lo tanto, ***es recomendable utilizarlos cuando se busca una solución clara y fácil de entender***. Además, la estructura de ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árbol</span>][r000]*** es intuitiva y fácil de visualizar, lo que hace que el proceso de toma de decisiones sea más fácil de entender.

* **Funcionan bastante bien con grandes conjuntos de datos**: Los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** pueden funcionar muy bien con grandes conjuntos de datos. ***A medida que el tamaño del conjunto de datos aumenta, los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** se vuelven más útiles***, ya que pueden segmentar el conjunto de datos en grupos más pequeños y más manejables para un análisis más profundo.

* **Relativamente robusto**: Los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** son relativamente robustos y ***pueden manejar datos faltantes o ruidosos***. Además, ***son útiles en situaciones en las que se necesitan resultados precisos con una alta tasa de precisión***.

* **Método útil para analizar datos cuantitativos**: Los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** son particularmente útiles para analizar datos cuantitativos. Por ejemplo, en el análisis de negocios, los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** ***pueden ayudar a identificar patrones en grandes conjuntos de datos y hacer recomendaciones basadas en esa información***.

* **Aplicable para clasificación y regresión**: los ***[<span style="font-family:Verdana; font-size:0.95em;color:red">árboles de decisión</span>][r000]*** se pueden utilizar para problemas de **clasificación** y **regresión**. ***En problemas de **clasificación**, se utiliza para asignar una etiqueta a un objeto***, mientras que ***en problemas de **regresión**, se utiliza para predecir una variable continua***.  

## Listado de referencias externas

* Árboles de decisión (Wikipedia)  

[r000]: https://es.wikipedia.org/wiki/%C3%81rbol_de_decisi%C3%B3n "referencia a árboles de decisión en Wikipedia"

* Machine Learning (Wikipedia)  

[r001]: https://es.wikipedia.org/wiki/Aprendizaje_autom%C3%A1tico "referencia a Machine Learning en Wikipedia"

* Aprendizaje supervisado (Wikipedia) 

[r002]: https://es.wikipedia.org/wiki/Aprendizaje_supervisado "referencia a Aprendizaje supervisado en Wikipedia"

* Leo Breiman (Wikipedia)  

[r003]: https://es.wikipedia.org/wiki/Leo_Breiman "referencia a Leo Breiman en Wikipedia"

* Decision Trees y Random Forest con Python y scikit-learn  (Carlos Mazzaroli)  

[r004]: https://deepnote.com/app/mazzaroli/Decision-Trees-y-Random-Forest-con-Python-y-scikit-learn-22e03409-93bd-4c7e-9ade-f94470cd6941 "referencia a Decision Trees y Random Forest con Python y scikit-learn  (Carlos Mazzaroli)"

* Clasificación estadística (Wikipedia)  

[r005]: https://es.wikipedia.org/wiki/Clasificaci%C3%B3n_estad%C3%ADstica "referencia a Clasificación estadística en Wikipedia"

* Análisis de la regresión (Wikipedia)  

[r006]: https://es.wikipedia.org/wiki/An%C3%A1lisis_de_la_regresi%C3%B3n "referencia a Análisis de la regresión en Wikipedia"

* Entropía (información) (Wikipedia)  

[r007]: https://es.wikipedia.org/wiki/Entrop%C3%ADa_(informaci%C3%B3n) "referencia a Entropía (información) en Wikipedia"

* ID3 (IBM)  

[r008]: https://www.ibm.com/es-es/topics/decision-trees "referencia a ID3 en IBM"  

* Ross Quinlan (Wikipedia)  

[r009]: https://es.wikipedia.org/wiki/Ross_Quinlan "referencia a Ross Quinlan en Wikipedia"

* C4.5 (IBM)  

[r010]: https://www.ibm.com/es-es/topics/decision-trees "referencia a C4.5 en IBM"  

* Guía completa sobre algoritmos de árboles de decisión en España  

[r011]: https://prompt.uno/aprendizaje-automatico/algoritmos-de-arboles-de-decision/ "referencia a Guía completa sobre algoritmos de árboles de decisión en España"
 
* Cómo elegir el mejor atributo en cada nodo (IBM)  

[r012]: https://es.wikipedia.org/wiki/Entrop%C3%ADa_(informaci%C3%B3n) "referencia a Cómo elegir el mejor atributo en cada nodo en IBM"

* Tipos de árboles de decisión (IBM)  

[r013]: https://es.wikipedia.org/wiki/Entrop%C3%ADa_(informaci%C3%B3n) "referencia a Tipos de árboles de decisión en IBM"
 
* La matriz de confusión y sus métricas  

[r014]: https://www.juanbarrios.com/la-matriz-de-confusion-y-sus-metricas/ "referencia a La matriz de confusión y sus métricas"

* Clasificación con Árboles de Decisión: el algoritmo CART  

[r015]: https://www.codificandobits.com/blog/clasificacion-arboles-decision-algoritmo-cart/ "referencia a Clasificación con Árboles de Decisión: el algoritmo CART"

* Clases desbalanceadas en modelos de Machine Learning  

[r016]: https://www.juanbarrios.com/clases-desbalanceadas/ "referencia a Clases desbalanceadas en modelos de Machine Learning"

* El superpoder de los hiperparámetros  

[r017]: https://impulsatek.com/8-el-superpoder-de-los-hiperparametros/ "referencia a El superpoder de los hiperparámetros"

* Índice (o impureza) de Gini (Wikipedia)  

[r018]: https://es.wikipedia.org/wiki/Aprendizaje_basado_en_%C3%A1rboles_de_decisi%C3%B3n#Impureza_de_Gini "referencia a Índice (o impureza) de Gini en Wikipedia"

## Listado de imágenes

* Leo Breiman  

[i000]: https://i.imgur.com/SszQ8rp.jpg "Leo Breiman"

* Aprendizaje supervisado  

[i001]: https://i.imgur.com/oOJqpy5.png "Aprendizaje supervisado" 

* Regresión vs clasificación 001  

[i002]: https://i.imgur.com/XlIxQhK.png "Regresión vs clasificación 001"

* Regresión vs clasificación 002  

[i003]: https://i.imgur.com/q1aJfN2.png "Regresión vs clasificación 002"

* Regresión vs clasificación 003  

[i004]: https://i.imgur.com/lIWGXgj.png "Regresión vs clasificación 003"

* Nodo  

[i005]: https://i.imgur.com/FjY24Nw.png "Nodo"  

* Nodo raíz  

[i006]: https://i.imgur.com/OUJejNh.png "Nodo raíz"  

* Rama  

[i007]: https://i.imgur.com/pUoPeUR.png "Rama"  

* Nodo de decisión  

[i008]: https://i.imgur.com/LVqwGAy.png "Nodo de decisión"  

* División  

[i009]: https://i.imgur.com/5fslA9D.png "División"  

* Nodo padre  

[i010]: https://i.imgur.com/WUGhyKD.png "Nodo padre"  

* Nodo hijo  

[i011]: https://i.imgur.com/aadGRYk.png "Nodo hijo"  

* Nodo hoja  

[i012]: https://i.imgur.com/Ps9f7Z8.png "Nodo hoja"  

* Overfitting  

[i013]: https://i.imgur.com/sMamasP.png "Overfitting" 

* Pruning  

[i014]: https://i.imgur.com/yKRally.png "Pruning" 

* Vectores  

[i015]: https://i.imgur.com/GxPsEFi.png "Vectores" 

* Flechas  

[i016]: https://i.imgur.com/BXdrEvn.png "Flechas" 

* Etiquetas  

[i017]: https://i.imgur.com/W3VVLyT.png "Etiquetas" 

* Clase  

[i018]: https://i.imgur.com/pKoyDIW.png "Clase" 

* Validación cruzada  

[i019]: https://i.imgur.com/42FaO1M.png "Validación cruzada" 

* Outliers  

[i020]: https://i.imgur.com/kQmu8fm.png "Outliers" 

* Entropía de la información  

[i021]: https://i.imgur.com/hUiUKay.png "Entropía de la información" 

* Ejemplo estudiantes  

[i022]: https://i.imgur.com/AwM84vI.png "Ejemplo estudiantes"

* Entropía, Mínimo error e Índice Gini  

[i023]: https://i.imgur.com/n1az3GF.png "Entropía, Mínimo error e Índice Gini"

* Matriz de confusión  

[i024]: https://i.imgur.com/a8Vl1dF.png "Matriz de confusión"

* Accuracy  

[i025]: https://i.imgur.com/rJ5d6rF.png "Accuracy"

* Precision  

[i026]: https://i.imgur.com/Ev3aWMB.png "Precision"

* Recall  

[i027]: https://i.imgur.com/ZX1ZMw7.png "Recall"

* Especificity  

[i028]: https://i.imgur.com/N9RdMWG.png "Especificity"

* Tasa de falsos positivos  

[i029]: https://i.imgur.com/keI2Lxg.png "Tasa de falsos positivos"

* F1 Score  

[i030]: https://i.imgur.com/erPJC6p.png "F1 Score"

* Resumen de métricas  

[i031]: https://i.imgur.com/XUqvrdJ.jpg "Resumen de métricas"

* Tasa de falsos negativos  

[i032]: https://i.imgur.com/5otAfdi.png "Tasa de falsos negativos"

* Métricas de la matriz de confusión  

[i033]: https://i.imgur.com/P6fZOdY.png "Métricas de la matriz de confusión"




