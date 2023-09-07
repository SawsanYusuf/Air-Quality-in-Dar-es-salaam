# Air-Quality-in-Dar-es-salaam


# Overview 
In this project, we worked with data from one of Africa's largest open data platforms [openAfrica](https://africaopendata.org/). We looked at air quality data from Dar es Salaam, Tanzania; and built a time series model to predict PM 2.5 readings throughout the day. The model will assist in understanding and forecasting air quality levels, which can be crucial for public health and policy decisions.

# Data Processing 
We query the MongoDB database to retrieve the dataset. Then, we took that query and turned it into a proper data frame to be used to train a model.

We set "timestamp" as an index. And Localized this DatetimeIndex for the dataframe to the correct timezone, "Africa/Dar-es-salaam."

# Explority Data Analysis [EDA]
1. The distribution of PM2.5 values over the dataset:
![](https://github.com/SawsanYusuf/Air-Quality-in-Dar-es-salaam/blob/main/Images/PM2.5_distribution.png)

Based on this distribution, we dropped the "P2" readings above 100  from the dataset
   
2. How do our "P2" readings move over time?
![](https://github.com/SawsanYusuf/Air-Quality-in-Dar-es-salaam/blob/main/Images/Time_series.png)

3. The general trend for the "P2" readings:
 ![](https://github.com/SawsanYusuf/Air-Quality-in-Dar-es-salaam/blob/main/Images/rolling_avarege.png)  

# Model Selection 
We used various algorithms: Linear Regression, Autoregressive model, and ARIMA model.

## 1. Linear Regression Model
   Our linear regression model is based on the concept of manipulating our target variable "P2" to turn it into a feature. This is achieved by shifting our data by 1, which means using the reading from the previous hour to predict the current one.

This scatter plot shows the PM2.5 mean reading for each hour as a function of the mean reading from the previous hour.
![](https://github.com/SawsanYusuf/Air-Quality-in-Dar-es-salaam/blob/main/Images/lag_correlation.png)
The plot shows a strong correlation between what happened in the previous hour and this hour. 

Then, we trained the selected model on the training data with our nwe feature. Finally, we evaluated model performance using the Mean Absolute Error (MAE) metric on the test data.

**The model performance**: 
![](https://github.com/SawsanYusuf/Air-Quality-in-Dar-es-salaam/blob/main/Images/Linear_regression_model.png)

## 2. Autoregressive model:
When we built the regression model, we looked at what happened a day ago and used that information to predict the present. But there is no reason to limit ourselves to a lag of one.

So, how many lags should we have in our model to still have a good predictive model? The ACF and PACF plots are indispensable tools in this process.
![](https://github.com/SawsanYusuf/Air-Quality-in-Dar-es-salaam/blob/main/Images/ACF.png)

![](https://github.com/SawsanYusuf/Air-Quality-in-Dar-es-salaam/blob/main/Images/PACF.png)
Beyond 28, we don’t get a lot of predictive power. So, we instituted an autoregressive model and fit it to the train data with the lag argument equal to 28.

The residuals for the model:
![](https://github.com/SawsanYusuf/Air-Quality-in-Dar-es-salaam/blob/main/Images/Autoregressive_residuals.png)



It appears that there is no discernible trend, and the residuals follow a normal distribution.

**The model performance**:
![](https://github.com/SawsanYusuf/Air-Quality-in-Dar-es-salaam/blob/main/Images/Autoregressive_model.png)

## 3. ARMA model:
A couple of other important notes, We call the number of time steps we look back for our AR model as lag and P for shorthand. For our MA term, we use the error lag, and the letter we use to abbreviate that is Q. So, in the ARMA model, we want to decide what P and Q are.

So, for the possible values for P, we’re going to create a range from 0 to 25 by step of 8. Next, we have the parameters for Q, and here we will do a smaller range from 0 to 3 by step of 1. Then, we trained an ARMA model with those hyperparameters.

The best one of the models is the model where P was 8 and Q was 0. So, we instituted our model and fit it to the train data with those hyperparameters. 

**The final model performance**:
![](https://github.com/SawsanYusuf/Air-Quality-in-Dar-es-salaam/blob/main/Images/ARMA_model.png)

# Conclusion
This project demonstrates the successful development of a machine-learning model for predicting air quality in a city. The model's accuracy and real-time capabilities make it a valuable tool for understanding and managing air quality levels.

