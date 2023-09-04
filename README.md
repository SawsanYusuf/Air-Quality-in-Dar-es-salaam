# Air-Quality-in-Dar-es-salaam


# Overview 
In this project, we worked with data from one of Africa's largest open data platforms [openAfrica](https://africaopendata.org/). We looked at air quality data from Dar es Salaam, Tanzania; and built a time series model to predict PM 2.5 readings throughout the day.

The model will assist in understanding and forecasting air quality levels, which can be crucial for public health and policy decisions.

In general, Time series models are not only important in public health; they're a key part of Financial Engineering and Natural Language Processing.

# Data Processing
1. Get the dataset by querying the MongoDB database. And then, we took that query and we turned it into a proper data frame, which will be able to use to train a model.And we put it into a single function.

2. Prepare the dataset for analysis:
   
