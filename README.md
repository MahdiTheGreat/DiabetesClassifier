# DiabetesClassifier
The overall goal of this project is to make a diabetes classifier based on the symptoms of diabetes and pre-diabetes for the given patients and use XGBoost library to classify the data to detect the presence or absence of diabetes.
In this dataset, we have the information of more than 70,000 patients through a questionnaire that they filled for the Centers for Disease Control and Prevention (CDC). This dataset contains 22 columns as follows:

- Diabetes_binay: The target column that determines whether a person has diabetes or pre-diabetes
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













