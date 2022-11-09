# Residential-Real-Estate-Analysis
## Luke DiPerna
### August, 2022
![movie_clapper](https://github.com/luke-lite/Residential-Real-Estate-Analysis/blob/main/houses.jpg?raw=true)

## Project Goal
This project is designed to assist a residential real estate company (KC Real Estate) operating in King County. The company primarily helps homeowners sell their homes. The company needs a reliable and efficient way to properly valuate their clients homes. For this to be feasible, they will need a model that can accurately and reliably predict the price of a home given enough data regarding the features of the home.

Using the data provided by the company, I will build regression models in an iterative process to refine my results and create a model that can assist them in setting a preliminary selling price.

## Table of Contents
- [Data Preparation](#Data-Preparation)
- [Feature Engineering](#Feature-Engineering)
- [Key Metrics and Assumptions](#Key-Metrics-and-Assumptions)
- [Regression Models](#Regression-Models)
- [Regression Results](#Regression-Results)
- [Repository Structure](#Repository-Structure)

## Data Preparation

The data for this project is the King County house sales dataset. It contains 21,596 house sales in the county in 2014 and 2015. This project assumes that the data is current, and as a result does not take inflation or other market factors into account.

The dataset can be found here. It is fairly clean already, so it does not require much preparation outside of filling the NaN values. 

## Feature Engineering

Several features included in the dataset are unsuable for a regression analysis, but contain important information, like `date`. Using the `date` feature, along with `yr_built` and `yr_renovated`, I engineer the following features:
- `house_age`
- `renovated` (boolean)

## Key Metrics and Assumptions

In order to compare the regression models, I will be using the following metrics:

**Root Mean Squared Error (RMSE)**: measures the standard deviation of the models prediction errors (residuals).
**R-squared**: measures goodness-of-fit for the model. The score (ranging between 0-1) will naturally increase as the number of variables in the model increase, so we will also need the adjusted R-squared score.
**Adjusted R-squared**: accounts for the number of features included in the model. This score will drop relative to the unadjusted score if the additional features do not improve the model.
**Cross-Validation Score**: the mean of the model's R-squared scores when performed 10 times on different splits of the training data.

I will then validate each model by testing if they meet the assumptions of linear regression. These assumptions are:

**Linearity**: the relationship between the independent and dependent variables is linear. As we will see, this assumption no longer applies once we introduce polynomial regression, since our model will no longer be linear.
**Normality**: the dependent variable is normally distributed for any fixed value of the independent variables.
**No multi-collinearity**: the independent variables are not highly correlated with one another (collinear).
**Homoscedasticity**: the variance of the residuals is constant for all values of X.

## Regression Models
I begin with a simple linear regression model using only one indepedent variable: `sqft_living`. It is the independent variable that is most highly correlated with 
my dependent variable `price` and has a correlation of 0.702. This is my baseline model that I can compare future models to.

I then build 6 more iterations with varying results. The methods used include:

- increasing the number of independent variables
- normalizing and standardizing the variables
- One-Hot-Encoding the categorical variables
- polynomial regression

Below is a dataframe containing the metrics for each model:



Ultimately, the last model, a polynomial regression model using all variables, was the most accurate. 

## Regression Results


## Repository Structure
