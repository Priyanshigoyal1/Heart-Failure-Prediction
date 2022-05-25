# Heart-Failure-Prediction
Heart failure is a common event caused by Cardiovascular diseases (CVDs) and this dataset contains 11 features that can be used to predict a possible heart disease. People with cardiovascular disease or who are at high cardiovascular risk (due to the presence of one or more risk factors such as hypertension, diabetes, hyperlipidaemia or already established disease) need early detection and management wherein a machine learning model can be of great help.


## ABSTRACT
This paper reports our experience with building a Heart Failure Prediction, We have dataset which is created by combining different datasets already available independently but not combined before. In this dataset, 5 heart dataset are combined over 11 common features. We use various classification algorithms and compare their results in this report. 

## INTRODUCTION
Cardiovascular diseases (CVDs) are the number 1 cause of death globally, taking an estimated 17.9 million lives each year, which accounts for 31% of all deaths worldwide. Four out of 5CVD deaths are due to heart attacks and strokes, and one-third of these deaths occur prematurely in people under 70 years of age. Heart failure is a common event caused by CVDs and this dataset contains 11 features that can be used to predict a possible heart disease.
People with cardiovascular disease or who are at high cardiovascular risk (due to the presence of one or more risk factors such as hypertension, diabetes, hyperlipidaemia or already established disease) need early detection and management wherein a machine learning model can be of great help.

## Dataset source:
This dataset was created by combining different datasets already available independently but not combined before. In this dataset, 5 heart datasets are combined over 11 common features which makes it the largest heart disease dataset available so far for research purposes. The five datasets used for its curation are:
•	Cleveland: 303 observations
•	Hungarian: 294 observations
•	Switzerland: 123 observations
•	Long Beach VA: 200 observations
•	Stalog (Heart) Data Set: 270 observations
Total: 1190 observations
Duplicated: 272 observations
Final dataset: 918 observations
Every dataset used can be found under the Index of heart disease datasets from UCI Machine Learning Repository on the following link: https://archive.ics.uci.edu/ml/machine-learning-databases/heart-disease/


## Attribute Information:
•	Age: age of the patient [years]
•	Sex: sex of the patient [M: Male, F: Female]
•	ChestPainType: chest pain type [TA: Typical Angina, ATA: Atypical Angina, NAP: Non-Anginal Pain, ASY: Asymptomatic]
•	RestingBP: resting blood pressure [mm Hg]
•	Cholesterol: serum cholesterol [mm/dl]
•	FastingBS: fasting blood sugar [1: if FastingBS > 120 mg/dl, 0: otherwise]
•	RestingECG: resting electrocardiogram results [Normal: Normal, ST: having ST-T wave abnormality (T wave inversions and/or ST elevation or depression of > 0.05 mV), LVH: showing probable or definite left ventricular hypertrophy by Estes' criteria]
•	MaxHR: maximum heart rate achieved [Numeric value between 60 and 202]
•	ExerciseAngina: exercise-induced angina [Y: Yes, N: No]
•	Oldpeak: oldpeak = ST [Numeric value measured in depression]
•	ST_Slope: the slope of the peak exercise ST segment [Up: upsloping, Flat: flat, Down: downsloping]
•	HeartDisease: output class [1: heart disease, 0: Normal]

## METHODOLOGY
Overview:
There are various classification algorithms present out of which we shall implement the following :
● KNN

● Random Forest Classification

● SVM

● MLP
We also make use of PCA and LDA for dimensionality reduction and Sequential Feature selector for feature selection.

### Exploring the dataset and preprocessing:
On counting the number of NULL values in the train dataset , it was found that there are no NULL values present.
On further looking, we found that there are categorical variables so we need to encode them. We  used make_column_transformer for that purpose.
‘Sex’ , ‘ChestPainType’ , ‘ExerciseAngina’ and ‘ST_Slope’ are encoded with help of OneHotEncoder as they contain nominal values.
‘RestingECG’ is encoded with the help of OrdinalEncoder as it contains ordinal values.
Thus, now our data is transformed. It only contains numeric values.

### Implementation of classification algorithms:

● KNN (k - nearest neighbors) : KNN are supervised algorithms which classify on the basis of distance from similar points.Here k is the number of nearest neighbors to be considered in the majority voting process. k=5 (constant)  is selected with the help of GridSearchCV.

○ Three types of KNN Classifiers were made :

■ Simple KNN with Sequential Feature selector (n_features=8)

■ KNN with PCA (n_components=12) and SFS (n_features=6)

■ KNN with LDA

● Random Forest Classifier : Random Forest Classifiers use boosting ensemble methods to train upon various decision trees and produce aggregated results. It is one of the most used machine learning algorithms. n_estimators=95,
max_depth=5 and criterion=’gini’ are selected with the help of GridSearchCV.


○ Three types of Random Forest Classifiers were made in the project :

■Simple Random Forest Classifier

■ Random forest with PCA (n_components=13)

■ Random forest with LDA


● Support Vector Machine : In SVM , data points are plotted into n-dimensional graphs which are then classified by drawing hyperplanes. After preprocessing, we need to scale the data with the help of StandardScaler.


○ Three types of SVM classifiers were used


■ Simple SVM with rbf kernel [ SFS(n_features=13)]

■ SVM with PCA (n_componets=13) [ SFS(n_features=9)]

■ SVM with LDA



● Multilayer Perceptron : MLP is a feedforward Neural Network which uses backpropagation to update weights and improve the results.


○ Three types of MLP were used


■ Simple MLP  with Sequential Feature selector (n_features=8)

■ MLP with PCA (n_componets=12)   [ SFS(n_features=8)]

■ MLP with LDA

## EVALUATION OF MODELS

K-Neighbours Classifier

Variant	Accuracy

a.	Simple KNN with Sequential Feature selector (n_features=8)	84.78260869565217

b.	KNN with PCA (n_components=12) and SFS (n_features=6)	86.59420289855072

c.	KNN with LDA	80.79710144927536



Random Forest Classifier

Variant	Accuracy

a.	Simple Random Forest	90.21739130434783

b.	Random forest with PCA (n_components=13)	89.85507246376811

c.	Random forest with LDA	84.42028985507247


Support Vector Machine

Variant	Accuracy

a.	Simple SVM with rbf kernel [ SFS(n_features=13)]	90.57971014492753

b.	SVM with PCA (n_componets=13) [ SFS(n_features=9)]	89.85507246376811

c.	SVM with LDA	86.23188405797102


Multilayer Perceptron

Variant	Accuracy

a.	Simple MLP  with Sequential Feature selector (n_features=8)	85.5072463768116

b.	MLP with PCA (n_componets=12)   [ SFS(n_features=8)]	84.42028985507247

c.	MLP with LDA	86.23188405797102



## CONCLUSION

Svm and Random forest performed nearly the same. KNN and MLP are not that good. After implementing PCA,  KNN showed slight increase in accuracy, opposite to other models.  MLP performed better with LDA, But other models did not perform well when implemented LDA.
Sequential feature selection also helped in increasing accuracy to a little bit.
