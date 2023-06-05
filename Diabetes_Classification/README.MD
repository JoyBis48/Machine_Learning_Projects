## Introduction
The dataset used for the classification is Diabetes Dataset which consists of information of female patients of at least 21 years of age from the National Institute of Diabetes and Digestive and Kidney. The data is given in the csv format containing several medical diagonostic measurements presented as attributes, and the classification of whether the patient is diabetic or not, is done based on these attributes.
The ML Algorithm used for this binary classification is Random Forest Classifier. Seaborn and Matplotlib libraries were used for plots and for the purpose of exploratory analysis.

Source of the dataset :- Kaggle

Link :-   https://www.kaggle.com/datasets/akshaydattatraykhare/diabetes-dataset

## Conclusion
The Random Forest Classifier used for the prediction of diabetic patients showed a training score of 0.950 and a testing score of 0.858. Both of the score is quite high and similar, which suggests that the model is likely not overfitting to the training data. The Confusion Matrix generated after the classification shows a 9.09 % of false positive and a 5.11 % of False Negative. The f1 score and accuracy of the prediction is 0.857 and 0.858 respectively.
Note that the score might deviate very slightly each time this notebook is run.