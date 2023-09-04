# Air-Quality-in-Dar-es-salaam


# Overview 
In this project, we worked with data from one of Africa's largest open data platforms [openAfrica](https://africaopendata.org/). We looked at air quality data from Dar es Salaam, Tanzania; and built a time series model to predict PM 2.5 readings throughout the day.

The model will assist in understanding and forecasting air quality levels, which can be crucial for public health and policy decisions.

In general, Time series models are not only important in public health; they're a key part of Financial Engineering and Natural Language Processing.

# Data Processing 
Get the dataset by querying the MongoDB database. And then, we took that query and we turned it into a proper data frame, which will be able to use to train a model.And we put it into a single function.

we made sure to set "Timestamp" as index, and Localize timezoneso that this *DatetimeIndex* for df is localized to the correct timezone, "Africa/Dar-es-salaam".

# Explority Data Analysis [EDA]
1. The distribution of PM2.5 values over the dataset.
   Fig
2. A time series plot of the "PM2" readings in df to indicate the trend changing.
3. A rolling average of the "P2" readings in df with using a window size of 168 (the number of hours in a week).
4. Pca
5. PcAf

   
