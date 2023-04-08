# Welcome to Crop-Recommender-System

## 1. About

This is a Mini-Project for SC1015 (Introduction to Data Science and Artificial Intelligence) which aims to recommend the most suitable crop to grow given a set of environmental conditions. For detailed walkthrough, please view the source code in order from:

1. Data Preparation
2. Exploratory Data Analysis (EDA) with ML

## Contributors

@teehee08 - Data Preparation, Documentation

@Nafees505 - Exploratory Data Analysis

@marcushooi - AI Model Building

## 2. Practical Motivation 

With the rising prices of water, fertilisers and other resources needed for farming, precision agriculture harnesses the potential to increase crop yields and profitability while lowering the resources (e.g. water, fertilisers) needed to grow crops. Farmers can make informed decisions about the farming strategy. Hence, we focused on building a predictive model to recommend the most suitable crops to grow in a particular farm based on various parameters including temperature and humidity levels.

## 3. Problem Definition 
- Are we able to accurately predict the type of crop to be planted based on a given set of environmental conditions?

## 4. Data Preparation
1 dataset used: crop recommender dataset (https://www.kaggle.com/datasets/atharvaingle/crop-recommendation-dataset)
 
Workflow for this section:

1. Inspection of dataset 

- We checked if the datatype of each attribute in the dataset is appropriate. For example, since we are looking at temperature at a numerical value, temperature attribute in the dataset should not be of datatype boolean.

- We checked for 2 data anomalies

    - Missing values

    - Duplicate values
    
2. Variable names were also changed so as to ensure that anyone who is reading the dataset have a sense of what the variable represents. For example, "N" was changed to Nitrogen, "P" was changed to Phosphorus.

## Exploratory Data Analysis 
The EDA for this dataset was done as such:

1. dfnumeric is a dataframe that was constructed to extract out all the numeric variables for the dataset. In this case, the numeric variables are "Nitrogen", "Phosphorus", "Potassium', "Temperature", "Humidity", "pH" and "Rainfall". "Crop" was determined to be a categorical value.

2. Relevant visualisations were done for each variable. 3 types of plot were used; Boxplot, Histogram and the violin plot.

- Lessons that we can learn from it:
  
      Looking at the histogram and violinplot:
      
          1. The "Temperature" variable, it somewhat follows a normal distribution.     
          
          2. The "Rainfall" variable is more skewed to the left.
          
          3. The "Humidity" variable is more skewed to the right.
          
          4. The "Potassium" variable is more skewed to the left, with the execption of some outliers on the right
      Looking at the boxplot:
      
          1. The "Nitrogen" variable does not seem to have any outliers present
          
          2. The "Phosphorus" variable do have quite a number of outliers, but a clustered closer to the boxplot, on the right.
          
          3. This is quite different for the "Potassium" variable, which has outliers far from the boxplot on the right.
          
          4. The "Temperature" variable has outliers clustered at both sides of the boxplot.
          
3. Through the visualisation, despite us knowing that that there are outliers for most of the variables, we are unable to determine how much ouliers each variable has. 
    - Thus, the next code serves the purpose to calculate the number of outliers for each variable. As predicted, "Nitrogen" has no variables, and " Potassium" has the most variable.
    
    - Despite finding out the number of outliers, it should be of utmost importance that removing the outliers could be dangerous for out dataset, as we need to know the data of all variables to find out out the right crop for a specific set of conditions.

4.Following this, we create another datafram called "dfCategorical"
   - As the name suggests, this dataframe is used to bring out the categorical variables from the dataset. In this case, there is only one; "Crop"
   
5. We also find out that there are 22 different crops present.

6. Under the dataset, we found out that there are 2200 rows in the dataset, indicating that there are 2200 data in the dataset. However, we want to determine number of crops for each crop, ie. How many rice crops are there? How many apple crops are there? etc.

    - Thus, the next code brings out the number of crops for each crop, and shows that there are an equal number of 100 crops for wach crop.
    
    - To better visualise this, a histogram was used, and we can visually see that each crop has the same number of crops.
    
7. In order to find out if there are any correlation between the variables, a heatmap was generated.

    - The lighter the colour of the box, the highter the positive correlation, the darker the colour of the box, the higher the negative correlation.
    
    - Instantly, we can point out that "Phosphorus" and "Potassium" have the highest correlation of 0.74 (2dp).

## 5. Algorithm Optimisation and Machine Learning

In this portion we will perform machine learning analysis and do a comparison of the trained models. Thereafter, we will use the "best performing model" to create a crop recommender system that predicts the best type of crop to grow, when the user (farmer) inputs the Nitrogen, Phosphorus, Potassium, Temperature, Humidity, pH, Rainfall

### 5.1 Type of Machine Learning Problem:

The problem we are facing is a classification problem. Most of the analysis and models we use, will be classification models. (Exception will be linear regression, to show what happens if a wrong model is used)

### 5.2 We will perform the following:

1. Anomaly detection & Data Cleaning

2. Separation of test and train set

3. Train Machine learning models
    1. Single Decision Tree
    2. Random Forest
    3. Neural Network
    4. Support Vector Machine
    5. Logistical Regression
    6. Linear Regression (to show error)
4. Saving of trained models using pickle
5. Comparison & Selection of Model using:
    1. Accuracy
    2. f1 score
    3. Cross validation
6. Create a crop recommendation system

### 5.3 Anomaly detection & Data Cleaning
As Previously Detected, there is no anomaly in each class of label (crop). There is also no missing values. 

### 5.4 Separation of test and train set
In the separation of test and train set, we will use a 70/30 split. Additionally, we will utilise stratified sampling methods.

Stratified random sampling ensure that for each class of label (crop), 70% will be used in training. If stratified is not used, 70% of datapoints will will be chosen from the entire dataset. This could lead to imbalance selection for each label. 

For example, in a non-stratified approach, the dataset contains 2200 rows of datapoints. 100 of them belonging to rice. if randomly selected, there is a chance, 100 rows of rice data can be randomly selected for training, hence leaving no rice data for testing.

In the stratified approach we use, 70 rows of each 22 crop data will be selected for training (giving us 1540 rows of train data). While the remaining 660 rows will be used for testing

### 5.5 Train Machine learning models

As identified, the problem we have is a classification model. Hence we utilise the following classification models

    1. Single Decision Tree
    2. Random Forest
    3. Neural Network
    4. Support Vector Machine
    5. Logistical Regression
    6. Linear Regression (to show error)

Note: We intentionally also train a linear regression model to show that when a wrong model is used for a wrong problem, the outcome is useless.

### 5.6 Saving of trained models using pickle

We will conveniently use pickle to save our trained machine learning models. The saved model can be found in the subdirectory "model/..."

### 5.7 Comparison & Selection of Model using:

After Training out models it is important for us to perform a comparison. We will compare using the following:

    1. Accuracy
    2. f1 score
    3. Cross validation
    
The reason we utilise these comparisons is because they are the more common metrics used for classificaiton models.

When we finish comparing the models, we will do a feature importance analysis of the selected model (Random Forest)

### 5.8 Create a crop recommendation system

Using the Random Forest Mode, we will create a crop recommendation system with a simple GUI where user can input the Nitrogen, Phosphorus, Potassium, Temperature, Humidity, pH, Rainfall. The crop recommendation system will then recommend a crop best suited to the conditions input.

## 6. Future Works that can be done

- Instead of recommending the crop given a set of conditions, future works can be done on predicting the optimal conditions for each type of crop.

## 7. Additional Learning Points from this Project beyond Lectures

- A new EDA technique called Point Plot, which is a visualisation that displays points on a specific variable for a specific crop

- Implemented various AI models, including
    1. Single Decision Tree
    2. Random Forest
    3. Neural Network
    4. Support Vector Machine
    5. Logistical Regression
    6. Linear Regression (to show error)

- Learnt additional performance metrics used to evaluate AI models, including
    1. Accuracy
    2. f1 score
    3. Cross validation
    4. feature importance analysis

- Collaborating on GitHub

## 8. References
- https://towardsdatascience.com/the-ultimate-guide-to-data-cleaning-3969843991d4
- https://seaborn.pydata.org/generated/seaborn.pointplot.html
- https://medium.com/mlearning-ai/performance-measure-of-a-machine-learning-model-fb657263bf98
- https://medium.com/swlh/feature-importance-hows-and-why-s-3678ede1e58f
- https://scikit-learn.org/stable/modules/svm.html
- https://www.lightly.ai/post/train-test-split-in-deep-learning
