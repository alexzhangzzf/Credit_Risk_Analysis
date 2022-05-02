# Credit Risk Analysis
## Overview of the analysis
In this analysis, we will empoly different machine learning algorithms to train and evaluate models with unbalanced classes using credit card credit risk dataset.  We will oversample the data with Random Over Sampler and SMOTE algorithms, undersample the data using the Cluster Centroids algorithm and use a combinatorial approach of over and undersampling using SMOTEENN algorithm. We will also compare two new machine learning models that reduce bias ( Balanced Random Forest Classifier and Easy EnsembleClassifier ) to predict credit risk. We will evalute the performances of each model and recommand the bet one for credit risk analysis. 
## Results
Six machine learning algorithms are used to train and predict credit risk. We will use balanced accuracy scores and precision and recall scores of all six machine learning models to evaluate and compare the models for predicting credit risk.

- Naive Random Oversampling
Naive random oversampling algorithm is used to train and predict loan status and balanced accuracy score and classification report are calculated, shown below. <br/>
![ROS](/Resources/ROS.png) <br/>
Balanced accuracy score is 0.64, meaning 64% of the predicted data is accurate, which is a not highly accurate. The recall score for high risk and low risk are similar : 0.66 and 0.62, indicating more than 50% of the real high risk and low risk cases are correctly classified. However, the highly unbalanced data create extreame precision score for high risk and low risk. Precision score for low risk is 1, meaning that low risk case is 100% correctly classified. On the contrary, precision score for high risk case is 0.01, meaning that out of 100 cases of high risk only 1 is real high risk, 99% are false positives. 
- SMOTE Oversampling
SMOTE algorithm is used for oversampling the same dataset. The balanced accuracy score and classification report are shown below.<br/>
![SMOTE](/Resources/SMOTE.png) <br/>
Using SMOTE, balanced accuracy score is 0.65, slightly more accurate than random oversampling. Precision score for high risk and low risk is the same as random oversampling algorithm, 0.01 for high risk and 1 for low risk. It means all classified low risk cases are correct while 99% of high risks are false positive. The recall score for high risk is 0.61, lower than random sampling; recall socre for low risk is 0.69, slightly higher than random sampling. Lower recall for high risk and higher recall score for low risk indicate more high risk identified as low risk and less low risk identified as high risk, which may not be a good thing for predicting credit risk as we would rather have low risk falsely identified as high risk than high risk falsely identified as low risk. 
- Cluster Centroids Undersampling 
Using Cluster Centroids undersampling algorithm, same values were calculated, shown below.<br/>
![CC](/Resources/CC.png) <br/>
Using model of undersampling, balanced accuracy score is even lower as 0.544. The precision score stays the same for high risk and low risk (0.01 and 1). The recall score for high risk increases to 0.69 ; recall score for low risk decreases to 0.40. This indicate that 69% high risk are correctly identified while only 40% of low risk are correctly identified. For predicting credit risk, higher recall score for high risk maybe more important than recall score for low risk as we don't want to risk giving loan to high risk group but would rather risk rejecting a low risk case. So this model could work better than oversampling if the precision stays the same.
- Combination Sampling using SMOTEENN
We use combination sampling method ( SMOTEENN ) to predict and generate accuracy and classification report, as shown below.<br/>
![SMOTEENN](/Resources/SMOTEENN.png) <br/>
Using combination of both over and under sampling, the balanced accuracy is 0.645, similar to the accuracy score for oversampling. The precision score stays the same as 0.01 and 1. Recall score for high risk increases to 0.72 while recall score for low risks is 0.57, lower than oversampling but higher than undersampling.  Since correctly identifying high risk is more important, 0.72 for high risk is more favourable than previous sampling method. 
- Balanced Random Forest Classifier
Next we employ ensemble algorithm Balanced Random Forest Classifier to train the data and calculate balanced accuracy score and imbalanced classification report.<br/>
![BRF](/Resources/BRF.png) <br/>
Using balanced random forest model generate considerably more accurate predictions. Accuracy score increases to 0.7885. Precison score for low risk stays the same as 1. Precison score for high risk increases to 0.03, meaning that 3% of predicted high risk is correct. Recall score for both high risk and low risk increase to 0.70 and 0.87, a significant increase from over and under sampling models. It shows that ensemble algorithms predicts credit risk better than over and under sampling models.
- Easy Ensemble AdaBoost Classifier
Last but not the least, we used Easy Ensemble AdaBoost classifier for the data, scores shown below. <br/>
![EEC](/Resources/EEC.png) <br/>
Accuracy score increases to 0.9317, indicating 93% of predicted classification is correct. Precision for low risk remains 1. Precision for high risk increases to 0.09. Recall scores for low risk and high risk are 0.92 and 0.94, meaning that 92% of high risk and 94% of low risk are correctly labeled. Overall scores are considerably better than all previous models.

## Summary
- We used six machine learning algorithms (four over and under sampling algorithm and two ensemble classifier) to train and predict credit risk data. By comparing balanced accuracy score and precision and recall scores, we showed that overall accuracy is over 50% for all models. The precision score for low risk is 100% while the precision score for high risk is low due to extrement unbalanced data. Overall recall scores are over 50%, indicating half of the predicted results are correctly labeled. 
- For over and under sampling models, they are relatively similar however, for this dataset, combination of both over and under sampling model seems better in predicting high risk groups correctly, which is important for credit risk.
- Between over and under sampling algorithms and ensemble algorithms, ensemble learners are significantly more accurate in predicting credit risk for both high risk and low risk groups. Easy Ensemble AdaBoost Classifier is better than Balanced Random Forest Classifier in predicting credit risk with over 90% in balanced accuracy and recall scores. 
- Based on our result and comparison, I will recommand using Easy Ensemble AdaBoost Classifer for credit risk analysis as it can correctly classifies high and low risk groups with over 90% accuracy. Even though the precision for high risk group is still low as 0.09, classifiying low risk as high risk in high risk group is a trade off which is acceptable for financial consideration. 
