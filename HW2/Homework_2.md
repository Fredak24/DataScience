# Homework 2
### Group: Luke/William/Kossi

# Part 1: Decision Tree  

We used GridSearchCV to find the optimal parameters for our DecisionTreeClassifier. Providing an array of options for criterion and maxDepth, we let the GridSearchCV algorithm determine the optimal parameters. While GridSearchCV was able to provide us optimal parameters for our training dataset, we knew this didn't necessarily mean it would fit our test dataset as well as there was still a risk of overfitting. We settled on parameters of 'entropy' and a maxDepth of 12. When looking at how our model performed against the test dataset the results were quite good.

Here are the metrics that were captured:
**accuracy:** 0.997
**recall:** 0.989
**precision:** 0.998
**f-measure:** 0.993

Confusion Matrix:
![confusion matrix](images/dt_confusion_matrix.png "Confusion Matrix")

![norm confusion matrix](images/dt_norm_confusion_matrix.png "Norm Confusion Matrix")

ROC Curve
![roc curve](images/dt_roc_curve.png "ROC Curve")

To determine the optimal set of features from the dataset we used the RFECV algorithm with the decision tree classifer. Our results were as follows:

![optimal number of features](images/dt_optimal_num_features.png "Optimal number of features")

As you can see, the cross validation scores only goes down after increasing the number of features.

As far as what features were selected, here were the resulting rankings (top 10):
feature|score
-------|-----
recoveries          | 1
funded_amnt         | 1
emp_length::9 years | 1
total_pymnt         | 1
emp_length::8 years | 2
emp_length::7 years | 3
emp_length::6 years | 4
emp_length::5 years | 5
emp_length::4 years | 6
dti                 | 7

So, using the top four features, we created a new feature set, and attempted to find the optimal parameters using GridSearchCV again.

This time our GridSearchCV settled on parameters of 'entropy' and a maxDepth of 11. The resulting metrics are performed against our test data is as follows:
**accuracy:** 0.996
**recall:** 0.982
**precision:** 0.999
**f-measure:** 0.991

Confusion Matrix:
![confusion matrix](images/dt_optimal_confusion_matrix.png "Confusion Matrix")

![norm confusion matrix](images/dt_optimal_norm_confusion_matrix.png "Norm Confusion Matrix")

ROC Curve
![roc curve](images/dt_optimal_roc_curve.png "ROC Curve")

The results here when compared are actually quite similar. The model with the full feature set gives slightly more accurate results, but given that the number of features dropped from 65 to 4, the second model is preferred in our opinion because of sheer simplicity.


# Part 2: Logistic Regression

In this part, you will implement a logistic regression model to predict how likely a loan is to default. 

Using all the features from your final dataset created in homework 1, implement a logistic regression model to predict the probability a loan will default.
1. Explain the process you used for selecting optimal model parameters and evaluating model performance.
2. Present a visualization of your model’s performance.

Using the optimal set of features from Part 1 above, implement a logistic regression
model to predict the probability a loan will default.
1. Explain the process you used for selecting optimal model parameters and
evaluating model performance.
2. Present a visualization of your model’s performance.
 
Compare the model performance for the best decision tree with the best logistic regression implementation.

# Part 3: Model Investigation

After learning and evaluating these models, Jasmin realized that the attributes she used in her models were not all underlying facts about the loan applicants, but possibly statistics calculated by LendingClub using their own models. She wanted to assess whether the predictive power of
her models came simply from LendingClub's own models to calculate Grade and Interest Rate. Carry out this investigation using logistic regression. 

**Make sure to put in terms of Recall/Precision, and 1-Recall?**

1. Fit and tune a logistic regression model using only the ‘Grade’ feature and another logistic regression model using only the ‘Interest Rate’ feature.
2. Fit and tune a logistic regression model using only the ‘Grade’ and ‘Interest Rate’ features.
3. Compare the performance of these three models with the performance of the logistic regression model in Part 2 #2 above.
4. How does this process and its results inform your investigation of Jasmin’s concerns and what do you conclude from the investigation?