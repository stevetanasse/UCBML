# IoT Device Classification
[iot_classification.ipynb](iot_classification.ipynb)

**Research Question**  
Which feature selection approach and machine learning model best classifies known and unknown IOT device network activity?

**Original Data Source**  
[Machine-Learning-for-Cybersecurity-Cookbook/Chapter05
/IoT Device Type Identification Using Machine Learning](https://github.com/PacktPublishing/Machine-Learning-for-Cybersecurity-Cookbook/tree/master/Chapter05/IoT%20Device%20Type%20Identification%20Using%20Machine%20Learning)

**Description**  
Identifying IOT network connection activity (security cameras, thermostats, etc.) is relevant for network security. Some network devices have logs or applications allowing you to view device connections, but sometimes meaningful information about the device type is missing. The goal of this machine learning project is to classify IoT network connections as their recognized type or as "unknown" when connections cannot be identified, in order to alert the user to scrutinize that network activity. The content appears in IoTClassification.ipynb

**Machine Learning Concepts**
LASSO, Random Forest Feature Impurity and SelectKBest feature selection techniques will be used. Decision Tress, Logistic Regression, Random Forests, Support Vector Classifiers and ensemble techniques will be compared to find the highest performing model.

**Expected Results**
Various feature selection techniques and machine learning models will be trained and results will be analyzed and compared. Benefits and trade-offs between approaches will be summarized.