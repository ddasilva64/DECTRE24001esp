## Executive Summary  

### **_Probability & Statistics notes_**  

## Average  

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Average</span>][r000]***: Refers to the arithmetic mean, the sum of numbers divided by how many numbers are averaged. ***It has the disadvantage that it is very susceptible to outliers***.  

![Average][i000]  

## Median  

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Median</span>][r001]***: In the field of statistics, it represents the value of the variable in the central position in a set of ordered data.  

![Median][i001]  

## Mode  

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Mode</span>][r002]***: In statistics, it is the value that appears most frequently in a set of data. ***It is only applicable to discrete (non-continuous) variables***.

![Mode][i002]  

## Bias

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Bias</span>][r003]***: In Statistics, the bias of an estimator is the difference between its mathematical expectation and the numerical value of the parameter it estimates. ***An estimator whose bias is zero is called unbiased or centered***.

* ***Unbiased (centered) distribution*** => ***average = median = mode*** (bayesian distribution).

* ***Right-skewed distribution (positive skew)*** => ***mode < median < average***. A distribution is skewed to the right ***if the right tail*** (the side with larger values) ***is longer or stretched out compared to the left tail***. This means that ***most of the data points are concentrated on the left side of the distribution***, while a few extreme values ​​push the mean to the right. ***The average is usually greater than the median*** in a right-skewed distribution.

* ***Left-skewed distribution (negative skew)*** => ***mode > median > average***. A distribution is skewed to the left ***if the left tail*** (the side with smaller values) ***is longer or stretched out compared to the right tail***. This means that ***most of the data points are concentrated on the right side of the distribution***, while a few extreme values ​​push the mean to the left. ***The average is usually smaller than the median*** in a left-skewed distribution.  

![Bias][i003]  

## Measures of central tendency

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Measures of central tendency</span>][r017]***: The measure of central tendency (mode, mean and median), ***parameter of a central tendency or measure of centralization is a number located towards the center of the distribution of the values ​​of a series of observations (measures)***, in which the set of data is located.

As we have seen, the measure of central tendency depends on the asymmetry (skewness), although kurtosis also influences it, for example, a large number of outliers causes a very flat kurtosis and normally the best indicator would be the mode, but if kurtosis is very sharp, it could be the median.

![Measures of central tendency][i017]  

***Outliers can alter the measure of central tendency***, i.e. the indicator can vary. ***If outliers are not treated properly, the entire interpretation of our data can be wrong!***  

## Range  

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Range</span>][r004]***: The range is the numerical difference between the maximum value and the minimum value. ***It provides an idea of ​​the dispersion of the data***.

## Probability distributions

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Probability distributions</span>][r018]***: In ***Statistics, a data distribution*** refers to the ***pattern or dispersion of values*** ​​that a ***variable*** can adopt ***within a dataset***. It describes ***how*** the values ***​​are distributed*** between the different **possible results**.

![Probability distribution][i008]  

## Normal or gaussian distribution

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Normal or gaussian distribution</span>][r019]***: It is a ***symmetrical bell-shaped distribution where the mean, median and mode are all equal. It is characterized by*** its ***mean and standard deviation***.  

![Normal or gaussian distribution][i019]  

## Uniform distribution

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Uniform distribution</span>][r020]***: A distribution in which ***all values*** within a specific range ***have the same probability of occurring. It is characterized by*** a ***constant probability density function over the entire range***.  

![Uniform distribution][i020]  

## Binomial distribution

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Binomial distribution</span>][r021]***: It is a discrete probability distribution that describes the ***number of successes in a fixed number*** of ***independent*** Bernoulli ***trials, each with the same probability of success***.

![Binomial distribution][i021]  

## Poisson distribution

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Poisson distribution</span>][r022]***: It is a discrete probability distribution that ***describes the number of events that occur in a fixed interval of time or space, given a constant rate of occurrence and independence between events***.

![Poisson distribution][i022]  

## Exponential distribution

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Exponential distribution</span>][r023]***: It is a continuous probability distribution that ***describes the time between events in a Poisson process, where events occur continuously and independently at a constant rate***.

![Exponential distribution][i023]  

## Gamma distribution

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Distribución gamma</span>][r024]***: It is a continuous probability distribution that ***generalizes the exponential distribution and describes the time to the nth event in a Poisson process***.

![Gamma distribution][i024]  

## Chi-squared distribution

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Chi-squared distribution</span>][r025]***: It is a continuous probability distribution that arises in the context of hypothesis testing and ***describes the distribution of the sum of the squared standard normal deviations***.

![Chi-squared distribution][i025]  

## Student's t distribution

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Distribución t de Student</span>][r026]***: It is a continuous probability distribution that ***has a shape similar to the normal distribution but has heavier tails. It is commonly used in hypothesis testing when the sample size is small and the population standard deviation is unknown***.

![Student's t distribution][i026]  

## Statistical Analysis (for EDA)

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Univariate analysis</span>][r005]***: Univariate analysis involves describing the distribution of a single variable. The shape of the data distribution can also be described by indices such as ***skewness*** and ***kurtosis***. The characteristics of the distribution of a variable can also be represented in the form of ***histograms, box plots, bar graphs, and summary statistics such as mean, median, and mode***.

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Bivariate analysis</span>][r006]***: It involves analyzing the relationship between two variables. It helps to understand how one variable changes with respect to another variable. Common techniques include ***scatter plots, correlation analysis, and cross tabulation***.

* ***[<span style="font-family:Verdana; font-size:0.95em;color:red">Multivariate analysis</span>][r007]***: It involves analyzing more than two variables simultaneously. It helps to understand the relationships and interactions between multiple variables. Common techniques include ***principal component analysis, factor analysis, and cluster analysis***.

Data analysts and scientists gain:
* ***Insights into data***
* ***Pattern identification***
* ***Relationships within data***
* ***Outliers***
* ***Reasons for making informed decisions***  

## Standard deviation

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Standard deviation</span>][r008]***: The standard deviation measures the ***dispersion of the data around the mean***. It is the ***square root of the variance***, which in itself is not a measure of dispersion.

![Standard deviation][i008]

## Variance

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Variance</span>][r009]***: Returns the sample variance, which must be an iterable of at least two real numbers. The variance, or second-order moment about the mean, is a ***measure of the variability (spread or dispersion) of the data***.

A ***high variance indicates that the data are spread out***; a ***low variance indicates that the data are clustered closely around the mean***.

![Variance][i009]

The image shows an example of samples from two populations with the same mean but different variances. The red population has mean 100 and variance 100 (standard deviation=10) while the blue population has mean 100 and variance 2500 (standard deviation=50).  

## Quartile 1 (25th percentile)

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Quartile 1</span>][r010]***: The concept is the same as that of the median, except that here the division is no longer at 50%. 25% of the observations are less than the first quartile.

![Quartile 1][i010]

## Quartile 2 (50th percentile)

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Quartile 2</span>][r011]***: The concept is the same as that of median, here the division is at 50%. 50% of the observations are less than the second quartile.

![Quartile 2][i011]

## Quartile 3 (75th percentile)

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Quartile 3</span>][r012]***: The concept is the same as that of median, except that here the division is no longer at 50%. 75% of the observations are less than the third quartile.

![Quartile 3][i012]  

## Interquartile range

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Interquartile range</span>][r013]***: The interquartile range or IQR is the difference between the third and first quartiles. It is a measure of statistical dispersion. ***It is an appropriate measure of variability when the central position measure used has been the median***.

It is defined as the difference between the third quartile (Q3) and the first quartile (Q1), that is: RQ = Q3 - Q1. Half of the interquartile range is known as the quartile deviation (QD), and is affected very little by extreme counts. This makes it a ***good measure of dispersion for skewed distributions***: DQ = RQ/2= (Q3 - Q1)/2.

It is used to construct ***box plot diagrams*** that serve to visualize the variability of a variable and compare distributions of the same variable; in addition to ***locating outliers***.

![Interquartile range][i013]  

## Upper limit outliers

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Upper limit outliers</span>][r014]***: These are the points to the right of the whiskers of the Q3 + 1.5 x IQR box.

![Upper limit outlier][i014]  

## Lower limit outliers

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Lower limit outliers</span>][r015]***: These are the points to the left of the whiskers of the Q1 box - 1.5 x IQR.

![Lower limit outliers][i015]  

## Number of outliers and how to treat them

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Number of outliers and how to treat them</span>][r016]***: The outliers would be the points to the left of the whiskers of the box plot (Q1 - 1.5 x IQR) and the points to the right of the whiskers of the box (Q3 + 1.5 x IQR).

***How ​​to treat outliers***

Once the outliers have been identified, we must decide what to do with them. There are different methods to manage them. The choice between one or the other will depend on the context and the objectives of the analysis. Some of these methods are:

* ***Keep them***: We can ***keep the outliers if we consider that they may be representative of a subset of our data***.

* ***Remove them***: ***If we are sure*** that the outliers come from an ***error in the data entry, such as a human or measurement error, and we cannot fix it***, we can remove them from the dataset.

To do this, we can filter the dataset.

* ***Imputation***: Imputation involves ***replacing outliers with other values ​​such as the median or mean***. This is usually done when we want to keep the largest amount of data, but eliminating the effect of outliers.

* ***Winzorization***: Winsorization is a technique that ***replaces outliers with the closest value that is not considered an outlier*** according to certain criteria.

![Number of outliers][i016]  

## Pearson correlation coefficient

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Pearson correlation coefficient</span>][r027]***: The ***Pearson correlation coefficient*** is a test that ***measures the statistical relationship between two continuous variables***. If the association between the elements is not linear, then the coefficient is not adequately represented.

| R value | Strength of correlation |
| :-------: | :----------------------- |
| 0.0 < 0.1 | no correlation |
| 0.1 < 0.3 | low correlation |
| 0.3 < 0.5 | medium correlation |
| 0.5 < 0.7 | high correlation |
| 0.7 < 1 | very high correlation |

The correlation coefficient can take a range of values ​​from +1 to -1.

A value greater than 0 indicates that there is a positive correlation. In this case the variables would be directly associated. The closer to +1, the higher their association. An exact value of +1 would indicate a perfect positive linear relationship.

![Pearson correlation coefficient][i027]  

## Pearson correlation matrix

***[<span style="font-family:Verdana; font-size:0.95em;color:red">Pearson correlation matrix</span>][r028]***: The correlation matrix shows the correlation values, which measure the degree of linear relationship between each pair of variables. Correlation values ​​can range from -1 to +1. If the two variables tend to increase or decrease at the same time, the correlation value is positive.

![Pearson correlation matrix][i028]  

## External references list  

* Average (Wikipedia)  

[r000]: https://en.wikipedia.org/wiki/Average "reference to average in Wikipedia"

* Median (Wikipedia)  

[r001]: https://en.wikipedia.org/wiki/Median "reference to median in Wikipedia"

* Mode (Wikipedia)  

[r002]: https://en.wikipedia.org/wiki/Mode_(statistics) "reference to mode in Wikipedia"

* Bias (Wikipedia)  

[r003]: https://en.wikipedia.org/wiki/Bias_of_an_estimator "reference to bias in Wikipedia"

* Range (Wikipedia)  

[r004]: https://es.wikipedia.org/wiki/Rango_(estad%C3%ADstica) "reference to range in Wikipedia"

* Univariate analysis (Wikipedia)  

[r005]: https://en.wikipedia.org/wiki/Descriptive_statistics#Univariate_analysis "reference to univariate analysis in Wikipedia"

* Bivariate analysis (Wikipedia)  

[r006]: https://en.wikipedia.org/wiki/Descriptive_statistics#Bivariate_and_multivariate_analysis "reference to bivariate analysis in Wikipedia"

* Multivariate analysis (Wikipedia)  

[r007]: https://en.wikipedia.org/wiki/Descriptive_statistics#Bivariate_and_multivariate_analysis "reference to multivariate analysis in Wikipedia"

* Standard deviation (Wikipedia)  

[r008]: https://en.wikipedia.org/wiki/Standard_deviation "reference to standard deviation in Wikipedia"

* Variance (Wikipedia)  

[r009]: https://en.wikipedia.org/wiki/Variance "reference to variance in Wikipedia"

* Quartile 1 (Wikipedia)   

[r010]: https://en.wikipedia.org/wiki/Percentile "reference to quartile 1 in Wikipedia"

* Quartile 2 (Wikipedia)   

[r011]: https://en.wikipedia.org/wiki/Percentile "reference to quartile 2 in Wikipedia"

* Quartile 3 (Wikipedia)   

[r012]: https://en.wikipedia.org/wiki/Percentile "reference to quartile 3 in Wikipedia"

* Interquartile range (Wikipedia)   

[r013]: https://en.wikipedia.org/wiki/Interquartile_range "reference to interquartile range in Wikipedia"

* Upper limit outliers (Wikipedia)   

[r014]: https://en.wikipedia.org/wiki/Outlier#Tukey's_fences "reference to upper limit outliers in Wikipedia"

* Lower limit outliers (Wikipedia)   

[r015]: https://en.wikipedia.org/wiki/Outlier#Tukey's_fences "reference to lower limit outliers in Wikipedia"

* How to identify and handle outliers with Python (Medium)

[r016]: https://medium.com/@martacasdelg/c%C3%B3mo-identificar-y-tratar-outliers-con-python-bf7dd530fc3 "reference to how to identify and handle outliers with Python in Medium"

* Measures of central tendency (Wikipedia)

[r017]: https://en.wikipedia.org/wiki/Central_tendency "reference to measures of central tendency in Wikipedia"

* Probability distribution (Wikipedia)

[r018]: https://en.wikipedia.org/wiki/Normal_distribution "reference to probability distribution in Wikipedia"

* Normal or gaussian distribution (Wikipedia)

[r019]: https://en.wikipedia.org/wiki/Normal_distribution "reference to normal or gaussian distribution in Wikipedia"

* Uniform distribution (Wikipedia)

[r020]: https://en.wikipedia.org/wiki/Continuous_uniform_distribution "reference to uniform distribution in Wikipedia"

* Binomial distribution (Wikipedia)

[r021]: https://en.wikipedia.org/wiki/Binomial_distribution "reference to binomial distribution in Wikipedia"

* Poisson distribution (Wikipedia)

[r022]: https://en.wikipedia.org/wiki/Poisson_distribution "reference to Poisson distribution in Wikipedia"

* Exponential distribution (Wikipedia)

[r023]: https://en.wikipedia.org/wiki/Exponential_distribution "reference to exponential distribution in Wikipedia"

* Gamma distribution (Wikipedia)

[r024]: https://en.wikipedia.org/wiki/Gamma_distribution "reference to gamma distribution in Wikipedia"

* Chi-squared distribution (Wikipedia)

[r025]: https://en.wikipedia.org/wiki/Chi-squared_distribution "reference to Chi-squared distribution in Wikipedia"

* Student's t-distribution (Wikipedia)

[r026]: https://en.wikipedia.org/wiki/Student%27s_t-distribution "reference to student's-t distribution in Wikipedia"

* Pearson correlation coefficient (DataTab)

[r027]: https://datatab.es/tutorial/pearson-correlation "reference to Pearson correlation coefficient in DataTab"

* Pearson correlation matrix (Wikipedia)

[r028]: https://en.wikipedia.org/wiki/Correlation#Correlation_matrices "reference to Pearson correlation matrix in Wikipedia"

## Pictures list

* Average  

[i000]: https://i.imgur.com/xA8EIFr.png "Average"

* Median  

[i001]: https://i.imgur.com/3QaFjUZ.png "Median"

* Moda  

[i002]: https://i.imgur.com/sq8tQ8H.png "Moda"

* Bias  

[i003]: https://i.imgur.com/I0Q0IA2.png "Bias"

* Standard deviation  

[i008]: https://i.imgur.com/34s7Flh.png "Standard deviation"

* Variance  

[i009]: https://i.imgur.com/PnRDpZU.png "Variance"

* Quartile 1 (percentile 25)  

[i010]: https://i.imgur.com/jXR2Wlw.png "Quartile 1 (percentile 25)"

* Quartile 2 (percentile 50)  

[i011]: https://i.imgur.com/n64wNxa.png "Quartile 2 (percentile 50)"

* Quartile 3 (percentile 75)  

[i012]: https://i.imgur.com/08Pt7BD.png "Quartile 3 (percentile 75)"

* Interquartile range  

[i013]: https://i.imgur.com/AeddtFp.jpg "Interquartile range"

* Upper limit outliers  

[i014]: https://i.imgur.com/RM6RVH6.jpg "Upper limit outliers"

* Lower limit outliers  

[i015]: https://i.imgur.com/pEbuiPP.png "Lower limit outliers"

* Number of outliers  

[i016]: https://i.imgur.com/wqxNpIK.png "Number of outliers"

* Measures of central tendency  

[i017]: https://i.imgur.com/a35E15z.png "Measures of central tendency"

* Normal or gaussian distribution

[i019]: https://i.imgur.com/ozdxtvE.png "Normal or gaussian distribution"

* Uniform distribution

[i020]: https://i.imgur.com/QO1kKuV.png "Uniform distribution"

* Binomial distribution

[i021]: https://i.imgur.com/y8MpqqY.png "Binomial distribution"

* Poisson distribution

[i022]: https://i.imgur.com/MuiQM2y.png "Poisson distribution"

* Exponential distribution

[i023]: https://i.imgur.com/PIm1tbK.png "Exponential distribution"

* Gamma distribution

[i024]: https://i.imgur.com/fXVkZbu.png "Gamma distribution"

* Chi-squared distribution

[i025]: https://i.imgur.com/rDeq5U4.png "Chi-squared distribution"

* Student's t-distribution

[i026]: https://i.imgur.com/4VWVQBz.jpg "Student's t-distribution"

* Pearson correlation coefficient

[i027]: https://i.imgur.com/okjY0k8.png "Pearson correlation coefficient"

* Pearson correlation matrix

[i028]: https://i.imgur.com/Yspew2y.png "Pearson correlation matrix"

<p><br></p> 

[ChatGPT usage](../CHATGPT_USAGE.md)  

<p><br></p>

[Back to Table of contents :arrow_double_up:](../README.md)