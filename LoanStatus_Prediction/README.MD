## Introduction

### 1) Acquisition and Understanding of the Dataset
The dataset that was used for the data analysis and prediction is Loan_status_2007-2020Q3.gzip . It was retrieved from Lending Club Datasets and sourced in the Kaggle Website. **LendingClub** is a peer to peer lending company of American Origin (McBride & Sarah, 2014). At its peak, it was considred the world's largest lending company (Schumpeter, 2013). The dataset consists of all the loan attributes recorded by the lending company. The descriptions of all the stats are mentioned in the LCDataDictionary.xlsx . We will manily focus on the loan status of the borrower as our target variable or outcome, for the purpose of classification and prediction, all the other loan attributes will act as the features on which the model will be trained.

Source of the dataset: https://www.kaggle.com/code/jkashish18/lending-club-python/data

Here, in this notebook we will perform extensive **data cleaning** and **preprocessing** as this a big data consisting of lots of information.
After the cleaning is done, **descriptive analysis** will be done on it, through visualisation in the exploratory analysis section. It will be done, in the form of histograms, bar plots and piechart of the value counts of certain attributes and comparision plots, with the help of libraries such as seaborn and matplotlib. After that, **diagnostic analysis** will be done using correlation method among many others. These are also mentioned in the exploratory analysis section. **Predictive analysis** will be conducted in the form of a binary classification, which will classify whether the borrower has charged off as its loan status or is it fully paid. The classifier used for this purpose would be Decision Tree Classifier. Confusion matrix, f1 score and accuracy are some of the metrics that will be used for the evaluation of the model performance. At the end a feature importance plot is also given which states which loan attribute plays the best role for predicting the loan status of the borrower.

## 2) Storage of the Dataset
 
The dataset will usually be stored in a local resource, but in case the need arises to store the dataset in a cloud based system. The following measures need to be taken.
First we need to choose an appropriate cloud storage provider such as Google Cloud, Dropbox, Amazon S3, Oracle Cloud storage etc. After that is sorted, we would have to create an account and configure the storage options present to meet the specific requirements. Once the cloud based storage is set up, it is time to transfer the dataset from the local storage to the cloud. This may involve exporting the data in a suitable format for the proper storage and future utilisation.
Finally, the data analysis and processing workflows need  to be adjusted to account for the new cloud based storage location, by changing the location of the filepath of the dataset and any other means. In this way, we would be able to work with datasets that are stored in cloud.


## 4) Recommendation/Conclusion 
Explorataory Analysis of the dataset gave us many insights on the various relationships among the loan attributes. The Decision Tree Classifier used for the prediction of loan status of the borrower showed a training score of 0.9747 and a testing score of 0.9745. Both of the score is quite high and similar, which suggests that the model is likely not overfitting to the training data. The Confusion Matrix generated after the classification shows a 1.01 % of false positive and a 1.53 % of False Negative. The f1 score and accuracy of the prediction is 0.9743 and 0.9745 respectively.
GridsearchCV was used to find the best hyperparameters for the Decision Tree Classifier which was {'max_depth': 6, 'min_samples_leaf': 1, 'min_samples_split': 2} in this case. The feature plot was drawn using the best_parameter function of the grid search. 

Even though Decision Tree Classifier showed a pretty good result,it would be recommended to use other classifers and check on how it works out, when a different algorithm is used for the classification. It can then be compared with the result we already have. 

Data profiling from Pandas Library was not used here. It would be interesting to use that for the exploratory analysis as well in the future.
