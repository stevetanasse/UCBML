[Assignment3]

## Objective
A term deposit an investment where money is deposited for a fixed period at a financial institution. The deposited money earns a set interest rate however, the funds cannot be accessed until the end of the term. The objective of analyzing the bank marketing is to determine the primary characteristics driving term deposit purchases and predicting when a customer will subscribe to a term deposit.

The data comes from the [Bank Marketing dataset](https://archive.ics.uci.edu/dataset/222/bank+marketing) from the UC Irvine Machine Learning Repository and consists of data from 17 marketing campaigns from a Portugese bank that occurred between May 2008 and November 2010.

## Conclusions
Recall was prioritized as the primary evaluation metric due to the class imbalance in the dataset and the business objective of avoiding missed sales opportunities. Under this assumption, false positives were considered tolerable if it meant capturing more true positives. The hyperparameter tuning of the Support Vector classifier, however was an exception and used F1 scoring instead. Otherwise, resulting SVC recall score would be 100% with poor precision.

None of the models demonstrated strong performance in predicting whether a customer would purchase a term deposit. There are two possible explanations for this outcome: (1) the dataset contains meaningful patterns that were not detected due to inadequate feature encoding or preprocessing, or (2) the features themselves may lack sufficient signal to distinguish between the target classes.

Among the models tested, the Support Vector Classifier (SVC) achieved the highest recall score at 0.81, but at the cost of a low precision score of 0.16. The next-best model in terms of recall was Logistic Regression, with a recall of 0.71 and a higher precision of 0.23.

The choice between the SVC and Logistic Regression depends on the acceptable cost of handling false positives. The SVC yields a 13.8% increase in true positives compared to Logistic Regression (91 vs. 80), but this comes with a 44.3% increase in false positives (476 vs. 265). If the operational cost of processing these additional false positives is acceptable, the SVC may be preferable. Otherwise, Logistic Regression offers a better balance between precision and recall, albeit with fewer captured positives.

Although the Decision Tree achieved the highest F1 score, its susceptibility to overfitting raises concerns about its ability to generalize to unseen data. As such, Logistic Regression and the SVC remain the more reliable options for deployment.

**Model Performance Summary**

| Model                      | Precision | Recall | F1       |
| ---------------------------|----------:|-------:|---------:|
| Baseline                   | 0.14      |   0.16 |   0.15   |
| Decision Tree              | 0.14      |   0.16 |   0.15   |
| Logistic Regression        | 0.14      |   0.16 |   0.15   |
| k-Nearest Neighbors        | 0.14      |   0.16 |   0.15   |
| Support Vector Classifier  | 0.14      |   0.16 |   0.15   |

</br>

**Logistic Regression Confusion Matrix**

|      | Predicted True | Predicted False |
|-----:|:---------------:|:--------------:|  
|True  | 80             | 33              |
|False | 265            | 652             |

</br>

**SVC Confusion Matrix**

|      | Predicted True | Predicted False |
|-----:|:---------------:|:--------------:|  
|True  | 91              | 22             |
|False | 476             | 441            |


