# Modeling (Metrics interpretation)  

## Metrics interpretation

* ***precision*** (positive predictive value): Proportion of relevant instances among the retrieved instances. In other words, it answers the question "What proportion of positive identifications have actually been correct?"

diabetes $=\frac{TP}{TP+FP}=\frac{33}{33+13}=\frac{33}{46}=0.72$

* ***recall*** (sensitivity or hit rate or true positive rate -TPR-): Proportion of the total number of relevant instances that have actually been retrieved. It answers the question "What proportion of true positives have been correctly identified?"  

diabetes $=\frac{TP}{TP+FN}=\frac{33}{33+22}=\frac{33}{55}=0.60$

* ***f1-score***: This is a measure of the accuracy of a test, it is the harmonic mean of precision and recall. It can have a maximum score of 1 (perfect precision and recall) and a minimum of 0. In general, it is a measure of the accuracy and robustness of your model  

diabetes $=\frac{2xprecisionxrecall}{precision+recall}=\frac{2x0.72x0.60}{0.72+0.60}=\frac{0.86}{1.32}=0.65$

* ***accuracy***: Proportion of predictions that the model has classified correctly.  

diabetes $=\frac{number of correct predictions}{number of predictions}=\frac{TP+TN}{TP+TN+FP+FN}=\frac{33+86}{33+86+13+22}=\frac{119}{154}=0.77$

The model identifies non-diabetic cases very well and diabetes cases a little worse. It is better, in a first analysis, to diagnose a healthy person than a sick one, since a second test will clarify whether the diabetes prediction is correct.

***A diabetic diagnosed as healthy and ruled out for a second test would be a disaster! Therefore, the prediction is correct!***. 

<p><br></p> 

[ChatGPT usage](../CHATGPT_USAGE.md)  

<p><br></p>

[Back to Table of contents :arrow_double_up:](../README.md)