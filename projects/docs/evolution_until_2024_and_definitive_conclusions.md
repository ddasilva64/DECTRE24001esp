# Preliminary conclusions & recommendations  

## Evolution until 2024

***Evolution (until 2024) of the native population [Pima of Arizona (USA)](https://en.wikipedia.org/wiki/Akimel_O%27odham), to be able to verify the forecasts of our RF***:

1. ***The dataset, [originally from the National Institute of Diabetes and Digestive and Kidney Diseases of the USA](https://www.kaggle.com/datasets/uciml/pima-indians-diabetes-database), is from*** 1984, ***exactly 40 years ago***, so we can already assess the evolution of the data.
2. ***Their traditional diet was based, above all, on traditional agriculture, hunting and gathering***, which required a lot of physical exercise.
3. The health problems, in this population, are basically of environmental origin related to the ***decline of their traditional economy and agriculture***.
4. ***The substitution of traditional diet with non-native diet was the main factor contributing to the high diabetes rate among the Pima***.
5. ***In 2000, the population living in the community was 742 people*** (less than 1/3 that in 1984).
6. ***They have the highest prevalence of type 2 diabetes in the world***, much higher than that observed in other populations in the US.

***The "[thrifty gene](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4418458/)" hypothesis in the Pima:***

* The overall increase in diabetes prevalence is the result of the interaction of ***genetic predisposition and*** a ***sudden change in diet over the last century from traditional agricultural crops to processed foods, along with a decrease in physical activity***.  

## Final conclusions

1. ***The key factors (features) that cause diabetes*** in this population are:
a) Directly, the concentration of ***glucose*** in the blood.
b) ***BMI*** (very important).
c) ***Age*** (to a lesser extent).
d) ***Family history***, which probably identifies a genetic predisposition.
2. The ***prevalence of female diabetes in this population is exaggeratedly higher than the general world average prevalence*** for men and women (approximately 6 times higher).

Therefore, ***the classification provided by our RF has worked perfectly***.

***Prediction test*** in the case of an anonymous Catalan woman:
0. ***Pregnancies*** = 0
1. ***Oral glucose tolerance test*** = 105 $\frac{mg}{dL}$
2. ***Diastolic blood pressure*** = 70 mm Hg
3. ***BMI*** ($\frac{weight\ in\ Kg}{(height\ in\ m)^2}$) = 31
4. ***History*** = 0
5. ***Age*** = 58 years
6. ***RF prediction = no diabetes (entropy=0.197)***
7. ***Diagnosed as = prediabetes***

Therefore, ***the prediction provided by our RF has worked perfectly***.

<p><br></p> 

[ChatGPT usage](../CHATGPT_USAGE.md)  

<p><br></p>

[Back to Table of contents :arrow_double_up:](../README.md)