# Housing Price Predictions: the Iowa Housing Market

## Problem Statement
The National Association of Home Builders (NAHB) seeks to grow their understanding of the housing market in Ames Iowa. They want to understand what buyers look for in a property and are investigating the factors that predict the price of a property. Geographic context and population demographics will be influential in the buyer market and relevant to NAHB, which is principally dedicated to building and enriching communities. 

## Executive Summary 
Through the use of multiple linear regression models, this analysis explores the role of property features based on a residential housing dataset.  Ames, Iowa is best known as the home of Iowa State University. Half of the city's population is made up of university students, which has a strong influence on the buyer market and sense of community.

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

### Data Cleaning and Exploratory Analysis
The data cleaning and exploratory data analysis can be reviewed in detail [here](https://github.com/jessicarose00/housing_price_predictions/blob/master/code/01_Cleaning_EDA.ipynb). Columns containing 80-99% NaN values were dropped. Many of the categorical variables in this dataset contain a category "NA" which indicates there is "No Pool", "No Alley" or "None". The NA category is being interpreted as a null value, rather than the fact that the property does not have this feature. For this reason NaN values were replaced by either a 0 or the string 'None'. Several ordinal categorical variables were converted to integers. Outliers that could be identified as incorrect data and those without strong relevance to the problem statement were dropped. Visualizations are used to understand the distribution of the target and correlations with other variables.

### Preprocessing and Feature Engineering
Prior to modeling, several preprocessing and feature engineering steps were taken, which can be reviewed in [this notebook](https://github.com/jessicarose00/housing_price_predictions/blob/master/code/02_Preprocessing_Feature_Engineering.ipynb). Polynomial features was used to create interaction terms and see how the combination of two variables affect the target. A higher cross validation score was achieved on the model that utilized these engineered variables.

### Modeling
The analysis uses simple sklearn regression models to determine which factors have the biggest role in determining the price of a home. The modeling process can be reviewed [here](https://github.com/jessicarose00/housing_price_predictions/blob/master/code/03_Modeling.ipynb). Lasso and ridge regularization methods were used to address overfitting. Using a higher number of variables and the polynomial features resulted in a lower RMSE.

### Business Recommendations
The strongest performing model was a classical linear regression model that used 20 independent variables to predict sale price. The model achieved a cross validated score of 84.7%. The features were selected because they had a correlation with the target variable of greater than .3.

> "A shift is taking place with home buyers. They want to invest in more than a home; they want to invest in the experience of living there." Source: [NABH Now](http://nahbnow.com/2020/01/how-to-build-communities-buyers-will-love-to-call-home/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+NAHBNow+%28NAHB+Now++%7C+The+News+Blog+of+the+National+Association+of+Home+Builders%29)

The feature that shared the strongest linear relationship to the target was the 'overall quality' variable, which rates the overall material and finish of a house on a scale of 1-10. Properties in this dataset averaged an overall quality of approximately 6.1 with a median of 6. Engineering a feature that looks at overall quality and the square foot measurement of the living area increased the correlation with sale price from .80 to .84. Similarly, engineering a feature that looks at overall quality and the square foot measurement of the garage area had a correlation of .81. Overall quality is an aggregate descriptor, so it makes sense that the relationship becomes stronger when combined with size variables. Size is often an indicator of price. Variables related to the size and capacity of garages are relevant because transportation would be an important consideration given geographic features and the population demographic.

### Limitations and Future Analysis
The next stage of analysis will focus on a few items:
**Location**: To what degree is the buyer market concerned with location? We cannot discount the role that location plays in property prices, so a deeper analysis would evaluate the relationship of each of these variables in the context of their location.  
**Outliers**: Several variables in the dataset contained outliers, which is notable because outliers can affect the regression line. Next phases of development would involve investigating these outliers in depth and determining an appropriate way of handling them. The technique should be context specific, so future iterations of this analysis focused on different geographical regions should account site specific factors.  
**Timing**: Are buyers looking to purchase homes around a certain time of year? It could be interesting to see if this correlates with a fluctuating student population in the summer months.    
