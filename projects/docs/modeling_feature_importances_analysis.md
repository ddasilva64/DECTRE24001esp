# Modeling (Feature importances analysis)  

## Feature importances analysis

An analysis of the feature importances (***feature importances***) reveals that the most influential for the model prediction are:

* ***glucose***: With an importance of 0.457435, it stands out as the most important feature. This indicates that ***blood plasma glucose concentration has a very significant impact on the prediction of diabetes***.

* ***bmi***: Body mass index (BMI) is the second most relevant feature, with an importance of 0.228741. This suggests that ***weight relative to height also plays a crucial role in the prediction of diabetes***.

* ***age***: Age is positioned as the third most important feature, with an importance of 0.050513. This indicates that ***the patient's age also contributes significantly to the prediction of the disease***.

* ***history***: The value of family history of diabetes has an importance of 0.044712. Although the value is very low, the data provided by the dataset is the result of a function that we do not know (black box), so it could be important, but much less than the previous three.

The remaining features ***(pregnancies and blood pressure) have relatively lower importance*** compared to the previous ones, but they still contribute to the prediction process. ***We insist that there are missing features to treat gestational diabetes, as well as other types of diabetes, in our model***.

<p><br></p> 

[ChatGPT usage](../CHATGPT_USAGE.md)  

<p><br></p>

[Back to Table of contents :arrow_double_up:](../README.md)