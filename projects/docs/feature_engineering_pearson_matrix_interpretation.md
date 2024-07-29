# Feature Engineering (Pearson matrix interpretation)  

## Pearson matrix interpretation  

***Note***: For a heatmap to work correctly, the data must already be in matrix form; the sns.heatmap function essentially colors it.  

If we exclude the relationship of the variables with themselves (diagonal of ones), we see that they are very related:  

* **pregnancies** and **age** (0.54): Obviously, with age, the probability of pregnancies decreases, but we cannot extrapolate that relationship with diabetes.  

* **diabetes** and **glucose** (0.49): [See business rules](https://github.com/ddasilva64/DECTRE24001esp/tree/master/projects/docs/executive_summary_business_rules.md).

* **diabetes** and **BMI** (0.29): [See business rules](https://github.com/ddasilva64/DECTRE24001esp/tree/master/projects/docs/executive_summary_business_rules.md).  

* **diabetes** and **age** (0.24): [See business rules](https://github.com/ddasilva64/DECTRE24001esp/tree/master/projects/docs/executive_summary_business_rules.md).  

* **pressure** and **age** (0.27): [See business rules](https://github.com/ddasilva64/DECTRE24001esp/tree/master/projects/docs/executive_summary_business_rules.md).  

* **glucose** and **age** (0.31): [See business rules](https://github.com/ddasilva64/DECTRE24001esp/tree/master/projects/docs/executive_summary_business_rules.md).  

* **pressure** and **BMI** (0.25): It is significant, but we cannot extrapolate that relationship with diabetes.  

* **glucose** and **BMI** (0.22): It is significant, but we cannot extrapolate that relationship with diabetes.  

* **glucose** and **pressure** (0.21): It is significant, but we cannot extrapolate that relationship with diabetes.  

In our study, it seems that for now, glucose, BMI, and age are highly related to diabetes.  

The predigree, which in the [business rules](https://github.com/ddasilva64/DECTRE24001esp/tree/master/projects/docs/executive_summary_business_rules.md) is highly related, in our model, does not seem to be. It could be because it is the result of a function.  

<p><br></p> 

[ChatGPT usage](../CHATGPT_USAGE.md)  

<p><br></p>

[Back to Table of contents :arrow_double_up:](../README.md)