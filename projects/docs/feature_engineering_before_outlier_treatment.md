# Feature Engineering (before outlier treatment)  

* ***We will remove the following features: skinfold and insulin***.
* ***We will remove the following features from outliers: pregnancies, glucose, blood pressure, bmi and age***.

## Numerical Characteristics (before outlier treatment)

***Pregnancies***  

* Some women in the sample have many children (12 or more), although most have few, typically only 1 child.  
* It seems that ***the graph for this category should show a skewed right and flattened distribution (around 3 approximately)***.  
* ***High data dispersion***.  
* There are errors in the samples when more than 12 pregnancies are measured (all of them are outliers, although this only happens in 4 cases).  
* ***We will need to reanalyze the graph after implementing some outlier treatment strategy, as they may distort it***.  

***Glucose***  

* A small percentage of women (0.65%) have a blood glucose level of 0, which is clearly an error.  
* The zero values in this category coincide with the number of outliers (5).  
* Below 37.12 is considered an outlier, and above 202.12 is also considered an outlier, which means:  
  1. The 5 cases of women with a glucose level of 0 are errors or missing data, and these are all the detected outliers.  
  2. Some women seem to suffer from severe hypoglycemia, and others from hyperglycemia. Since our dataset is labeled, we know the incidence of diabetes in all cases.  
* Most women seem to have a normal glucose level.  
* We do not have data to assess gestational diabetes.  
* It seems that ***the graph for this category should show a skewed right and flattened distribution (around 117 approximately)***.  
* ***Low data dispersion***.  
* ***We will need to reanalyze the graph after implementing some outlier treatment strategy, as they may distort it***.  

***Blood pressure (pressure)***  

* A percentage of women (4.56%) have a diastolic blood pressure of 0, which is clearly an error.
* The zero values in this category (35) almost coincide with the number of outliers (45).
* Below 35.0 and above 107.0 are considered outliers, which means:
  1. The 35 cases of women with a blood pressure of 0 are errors or missing data, and these are all the detected outliers.
  2. Some women seem to suffer from severe hypotension, and others from hypertension. Since our dataset is labeled, we know the incidence of diabetes in all cases.
* Diastolic blood pressure is distributed around 72.0 and seems to correspond to a somewhat aged but hypotensive population.
* It seems normal for women to be slightly hypotensive (70.0).
* It seems that ***the graph for this category should show a skewed left and pointed distribution (around 72 approximately)***.
* ***Low data dispersion***.
* ***We will need to reanalyze the graph after implementing some outlier treatment strategy, as they may distort it***.

***Skin thickness (skinfold)***  

* The percentage of zeros (29.56%), which are also outliers in this case, is > 20%, making it unmanageable. ***We will remove the feature***.

***Insulin***  

* The percentage of zeros (48.7%), which are also outliers in this case, is > 20%, making it unmanageable. ***We will remove the feature***.

***BMI***  

* These women generally seem to be obese (type I), and in some cases, they may suffer from morbid obesity (type III).
* A percentage of women (1.43%) have a BMI of 0, which is clearly an error.
* The zero values in this category (11) almost coincide with the number of outliers (19).
* It seems that ***the graph for this category should show a skewed left and pointed distribution (around 32 approximately)***.
* ***Low data dispersion***.
* ***We will need to reanalyze the graph after implementing some outlier treatment strategy, as they may distort it***.

***Diabetes pedigree function (pedigree)***  

* There are no zero values, indicating a high incidence of diabetes in this population.
* We found a high percentage of outliers (3.78%), only surpassed by another category (diastolic blood pressure).
* Above 1.21 is considered an outlier.
* Most women have a pedigree function of 0.26 (which is a low value).
* It seems that ***the graph for this category should show a skewed right and very pointed distribution (around 0.37 approximately)***.
* ***Medium data dispersion***.
* ***We will need to reanalyze the graph after implementing some outlier treatment strategy, as they may distort it***.

***Age***  

* There are no zero values, indicating that data collection for this category includes women over 0 years (months).
* The average age of the women in the dataset is 33.24 years.
* The most common age is 22 years, indicating that most women are in their fertile age.
* We found a very low percentage of outliers (1.17%).
* Above 66.5 years is considered an outlier.
* The population is relatively young.
* It seems that ***the graph for this category should show a skewed right and slightly pointed distribution (around 29 years approximately)***.
* ***Medium data dispersion***.
* ***We will need to reanalyze the graph after implementing some outlier treatment strategy, as they may distort it***.


<p><br></p> 

[ChatGPT usage](../CHATGPT_USAGE.md)  

<p><br></p>

[Back to Table of contents :arrow_double_up:](../README.md)