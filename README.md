# Credit Risk Analysis

## Overview

The purpose of this analysis is to assess the risk of credit card loans.  Credit card loans tend to be hihgly imbalanced meaning that a very large number of loans are good (re-paid) and a very small number of loans are bad (not re-paid).  Imbalanced problems are particularly challenging for machine lerning algorithms becuase the dataset of "bad" is so small the model can appear to be quite accurate even as it misses almost everything it's meant to identify.  This project invovled testing 6 different machine leraning methods to see if any might perform well enough to be used to assess the risk of credit card loans automatially.  

## Analysis

The analysis started with perparing the data which meant converting all data columns to numeric data to allow the machine learning algorithms to run.  And, then the data was split into training and testing data sets.  

The first analysis employed random oversampling.  Oversampling attempts to increae the size of the target group to make it easier to learn from.  This produced an accuracy of 63.5%.  Precision of the model was very poor though and many good loans were labelled as bad by the algorithm.  Recall, or sensitivity, was higher but at 62% it reflects that it flagged more loans as bad than actually were.   

![Random Oversampling Classification Report](https://github.com/hal1277/credit_risk_analysis/blob/fa2a6c41097b21bf701409cc354adc9d04c22657/Images/random_oversampling.png)

The second analysis used SMOTE oversampling.  This prdouced similar results to the random oversampling with an accuracy of 63%.  Precision was also very low and recall was higher becuase again it flagged more loans as bad than actually were.  This model also flagged a similarly large number of goods loans as bad as the random oversampling model.  

![SMOTE Oversampling Classification Report](https://github.com/hal1277/credit_risk_analysis/blob/fa2a6c41097b21bf701409cc354adc9d04c22657/Images/SMOTE_oversampling.png)

The third analysis used undersampling which reduces the number of samples of goods loans so they don't outweitgh the bad loan data so much.  This also produced an accuracy of 63% with low precision on the bad loans and a very poor recall, sensitivity, on the good loans with a very large number of them being flagged as bad loans by the model.  

![Undersampling Classification Report](https://github.com/hal1277/credit_risk_analysis/blob/fa2a6c41097b21bf701409cc354adc9d04c22657/Images/undersampling.png)

The fourth analysis used combination (over and under) sampling but resulted in an accuracy of only 52.9% again with low precision and simliar recall as the random oversampling and SMOTE oversampling models.  

![Combination Sampling Classification Report](https://github.com/hal1277/credit_risk_analysis/blob/fa2a6c41097b21bf701409cc354adc9d04c22657/Images/combination_sampling.png)

The fifth analysis used the Random Forest Classifier model which breaks the problem down into many smaller decision trees and takes a concensus.  It has a slightly higher accuracy of 66%.  But, precision was much higher at 78% as very few good loans were identified as bad by the model.  Recall was low at 32% because the model missed a large portion of the actual bad loans and flagged them as good.   

![Random Forest Classification Report](https://github.com/hal1277/credit_risk_analysis/blob/fa2a6c41097b21bf701409cc354adc9d04c22657/Images/random_forest_classifier.png)

The sixth and final analysis was done using Easy Ensemble AdaBoost Classifier.  It has the highest accuracy at 92.5%.  Precision was low because a significant number of good loans were identified as bad by the model.  However, recall was very high as the model correctly identified nearly every bad loan.  

![Easy Ensemble AdaBoost Classification Report](https://github.com/hal1277/credit_risk_analysis/blob/fa2a6c41097b21bf701409cc354adc9d04c22657/Images/easy_ensembe_adaboost_classifier.png)

## Summary

After running the 6 models and reviewing the results it can be seen that the Random Forest and East Ensemble AdaBoost models significatnly outperformed all of the versions of under and over sampling models.  I would recommend the use of the Easy Ensemble AdaBoost Classifier model.  It has the highest overall accuracy but also the highest recall meaning it did the best job of identifying the bad loans in the dataset which is ultimately the purpose of this model.  Precision is somewhat sacrificed in this model, meaning that a number of good loans are idenfitied as bad when they are in fact not bad.  But, risk is higher if a loan is mis-identified as good when it is in fact bad since that is money that will not be re-paid by the client.  The lending institution can implement a process to have an employee do a seconday review of loans identified as bad by the model or further work can be done to refine this model by feature selection to tune the model to perform better.  