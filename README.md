# DiabetesClassifier
The overall goal of this project is to make a diabetes classifier based on the symptoms of diabetes and pre-diabetes for the given patients and use XGBoost library to classify the data to detect the presence or absence of diabetes.
In this dataset, we have the information of more than 70,000 patients through a questionnaire that they filled for the Centers for Disease Control and Prevention (CDC). This dataset contains 22 columns as follows:

- Diabetes_binay: The target column that determines whether a person has diabetes or pre-diabetes.We separate the Diabetes_binary column as a label from the data set(after preprocessing) and use the data and labels for training and model building.
- HighBP: person has high blood pressure or not
- High Cholesterol: person has High cholesterol or not
- Cholesterol Check: Has the person in question had a check-up for cholesterol or not?
- BMI
- Smoker: Use of drugs
- Stroke: Person had a stroke or not
- HeartDiseaseorAttack: person has a heart disease or had a heart attack or not
- Physical Activity: Person has Physical activity or not
- Fruits: person consumes fruits or not
- Veggies: person consumes vegtables or not
- Heavy Alcohol Consumption: person consumes heavy alcohol or not
- any Health Care: Does the person in question have health insurance or not?
- No doctor because of Cost:  Has it ever happened that the person in question turned away from a doctor in a necessary situation due to costs?
- General Health: general health of person
- Mental Health: mental health of person
- Physical Health: physical health of person
- Difficulty Walking: Is walking difficult for the person in question or not?
- Sex
- Age
- Education
- Income

# Introducing XGBoost
XGBoost or Extreme Gradient Boost is an open-source library for Gradient Boosting regularization. Many machine learning algorithms can be implemented using this library. Apart from performance improvements such as high speed, this library has other advantages, including parallelism in the construction of trees, use of cache memory to increase speed, regularization to deal with overfitting, use of mutual validation, etc.

# Preprocessing

In this step, we prepare the data set for the classification model training operation. Necessary actions for this step:

- Removing null data: In the data set, there may be many points in the table with Null and other values outside the set of acceptable values. Our task is to find these points and replace them with acceptable values according to several possible policies. One of these policies is to replace them with the average value of the column or attribute or randomly select one of the values of a column or attribute and replace them with that. If there are too many null data points, we will remove them.
- Renaming columns or words from the data set that have spaces. These spaces may cause errors during tree construction. Therefore, it is recommended to remove these spaces or replace them with "_" lines.

# Normalization
Normalizing some features, so that there is no obvious difference between the features due to the length of the interval of possible values. Apart from rescaling the feature, we can also split a large range into a smaller number of categories. For example, for the range 1 to 100, convert the numbers 1 to 10 to category 1, Put numbers 11 to 20 into category 2 and ...

# Dealing with Categorical Features
In general, our data is divided into two numerical or categorical categories. In building the decision tree, it is preferable not to use categorical features. In this part, after identifying the categorized features, you must convert them into numerical features using the one-hot-encoding method.
Pay attention that one of the most important features of numerical data is the possibility of numerical comparison. For example, if there are four color categories (blue, red, yellow, green) we cannot have a numerical comparison between these categories, but instead if we divide the numbers from 1 to 100 into 10 categories, 1 to 10, 10 to 20, 20 to 30 and..., we can have a numerical comparison for each category because For example, the numbers of the first category are less than the second category! Therefore, 10 groups of numbers from 1 to 10 are not considered Categorical features!

# Building the model
In this step, we define an XGBoost Classifier and train it on the dataset. We use the following parameters to build the model:

- Learning_rate=0.1
- Max_depth=4
- N_estimator=200
- Subsample = 0.5
- Colsample_bytree=1
- Random_seed=123
- Eval_metric='auc'
- Verbosity=1

To perform learning operations, set early_stopping_rounds equal to 10 so that learning does not take time.
At the end, we report the accuracy of the model on the training and test data and also calculate the confusion matrix, precision and recall.

# Setting hyperparameters
As you saw in the previous section. Many parameters are involved in making the model.
To see all the parameters, you can use the following line of code:

xgboost.XGBClassifier().get_params()

All these parameters have a significant effect on the performance of this model. To find the best parameters, we can build the model on different combinations of these parameters and output the best model. In this part, We need to test the model on different combinations of the following parameters and output the best model. Below are recommended values for parameters to try:

- learning_rate_list = [0.02, 0.05, 0.1, 0.3]
- max_depth_list = [2, 3, 4]
- n_estimators_list = [100, 200, 300]
- colsample_bytree = [0.8, 1]

We can use evoluionatry algorithms to solve this problem, however becasue the search space isn't that big, we can examine all the different possible states and select the best one. 

Note that there is no need to create models manually and you can use GridSearchCV. In this case, use cross-validation 2 with 3 points of separation. For the scoring function, we can use the following function (it should be noted that we must import roc_auc_score from the sklearn.metrics package):
‎
- def my_roc_auc_score(model, X, y): 
 - return roc_auc_score(y, model.predict_proba(X)[:,1]))

This is essentially our fitness function for the models.

We use the following parameters for the initial construction of the model:

- eval_metric='auc'
- subsample = 0.5

After building the model and performing learning on all combinations of parameters, we report the best parameters. We get the best model (set by the best parameters) and we calculate the accuracy of the test data, the confusion matrix, and the precision and recall for this model.
At the end, we plot the changes in the model via changing the four parameters mentioned in the previous part and show what effect the changes of these parameters have had on the accuracy or performance of the model.




















