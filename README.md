# Welcome to Crop-Recommender-System

## About

This is a Mini-Project for SC1015 (Introduction to Data Science and Artificial Intelligence) which aims to recommend the most suitable crop to grow given a set of environmental conditions. For detailed walkthrough, please view the source code in order from:

1. Data Preparation
2. Data Visualization/Exploratory Data Analysis
3. XXX

## Contributors

@teehee08 - Data Preparation, Documentation

@Nafees505 - Exploratory Data Analysis

@marcushooi - AI Model Building

## Practical Motivation 

With the rising prices of water, fertilisers and other resources needed for farming, precision agriculture harnesses the potential to increase crop yields and profitability while lowering the resources (e.g. water, fertilisers) needed to grow crops. Farmers can make informed decisions about the farming strategy. Hence, we focused on building a predictive model to recommend the most suitable crops to grow in a particular farm based on various parameters including temperature and humidity levels.

## Problem Definition 
- Are we able to accurately predict the type of crop to be planted based on a given set of environmental conditions?

## Data Preparation
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
2. Relvant visualisations were done for each variable. 3 types of plot were used; Boxplot, Histrogam and the violin plot.
  -Lessons that we can learn from it:
      Looking at the histogram and violinplot:
          1. The "Temperature" variable, it somewhat follows a normal distribution.      
          2. The "Rainfall" variable is more skewed to the left.
          3. The "Humidity" variable is more skewed to the right.
          4. The "Potassium" variable is more skewed to the left, with the execption of some outliers on the right
      Looking at the boxplot:
          1. The "Nitrogen" variable does not seem to have any outliers present
          2. The "Phosphorus" variable do have quite a number of outliers, but a clustered closer to the boxplot, on the right
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
7. In order to find out if there are any correlation between the variables, a heatmap was generatated
    - The lighter the colour of the box, the highter the positive correlation, the darker the colour of the box, the higher the negative correlation.
    - Instantly, we can poin out that "Phosphorus" and "Potassium" has the highest correlation of 0.74(2dp).




## Algorithm Optimisation and Machine Learning


## Conclusions Derived


## Ethical Considerations and Intelligent Decisions


## Future Works that can be done

- Instead of recommending the crop given a set of conditions, future works can be done on predicting the optimal conditions for each type of crop.

## Additional Learning Points from this Project beyond Lectures

- A new EDA technique called Point Plot, which is a visualisation that displays points on a specific variable for a specific crop

- Implemented various AI models, including XXX

- Learnt additional performance metrics used to evaluate AI models, including XXX

- Collaborating on GitHub

## References
- https://towardsdatascience.com/the-ultimate-guide-to-data-cleaning-3969843991d4
