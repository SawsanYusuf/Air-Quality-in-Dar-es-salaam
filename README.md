# Air-Quality-in-Dar-es-salaam


# Overview 
In this project, we worked with data from one of Africa's largest open data platforms [openAfrica](https://africaopendata.org/). We looked at air quality data from Dar es Salaam, Tanzania; and built a time series model to predict PM 2.5 readings throughout the day. The model will assist in understanding and forecasting air quality levels, which can be crucial for public health and policy decisions.

# Data Processing 
We query the MongoDB database to retrieve the dataset. Then, we took that query and turned it into a proper data frame to be used to train a model.

We set "timestamp" as an index. And Localized this DatetimeIndex for the dataframe to the correct timezone, "Africa/Dar-es-salaam."

# Explority Data Analysis [EDA]
1. The distribution of PM2.5 values over the dataset.
   Fig

Based on this distribution, we dropped the "P2" readings above 100  from the dataset
   
2. How do our "P2" readings move over time?

3. The general trend for the "P2" readings:
   
# Model Selection 
We used various algorithms: Linear Regression, Autoregressive model, and ARIMA model.

## 1. Linear Regression Model
   Our linear regression model is based on the concept of manipulating our target variable "P2" to turn it into a feature. This is achieved by shifting our data by 1, which means using the reading from the previous hour to predict the current one.

This scatter plot shows the PM2.5 mean reading for each hour as a function of the mean reading from the previous hour.
Fig 
The plot shows a strong correlation between what happened in the previous hour and this hour. 

So, we trained the selected model on the training data. Finally, we evaluated model performance using the Mean Absolute Error (MAE) metric on the test data.

## 2. Autoregressive model:

