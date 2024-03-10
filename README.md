# Boom bikes Case Study

## Table of Contents
* [Problem Statement](#problem-statement)
* [Objectives](#objectives)
* [Data Understanding](#data-understanding)
* [Data cleaning and manipulation](#data-cleaning-and-manipulation)
* [Data Analysis](#data-analysis)
* [Creating and training the model](#Creating-and-training-the-model)
* [Validate the model](#Validate-the-model)
* [Validate the model against test data](#Validate-the-model-against-test-data)
* [Conclusion](#Conclusion)
* [Technologies Used](#technologies-used)
* [Glossary](#glossary)
* [Team](#team)

## Problem Statement

A US bike-sharing provider BoomBikes has recently suffered considerable dips in their revenues due to the ongoing Corona pandemic. The company is finding it very difficult to sustain in the current market scenario. So, it has decided to come up with a mindful business plan to be able to accelerate its revenue as soon as the ongoing lockdown comes to an end, and the economy restores to a healthy state. 

## Objectives

BoomBikes aspires to understand the demand for shared bikes among the people after this ongoing quarantine situation ends across the nation due to Covid-19. 

Using Liner Regression we can understand the data, create a model, train it and validate it against test data.

The company wants to understand the variables that play a significant role in deciding the number of bikes on rent increases.

## Data Understanding

The data provides different variables which are noted when a bike is given on rent.

Few of the important columns of this dataset are - 
- temp
- yr (2018 and 2019)
- seasons (Summer/Winter/Spring/Fall)
- months (Jan to Dec)
- weekdays (Sunday to Saturday)
- Holiday	
- waether

## Data cleaning and manipulation
- Convert "season","mnth","weekday","weathersit" columns to categorical
- Convert categorical columns to dummy varaibles.
- atemp and temp varaibleds - both speak about temprature so we can ignore one of them. I have ignored atemp.

## Visulizing data
- Visualize numerical data
- Visualize categorcal data

## Data Analysis
- By plotting pair plot we can see which variables have a direct correlation with cnt.
- By plotting heat-map we can see which variables has a significant role in deciding cnt
- By plotting boc plot ont he categorical variables we decide which of those variables are significant
- Based on this we can eliminate the variables that are less significant. For eg - 'atemp', 'instant', 'dteday', 'casual', 'registered'

## Creating and training the model
- Rescaling using Min-Max - 'temp','hum','windspeed','cnt' - variables are rescaled so that the r-squared values can be easily compared.
- Created a model using LinerRegresion - RFE - To begin with all the variables are considered.
- Following steps are reiterated till we get the best fit
    -  Check the variables that has the highest p-value
    -  Drop that variable and re-fit the model
    -  Now check the VIF
    -  Check the variable that high VIF
    -  Drop the variable and re-fit the model and check the VIF
-  We can conclude that the model is good when none of the variables have p-value >0.05 (5%) and VIF > 5
-  I have removed variables - hum,workingday,weekday_Saturday, windspeed

## Validate the model
- We can validate the model using predict(), which gives the predictions.
- Find the residual and the polt on the residual
    - Residuals are approximately normally distributed with mean centered at 0 and hence the model is valid
- Plot a scatter chart on y_train and residual
    - There does not seem to be any sort of a pattern in the residuals, so the error terms are independent of each other
- Plot a pair plot on the train dataset now
    - There is no clear relationship between any of the variable in the final model, so there is no multicollinearity that exists
 
## Validate the model against test data
- Do the scaler transformation on the variables -  'temp','hum','windspeed','cnt'
- Check the predictions on the test data for the model we have created

## Conclusion
- R-squared is 82.4% on train set and 80.9$% on test set
- Adjusted R-squared is 82.1% on train set and 80.0% on test set¶
- Hence we conclude the model is statistically fit.
- Following are the variables that are significant in the cnt -
    - temp
    - yr
    - season_Summer
    - season_winter
    - mnth_July
    - weathersit_Mist + Cloudy
    - season_Spring
    - mnth_September
    - weekday_Sunday
    - weathersit_Light Precipitation 
- Inferences
    - Count of total rental bikes (cnt) in year 2019 is 23.2% higher than that in 2018
    - Unit increase in feeling temperature increases cnt by 50.4%
    - Unit increase in spring season decreases cnt by 7%
    - Cnt is 3% increase in summer season
    - Cnt is 8% higher in Winter season
    - Cnt is 4% lower in the month of July
    - Cnt is 7% higher in the month of September
    - Cnt is 4% lower on sunday
    - Cnt is 30% lower when there is light precipitation
    - Cnt is 7% lower when the weather is misty and cloudy

## Technologies Used
- [Python - Version 3.12.1](https://www.python.org/downloads/release/python-3121/)
- [numpy - Version 1.26.2](https://github.com/numpy)
- [pandas - Version 2.1.4](https://github.com/pandas-dev/pandas)
- [matplotlib - Version 3.8.2](https://github.com/matplotlib)
- [seaborn - Version 0.13.1](https://github.com/seaborn)
- [Jupyter Notebook - Version 7.0.6]()
- [JupyterLab - Version 4.0.9]()
- [sklearn - Version - 1.4.1](https://scikit-learn.org/stable/)
- [statsModel - Version - 0.14.1](https://www.statsmodels.org/stable/index.html) 

## Glossary
- Liner Regression

## Team
* [Prachi Goliwadekar](https://www.linkedin.com/in/prachi-goliwadekar-88321822/)
