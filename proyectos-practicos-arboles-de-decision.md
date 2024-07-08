# Proyecto práctico: árbol de decisión 

* **Dataset**: [A Titanic Probability->Titanic Dataset, Standford University](https://web.stanford.edu/class/archive/cs/cs109/cs109.1166/problem12.html)   

  El archivo titanic.csv contiene datos de 887 de los pasajeros reales del Titanic. Cada fila representa una persona. Las columnas describen diferentes atributos sobre la persona, incluido si sobrevivió (S), su edad (A), su clase de pasajero (C), su sexo (G) y la tarifa que pagó (X).

## Análisis exploratorio de datos para obtener el árbol de decisión  

***Atributos***  

El conjunto de datos Titanic de CS109 contiene 887 filas y 8 columnas.

1) ***Survived*** (superviviente): 0 = No, 1 = Sí
2) ***Pclass*** (clase pasaje): 1 = 1ª clase, 2 = 2ª clase, 3 = 3ª clase
3) ***Name*** (nombre): Nombre completo.
4) ***Sex*** (género): Masculino o femenino.
5) ***Age*** (edad): Edad en años.
6) ***Siblings/Spouses Aboard*** (hermanos/cónyuges a bordo): Número de hermanos/cónyuges del pasajero que también estaban a bordo del Titanic.
7) ***Parents/Children Aboard*** (padres/hijos a bordo): Número de padres/hijos del pasajero que también estaban a bordo del Titanic.
8) ***Fare*** (tarifa): la tarifa pagada por el pasajero por su viaje en el Titanic.

***Columnas eliminadas***

Eliminación de columnas, que en el contexto de un análisis específico de la supervivencia de los pasajeros del Titanic, no son relevantes:
1) ***Fare***, que es equivalente a ***Pclass***.
2) ***Name***.

## Árbol de decisión *(solución propuesta en el curso, con ganania de la información)*

### Dataset

````Python
#Importación de librerias principales
import pandas as pd
import matplotlib.pyplot as plt

#Carga del dataset
titanic = pd.read_csv('https://web.stanford.edu/class/archive/cs/cs109/cs109.1166/stuff/titanic.csv', sep=',')
````
### Análisis exploratorio de datos
````Python
#Visualización del DataFrame
titanic.head(10)
````
|index|Survived|Pclass|Name|Sex|Age|Siblings/Spouses Aboard|Parents/Children Aboard|Fare|
|---|---|---|---|---|---|---|---|---|
|0|0|3|Mr\. Owen Harris Braund|male|22\.0|1|0|7\.25|
|1|1|1|Mrs\. John Bradley \(Florence Briggs Thayer\) Cumings|female|38\.0|1|0|71\.2833|
|2|1|3|Miss\. Laina Heikkinen|female|26\.0|0|0|7\.925|
|3|1|1|Mrs\. Jacques Heath \(Lily May Peel\) Futrelle|female|35\.0|1|0|53\.1|
|4|0|3|Mr\. William Henry Allen|male|35\.0|0|0|8\.05|
|5|0|3|Mr\. James Moran|male|27\.0|0|0|8\.4583|
|6|0|1|Mr\. Timothy J McCarthy|male|54\.0|0|0|51\.8625|
|7|0|3|Master\. Gosta Leonard Palsson|male|2\.0|3|1|21\.075|
|8|1|3|Mrs\. Oscar W \(Elisabeth Vilhelmina Berg\) Johnson|female|27\.0|0|2|11\.1333|
|9|1|2|Mrs\. Nicholas \(Adele Achem\) Nasser|female|14\.0|1|0|30\.0708|

````Python
#Eliminación de columnas que no interesan
columns_to_drop = ['Name', 'Fare']
titanic.drop(columns_to_drop, axis = "columns", inplace = True)

#Renombrado de columnas
titanic.columns = ['Survived', 'Pclass', 'Sex', 'Age', 'SibSp', 'Parch']
titanic.head()
````
|index|Survived|Pclass|Sex|Age|SibSp|Parch|
|---|---|---|---|---|---|---|
|0|0|3|male|22\.0|1|0|
|1|1|1|female|38\.0|1|0|
|2|1|3|female|26\.0|0|0|
|3|1|1|female|35\.0|1|0|
|4|0|3|male|35\.0|0|0|

````Python
#Análisis del shape del objeto
print(titanic.shape)
````
(887, 6)

````Python
#Visualización de los tipos de datos
titanic.dtypes
````
|        |      |
| -----: | ---: |
| Survived | int64 | 
| Pclass | int64 | 
| Sex | object | 
| Age | float64 | 
| SibSp | int64 | 
| Parch | int64 | 
dtype: object

````Python
#Cambio de los tipos de datos
titanic = pd.get_dummies(titanic, columns = ["Sex"], drop_first = True)
titanic.dtypes
````
|        |      |
| -----: | ---: |
| Survived | int64 | 
| Pclass | int64 |
| Age | float64 |
| SibSp | int64 |
| Parch | int64 |
| Sex_male | uint8 |
dtype: object

````Python
titanic.head()
````
|index|Survived|Pclass|Age|SibSp|Parch|Sex\_male|
|---|---|---|---|---|---|---|
|0|0|3|22\.0|1|0|true|
|1|1|1|38\.0|1|0|false|
|2|1|3|26\.0|0|0|false|
|3|1|1|35\.0|1|0|false|
|4|0|3|35\.0|0|0|true|

````Python
#Reemplazar el DataFrame
titanic.rename(columns = {'Sex_male': 'Sex'}, inplace = True)

#Ordenación de columnas por nombres
titanic = titanic[['Survived','Pclass', 'Sex',  'Age', 'SibSp', 'Parch']]
titanic.head()
````
|index|Survived|Pclass|Sex|Age|SibSp|Parch|
|---|---|---|---|---|---|---|
|0|0|3|true|22\.0|1|0|
|1|1|1|false|38\.0|1|0|
|2|1|3|false|26\.0|0|0|
|3|1|1|false|35\.0|1|0|
|4|0|3|true|35\.0|0|0|

### Entrenamiento del modelo de clasificación

````Python
#Separación en X e y
X = titanic.drop("Survived", axis = 1)
y = titanic.Survived
#Importación de las librerias necesarias para la creación del modelo
from sklearn.model_selection import train_test_split

#30% para test y 70% para train
X_train, X_test, y_train, y_test =  train_test_split(X, y, test_size = 0.30, random_state = 00000)

#Árbol de Decisión
from sklearn.tree import DecisionTreeClassifier

#Creación del modelo
tree = DecisionTreeClassifier(max_depth=2, random_state = 00000)

#Entrenamiento
tree.fit(X_train,y_train)

````

DecisionTreeClassifier(max_depth=2, random_state=0)

### Evaluación del modelo

````Python
#Cálculo de las predicciones en Train(ing) y Test
y_train_pred = tree.predict(X_train)
y_test_pred = tree.predict(X_test)

#Cálculo de metricas 
from sklearn.metrics import accuracy_score

#Cálculo del accuracy en Train
train_accuracy = accuracy_score(y_train,y_train_pred)

#Cálculo del accuracy en Test
test_accuracy = accuracy_score(y_test,y_test_pred)

print('El accuracy en train(ing) es:', train_accuracy)
print('El accuracy en test es:', test_accuracy)
````
El accuracy en train(ing) es: 0.8048387096774193  
El accuracy en test es: 0.7640449438202247

````Python
#Verificación del feature importances
import seaborn as sns

importances = tree.feature_importances_
columns = X.columns
sns.barplot(x=columns,y=importances, palette = 'bright', saturation = 2.0, edgecolor = 'black', linewidth = 2)
plt.title('Importancia de cada Feature')
plt.show()
````
![primer_proyecto](https://i.imgur.com/JVD7oXJ.png)  
***Resultado primer proyecto*** 

## Árbol de decisión *(solución de Carlos Mazzaroli, con ganancia, impureza de Gini y entropía de la información)*

### Dataset
````Python
# Importación de librerias
import numpy              as np
import pandas             as pd
import matplotlib.pyplot  as plt 
import seaborn            as sns
from sklearn.model_selection import train_test_split    # necesarias para la creación del modelo

# Carga del dataset
titanic = pd.read_csv('https://web.stanford.edu/class/archive/cs/cs109/cs109.1166/stuff/titanic.csv', sep=',')
````
### Análisis exploratorio de datos
````Python
# Visualización del DataFrame
titanic.head(10)

````
|index|Survived|Pclass|Name|Sex|Age|Siblings/Spouses Aboard|Parents/Children Aboard|Fare|
|---|---|---|---|---|---|---|---|---|
|0|0|3|Mr\. Owen Harris Braund|male|22\.0|1|0|7\.25|
|1|1|1|Mrs\. John Bradley \(Florence Briggs Thayer\) Cumings|female|38\.0|1|0|71\.2833|
|2|1|3|Miss\. Laina Heikkinen|female|26\.0|0|0|7\.925|
|3|1|1|Mrs\. Jacques Heath \(Lily May Peel\) Futrelle|female|35\.0|1|0|53\.1|
|4|0|3|Mr\. William Henry Allen|male|35\.0|0|0|8\.05|
|5|0|3|Mr\. James Moran|male|27\.0|0|0|8\.4583|
|6|0|1|Mr\. Timothy J McCarthy|male|54\.0|0|0|51\.8625|
|7|0|3|Master\. Gosta Leonard Palsson|male|2\.0|3|1|21\.075|
|8|1|3|Mrs\. Oscar W \(Elisabeth Vilhelmina Berg\) Johnson|female|27\.0|0|2|11\.1333|
|9|1|2|Mrs\. Nicholas \(Adele Achem\) Nasser|female|14\.0|1|0|30\.0708|

````Python
# Eliminación de columnas que no interesan
columns_to_drop = ['Name', 'Fare']
titanic.drop(columns_to_drop, axis = "columns", inplace = True)

# Renombrado de columnas
titanic.columns = ['Survived', 'Pclass', 'Sex', 'Age', 'SibSp', 'Parch']
titanic.head()
````
|index|Survived|Pclass|Sex|Age|SibSp|Parch|
|---|---|---|---|---|---|---|
|0|0|3|male|22\.0|1|0|
|1|1|1|female|38\.0|1|0|
|2|1|3|female|26\.0|0|0|
|3|1|1|female|35\.0|1|0|
|4|0|3|male|35\.0|0|0| 

````Python
# Análisis del shape del objeto 
print(titanic.shape)
````
(887, 6)

````Python
# Visualización de tipos de datos
titanic.dtypes
````

|        |      |
| -----: | ---: |
| Survived | int64 | 
| Pclass | int64 | 
| Sex | object | 
| Age | float64 | 
| SibSp | int64 | 
| Parch | int64 | 
dtype: object

````Python
titanic.info()
````
<class 'pandas.core.frame.DataFrame'>  
RangeIndex: 887 entries, 0 to 886  
Data columns (total 6 columns):  
| #   | Column | Non-Null Count | Dtype |  
| :-: | :----- | :------------- | :---- |
| 0 | Survived | 887 non-null | int64 | 
| 1 | Pclass | 887 non-null | int64 | 
| 2 | Sex | 887 non-null | object | 
| 3 | Age | 887 non-null | float64 | 
| 4 | SibSp | 887 non-null | int64 | 
| 5 | ParCh | 887 non-null | int64 | 
dtypes: float64(1), int64(4), object(1)
memory usage: 41.7+ KB

````Python
# Cambio de tipos de datos
titanic = pd.get_dummies(titanic, columns = ["Sex"], drop_first = True)
titanic.dtypes
````

|        |      |
| -----: | ---: |
| Survived | int64 | 
| Pclass | int64 |
| Age | float64 |
| SibSp | int64 |
| Parch | int64 |
| Sex_male | uint8 |
dtype: object

````Python
titanic.head()
````
|index|Survived|Pclass|Age|SibSp|Parch|Sex\_male|
|---|---|---|---|---|---|---|
|0|0|3|22\.0|1|0|true|
|1|1|1|38\.0|1|0|false|
|2|1|3|26\.0|0|0|false|
|3|1|1|35\.0|1|0|false|
|4|0|3|35\.0|0|0|true|

````Python
# Renombrado de columna sex_male
titanic.rename(columns = {'Sex_male': 'Sex'}, inplace = True)
````
* Sex = 1 = Male
* Sex = 0 = Female

````Python
# Ordenación de columnas por nombres
titanic = titanic[['Survived','Pclass', 'Sex',  'Age', 'SibSp', 'Parch']]
titanic.head()
````
|index|Survived|Pclass|Sex|Age|SibSp|Parch|
|---|---|---|---|---|---|---|
|0|0|3|true|22\.0|1|0|
|1|1|1|false|38\.0|1|0|
|2|1|3|false|26\.0|0|0|
|3|1|1|false|35\.0|1|0|
|4|0|3|true|35\.0|0|0|

### Entrenamiento del modelo de clasificación

````Python
# Proporcion del a variable objetivo
titanic.Survived.value_counts(normalize=True)
````

|     |          |
| :-: | -------: |
| 0 | 0.614431 | 
| 1 | 0.385569 |
Name: Survived, dtype: float64

````Python
# Importar libreria para balancear los datos
from imblearn.under_sampling import RandomUnderSampler
undersample = RandomUnderSampler(random_state=42)

# Separación en X e y
X_titanic = titanic.drop("Survived", axis = 1)
y_titanic = titanic.Survived

# Balanceo de datos
X_over_titanic, y_over_titanic  = undersample.fit_resample(X_titanic,y_titanic)
y_over_titanic.value_counts(normalize=True)
````
|     |          |
| :-: | -------: |
| 0 | 0.5 | 
| 1 | 0.5 |
Name: Survived, dtype: float64

````Python
# Importación de librerias para dividir el dataset
from sklearn.model_selection  import train_test_split

#30% para test y 70% para train
X_train_titanic, X_test_titanic, y_train_titanic, y_test_titanic = train_test_split(X_over_titanic,y_over_titanic, test_size=0.30, random_state=42)

# Importación librerias para crear modelo
from sklearn.tree             import DecisionTreeClassifier
from sklearn.model_selection  import GridSearchCV

# Definición clasificador y valores de los hiperparámetros a probar
clf = DecisionTreeClassifier(random_state=42)
param_grid = {'criterion': ['gini', 'entropy'], 'max_depth': [2, 3, 4, 5]}

# Búsqueda de hiperparámetros utilizando GridSearchCV
grid_search = GridSearchCV(clf, param_grid=param_grid, cv=10, return_train_score=True)
grid_search.fit(X_train_titanic, y_train_titanic)

# Impresión de los resultados
print("Mejores hiperparámetros encontrados:")
print(grid_search.best_params_)
print("Mejor puntuación de validación cruzada:")
print(grid_search.best_score_)
````

Mejores hiperparámetros encontrados:  
{'criterion': 'gini', 'max_depth': 4}  
Mejor puntuación de validación cruzada:  
0.7908687943262411  

````Python
# Modelo con parámetros optimizados
best_clf = grid_search.best_estimator_

# Predicción de Y
y_train_pred_titanic = best_clf.predict(X_train_titanic)
y_test_pred_titanic = best_clf.predict(X_test_titanic)
````

### Evaluación del resultado del modelo

````Python
# Gráfica de matriz de confusion
from sklearn.metrics import confusion_matrix
from sklearn.metrics import ConfusionMatrixDisplay
cm = confusion_matrix(y_test_titanic,y_test_pred_titanic,labels=best_clf.classes_)
ConfusionMatrixDisplay(cm, display_labels=best_clf.classes_).plot()
```` 

![DECTRE02](https://i.imgur.com/JJnEh5X.png)  

````Python
# Cálculo de las predicciones en Train(ing) y test
y_train_pred = best_clf.predict(X_train_titanic)
y_test_pred = best_clf.predict(X_test_titanic)

from sklearn.metrics import accuracy_score
print('El accuracy en train(ing) es:',accuracy_score(y_train_titanic,y_train_pred_titanic))
print('El accuracy en test es:', accuracy_score(y_test_titanic,y_test_pred_titanic))
````
El accuracy en train(ing) es: 0.8179916317991632  
El accuracy en test es: 0.8252427184466019  

````Python
feature_scores_titanic = pd.DataFrame(pd.Series(grid_search.best_estimator_.feature_importances_, index=X_train_titanic.columns).sort_values(ascending=False)).T

plt.figure(figsize=(12,4))
sns.barplot(data=feature_scores_titanic)

for index, value in enumerate(feature_scores_titanic.values.flatten()):
    plt.annotate(f'{value:.2f}', xy=(index, value), ha='center', va='bottom')


plt.title("Factores clave en la predicción de la supervivencia en el Titanic")
plt.show()
````
![DECTRE03](https://i.imgur.com/cUrVVxG.png)  

## Análisis de datos del árbol de decisión  

Podemos observar que para la clasificación del modelo en base a la variable target: ***Survived***, los features más importantes son: ***Sex***, seguido de ***Age*** y luego de ***Pclass***.  

***SibSp*** y ***ParCh*** no tienen un impacto significativo en la capacidad del modelo para predecir la variable objetivo, se podrían eliminar sin afectar la capacidad de predicción.  

Tambien es importante destacar que se observa una performance parecida en la métrica de **Accuracy** para los datos de **Train** y de **Test**, lo cual es claramente positivo para nuestro modelo. 
