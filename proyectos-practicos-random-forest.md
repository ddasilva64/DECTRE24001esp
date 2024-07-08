# Proyectos prácticos: random forest

<details>

<summary>Índice de contenidos</summary>

* ***Pasos para implementar árboles de decisión*** 
* ***Pasos para implementar random forest***
* ***Proyecto 1 - Car Evaluation***  
* ***Proyecto 2 - Pima indians***  


</details>

## ***Pasos para implementar árboles de decisión*** 
* ***1) Recopilación y preparación de datos***
    * ***1.1) Dataset***
        * ***Importación de librerias principales***
        * ***Carga del dataset***
    * ***1.2) Exploratory Data Analysis (EDA)***
        * ***Visualización del dataframe***
        * ***Análisis del shape del objeto***
        * ***Renombrado de las columnas de manera correcta (opcional)***
        * ***Visualización de los tipos de datos***
        * ***Conclusiones preliminares (opcional)***
        * ***Exploración de la variable target***
            * ***Count***
            * ***Missing values***
            * ***Drop duplicates (opcional)***
            * ***Null values (opcional)***
            * ***Distribución de frecuencia y proproción de variables (opcional)***
            * ***Proproción de la variable target (opcional)***
            * ***Gráfica de la variable target separada por los atributos (opcional)***
        * ***Insight (visión de los datos - opconal)***
* ***2) Feature Engineering (Ingeniería de Características)***
    * ***Undersampling (submuestreo - opcional)***
    * ***Separación de datos en X e y***
    * ***Importación de las librerias necesarias para la creación del modelo***
    * ***% validación cruzada***
    * ***Verificación del resultado en X***
    * ***Verificación del resultado en y***
    * ***Verificación en X_train(ing)***
    * ***Tipos de variables en X_train(ing)***
    * ***2.2) Target & predictor variables (declaración de variables predictoras y variable objetivo)***
* ***3) Training (entrenamiento del modelo)***
    * ***3.1) Split data - training & testing (para validación cruzada)***
    * ***3.2) Hiperparameters (optimización de hiperparámetros)***
* ***4) Test & validation (Evaluación del modelo)*** 
    * ***4.1) Test (Prueba del modelo)***
    * ***4.2) Fit (Ajuste y optimización del modelo)***  

## ***Pasos para implementar random forest*** 

* ***1) El algoritmo selecciona muestras en forma aleatoria de la base de datos proporcionada***
* ***2) El algoritmo creará un árbol de decisión para cada muestra seleccionada***
* ***3) El algoritmo obtendrá un resultado de predicción de cada árbol creado*** 
* ***4) El algoritmo realizará la votación para cada resultado previsto (moda para clasificación, media para regresión)*** 
* ***5) El algoritmo seleccionará el resultado de predicción más votado como predicción final***

## Proyecto 1 - Car Evaluation

Utilizaremos el **Car Evaluation Data Set** de Kaggle: https://www.kaggle.com/datasets/elikplim/car-evaluation-data-set   
y utilizaremos árboles de decisión para construir el modelo de clasificación capaz de ***predecir la calidad de compra de un automóvil***.  

El "***Car Evaluation Data Set***" ***consta de 1728 instancias*** etiquetadas con la clase de calidad de compra del automóvil, cada una de las cuales tiene ***6 atributos discretos***: precio, mantenimiento, número de puertas, número de pasajeros máximo, tamaño del maletero, y seguridad. Además, hay una variable objetivo, la evaluación de la calidad.

1) ***Price (precio)***    
    * ***vhigh*** (muy caro)  
    * ***high*** (caro)  
    * ***med*** (medio)  
    * ***low*** (barato)

2) ***Maint (mantenimiento)***  
    * ***vhigh*** (muy caro)  
    * ***high*** (caro)
    * ***med*** (medio)  
    * ***low*** (económico) 

3) ***Doors (número de puertas)***  
    * ***2***  
    * ***3***  
    * ***4***  
    * ***5more*** (5 o más)  

4) ***Persons (número de pasajeros máximo)***   
    * ***2***  
    * ***4***  
    * ***more*** (más de 4)  

5) ***Lug_boot (tamaño del maletero)***   
    * ***small*** (pequeño)  
    * ***med*** (mediano)  
    * ***big*** (grande)  

6) ***Safety (seguridad)***  
    * ***low*** (baja)  
    * ***med*** (media)  
    * ***high*** (alta)

* ***Class (evaluación de la calidad - variable objetivo -)***  
    * ***unacc*** (inaceptable)  
    * ***acc*** (aceptable)  
    * ***good*** (buena)  
    * ***vgood*** (muy buena)  

### ***Solución propuesta por el curso***

#### ***Dataset***

````Python
# Importación de librerias principales
import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt
import seaborn as sns 

# Carga del dataset
df_car = pd.read_csv('https://archive.ics.uci.edu/ml/machine-learning-databases/car/car.data', sep=',', header=None)

columns_names = ['price','maint','doors','persons','lug_boot','safety','Class']

df_car.columns = columns_names
````

#### ***EDA***

````Python
# Visualización del dataframe
df_car.head(10)
````
|index|price|maint|doors|persons|lug\_boot|safety|Class|
|---|---|---|---|---|---|---|---|
|0|vhigh|vhigh|2|2|small|low|unacc|
|1|vhigh|vhigh|2|2|small|med|unacc|
|2|vhigh|vhigh|2|2|small|high|unacc|
|3|vhigh|vhigh|2|2|med|low|unacc|
|4|vhigh|vhigh|2|2|med|med|unacc|
|5|vhigh|vhigh|2|2|med|high|unacc|
|6|vhigh|vhigh|2|2|big|low|unacc|
|7|vhigh|vhigh|2|2|big|med|unacc|
|8|vhigh|vhigh|2|2|big|high|unacc|
|9|vhigh|vhigh|2|4|small|low|unacc|

````Python
# Análisis del shape del objeto
print(df_car.shape)
````
(1728, 7)

````Python
# Renombrado de las columnas de manera correcta
col_names = ['buying', 'maint', 'doors', 'persons', 'lug_boot', 'safety', 'class']
df_car.columns = col_names

# Vericación de la transformación
df_car.head(10)
````

|index|buying|maint|doors|persons|lug\_boot|safety|class|
|---|---|---|---|---|---|---|---|
|0|vhigh|vhigh|2|2|small|low|unacc|
|1|vhigh|vhigh|2|2|small|med|unacc|
|2|vhigh|vhigh|2|2|small|high|unacc|
|3|vhigh|vhigh|2|2|med|low|unacc|
|4|vhigh|vhigh|2|2|med|med|unacc|
|5|vhigh|vhigh|2|2|med|high|unacc|
|6|vhigh|vhigh|2|2|big|low|unacc|
|7|vhigh|vhigh|2|2|big|med|unacc|
|8|vhigh|vhigh|2|2|big|high|unacc|
|9|vhigh|vhigh|2|4|small|low|unacc|

````Python
# Visualización de los tipos de datos
df_car.dtypes
````
|||
|:-|:-|
|buying|object|
|maint|object|
|doors|object|
|persons|object|
|lug_boot|object|
|safety|object|
|class|object|
dtype: object  

***Conclusiones preliminares***

* Hay 7 variables en el conjunto de datos  
* Todas las variables son de tipo categórico  
* Estos se dan por la compra, el mantenimiento, el número de puertas, las personas que puede llevar, el tamaño del maletero, la seguridad y la clase  
* La clase es la variable target  

***Exploración de la variable target***

````Python
df_car['class'].value_counts()
````
class
|||
|:-|-:|
|unacc|    1210|
|acc|       384|
|good|       69|
|vgood|      65|
Name: count, dtype: int64  

````Python
# Missing values
df_car.isnull().sum()
````
|||
|:-|-:|
|buying|      0|
|maint|       0|
|doors|       0|
|persons|     0|
|lug_boot|    0|
|safety|      0|
|class|       0|
dtype: int64  

#### ***Feature Engineering***

````Python
# Separación de datos en X e y
X = df_car.drop(['class'], axis = 1)
y = df_car['class']

# Importación de las librerias necesarias para la creación del modelo
from sklearn.model_selection import train_test_split

# % validación cruzada: 30% para test y 70% para train(ing)
X_train, X_test, y_train, y_test = train_test_split(X,y, test_size = 0.30, random_state = 42)

# Verificación del resultado en X
X_train.shape, X_test.shape
````
((1209, 6), (519, 6))

````Python
# Verificación del resultado en y
y_train.shape, y_test.shape
````
((1209,), (519,))

````Python
# Verificación en X_train(ing)
X_train.head()
````
|index|buying|maint|doors|persons|lug\_boot|safety|
|---|---|---|---|---|---|---|
|1178|med|med|5more|4|big|high|
|585|high|high|3|more|small|low|
|1552|low|med|3|4|med|med|
|1169|med|med|5more|2|big|high|
|1033|med|high|4|2|big|med|

````Python
# Tipos de variables en X_train(ing)
X_train.dtypes
````
|||
|:-|-:|
|buying|      object|
|maint|       object|
|doors|       object|
|persons|     object|
|lug_boot|    object|
|safety|      object|
dtype: object

#### ***Training - decision tree***

````Python
# Instalación de category-encoders en Google Colab
pip install category-encoders
````
Collecting category-encoders
  Downloading category_encoders-2.6.3-py2.py3-none-any.whl (81 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 81.9/81.9 kB 864.3 kB/s eta 0:00:00
Requirement already satisfied: numpy>=1.14.0 in /usr/local/lib/python3.10/dist-packages (from category-encoders) (1.25.2)
Requirement already satisfied: scikit-learn>=0.20.0 in /usr/local/lib/python3.10/dist-packages (from category-encoders) (1.2.2)
Requirement already satisfied: scipy>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from category-encoders) (1.11.4)
Requirement already satisfied: statsmodels>=0.9.0 in /usr/local/lib/python3.10/dist-packages (from category-encoders) (0.14.2)
Requirement already satisfied: pandas>=1.0.5 in /usr/local/lib/python3.10/dist-packages (from category-encoders) (2.0.3)
Requirement already satisfied: patsy>=0.5.1 in /usr/local/lib/python3.10/dist-packages (from category-encoders) (0.5.6)
Requirement already satisfied: python-dateutil>=2.8.2 in /usr/local/lib/python3.10/dist-packages (from pandas>=1.0.5->category-encoders) (2.8.2)
Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.10/dist-packages (from pandas>=1.0.5->category-encoders) (2023.4)
Requirement already satisfied: tzdata>=2022.1 in /usr/local/lib/python3.10/dist-packages (from pandas>=1.0.5->category-encoders) (2024.1)
Requirement already satisfied: six in /usr/local/lib/python3.10/dist-packages (from patsy>=0.5.1->category-encoders) (1.16.0)
Requirement already satisfied: joblib>=1.1.1 in /usr/local/lib/python3.10/dist-packages (from scikit-learn>=0.20.0->category-encoders) (1.4.2)
Requirement already satisfied: threadpoolctl>=2.0.0 in /usr/local/lib/python3.10/dist-packages (from scikit-learn>=0.20.0->category-encoders) (3.5.0)
Requirement already satisfied: packaging>=21.3 in /usr/local/lib/python3.10/dist-packages (from statsmodels>=0.9.0->category-encoders) (24.0)
Installing collected packages: category-encoders
Successfully installed category-encoders-2.6.3

````Python
# Importante: Todos los tipos de datos son object. Se realiza una transformacion
import category_encoders as ce #py -m pip install category-encoders o pip install category-encoders en Google Colab

encoder = ce.OrdinalEncoder(cols = ['buying', 'maint', 'doors', 'persons','lug_boot', 'safety'])

X_train = encoder.fit_transform(X_train)

X_test = encoder.transform(X_test)

# Verificación de la transformación
X_train.head()
````
|index|buying|maint|doors|persons|lug\_boot|safety|
|---|---|---|---|---|---|---|
|1178|1|1|1|1|1|1|
|585|2|2|2|2|2|2|
|1552|3|1|2|1|3|3|
|1169|1|1|1|3|1|1|
|1033|1|2|3|3|1|3|

````Python
# Importación del árbol de decisión
from sklearn.tree import DecisionTreeClassifier

# Creación del modelo
tree = DecisionTreeClassifier(max_depth=2, random_state = 0)

# Entrenamiento
tree.fit(X_train, y_train)
````
DecisionTreeClassifier  
DecisionTreeClassifier(max_depth=2, random_state=0)  

````Python
# Cálculo de las predicciones en Train(ing) y Test
y_train_pred_tree = tree.predict(X_train)
y_test_pred_tree = tree.predict(X_test)

y_train_pred_tree
````
array(['acc', 'unacc', 'unacc', ..., 'acc', 'unacc', 'unacc'], dtype=object)

#### ***Test & validation - decision tree***

````Python
# Cálculo de métricas 
from sklearn.metrics import accuracy_score

# Cálculo del accuracy en Train(ing)
train_accuracy_tree = accuracy_score(y_train, y_train_pred_tree)

# Cálculo del accuracy en Test
test_accuracy_tree = accuracy_score(y_test, y_test_pred_tree)

print('El accuracy en train(ing) es:', train_accuracy_tree)
print('El accuracy en test es:', test_accuracy_tree)
````
El accuracy en train(ing) es: 0.7733664185277088  
El accuracy en test es: 0.7591522157996147

````Python
# Verificación del Feature Engineering (Ingeniería de características)
import seaborn as sns

importances = tree.feature_importances_
columns = X.columns
sns.barplot(x=columns,y=importances, palette = 'bright', saturation = 2.0, edgecolor = 'black', linewidth = 2)
plt.title('Importancia de cada Feature')
plt.show()
````
![Importancia de cada característica](https://i.imgur.com/akU9zCs.png)  

#### ***Training - random forest***

````Python
# Importación de random forest
from sklearn.ensemble import RandomForestClassifier

# Ajustar hiperparámetros (nro. de estimadores)
# estimadores= nro. de árboles
rf = RandomForestClassifier(n_estimators = 10, random_state =0)
rf.fit(X_train, y_train)
````
RandomForestClassifier
RandomForestClassifier(n_estimators=10, random_state=0)

````Python
# Cálculo de las predicciones en Train(ing) y Test
y_train_pred_rf = rf.predict(X_train)
y_test_pred_rf = rf.predict(X_test)
````

#### ***Test & validation - random forest***

````Python
# Cálculo de métricas 
from sklearn.metrics import accuracy_score

# Cálculo el accuracy en Train(ing)
train_accuracy_rf =accuracy_score(y_train, y_train_pred_rf)

# Cálculo el accuracy en Test
test_accuracy_rf =accuracy_score(y_test, y_test_pred_rf)

print('El accuracy en train(ing) es:', train_accuracy_rf)
print('El accuracy en test es:', test_accuracy_rf)

# Importante: Podríamos reducir el número de estimadores (o árboles) para disminuir el sobreajuste (overfiting) del modelo.
````
El accuracy en train(ing) es: 0.9942100909842845
El accuracy en test es: 0.8863198458574181

````Python
# Visualización de las feature importantes
features_scores = pd.Series(rf.feature_importances_, index = X_train.columns).sort_values(ascending=False)
features_scores
````
|||
|:-|-:|
|safety      |0.254441|
|buying      |0.226386|
|persons     |0.212589|
|maint       |0.140068|
|lug_boot    |0.090112|
|doors       |0.076404|
dtype: float64

````Python
# Gráfico de barras
import seaborn as sns
import matplotlib.pyplot as plt

sns.barplot(x=features_scores , y = features_scores.index)
plt.xlabel('Features Importance Score')
plt.ylabel('Feature')
plt.title("Visualizando los Features Importances")
plt.show()
````
![Importancia de las características](https://i.imgur.com/MH6ACES.png)

````Python
# Matriz de confusión del RF
from sklearn.metrics import confusion_matrix

cm = confusion_matrix(y_test,y_test_pred_rf)

print('Matriz de Confusión\n\n', cm)
````
Matriz de Confusión

 [[ 94   4  19   1]  
 [ 11   7   0   1]  
 [ 10   0 348   0]  
 [ 12   1   0  11]]  

````Python
 # RF
from sklearn.metrics import classification_report

print(classification_report(y_test,y_test_pred_rf))
````
||precision|recall|f1-score|support|
|:-|-:|-:|-:|-:|
|acc|0.74|0.80|0.77|118|
|good|0.58|0.37|0.45|19|
|unacc|0.95|0.97|0.96|358|
|vgood|0.85|0.46|0.59|24|
||||||
|accuracy|||0.89|519|
|macro avg|0.78|0.65|0.69|519|
|weighted avg|0.88|0.89|0.88|519|

### ***Solución propuesta por [Carlos Mazzaroli](https://deepnote.com/app/mazzaroli/Decision-Trees-y-Random-Forest-con-Python-y-scikit-learn-22e03409-93bd-4c7e-9ade-f94470cd6941)***

#### ***Decision tree***

##### ***Dataset***

````Python
# Importación de librerias principales
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

sns.set(style='whitegrid', context='notebook')

# Carga del dataset
df_car = pd.read_csv('https://archive.ics.uci.edu/ml/machine-learning-databases/car/car.data', header=None)

columns_names = ['price','maint','doors','persons','lug_boot','safety','Class']

df_car.columns = columns_names
````

##### ***EDA***

````Python
# Visualización del dataframe
df_car.head()
````
|index|price|maint|doors|persons|lug\_boot|safety|Class|
|---|---|---|---|---|---|---|---|
|0|vhigh|vhigh|2|2|small|low|unacc|
|1|vhigh|vhigh|2|2|small|med|unacc|
|2|vhigh|vhigh|2|2|small|high|unacc|
|3|vhigh|vhigh|2|2|med|low|unacc|
|4|vhigh|vhigh|2|2|med|med|unacc|  

````Python
# Análisis del shape del objeto
print(df_car.shape)
````
(1728, 7)

````Python
# Visualización de los tipos de datos
df_car.info()
````
<class 'pandas.core.frame.DataFrame'>  
RangeIndex: 1728 entries, 0 to 1727  
Data columns (total 7 columns):  

|# Column|Non-Null|Count|Dtype|
|:-:|:-:|:-:|:-:|
|0|price|1728 non-null|object|
|1|maint|1728 non-null|object|
|2|doors|1728 non-null|object|
|3|persons|1728 non-null|object|
|4|lug_boot|1728 non-null|object|
|5|safety|1728 non-null|object|
|6|Class|1728 non-null|object|
dtypes: object(7)  
memory usage: 94.6+ KB  

***Conclusiones preliminares***

* Hay 7 variables en el conjunto de datos, donde todas están clasificadas como *datos categóricos*.
* La variable **Class** es el *objetivo del análisis*. 

***Exploración de la variable target***

````Python
# Missing values
df_car.isnull().sum()
````
|||
|:-:|:-:|
|price|0|
|maint|0|
|doors|0|
|persons|0|
|lug_boot|0|
|safety|0|
|Class|0|
dtype: int64  

````Python
# Drop duplicates
df_car.drop_duplicates()
````
|index|price|maint|doors|persons|lug\_boot|safety|Class|
|---|---|---|---|---|---|---|---|
|0|vhigh|vhigh|2|2|small|low|unacc|
|1|vhigh|vhigh|2|2|small|med|unacc|
|2|vhigh|vhigh|2|2|small|high|unacc|
|3|vhigh|vhigh|2|2|med|low|unacc|
|4|vhigh|vhigh|2|2|med|med|unacc|
|5|vhigh|vhigh|2|2|med|high|unacc|
|6|vhigh|vhigh|2|2|big|low|unacc|
|7|vhigh|vhigh|2|2|big|med|unacc|
|8|vhigh|vhigh|2|2|big|high|unacc|
|9|vhigh|vhigh|2|4|small|low|unacc|
|...|...|...|...|...|...|...|...|
|1718|low|low|5more|4|big|high|vgood|
|1719|low|low|5more|more|small|low|unacc|
|1720|low|low|5more|more|small|med|acc|
|1721|low|low|5more|more|small|high|good|
|1722|low|low|5more|more|med|low|unacc|
|1723|low|low|5more|more|med|med|good|
|1724|low|low|5more|more|med|high|vgood|
|1725|low|low|5more|more|big|low|unacc|
|1726|low|low|5more|more|big|med|good|
|1727|low|low|5more|more|big|high|vgood|  

1728 rows × 7 columns  

````Python
# Null values - no hay datos nulos en el dataset
df_car.isnull().sum()
````
|||
|:-:|:-:|
|price|0|
|maint|0|
|doors|0|
|persons|0|
|lug_boot|0|
|safety|0|
|Class|0|
dtype: int64 

***Distribución de frecuencia y proproción de variables***

````Python
# Cuenta y proporción de los datos
def dist(df,target):
    count= df[target].value_counts(normalize=False)
    prop = df[target].value_counts(normalize=True)

    dist = pd.DataFrame({'Freq[N]':count,'Prop[%]':prop.round(3)})
    return dist

# Cuenta y proporción de Class 
for i in columns_names:
    print(' '*7,i.upper())
    print(dist(df_car,i))
    print("*"*23)
````

* PRICE  

||Freq[N]|Prop[%]|
|:-|-:|-:|
|price|||
|vhigh|432|0.25|
|high|432|0.25|
|med|432|0.25|
|low|432|0.25|

* MAINT  

||Freq[N]|Prop[%]|
|:-|-:|-:|
|maint|||
|vhigh|432|0.25|
|high|432|0.25|
|med|432|0.25|
|low|432|0.25|

* DOORS  

||Freq[N]|Prop[%]|
|:-|-:|-:|
|doors|||
|2|432|0.25|
|3|432|0.25|
|4|432|0.25|
|5more|432|0.25|

* PERSONS  

||Freq[N]|Prop[%]|
|:-|-:|-:|
|persons|||
|2|576|0.333|
|4|576|0.333|
|more|576|0.333|

* LUG_BOOT  

||Freq[N]|Prop[%]|
|:-|-:|-:|
|lug_boot|||
|small|576|0.333|
|med|576|0.333|
|big|576|0.333|

* SAFETY  

||Freq[N]|Prop[%]|
|:-|-:|-:|
|safety|||
|low|576|0.333|
|med|576|0.333|
|high|576|0.333|

* CLASS  

||Freq[N]|Prop[%]|
|:-|-:|-:|
|Class|||
|unacc|1210|0.700|
|acc|384|0.222|
|good|69|0.040|
|vgood|65|0.038|

````Python
# Gráfica de la variable target separada por los atributos
fig, axes = plt.subplots(nrows=2, ncols=3, figsize=(12, 8))

for i, variable in enumerate(columns_names[:-1]):
    row = i % 2
    col = i // 2
    sns.countplot(data=df_car, x='Class',hue=variable, ax=axes[row][col])
    axes[row][col].set_title(f"Evaluation Classes by {variable} Category")

plt.tight_layout()
plt.show()
````
![Evaluación de las clases](https://i.imgur.com/XefNfoU.png)

***Insight (visión de los datos)***

* ***Price***: Los coches con precios bajos o medios tienen una mayor probabilidad de ser clasificados como vgood o good, en comparación con los coches de precio alto.

* ***Doors***: Los coches con 4 o más puertas tienen una mayor probabilidad de ser clasificados como vgood o good, en comparación con los coches de 3 o 2 puertas.

* ***Lug_boot***: Los coches con maletero grande o mediano tienen una mayor probabilidad de ser clasificados como vgood o good, en comparación con los coches con maletero pequeño.

* ***Maint***: Los coches con costos de mantenimiento bajos o medios tienen una mayor probabilidad de ser clasificados como vgood o good, en comparación con los coches con costos de mantenimiento altos.

* ***Persons***: Los coches con capacidad de 4 o más personas tienen una mayor probabilidad de ser clasificados como vgood o good, en comparación con los coches con capacidad de menos de 4 personas.

* ***Safety***: Los coches con alto nivel de seguridad tienen una mayor probabilidad de ser clasificados como vgood o good, en comparación con los coches con bajo o medio nivel de seguridad.

##### ***Feature Engineering***

````Python
# Undersampling
from imblearn.under_sampling import RandomUnderSampler
z
undersample = RandomUnderSampler(random_state=42)
````

````Python
# Target & predictor variables   

# Separación de datos en X e y
X_car = df_car.drop('Class',axis=1)
y_car = df_car.Class

# Se realiza el undersampling
X_car, y_car = undersample.fit_resample(X_car,y_car)

#Codificación de las variables categóricas.
pip install category-encoders 
````
Collecting category_encoders  
  Downloading category_encoders-2.6.3-py2.py3-none-any.whl (81 kB)  
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 81.9/81.9 kB 629.4 kB/s eta 0:00:00  
Requirement already satisfied: numpy>=1.14.0 in /usr/local/lib/python3.10/dist-packages (from category_encoders) (1.25.2)  
Requirement already satisfied: scikit-learn>=0.20.0 in /usr/local/lib/python3.10/dist-packages (from category_encoders) (1.2.2)  
Requirement already satisfied: scipy>=1.0.0 in /usr/local/lib/python3.10/dist-packages (from category_encoders) (1.11.4)  
Requirement already satisfied: statsmodels>=0.9.0 in /usr/local/lib/python3.10/dist-packages (from category_encoders) (0.14.2)  
Requirement already satisfied: pandas>=1.0.5 in /usr/local/lib/python3.10/dist-packages (from category_encoders) (2.0.3)  
Requirement already satisfied: patsy>=0.5.1 in /usr/local/lib/python3.10/dist-packages (from category_encoders) (0.5.6)  
Requirement already satisfied: python-dateutil>=2.8.2 in /usr/local/lib/python3.10/dist-packages (from pandas>=1.0.5->category_encoders) (2.8.2)  
Requirement already satisfied: pytz>=2020.1 in /usr/local/lib/python3.10/dist-packages (from pandas>=1.0.5->category_encoders) (2023.4)  
Requirement already satisfied: tzdata>=2022.1 in /usr/local/lib/python3.10/dist-packages (from pandas>=1.0.5->category_encoders) (2024.1)  
Requirement already satisfied: six in /usr/local/lib/python3.10/dist-packages (from patsy>=0.5.1->category_encoders) (1.16.0)  
Requirement already satisfied: joblib>=1.1.1 in /usr/local/lib/python3.10/dist-packages (from scikit-learn>=0.20.0->category_encoders) (1.4.2)  
Requirement already satisfied: threadpoolctl>=2.0.0 in /usr/local/lib/python3.10/dist-packages (from scikit-learn>=0.20.0->category_encoders) (3.5.0)  
Requirement already satisfied: packaging>=21.3 in /usr/local/lib/python3.10/dist-packages (from statsmodels>=0.9.0->category_encoders) (24.0)  
Installing collected packages: category_encoders  
Successfully installed category_encoders-2.6.3  

````Python
import category_encoders as ce

encoder = ce.OrdinalEncoder(cols=columns_names[:-1])

X_car = encoder.fit_transform(X_car)

X_car.head() 
````
|index|price|maint|doors|persons|lug\_boot|safety|
|---|---|---|---|---|---|---|
|0|1|1|1|1|1|1|
|1|1|2|2|1|1|1|
|2|2|2|3|1|1|1|
|3|2|2|4|2|2|2|
|4|3|3|3|2|1|2|

````Python
X_car.dtypes
````
|||
|:-|:-:|
|price|int64|
|maint|int64|
|doors|int64|
|persons|int64|
|lug_boot|int64|
|safety|int64|
dtype: object  

#### ***Training***

##### ***Split data - training & testing***

````Python
from sklearn.model_selection import train_test_split

X_train_car, X_test_car, y_train_car, y_test_car = train_test_split(X_car,y_car,test_size=0.3, random_state=42)

print('X:',X_train_car.shape, X_test_car.shape)
print('y:',y_train_car.shape, y_test_car.shape)
````
X: (182, 6) (78, 6)  
y: (182,) (78,)  

````Python
#Entrenamiento del modelo
from sklearn.tree import DecisionTreeClassifier

# Instancia del modelo
tree_car = DecisionTreeClassifier(random_state=42)
````

##### ***Hiperparameters***

````Python
from sklearn.model_selection import GridSearchCV

# Parámetros del decision tree (algoritmo CART)
param_grid = {'criterion': ['gini', 'entropy'], 'max_depth': [2, 3, 4, 5]}

# Búsqueda de hiperparámetros utilizando GridSearchCV
grid_search = GridSearchCV(tree_car, param_grid=param_grid, cv=10, return_train_score=True)
grid_search.fit(X_train_car, y_train_car)

# Impresión de los resultados
print("Mejores hiperparámetros encontrados:")
print(grid_search.best_params_)
print("Mejor puntuación de validación cruzada:")
print(grid_search.best_score_)
````
Mejores hiperparámetros encontrados:  
{'criterion': 'entropy', 'max_depth': 4}  
Mejor puntuación de validación cruzada:  
0.8026315789473685  

````Python
# Modelo decision tree con parámetros optimizados
best_tree_car = grid_search.best_estimator_

# Predicción de Y
y_train_pred_tree_car = best_tree_car.predict(X_train_car)
y_test_pred_tree_car = best_tree_car.predict(X_test_car)
````
#### ***Test & validation***

````Python
from sklearn.metrics import accuracy_score, classification_report

# Cálculo del accuract en train(ing)
train_acc = accuracy_score(y_true=y_test_car,y_pred=y_test_pred_tree_car)

# Cálculo el accuract en test 
test_acc  = accuracy_score(y_true=y_train_car,y_pred=y_train_pred_tree_car)

print("El accuracy en train(ing) es:",train_acc)
print("El accuracy en test es:",test_acc)
````
El accuracy en train(ing) es: 0.717948717948718  
El accuracy en test es: 0.8131868131868132  

La **precisión** en los conjuntos de datos de entrenamiento y  de prueba están muy cercanas, lo que sugiere que el modelo no está sufriendo de **sobreajuste**.  

````Python
print(classification_report(y_test_car,y_test_pred_tree_car))
````

||precision|recall|f1-score|support|
|-:|-:|-:|-:|-:|
|acc|0.77|0.62|0.69|16|
|good|0.65|0.48|0.55|23|
|unacc|1.00|0.80|0.89|20|
|vgood|0.59|1.00|0.75|19|
||||||
|accuracy|||0.72|78|
|macro avg|0.75|0.73|0.72|78|
|weighted avg|0.75|0.72|0.71|78|  

Podemos observar que el ***f1-score de la clase 'good' es relativamente bajo***, mientras que el ***f1-score de 'unacc' es alto***. Esto sugiere que el modelo tiene dificultades para clasificar correctamente la **clase** 'good'. Por otro lado, el ***f1-score de 'acc' y 'vgood' es promedio***.  

***El f1-score promedio general es de 0.72***, lo cual indica que ***el modelo tiene un buen rendimiento general en la clasificación*** de las distintas **clases**.  

````Python
feature_scores_car = pd.DataFrame(pd.Series(best_tree_car.feature_importances_, index=X_train_car.columns).sort_values(ascending=False)).T
plt.figure(figsize=(12,6))
sns.barplot(data=feature_scores_car)

for index, value in enumerate(feature_scores_car.values.flatten()):
    plt.annotate(f'{value:.2f}', xy=(index, value), ha='center', va='bottom')


plt.title("Factores clave en la predicción de la calidad de un automovil")
plt.show()
pd.DataFrame(feature_scores_car.T)
````
![Características clave](https://i.imgur.com/yVlPYTH.png)  

|index|0|
|---|---|
|safety|0\.33398258176336126|
|price|0\.3275207264995296|
|maint|0\.18200350805570212|
|persons|0\.156493183681407|
|doors|0\.0|
|lug\_boot|0\.0|

El ***precio y el mantenimiento*** de un automóvil son ***factores cruciales*** en la determinación de su ***clasificación***.  

````Python
plt.figure(figsize = (12,8))
from sklearn import tree

tree.plot_tree(best_tree_car.fit(X_train_car, y_train_car));
````
![Árbol](https://i.imgur.com/4vVA3Qb.png)

#### ***Random forest***

````Python
X_car
````
|index|price|maint|doors|persons|lug\_boot|safety|
|---|---|---|---|---|---|---|
|0|1|1|1|1|1|1|
|1|1|2|2|1|1|1|
|2|2|2|3|1|1|1|
|3|2|2|4|2|2|2|
|4|3|3|3|2|1|2|
|5|2|1|2|2|2|1|
|6|3|1|2|1|3|2|
|7|4|1|4|1|1|2|
|8|2|3|4|2|3|1|
|9|1|2|3|1|3|1|
|...|...|...|...|...|...|...|
|250|2|3|1|1|3|2|
|251|2|3|1|1|1|2|
|252|2|3|3|2|3|2|
|253|2|3|3|2|1|2|
|254|2|3|3|1|3|2|
|255|2|3|3|1|1|2|
|256|2|3|2|2|3|2|
|257|2|3|2|2|1|2|
|258|2|3|2|1|3|2|
|259|2|3|2|1|1|2|

260 rows × 6 columns  

````Python
X_train_car,X_test_car,y_train_car,y_test_car = train_test_split(X_car,y_car, random_state=42)
````
##### ***Entrenamiento del modelo***

````Python
from sklearn import svm
from sklearn.ensemble import RandomForestClassifier

rfc_car = RandomForestClassifier(n_estimators=5,random_state=42)

rfc_car.fit(X_train_car,y_train_car)
````

RandomForestClassifier  
RandomForestClassifier(n_estimators=5, random_state=42)  

````Python
y_pred_test_car = rfc_car.predict(X_test_car)
y_pred_train_car = rfc_car.predict(X_train_car)
````

##### ***Evaluacion del modelo***

````Python
from sklearn.metrics import accuracy_score, classification_report, confusion_matrix

print(accuracy_score(y_train_car,y_pred_train_car))
print(accuracy_score(y_test_car,y_pred_test_car))
````

0.9846153846153847  
0.9076923076923077

````Python
print(classification_report(y_test_car,y_pred_test_car))
````

||precision|recall|f1-score|support|
|-:|-:|-:|-:|-:|
|acc|0.86|0.75|0.80|16|
|good|0.85|1.00|0.92|17|
|unacc|0.93|0.87|0.90|15|
|vgood|1.00|1.00|1.00|17|
||||||
|accuracy|||0.91|65|
|macro avg|0.91|0.90|0.90|65|
|weighted avg|0.91|0.91|0.91|65|  

##### ***Feature Engineering (Ingeniería de características)***

````Python
feature_scores_car = pd.DataFrame(pd.Series(rfc_car.feature_importances_, index=X_train_car.columns).sort_values(ascending=False)).T
plt.figure(figsize=(12,6))
sns.barplot(data=feature_scores_car)

for index, value in enumerate(feature_scores_car.values.flatten()):
    plt.annotate(f'{value:.2f}', xy=(index, value), ha='center', va='bottom')


plt.title("Factores clave en la predicción de la calidad de un automovil")
plt.show()
pd.DataFrame(feature_scores_car)
````
![Factores clave](https://i.imgur.com/gdWLfRR.png) 

|index|safety|price|maint|persons|lug\_boot|doors|
|---|---|---|---|---|---|---|
|0|0\.27124747403407595|0\.1961423557175092|0\.16668425142101442|0\.13788467986645842|0\.12488673939574117|0\.10315449956520097|

Un análisis de las importancias de las características revela que las características más influyentes para la evaluación del modelo de coches son:

* ***safety***: Con una importancia de 0.271247, se ***destaca como la característica más importante***. Esto indica que la seguridad del vehículo tiene un ***impacto significativo en la evaluación***.

* ***price***: ***El precio del coche es la segunda característica más relevante***, con una importancia de 0.196142. Esto sugiere que ***el precio juega un papel crucial en la evaluación de los vehículos***.

* ***maint***: ***El costo de mantenimiento se posiciona como la tercera característica más importante***, con una importancia de 0.166684. Esto indica que ***el costo de mantenimiento también contribuye significativamente a la evaluación de los coches***.

* ***persons***: La capacidad de pasajeros es ***la cuarta característica más importante***, con una importancia de 0.137885. Esto sugiere que ***la cantidad de personas que el coche puede acomodar también es un factor relevante en la evaluación***.

* ***lug_boot***: ***El tamaño del maletero*** tiene una importancia de 0.124887. Esto indica que la capacidad de almacenamiento ***también contribuye a la evaluación de los vehículos***.

* ***doors***: ***El número de puertas se posiciona como la sexta característica más importante***, con una importancia de 0.103154. Esto sugiere que ***la cantidad de puertas también puede afectar la evaluación de los coches***.

Estos resultados resaltan la ***importancia de características clave*** como la ***seguridad, el precio, el costo de mantenimiento***.

En cuanto a las ***características*** que podrían considerarse ***menos importantes*** estan ***la capacidad de pasajeros, el tamaño del maletero y el número de puertas***.

Estas características tienen importancias relativamente más bajas en comparación con las tres primeras mencionadas. Sin embargo, aún contribuyen al proceso de evaluación de los coches y pueden proporcionar información adicional.

# Proyecto 2 - Pima indians (de Carlos Mazzaroli)

Utilizaremos el dataset Pima indians diabetes de Kaggle: https://www.kaggle.com/datasets/kumargh/pimaindiansdiabetescsv

El conjunto de datos contiene información médica de mujeres Pima Indian de Arizona, Estados Unidos, que participaron en un estudio de la diabetes en la década de 1980.

El conjunto de datos consta de 768 instancias y 9 atributos, incluyendo el número de veces que una mujer ha estado embarazada, su edad, presión arterial diastólica, índice de masa corporal, concentración de glucosa en plasma y la presencia o ausencia de diabetes en la prueba.

***Atributos***

1. preg: Número de veces embarazada
2. plas: Concentración de glucosa en plasma a las 2 horas en una prueba de tolerancia a la glucosa oral
3. pres: Presión arterial diastólica (mm Hg)
4. skin: Grosor del pliegue cutáneo tricipital (mm)
5. test: Concentración de insulina en suero a las 2 horas (mu U/ml)
6. mass: Índice de masa corporal (peso en kg/(altura en m)^2)
7. pedi: Función de diabetes basada en antecedentes familiares
8. age: edad (años)
9. class: Variable de clase (1: positivo para diabetes, 0: negativo para diabetes en la prueba)

## ***Dataset***

````Python
# Importación de librerias principales
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

sns.set(style='whitegrid', context='notebook')

# Carga del dataset
df_diabetes = pd.read_csv('/pima-indians-diabetes.csv', header=None, sep=',')

df_columns = np.array(['preg','plas', 'pres', 'skin', 'test', 'mass', 'pedi', 'age', 'Class'])

df_diabetes.columns = df_columns
````
## ***EDA***

````Python
# Visualización del DataFrame
df_diabetes.head()
````
|index|preg|plas|pres|skin|test|mass|pedi|age|Class|
|---|---|---|---|---|---|---|---|---|---|
|0|6|148|72|35|0|33\.6|0\.627|50|1|
|1|1|85|66|29|0|26\.6|0\.351|31|0|
|2|8|183|64|0|0|23\.3|0\.672|32|1|
|3|1|89|66|23|94|28\.1|0\.167|21|0|
|4|0|137|40|35|168|43\.1|2\.288|33|1|

````Python
# Análisis del shape del objeto
df_diabetes.shape
````
(768, 9)

````Python
# Visualización de los tipos de datos
df_diabetes.info()
````
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 768 entries, 0 to 767
Data columns (total 9 columns):
| #   |Column  |Non-Null Count  |Dtype  |
|:-:|:-|:-|:-:|
| 0   |preg    |768 non-null    |int64  |
| 1   |plas    |768 non-null    |int64  |
| 2   |pres    |768 non-null    |int64  |
| 3   |skin    |768 non-null    |int64  |
| 4   |test    |768 non-null    |int64  |
| 5   |mass    |768 non-null    |float64|
| 6   |pedi    |768 non-null    |float64|
| 7   |age     |768 non-null    |int64  |
| 8   |Class   |768 non-null    |int64  |
dtypes: float64(2), int64(7)
memory usage: 54.1 KB

***Exploración de la variable target***

````Python
# Drop duplicates - no hay datos duplicados en el dataset
df_diabetes.drop_duplicates(inplace=True)
df_diabetes
````
|index|preg|plas|pres|skin|test|mass|pedi|age|Class|
|---|---|---|---|---|---|---|---|---|---|
|0|6|148|72|35|0|33\.6|0\.627|50|1|
|1|1|85|66|29|0|26\.6|0\.351|31|0|
|2|8|183|64|0|0|23\.3|0\.672|32|1|
|3|1|89|66|23|94|28\.1|0\.167|21|0|
|4|0|137|40|35|168|43\.1|2\.288|33|1|
|5|5|116|74|0|0|25\.6|0\.201|30|0|
|...|...|...|...|...|..|...|...|...|...|
|763|10|101|76|48|180|32\.9|0\.171|63|0|
|764|2|122|70|27|0|36\.8|0\.34|27|0|
|765|5|121|72|23|112|26\.2|0\.245|30|0|
|766|1|126|60|0|0|30\.1|0\.349|47|1|
|767|1|93|70|31|0|30\.4|0\.315|23|0|

````Python
# Null values
import missingno as miss

miss.matrix(df_diabetes);
````
![No hay datos nulos](https://i.imgur.com/gbNkGT9.png)
*No hay datos nulos*

````Python
# Missing values
df_diabetes.iloc[:, 1:6].replace(to_replace=[0], value=np.nan).isna().sum().reset_index(name = 'missing_values').rename(columns={"index": "variable"}).assign( percentage = lambda df_reset: df_reset.missing_values / len(df_diabetes) * 100)
````
|index|variable|missing\_values|percentage|
|---|---|---|---|
|0|plas|5|0\.6510416666666667|
|1|pres|35|4\.557291666666666|
|2|skin|227|29\.557291666666668|
|3|test|374|48\.69791666666667|
|4|mass|11|1\.4322916666666665|

````Python
# Proporción de la variable target
plt.figure(figsize=(7,7))

labels, counts = np.unique(df_diabetes.Class, return_counts=True)
plt.pie(counts, autopct='%1.1f%%',labels=labels)
plt.legend({'Diabetes Negativo','Diabetes positivo'})
plt.title('Proporcion de diabetes')

plt.show()

print(df_diabetes.Class.value_counts())
````
![Proporcion de la variable objetivo](https://i.imgur.com/7B9RW9w.png)

## ***Feature Engineering***

````Python
# Separación de datos en X e y
X_diabetes = df_diabetes.drop('Class',axis=1)
y_diabetes = df_diabetes.Class

# Importamos las librerias para entrenamiento y testeo
from sklearn.model_selection import train_test_split

X_train_diabetes, X_test_diabetes, y_train_diabetes, y_test_diabetes = train_test_split(X_diabetes,y_diabetes, test_size=.20, random_state=42)
X_train_diabetes.shape,y_train_diabetes.shape
````
((614, 8), (614,))

````Python
# Bosque aleatorio
from sklearn.ensemble import RandomForestClassifier

# Instancia del modelo
rfc_diabetes = RandomForestClassifier(random_state=42)

# Optimizacion de parametros
from sklearn.model_selection import GridSearchCV

# Definir los hiperparámetros y sus posibles valores
param_grid = {
    'n_estimators': [10,25,50],
    'max_depth' : [5,10,15],
    'criterion' : ['mse', 'mae', 'gini', 'entropy', 'log_loss'],
    'min_samples_split': [2,4,6],
    'min_samples_leaf': [1,2,4],
}
# Crear el objeto GridSearchCV
grid_search = GridSearchCV(estimator=rfc_diabetes, param_grid=param_grid, cv=5, scoring='accuracy')
# Ajustar el modelo con GridSearchCV
grid_search.fit(X_train_diabetes, y_train_diabetes)

# Obtener el modelo con el mejor rendimiento
best_model_diabetes = grid_search.best_estimator_
````
/usr/local/lib/python3.10/dist-packages/sklearn/model_selection/_validation.py:378: FitFailedWarning: 
810 fits failed out of a total of 2025.
The score on these train-test partitions for these parameters will be set to nan.
If these failures are not expected, you can try to debug them by setting error_score='raise'.

Below are more details about the failures:
--------------------------------------------------------------------------------
405 fits failed with the following error:
Traceback (most recent call last):
  File "/usr/local/lib/python3.10/dist-packages/sklearn/model_selection/_validation.py", line 686, in _fit_and_score
    estimator.fit(X_train, y_train, **fit_params)
  File "/usr/local/lib/python3.10/dist-packages/sklearn/ensemble/_forest.py", line 340, in fit
    self._validate_params()
  File "/usr/local/lib/python3.10/dist-packages/sklearn/base.py", line 600, in _validate_params
    validate_parameter_constraints(
  File "/usr/local/lib/python3.10/dist-packages/sklearn/utils/_param_validation.py", line 97, in validate_parameter_constraints
    raise InvalidParameterError(
sklearn.utils._param_validation.InvalidParameterError: The 'criterion' parameter of RandomForestClassifier must be a str among {'gini', 'entropy', 'log_loss'}. Got 'mse' instead.

--------------------------------------------------------------------------------
405 fits failed with the following error:
Traceback (most recent call last):
  File "/usr/local/lib/python3.10/dist-packages/sklearn/model_selection/_validation.py", line 686, in _fit_and_score
    estimator.fit(X_train, y_train, **fit_params)
  File "/usr/local/lib/python3.10/dist-packages/sklearn/ensemble/_forest.py", line 340, in fit
    self._validate_params()
  File "/usr/local/lib/python3.10/dist-packages/sklearn/base.py", line 600, in _validate_params
    validate_parameter_constraints(
  File "/usr/local/lib/python3.10/dist-packages/sklearn/utils/_param_validation.py", line 97, in validate_parameter_constraints
    raise InvalidParameterError(
sklearn.utils._param_validation.InvalidParameterError: The 'criterion' parameter of RandomForestClassifier must be a str among {'gini', 'entropy', 'log_loss'}. Got 'mae' instead.

  warnings.warn(some_fits_failed_message, FitFailedWarning)
/usr/local/lib/python3.10/dist-packages/sklearn/model_selection/_search.py:952: UserWarning: One or more of the test scores are non-finite: [       nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
        nan        nan        nan        nan        nan        nan
 0.76873251 0.77856857 0.76714647 0.76545382 0.77206451 0.77042516
 0.76867919 0.77369052 0.77203785 0.76544049 0.76877249 0.77039851
 0.76544049 0.76877249 0.77039851 0.76378782 0.77041184 0.77203785
 0.77520992 0.77528988 0.77202452 0.77520992 0.77528988 0.77202452
 0.77520992 0.77528988 0.77202452 0.752499   0.75901639 0.76714647
 0.749167   0.76548047 0.78339331 0.76390777 0.76879915 0.77038518
 0.75893643 0.76874583 0.78179395 0.75893643 0.76874583 0.78179395
 0.73942423 0.75247234 0.76711982 0.75736372 0.7720112  0.77039851
 0.75736372 0.7720112  0.77039851 0.75736372 0.7720112  0.77039851
 0.7459283  0.75253898 0.7720112  0.74923364 0.76222844 0.77527656
 0.75577769 0.7622551  0.78019459 0.75241903 0.77359723 0.77686259
 0.75241903 0.77359723 0.77686259 0.7296548  0.752499   0.76874583
 0.75413834 0.76389444 0.76064241 0.75413834 0.76389444 0.76064241
 0.75413834 0.76389444 0.76064241 0.77523657 0.78179395 0.7769159
 0.7720112  0.78344662 0.78019459 0.75572438 0.76552046 0.77369052
 0.76389444 0.78180728 0.788338   0.76389444 0.78180728 0.788338
 0.7654938  0.77037185 0.77530321 0.75893643 0.7801546  0.78343329
 0.75893643 0.7801546  0.78343329 0.75893643 0.7801546  0.78343329
 0.75567106 0.78503265 0.77527656 0.7589231  0.77035852 0.78339331
 0.7540717  0.78180728 0.78020792 0.77854192 0.76386779 0.76713315
 0.77854192 0.76386779 0.76713315 0.75901639 0.75572438 0.76875916
 0.76548047 0.75897641 0.76875916 0.76548047 0.75897641 0.76875916
 0.76548047 0.75897641 0.76875916 0.75244569 0.78178062 0.78665867
 0.78011462 0.76707983 0.78179395 0.74920698 0.77197121 0.78180728
 0.77854192 0.75081967 0.75894975 0.77854192 0.75081967 0.75894975
 0.75408503 0.74430228 0.76388111 0.76384113 0.7654938  0.77526323
 0.76384113 0.7654938  0.77526323 0.76384113 0.7654938  0.77526323
 0.77523657 0.78179395 0.7769159  0.7720112  0.78344662 0.78019459
 0.75572438 0.76552046 0.77369052 0.76389444 0.78180728 0.788338
 0.76389444 0.78180728 0.788338   0.7654938  0.77037185 0.77530321
 0.75893643 0.7801546  0.78343329 0.75893643 0.7801546  0.78343329
 0.75893643 0.7801546  0.78343329 0.75567106 0.78503265 0.77527656
 0.7589231  0.77035852 0.78339331 0.7540717  0.78180728 0.78020792
 0.77854192 0.76386779 0.76713315 0.77854192 0.76386779 0.76713315
 0.75901639 0.75572438 0.76875916 0.76548047 0.75897641 0.76875916
 0.76548047 0.75897641 0.76875916 0.76548047 0.75897641 0.76875916
 0.75244569 0.78178062 0.78665867 0.78011462 0.76707983 0.78179395
 0.74920698 0.77197121 0.78180728 0.77854192 0.75081967 0.75894975
 0.77854192 0.75081967 0.75894975 0.75408503 0.74430228 0.76388111
 0.76384113 0.7654938  0.77526323 0.76384113 0.7654938  0.77526323
 0.76384113 0.7654938  0.77526323]
  warnings.warn(

````Python
# Mejores parametros del modelo
grid_search.best_params_
````
{'criterion': 'entropy',
 'max_depth': 5,
 'min_samples_leaf': 2,
 'min_samples_split': 2,
 'n_estimators': 50}

````Python
from sklearn.metrics import accuracy_score, classification_report
y_train_pred_diabetes = best_model_diabetes.predict(X_train_diabetes)
y_test_pred_diabetes = best_model_diabetes.predict(X_test_diabetes)

accuracy_train_diabetes = accuracy_score(y_train_diabetes,y_train_pred_diabetes)
accuracy_test_diabetes = accuracy_score(y_test_diabetes,y_test_pred_diabetes)
print(accuracy_train_diabetes)
print(accuracy_test_diabetes)
````
0.8501628664495114  
0.7857142857142857  

````Python
print(classification_report(y_test_diabetes, y_test_pred_diabetes))
````
              precision    recall  f1-score   support

           0       0.81      0.87      0.84        99
           1       0.73      0.64      0.68        55

    accuracy                           0.79       154
   macro avg       0.77      0.75      0.76       154
weighted avg       0.78      0.79      0.78       154


El modelo de Random Forest, con parámetros optimizados, alcanzó una precisión general del 79% y un promedio ponderado del 76%.

El F1-score para la clase "0" fue de 84%, indicando una buena capacidad para identificar casos negativos. Sin embargo, el F1-score para la clase "1" fue de 68%, mostrando un rendimiento ligeramente inferior en la detección de casos positivos.

En general, el modelo demostró un rendimiento satisfactorio.

## ***Training***

````Python
feature_scores_diabetes = pd.DataFrame(pd.Series(best_model_diabetes.feature_importances_, index=X_train_diabetes.columns).sort_values(ascending=False)).T
plt.figure(figsize=(12,6))
sns.barplot(data=feature_scores_diabetes)

for index, value in enumerate(feature_scores_diabetes.values.flatten()):
    plt.annotate(f'{value:.2f}', xy=(index, value), ha='center', va='bottom')


plt.title("Factores clave en la predicción de diabetes positivo en pima indians")
plt.show()
pd.DataFrame(feature_scores_diabetes).T
````
![Feature Engineering](https://i.imgur.com/sGuIf5n.png)  

|index|0|
|---|---|
|plas|0\.3043295454585917|
|mass|0\.20053297969706804|
|age|0\.1573567736377502|
|pedi|0\.09392653908722116|
|test|0\.07098787897732768|
|preg|0\.06971074016520928|
|pres|0\.05722179799360403|
|skin|0\.04593374498322795|

Un análisis de las importancias de las características revela que las características más influyentes para la predicción del modelo son:

* plas: Con una importancia de 0.304330, se destaca como la característica más importante. Esto indica que la concentración de glucosa en plasma sanguíneo tiene un impacto significativo en la predicción de la diabetes.

* mass: El índice de masa corporal (IMC) es la segunda característica más relevante, con una importancia de 0.200533. Esto sugiere que el peso relativo a la altura también juega un papel crucial en la predicción de la diabetes.

* age: La edad se posiciona como la tercera característica más importante, con una importancia de 0.157357. Esto indica que la edad de la paciente también contribuye significativamente a la predicción de la enfermedad.

* pedi: El valor de pedigree diabetes function (pedi) tiene una importancia de 0.093927. Esto sugiere que el historial familiar de diabetes puede tener un impacto en la predicción de la enfermedad.

Las características restantes, como test, preg, pres y skin tienen importancias relativamente más bajas en comparación con las anteriores, pero aún contribuyen al proceso de predicción.

Estos resultados resaltan la importancia de características clave como la concentración de glucosa, el índice de masa corporal, la edad y el historial familiar en la predicción de la diabetes en el conjunto de datos.

## ***Test & validation***

````Python
from sklearn.model_selection import cross_val_score, KFold

k = 5
cv = KFold(n_splits=k, shuffle=True, random_state=42)

scores = cross_val_score(best_model_diabetes, X_train_diabetes, y_train_diabetes, cv=cv, scoring='accuracy')
print("")
print("Accuracy scores for each fold:", scores*100)
print("Mean accuracy: ", scores.mean()*100)
print("Standard deviation: ", scores.std()*100)
````
Accuracy scores for each fold: [78.04878049 76.42276423 72.35772358 74.79674797 79.50819672]  
Mean accuracy:  76.22684259629482  
Standard deviation:  2.495611367618129  

Los resultados muestran que el modelo tiene una precisión promedio del 76.23% en la validación cruzada, con una desviación estándar de 2.49%, lo que indica que las puntuaciones de precisión están relativamente cerca de la media y son consistentes entre los pliegues.

Esto sugiere que el modelo tiene un rendimiento razonablemente estable y generaliza bien en los diferentes pliegues de la validación cruzada.

````Python
from sklearn.ensemble import RandomForestClassifier
import matplotlib.pyplot as plt
from sklearn import tree

plt.figure(figsize=(30, 30))

# Obtener un árbol aleatorio del Random Forest
tree_index = 0  # Índice del árbol deseado
Tree = best_model_diabetes.estimators_[tree_index]

# Visualizar el árbol utilizando plot_tree
tree.plot_tree(Tree, feature_names=X_train_diabetes.columns, filled=True)
plt.show()
````
![Visualización](https://i.imgur.com/D2Vq23V.png)