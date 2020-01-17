# Predicting Housing Prices in Ames, Iowa

### Problem Statement
 
What factors have the biggest role in determining the price of a home?
This analyses is a preliminary investigation into the factors that predict the price of residential property at sale. Throuhg the use of regression hrough a regression model based on the Ames Housing data set. 

"A shift is taking place with home buyers. They want to invest in more than a home; they want to invest in the experience of living there." 
(http://nahbnow.com/2020/01/how-to-build-communities-buyers-will-love-to-call-home/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+NAHBNow+%28NAHB+Now++%7C+The+News+Blog+of+the+National+Association+of+Home+Builders%29)

## Executive Summary -- How are you tackling the problem statement?
Ames, Iowa is best known as the home of Iowa State University. Half of the city's population is made up of university students.

To better understand

Focused on several features showing the highest correlation to sale price in the dataset. This inlcuded the following:
- 

### [Data Cleaning and Exploratory Analysis]()
Columns containing 80-99% NaN values were dropped. Many of the categorical variables in this dataset contain a category "NA" which indicates there is "No Pool", "No Alley" or "None". The NA category is being interpreted as a null value, rather than the fact that the property does not have this feature. For this reason NaN values were replaced by either a 0 or the string 'None'. Several ordinal categorical variables were converted to integers. Outliers that could be identified as incorrect data and those without strong relevance to the problem statement were dropped. Visualizations are used to understand the distribution of the target and correlations with other variables.

### [Preprocessing and Feature Engineering]()
Polynomial features was used to create interaction terms and see how the combination of two variables affect the target. A higher cross validation score was achieved on the model that utilized these engineered variables.

### [Modeling]()
The analysis uses simple sklearn regression models to determine which factors have the biggest role in determining the price of a home. Lasso and ridge regularization methods were used to simplify the models. Using a higher number of variables and the polynomial features resulted in a lower RMSE.

### Description of Data
The data set contains information from the Ames Assessor’s Office used in computing assessed values for residential properties sold in Ames, Iowa from 2006 to 2010. The information included in the data set is similar to what a home buyer would want to know before making a purchase. 

#### Data Files
train.csv - raw training set
test.csv - raw test set
train_clean.csv - clean training set, used for modeling
test_clean.csv - clean test set, used for modeling
first_submission.csv - submission of linear regression model to Kaggle
second_submission.csv - submission of linear regression model to Kaggle
third_submission.csv - submission of linear regression model to Kaggle

### Data Dictionary
A data dictionary can be found [here](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt) containing a full description of each column. 

### Business Recommendations
The strongest performing model was a classical linear regression model that used 14 independent variables to predict sale price. The model achieved a cross validated score of 84.7%. The features were selected because they had a correlation with the target variable of greater than .3.

The feature that shared the strongest linear relationship to the target was the 'overall quality' variable, which rates the overall material and finish of a house on a scale of 1-10. Properties in this dataset averaged an overall quality of approximately 6.1 with a median of 6. Engineering a feature that looks at overall quality and the square foot measurement of the living area increased the correlation with sale price from .80 to .84. Similarly, engineering a feature that looks at overall quality and the square foot measurement of the garage area had a correlation of .81. Overall quality is an aggregate descriptor that doesn't give much insight into the specific property features that might increase price. It makes sense that the relationship is stronger for properties with larger living and garage areas because size is often an indicator of price.

### Limitations and Future Analysis
The next stage of analysis will focus on a few items:
**Location**: cannot discount the role that location plays in property prices, so a deeper analysis would evaluate the relationship of each of these variables in the context of their location.
**Outliers**: several variables in the dataset contained outliers, which is notable because outliers can affect the regression line. Next phases of development would involve investigating these outliers in depth and determining an appropriate way of handling them. The technique should be context specific, so future iterations of this analysis focused on different geographical regions should account site specific factors.
**Timing**: Are more properties sold around a certain time of year? It would be interesting to see if this correlates with a fluctuating student population in the summer months.
