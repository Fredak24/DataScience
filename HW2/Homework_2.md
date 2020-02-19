# Homework 2
### Group: Luke/William/Kossi

# Part 1: Decision Tree  

In this part, you will implement decision trees to predict how likely a loan is to default. 

Using all the features from your final dataset created in homework 1, implement a decision tree to predict the probability a loan will default.
1. Explain the process you used for selecting optimal model parameters and evaluating model performance.
2. Present a visualization of your model’s performance.

Using an optimal set of features from your final dataset created in homework 1,
implement a decision tree to predict the probability a loan will default.
1. Explain the process you used for selecting the optimal set of features, selecting
optimal model parameters, and evaluating model performance.
2. Present a visualization of your model’s performance.

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

1. Fit and tune a logistic regression model using only the ‘Grade’ feature and another logistic regression model using only the ‘Interest Rate’ feature.
2. Fit and tune a logistic regression model using only the ‘Grade’ and ‘Interest Rate’ features.
3. Compare the performance of these three models with the performance of the logistic regression model in Part 2 #2 above.
4. How does this process and its results inform your investigation of Jasmin’s concerns and what do you conclude from the investigation?