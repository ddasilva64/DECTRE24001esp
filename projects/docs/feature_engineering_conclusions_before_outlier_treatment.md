# Feature Engineering (conclusions before outlier treatment)  

## Conclusions

It is clear that we need to find a different strategy than simply deleting rows that have outliers.

If we were to delete rows with outliers, we would be left with half the data, and this would reduce our expectations for classification or making predictions with the dataset.

***We will choose*** the mean ***imputation algorithm to remove outliers*** from the dataset while maintaining the rows (measurements). This is typically done ***when we want to preserve the maximum amount of data but eliminate the effect of outliers***.

## Strategy (for each feature where we want to remove outliers):

1. ***Obtain the interval of non-outliers***.
2. ***Calculate the mean of the non-outliers***.
3. ***Replace the outliers with the obtained mean***.

<p><br></p> 

[ChatGPT usage](../CHATGPT_USAGE.md)  

<p><br></p>

[Back to Table of contents :arrow_double_up:](../README.md)