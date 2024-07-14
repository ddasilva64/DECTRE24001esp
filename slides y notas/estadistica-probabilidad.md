# Notas de Estadística y Probabilidad

<details>

<summary>Índice de contenidos</summary>

* ***Promedio***
* ***Mediana***
* ***Moda***
* ***Sesgo***
* **Rango**
* ***Análisis estadístico (para EDA)***
* ***Desviación estándar***
* ***Varianza***  

</details>

## Promedio

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Promedio</span>][r000]***: Se refiere a la media aritmética, la suma de los números dividida por cuántos números se promedian. ***Tiene el inconveniente de que es muy susceptible a los valores atípicos (outliers)***.  

![Promedio][i000] 

## Mediana

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Mediana</span>][r001]***: En el ámbito de la estadística, representa el valor de la variable de posición central en un conjunto de datos ordenados.  

![Mediana][i001] 

## Moda

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Moda</span>][r002]***: En estadística, es el valor que aparece con mayor frecuencia en un conjunto de datos. ***Solo es aplicable a variables discretas (no contínuas)***.  

![Moda][i002] 

## Sesgo

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Sesgo</span>][r003]***: En Estadística se llama sesgo de un estimador a la diferencia entre su esperanza matemática y el valor numérico del parámetro que estima. Un estimador cuyo sesgo es nulo se llama insesgado o centrado.  

* ***Distribución no sesgada*** => ***media = mediana = moda*** (distribución bayesiana).  
* ***Distribución sesgada hacia la izquierda*** => ***moda < mediana < media***.  
* ***Distribución sesgada hacia la derecha*** => ***moda > mediana > media***. 

![Sesgo][i003]  

## Rango

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Rango</span>][r004]***: El Rango es la diferencia numérica entre el valor máximo y el valor mínimo. ***Permite obtener una idea de la dispersión de los datos***.  


## Análisis estadístico (para EDA)  

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Análisis univariado</span>][r005]***: El análisis univariante implica describir la distribución de una sola variable. La forma de la distribución de los datos también se puede describir mediante índices como la ***asimetría*** y la ***curtosis***. Las características de la distribución de una variable también se pueden representar en forma de ***histogramas, diagramas de caja, gráficos de barras y estadísticas resumidas como la media, la mediana y la moda***.

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Análisis bivariado</span>][r006]***: Implica analizar la relación entre dos variables. Ayuda a comprender cómo cambia una variable con respecto a otra variable. Las técnicas más comunes incluyen ***diagramas de dispersión, análisis de correlación y tabulación cruzada***.

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Análisis multivariado</span>][r007]***: Implica analizar más de dos variables simultáneamente. Ayuda a comprender las relaciones e interacciones entre múltiples variables. Las técnicas más comunes incluyen ***análisis de componentes principales, análisis factorial y análisis de conglomerados***.

Los analistas de datos y los científicos obtienen:
* ***Información sobre los datos***
* ***Identificación de patrones***
* ***Relaciones entre los datos***
* ***Valores atípicos (outliers)***
* ***Razones para tomar decisiones informadas***

## Desviación estándar  

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Desviación estándar</span>][r008]***: La desviación estándar mide la ***dispersión de los datos respecto a la media***. Se trata de la ***raíz cuadrada de la varianza***, que en sí misma no es una medida de dispersión.

![Desviación estándar][i008]  

## Varianza

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Varianza</span>][r009]***: Retorna la varianza muestral, que debe ser un iterable de al menos dos números reales. La varianza, o momento de segundo orden respecto a la media, es una ***medida de la variabilidad (difusión o dispersión) de los datos***.  

Una ***alta varianza indica que los datos están dispersos***; una ***baja varianza indica que los datos están agrupados estrechamente alrededor de la media***.  

![Varianza][i009]  

En la imagen se muestra un ejemplo de muestras de dos poblaciones con la misma media pero varianzas diferentes. La población roja tiene media 100 y varianza 100 (desviación estándar=10) mientras que la población azul tiene media 100 y varianza 2500 (desviación estándar=50).

## Cuartil 1 (percentil 25)

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Cuartil 1</span>][r010]***: El concepto es igual al de mediana, salvo que aquí la división ya no es en el 50%. El 25% de las observaciones es menor que el primer cuartil.

![Cuartil 1][i010]  

## Cuartil 2 (percentil 50)

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Cuartil 2</span>][r011]***: El concepto es igual al de mediana, aquí la división es en el 50%. El 50% de las observaciones es menor que el segundo cuartil.

![Cuartil 2][i011]  

## Cuartil 3 (percentil 75)

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Cuartil 3</span>][r012]***: El concepto es igual al de mediana, salvo que aquí la división ya no es en el 50%. El 75% de las observaciones es menor que el tercer cuartil

![Cuartil 3][i012]  

## Rango intercuartílico

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Rango intercuartílico</span>][r013]***: El rango intercuartílico o IQR es la diferencia entre el tercer y el primer cuartil. Es una medida de la dispersión estadística. ***Es una medida de variabilidad adecuada cuando la medida de posición central empleada ha sido la mediana***.  

    Se define como la diferencia entre el tercer cuartil (Q3) y el primer cuartil (Q1), es decir: RQ = Q3 - Q1. A la mitad del rango intercuartílico se le conoce como desviación cuartil (DQ), es afectada muy poco por cuentas extremas. Esto lo hace una ***buena medida de dispersión para distribuciones sesgadas***: DQ = RQ/2= (Q3 - Q1)/2.

    Se usa para construir los ***diagramas de caja y bigote*** (box plots) que sirven para visualizar la variabilidad de una variable y comparar distribuciones de la misma variable; además de ***ubicar valores extremos***.  

    ![Rango intercuartílico][i013]  

## Límite superior outliers

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Límite superior outliers</span>][r014]***: Son los puntos a la derecha de los bigotes de la caja Q3 + 1.5 x IQR.

![Límite superior outlier][i014] 

## Límite inferior outliers

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Límite inferior outliers</span>][r015]***: Son los puntos a la izquierda de los bigotes de la caja Q1 - 1.5 x IQR.

![Límite inferior outliers][i015] 

## Listado de referencias externas

* Promedio (Wikipedia)  

[r000]: https://es.wikipedia.org/wiki/Promedio "referencia a promedio en Wikipedia"

* Mediana (Wikipedia)  

[r001]: https://es.wikipedia.org/wiki/Mediana_(estad%C3%ADstica) "referencia a mediana en Wikipedia"

* Moda (Wikipedia)  

[r002]: https://es.wikipedia.org/wiki/Moda_(estad%C3%ADstica) "referencia a moda en Wikipedia"

* Sesgo (Wikipedia)  

[r003]: https://es.wikipedia.org/wiki/Sesgo_estad%C3%ADstico "referencia a sesgo en Wikipedia"

* Rango (Wikipedia)  

[r004]: https://es.wikipedia.org/wiki/Rango_(estad%C3%ADstica) "referencia a rango en Wikipedia"

* Análisis univariado (Wikipedia)  

[r005]: https://es.wikipedia.org/wiki/Estad%C3%ADstica_descriptiva#An%C3%A1lisis_univariante "referencia a análisis univariado en Wikipedia"

* Análisis bivariado (Wikipedia)  

[r006]: https://es.wikipedia.org/wiki/Estad%C3%ADstica_descriptiva#An%C3%A1lisis_bivariante_y_multivariante "referencia a análisis bivariado en Wikipedia"

* Análisis multivariado (Wikipedia)  

[r007]: https://es.wikipedia.org/wiki/Estad%C3%ADstica_descriptiva#An%C3%A1lisis_bivariante_y_multivariante "referencia a análisis multivariado en Wikipedia"

* Desviación estándar (Wikipedia)  

[r008]: https://es.wikipedia.org/wiki/Desviaci%C3%B3n_t%C3%ADpica "referencia a desviación estándar en Wikipedia"

* Varianza (Wikipedia)  

[r009]: https://es.wikipedia.org/wiki/Varianza "referencia a varianza en Wikipedia"

* Cuartil 1 (Wikipedia)   

[r010]: https://es.wikipedia.org/wiki/Percentil "referencia a cuartil 1 en Wikipedia"

* Cuartil 2 (Wikipedia)   

[r011]: https://es.wikipedia.org/wiki/Percentil "referencia a cuartil 2 en Wikipedia"

* Cuartil 3 (Wikipedia)   

[r012]: https://es.wikipedia.org/wiki/Percentil "referencia a cuartil 3 en Wikipedia"

* Rango intercuartílico (Wikipedia)   

[r013]: https://es.wikipedia.org/wiki/Rango_intercuart%C3%ADlico "referencia a rango intercuartílico en Wikipedia"

* Límite superior outliers (Wikipedia)   

[r014]: https://es.wikipedia.org/wiki/Valor_at%C3%ADpico#Valor_at%C3%ADpico_extremo "referencia a límite superior outliers en Wikipedia"

* Límite inferior outliers (Wikipedia)   

[r015]: https://es.wikipedia.org/wiki/Valor_at%C3%ADpico#Valor_at%C3%ADpico_extremo "referencia a límite inferior outliers en Wikipedia"

## Listado de imágenes

* Promedio  

[i000]: https://i.imgur.com/xA8EIFr.png "Promedio"

* Mediana  

[i001]: https://i.imgur.com/3QaFjUZ.png "Mediana"

* Moda  

[i002]: https://i.imgur.com/sq8tQ8H.png "Moda"

* Sesgo  

[i003]: https://i.imgur.com/ObehJLM.png "Sesgo"

* Desviación estándar  

[i008]: https://i.imgur.com/34s7Flh.png "Desviación estándar"

* Varianza  

[i009]: https://i.imgur.com/PnRDpZU.png "Varianza"

* Cuartil 1 (percentil 25)  

[i010]: https://i.imgur.com/jXR2Wlw.png "Cuartil 1 (percentil 25)"

* Cuartil 2 (percentil 50)  

[i011]: https://i.imgur.com/n64wNxa.png "Cuartil 2 (percentil 50)"

* Cuartil 3 (percentil 75)  

[i012]: https://i.imgur.com/08Pt7BD.png "Cuartil 3 (percentil 75)"

* Rango intercuartílico  

[i013]: https://i.imgur.com/AeddtFp.jpg "Rango intercuartílico"

* Límite superior outliers  

[i014]: https://i.imgur.com/RM6RVH6.jpg "Límite superior outliers"

* Límite inferior outliers  

[i015]: https://i.imgur.com/pEbuiPP.png "Límite inferior outliers"