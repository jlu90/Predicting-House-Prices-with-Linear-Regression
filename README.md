# README: Predicting House Prices with Linear Regression
#### Author: Jocelyn Lutes

## Problem Statement
Ames, Iowa is a city in central Iowa, located approximately 37 miles from the capital city of Des Moines. In 2016, the population of Ames was approximately 65,000 residents [(1)](https://datausa.io/profile/geo/ames-ia/). Home to Iowa State University, and hosting offices for several major companies, including 3M, Barilla, Boehringer Ingelheim, and Syngenta, Ames offers a small-town feel with the amenities of a larger city [(2)](https://www.cityofames.org/about-ames/about-ames). At Ames Realty Co., we are passionate about helping our clients find a house that feels like a home. 

In the past, Ames Realty Co. has relied heavily on the opinions and expertise of our realtors to manually determine the prices of the homes that we list. However, as the industry moves to automating the appraisal of housing prices [(3)](https://unionstreetmedia.com/the-rise-of-machine-learning-in-real-estate/#:~:text=Personalized%20Marketing%20Automation%20%E2%80%93%20machine%20learning,neighborhood%20and%20property%20is%20best), we are ready to join the growing number of real estate companies that use machine learning to estimate the sales prices of their properties.

**Problem Statement:** As a member of the newly-hired data science team, I will use housing data collected from 2006 to 2010 to build a Linear Regression model that best predicts sale prices for properties located in Ames. 

## Executive Summary
The Ames Housing Dataset was first described in 2011 by Dean De Cock [(4)](http://jse.amstat.org/v19n3/decock.pdf). This dataset provides 80 features (of nominal, discrete, and ordinal types) to describe properties in Ames, Iowa that were sold between the years 2006-2010. During the first step in the workflow (data cleaning), missing values were fixed to the best of my abilities, correct data types were confirmed, and any unsual values were investigated. Once the data was cleaned, Exploratory Data Analysis (EDA) was conducted to explore the relationship between Sale Price and each feature in the model. For numeric features, the linear relationship was examined using a heatmap and correlation coefficients. For categorical data, bar plots were created to visualize the mean Sale Price across categories. During EDA for categorical features, special attention was paid to any patterns or clusters that emerged. 

Following EDA, features were engineered to reduce dimensionality of the data and to account for the patterns and clusters that emerged during EDA. If a categorical variable was coded during feature engineering, it was removed from the data frame. Any categorical variables of interest were dummified. Data was divided into training sets (80% of data) and testing sets (20% of data) to prepare for modeling. (NOTE: For this project several models were created, including RidgeCV Regression, LassoCV Regression, and Linear Regression. For the regression models with regularization techniques, dummy variables were created for all categorical variables that had not yet been coded. For Linear Regression, dummy variables were hand-selected based on EDA and the Lasso Regression. Because different sets of dummy variables were included in the models, there are two sets of data.)

During modeling, four models were built: Null Model, RidgeCV Regression with 305 features, LassoCV Regression with 124 features, and Linear Regression with 46 features. It is important to note that all of the features included in the Linear Regression Model were determined to be important based on EDA or the LassoCV regression. The models were compared based on R2 score, and the highest scoring model was selected for further evaluation using root mean square error and residuals plots. 

Interpretations and recommendations were made based off of the best-performing model. 

## Table of Contents
1. [Project Files](#../datasets)
2. [Data Dictionary](#Data-Dictionary)
2. [Model Selection](#Model-Selection)
3. [Conclusions and Recommendations](#Conclusions-and-Recommendations)

## Data Dictionary
A link to the data dictionary can be found [here](https://www.kaggle.com/c/dsi-us-12-project-2-regression-challenge/data). 

## Model Selection
As previously mentioned, four models were created for this project. 

Model Name | Training Score | Testing Score
-|-|-
Baseline/Null Model|0%|0%
Ridge|90.2%|82.3%
LASSO|91.5%|80.7%
Linear Regression|87.4%|87.8%

As shown in this table, of each of the models that I built, the Linear Regression performed the best in terms of R2 score. It had low bias, and was also not overfit.

## Conclusions and Recommendations
Although the linear regression model that was created during this sprint, is not perfect, it is able to account for approximately 87.8% of the variation in Sale Price of a property, and it also is able to predict the Sale Price within \$23,673.28. Further exploration of the residuals of this model revealed a specific weakness in this model at predicting extreme values. Specifically, the ideal range for predictions appeared to be within $90,000 to \$225,000. In order to better predict prices outside of this range, changes will need to be made to the model.

However, based on the current model, insights about the contribution of specific features to Sale Price can be derived from this model. Holding all else constant, we expect that:
* Having paved access to the property will result in a 19.7% increase in sale price.
* Being located on a hillside will result in a 16.9% increase in sale price.
* Having a paved driveway will result in a 10.7% increase in sale price.
* Having an attached garage will result in a 9.4% increase in sale price. 
* Having a basement garage will result in a 9.4% increase in sale price.
* Having an excellent kitchen will result in a 8.9% increase in sale price
* Having a built-in garage will result in a 8.2% increase in sale price
* A one-unit increase in overall quality will result in an 8.2% increase in sale price.
* Having an exterior quality of fair will result in a 17% decrease in sale price.
* Having a townhouse will result in a 11.4% decrease in sale price. 
* Having a duplex will result in a 8.2% decrese in sale price.

From this model, it also appears that a property in the first cluster of neighborhoods results in a 7.5% increase in sale price. These neighborhoods are: Stone Brooke, Northridge Heights, Veenker, North Ridge, and Green Hill. 

I hope to continue making improvements to this model to help automate the property appraisal process.

## References
1. [Population of Ames Iowa](https://datausa.io/profile/geo/ames-ia/)
2. [City of Ames Website](https://www.cityofames.org/about-ames/about-ames)
3. [Machine Learning in Real Estate](https://unionstreetmedia.com/the-rise-of-machine-learning-in-real-estate/#:~:text=Personalized%20Marketing%20Automation%20%E2%80%93%20machine%20learning,neighborhood%20and%20property%20is%20best)
4. [Ames Housing Data - Original Article](#http://jse.amstat.org/v19n3/decock.pdf)
