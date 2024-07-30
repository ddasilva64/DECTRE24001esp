# Feature Engineering (Insight)  

## Insight

* ***Case 2 (glucose-diabetes) resume***

| |glucose-diabetes|
|:------:|:--------------:|
|Pearson |3 |
|Outliers|1 |
|Diabetes|>131 |

* ***Case 3 (diabetes-pressure) resume***

| |diabetes-pressure|
|:------:|:--------------:|
|Pearson |1 |
|Outliers|2 |
|Diabetes|40 and >98 |

* ***Case 4 (bmi-pressure) resume***

| |bmi-diabetes|
|:------:|:--------------:|
|Pearson |1 |
|Outliers|2 |
|Diabetes|>22.9 |

* ***Case 5 (pedigree-pressure) resume***

|        |pedigree-diabetes|
|:------:|:--------------:|
|Pearson |1               |
|Outliers|3               |
|Diabetes|>0.09           |

* ***Case 6 (age-diabetes) resume***

|        |age-diabetes|
|:------:|:--------------:|
|Pearson |1               |
|Outliers|3               |
|Diabetes|>43             |

* ***Summary of possible variable combinations***

| number | relation | Pearson | Outliers | Approximate value diabetes |
| :----: | :---------------- | :-----: | :------: | :-------------------: |
| 2 | glucose-diabetes | 3 | 1 | >131 |
| 3 | blood-pressure-diabetes | 1 | 2 | 40 and >98 |
| 4 | bmi-diabetes | 1 | 2 | >22.9 |
| 5 | history-diabetes | 1 | 3 | >0.09 |
| 6 | age-diabetes | 1 | 3 | >43 |

* Insight

The insight, up to this point, into the characteristics of the model reveals that:

* ***glucose***: It seems that with glucose values ​​> 131, we already have cases of diabetes, that is, cases of diabetes occur earlier than expected.

* ***pressure***: It seems that with diastolic blood pressure values ​​> 98, we already have cases of diabetes, that is, cases of diabetes with a very high pressure occur earlier than expected.

* ***imc***: It seems that with body mass index (BMI) values ​​> 22.9, we already have cases of diabetes, that is, cases of diabetes occur earlier than expected.

* ***pedigree***: It seems that with pedigree values ​​> 0.09 (very low), we already have cases of diabetes, that is, it seems that there is a very high prevalence in this population of a history of diabetes, which could explain why diabetes appears earlier than expected, with the other characteristics.

* ***age***: It seems that with age values ​​> 43, we already have cases of diabetes, that is, cases of diabetes occur earlier than expected.

The level of outliers is acceptable in all cases.

It seems that this bivariate analysis has revealed the enormous importance of pedigree in suffering from diabetes.

<p><br></p> 

[ChatGPT usage](../CHATGPT_USAGE.md)  

<p><br></p>

[Back to Table of contents :arrow_double_up:](../README.md)