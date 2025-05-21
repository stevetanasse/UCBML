# IoT Device Classification
[iot_classification.ipynb](iot_classification.ipynb)

**Research Question**  
Which machine learning model best classifies IOT device network activity? Can probability thresholds be used to detect the presence of unknown IoT device network activity?

**Original Data Source**  
[Machine-Learning-for-Cybersecurity-Cookbook/Chapter05
/IoT Device Type Identification Using Machine Learning](https://github.com/PacktPublishing/Machine-Learning-for-Cybersecurity-Cookbook/tree/master/Chapter05/IoT%20Device%20Type%20Identification%20Using%20Machine%20Learning)

**Description**  
Identifying IOT network connection activity (security cameras, thermostats, etc.) is relevant for network security. Some network devices have logs or applications allowing you to view device connections, but sometimes meaningful information about the device type is missing. The goal of this machine learning project is to classify IoT network connections as their recognized IoT device type and to investigate if probability thresholds can be used to classify samples not trained on the model as an "unknown" connection. The ability to identify IoT connections in this way can be used alert the user and scrutinize IoT network activity.

**Machine Learning Concepts**
Decision Tree, Logistic Regression, Random Forest, XGBoost, Neural Network and ensemble techniques will be compared to find the highest performing model.

**Conclusion**
The OneVsRest, Random Forest, XGBoost classifiers all tied for the highest accuracy (0.855) and the OneVsRest (Baseline) achieved the highset precision (0.869). Both OneVsRest classifiers tied for the highest recall (0.847). The highest f1 scores were achieved by the Random Forest and XGBoost classifiers (0.839). This performance contrasts with the validation set results, where the Random Forest classifier performed best overall, with an accuracy of 0.845, precision of 0.838, recall of 0.825, and F1 score of 0.828. Interestingly, the test set metrics were slightly higher than those from the validation set—an unexpected outcome that suggests either random variation or possible differences in sample composition.

Several models produced identical accuracy values on the test set. To ensure these results were valid, confusion matrices were examined, and the number of correct predictions was tallied. Even though some models had the same number of correct predictions (325), the distribution of those predictions varied across classes, indicating differing classification behavior despite identical accuracy.

A recurring challenge for all models was accurately identifying the lights, socket, and water_sensor IoT device classes. Even after applying SMOTE oversampling to address class imbalance, the neural network showed no substantial improvement in classifying these three device types. LASSO feature selection revealed that these classes had the fewest distinguishing features, which likely contributed to their classification difficulty.

One objective of this project was to explore whether it is possible to distinguish unseen (untrained) IoT device types using the probability scores returned by predict_proba(). For most classifiers, successful predictions typically had a maximum class probability above 0.85, while unsuccessful predictions often fell between 0.2 and 0.8. However, both XGBoost and the neural network occasionally returned incorrect predictions with high confidence (probabilities above 0.8). Although there was a noticeable drop in successful predictions below a probability threshold of 0.85, a significant number of correct predictions still occurred below this threshold. As a result, no clear cutoff probability emerged for reliably detecting unseen classes.

To investigate this further, an XGBoost model was trained on all device classes except for the smoke_detector, which was treated as an unseen class. When tested on the excluded smoke_detector samples, the classifier predicted most of them as a watch (186 samples), with the remaining 14 samples distributed among motion_sensor, thermostat, and water_sensor. The predict_proba() values for these predictions formed a roughly normal distribution centered around 0.5, suggesting that untrained (unseen) samples yield outputs that resemble random classification behavior
