# Feature Engineering (bivariate analysis first interpretation)  

## Bivariate analysis first interpretation

Since the ***scatter plot*** shows possible relationships between multiple variables, examining all combinations of two by two, ***the results obtained should match the detailed analysis that we will do later***. In addition, the incidence of diabetes on the individual variable can be observed.

***Possible combinations of variables with the target variable (diabetes)***

| number | relation | Pearson index | index assessment | applies to our dataset |
| :----: | :---------------- | :---------------: | :---------------: | :---------------: |
| 1 | pregnancies-diabetes | 0.20 | low correlation |no |
| 2 | glucose-diabetes | 0.54 | high correlation |yes |
| 3 | blood pressure-diabetes | 0.17 | low correlation |yes |
| 4 | bmi-diabetes | 0.30 | low correlation |yes |
| 5 | pedigree-diabetes | 0.16 | low correlation |yes |
| 6 | age-diabetes | 0.24 | low correlation |yes |

We cannot assess gestational diabetes, we are missing features in the dataset.

From now on:

Pearson  

1: 0.1 < 0.3 low correlation  
2: 0.3 < 0.5 medium correlation  
3: 0.5 < 0.7 high correlation  
4: 0.7 < 1 very high correlation  

Outliers  

1: no outliers  
2: very acceptable outliers  
3: acceptable outliers  
4: acceptable outliers  

<p><br></p> 

[ChatGPT usage](../CHATGPT_USAGE.md)  

<p><br></p>

[Back to Table of contents :arrow_double_up:](../README.md)