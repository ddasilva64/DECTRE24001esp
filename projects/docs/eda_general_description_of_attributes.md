## EDA (Exploratory Data Analysis)  

### **_General description of attributes_**   

The dataset consists of 768 instances (from 0 to 767) and 9 attributes (no duplicates), containing medical information of native Pima women from Arizona (USA), who participated in a diabetes study in 1984.

***There are 9 variables (attributes) in the dataset***

- **Pregnancies:** Number of pregnancies.
- **Glucose:** Plasma glucose concentration at 2 hours in an oral glucose tolerance test ($\frac{mg}{dL}$).
- **Blood pressure:** Diastolic blood pressure (mm Hg).
- **Skin thickness:** Triceps skin fold thickness (mm).
- **Insulin:** 2-hour serum insulin concentration ($mu=\frac{U}{ml}; U=insulin\ units$).
- **BMI:** Body Mass Index ($\frac{weight\ in\ Kg}{(height\ in\ m)^2}$).
- **Diabetes pedigree function:** Diabetes function based on family history.
- **Age:** Age (years).
- **Diabetes:** Target variable in the test (1 = diabetes, 0 = no diabetes).

**Note**: We do not know if the woman is pregnant at the time of the oral glucose tolerance test. Therefore, we cannot detect gestational diabetes, which is a limitation of our dataset.

***Data types***  
- Most columns (7 out of 9) are of type `int64`, representing integer values.
- Two columns (5 and 6) are of type `float64`, representing floating-point values.

***Null and missing values***  
There do not appear to be any missing or null values in the dataset as each column has 768 non-null entries, but many zeros do appear.

***Duplicate values***  
There are no duplicate values present in the dataset, ensuring data integrity and reliability. Each row is unique among the 768 entries.

<p><br></p> 

[ChatGPT usage](../CHATGPT_USAGE.md)  

<p><br></p>

[Back to Table of contents :arrow_double_up:](../README.md)