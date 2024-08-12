# Modeling (Feature importances analysis)  

## Feature importances analysis

An analysis of the ***feature importances*** reveals that the most influential for the model prediction are:

* ***glucose***: With an importance of **48%**, it stands out as the most important feature. This indicates that ***blood plasma glucose concentration has a very significant impact on the prediction of diabetes***.  

* ***age***: Age is positioned as the second most important feature, with an importance of **20%**. This indicates that ***the patient's age also contributes significantly to the prediction of the disease***. People cannot avoid being the age they are, but they can improve their quality of life, with exercise and a healthy diet, for example.   

* ***bmi***: Body mass index (BMI) is the third most relevant feature, with an importance of **20%** (the same as age). This suggests that ***weight relative to height also plays a crucial role in the prediction of diabetes***. A 20 years old person with a very high BMI (obesity II or III) may have a risk situation similar to a 60 years old person. ***BMI is controllable, age is not***.

* ***pedigree***: The value of family family history of diabetes has an importance of **6%**. Although the value is very low, the data provided by the dataset is the result of a function that we do not know (black box), so it could be important, but much less than the previous three. In this case, ***we know that all women have a pedigree > 0***, which indicates that ***whatever is affecting this female population has spread generations into the past and this makes the problem even more serious***.  

The remaining features ***(pregnancies, with 4%, and blood pressure, with 2%) have relatively lower importance*** compared to the previous ones, but they still contribute to the prediction process. ***We insist that there are missing features to treat gestational diabetes, as well as other types of diabetes, in our model***.

***Important***: Note that the characteristic with the least importance is pressure, which means that it must be the one that indicates the greatest impurity in the data (it tells us the least), ***so pressure must be the root of our tree***.  

## Importance of key features without outliers (we did it like this)

![Importance of key features, done right](https://i.imgur.com/fBHtxMj.png)

***Everything seems fine, right?***

## Importance of key features with outliers (we didn't do it this way)

![Importance of key features, done wrong](https://i.imgur.com/EdJnAje.png)

***Warning!***: Pedigree, insulin and pregnancies have the same weight (7%). ***Something went wrong, right?***

<p><br></p> 

[ChatGPT usage](../CHATGPT_USAGE.md)  

<p><br></p>

[Back to Table of contents :arrow_double_up:](../README.md)