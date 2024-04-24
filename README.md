# SC1015-Project

FDDC Team 7

1. Motivation

Our project aims to find out what are the top risk factors contributing to the development of diabetes across different age groups. This is especially important with the rapidly increasing number of diabetes cases globally, so it is important for us to be able to detect diabetes. Recognizing that early detection and timely intervention can drastically alter the course of diabetes, we were driven to uncover the patterns that precede its development. Ultimately, our goal was to derive actionable insights that could guide healthcare providers in risk assessment and management, particularly targeting resources where they can make the most difference – an objective inspired by the transformative potential of data in health outcomes.

Diabetes Dataset:
Our project utilized a comprehensive dataset from Kaggle on diabetes, comprising various health indicators such as pregnancies, glucose levels, blood pressure, skin thickness, insulin levels, and age. This dataset includes a diverse demographic, providing a wide-ranging perspective on the risk factors associated with diabetes.

Problem Definition:
What are the top risk factors contributing to the development of  diabetes across different age groups.



2. Set the Stage

Collecting & cleaning of data

Remove all rows where these variables = 0  

EDA to obtain initial data-driven insights from the dataset.




3. Core Analysis

	Machine Learning Approaches for Diabetes Prediction:

ML techniques used: Decision Tree and Random Forest Classifier 
The objective was to identify the key factors that contribute to diabetes outcomes across different age groups. The use of binary classification aligns with our objective because it allows us to predict a binary outcome - the presence or absence of diabetes.
We trained our models on a set of predictors including 'Pregnancies', 'Glucose', ‘BMI’, 'BloodPressure', 'SkinThickness', 'Insulin', and 'Age' with these supervised learning models for categorical prediction.
While linear regression was NOT used due to its suitability for continuous data, not for predicting a binary outcome 
Decision Trees provides a clear and concise visualization of the decision-making process, while Random Forests leveraged the power of multiple trees to enhance prediction accuracy and reduce overfitting and gave us insight into feature importance.



	Part I: Using Decision Tree

In our first decision tree of depth 3. The number of false negatives is higher than false positives in both sets, which could be critical as in the context of diabetes, it could lead to a wrong prediction that the individual does not have diabetes when the person actually has diabetes. The decision tree also suggests that glucose ad age is an important feature of predicting diabetes as the splits are made on glucose and age.

With increasing depth of the decision tree, Accuracy generally increased. This model is better at predicting the negative class than positive one as TN > TP. The rate of false negatives < false positives, better than previous model.

Increasing the depth of the decision tree resulted in:

A higher accuracy on both the training and test sets, suggesting the model is correctly identifying more true positives (cases of diabetes).
A lower precision on the test set, which means there are more false positives (cases where the model incorrectly predicts diabetes).

An increase in the false positive rate on the test set, indicating a trade-off where the model is capturing more true positives at the cost of also increasing incorrect positive predictions.

The increased True Positive Rate (TPR) (sensitivity) is often considered more important in medical diagnostics than a low false positive rate because it is preferable to catch as many true cases as possible, even if some healthy patients are misclassified. However, the increased false positive rate suggests that the model's specificity has decreased, which may lead to more false alarms and potentially unnecessary follow-up treatments.

Hence, increasing the tree depth improved the model's ability to identify individuals with diabetes (as shown by the increased TPR and accuracy), but it also led to a higher number of false alarms (as shown by the increased false positive rate). This illustrates the precision-TPR trade-off in classification problems. ​



	Part II : Using Random Forest

Next, we used random forest algorithms. We first categorize the diabetes data by age and perform analysis on each age group using random forest algorithm.  We Train a RandomForestClassifier on the training data to predict the Outcome. Extract the feature importances from the trained RandomForestClassifier, which indicates the relative importance of each feature in predicting the 'Outcome'. Show result in horizontal bar chart with the factor with the most significant impact on predicting the outcome first. We Loop through each age group and perform analysis, calculating correlation matrix and feature importance for each age group. We found that there is an empty feature importance graph for the age group ‘61+’. 
Choice of indicator: Feature Importance
​​Correlation Coefficients:
- measures the strength and direction of a linear relationship between two variables.
- doesn't consider any other relationships or interactions beyond pairwise linear associations. It does not take into account the complex interactions that the model might be using to make predictions.
- High correlation with the outcome variable suggests a strong linear relationship but doesn't necessarily imply causality or that the feature is useful in the context of a complex model.

Feature Importance from Random Forest:
measures the average gain of purity (e.g., Gini impurity) by splits of a particular feature, derived from the model's internal logic which involves numerous decision trees.
takes into account the nonlinear relationships and interactions between features, especially important and more relevant in the case of health indicators and diseases.
The importance is based on how much a feature, on average, decreases the impurity across all trees within the forest. If  a feature  splits data in a way that leads to more accurate predictions, its importance value will be high 
provides insight into the predictive power of each feature when used in conjunction with other features

Hence, we decided to focus on feature importance for all the ages groups.



Random Forest works by creating multiple decision trees from different samples of the dataset. With only 3 entries, it's probably not possible to create diverse trees, and the model cannot perform the random subsampling necessary for building the individual trees.

Hence, we removed this age group from subsequent analysis.
	Finally, we represented our findings in both a heatmap and a bar graph.

 

4. Conclusion
   
In conclusion, the outcome of our project was a comprehensive machine learning model capable of predicting diabetes risk across different age groups. By applying Random Forest classifiers, we derived a detailed view of the relative importance of various health indicators in relation to diabetes.

The project addressed the original problem by identifying critical variables that influence the likelihood of diabetes in specific age groups. This was achieved by evaluating feature importances and assessing the predictive power of each variable.

One intriguing insight was the variability in feature importances across age groups. While binary tree analysis on the entire dataset showed glucose to be the most significant contributing factor, age-group specific analysis showed other results in different age groups, highlighting that certain factors may have a greater impact on diabetes risk at certain life stages.

The analysis recommends that healthcare providers consider age-specific risk profiles when advising patients on diabetes prevention, which could lead to more personalized and effective healthcare strategies.

The varying importance of predictors suggests that interventions should be tailored based on the patient’s age. For instance, younger individuals might benefit from lifestyle modifications targeting specific risk factors more than others.

The findings can inform public health campaigns by focusing resources and educational efforts on the most impactful risk factors for each age group.

