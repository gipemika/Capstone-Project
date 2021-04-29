# DSI Capstone Project: Airbnb Rentals Price Prediction

## Problem Statement

Since 2008, Airbnb is a fast-growing online marketplace for lodging, primarily homestays for vacation rental, and tourism activities. Millions of guests and hosts have used Airbnb to expand on traveling possibilites and present a more unique, personalized way of experiencing the world. With that being said, millions of listings generate a lot of data, which can be analyzed and used to understand customers' and hosts' better in terms of behaviors and platform usage. 

New York City has been one of the hottest markets for Airbnb, with over 7.9 million active listings as of December 2020, a 2.6% increase from 7.7 million active listings in 2019. Having personal interest in renting Airbnb in New York City in this upcoming months and its location being one of the top major cities with highest active Airbnb listings, I will build a regression model to predict the rental price of Airbnb in New York City based on the dataset collected and identify the factors affecting the price of those Airbnb. The result will be helpful to Airbnb's data analysis team as well as Airbnb hosts who are looking to increase the price of their Airbnb properties. 

Model performance will be evaluated by RMSE, and the model should at least improve upon baseline by 10%. Baseline is defined as the mean of the target variable. 

## Executive Summary

I started off the project by importing the relevant libraries and the dataset: nyc. First, I explored the data by looking at size and general information of the datasets. Then, I began cleaning the dataset by filling in the missing data as we cannot have null values in our model and drop some irrelevant columns. I explored the data visualization of the dataset through bar charts, histograms, heat map, and box plots. The visualization provided the insights in terms of correlation and outliers between the target variable and other features. I also created dummy variables for nominal data and dropped some outliers to ensure better prediction for the model. 

I used train/test split to seperate datasets for training and testing. Then, I created the model benchmarks and linear regression model. I used R2 and RMSE as evaluation metrics for my model. Additionally, I used Ridge and Lasso regression to regularize my regression model. After finding the optimal alpha, I ran the models to find that Lasso regression performed slightly better than Ridge regression, hence I used Lasso model for my final evaluation, which I successfully achieved my goal of obtaining 27% better RMSE than the baseline model. 

## Data Dictionary

The data collected is the detailed listings data of Airbnb in New York City collected from airbnb website by http://insideairbnb.com/get-the-data.html , which is an independent, non-commercial set of tools and data that allow the community to explore how Airbnb is being used in cities around the world, as of February 4th, 2021. The dataset is composed of 16 columns and 37,012 rows. The columns correspond to each variable and the rows correspond to each advertisement/listing published on Airbnb.com across New York City.

       
| Feature                      | Variable type | Datatype | Dataset   | Description                                                                     |
|------------------------------|---------------|----------|-----------|---------------------------------------------------------------------------------|
| id                           | Norminal      | int64    | nyc       | Unique id assigned to the property                                                          |
| name                         | Norminal      | object   | nyc       | Name or description of airbnb                                             |
| host_id                      | Norminal      | int64    | nyc       | unique id assigned to the host                                    |
| host_name                    | Norminal      | object   | nyc       | Name of the host                                                            || neighbourhood+h              
| neighbourhood_group          | Norminal      | object   | nyc       | Neighbourhood group of airbnb                                                           |
| neighbourhood                | Norminal      | object   | nyc       | Neighbourhood name of airbnb                                           |
| latitude                     | Continuous    | float64  | nyc       | property latitude                                    |
| longtitude                   | Continuous    | float64  | nyc       | property longtitude     
| room_type                    | Norminal      | object   | nyc       | Type of room of airbnb                                                           |
| price                        | Discrete      | int64    | nyc       | Price per night of airbnb                                             |
| minimum_nights               | Discrete      | int64    | nyc       | Minimum nights required to stay at airbnb                                     |
| number_of_reviews            | Discrete      | int64    | nyc       | Number of reviews this airbnb received    
| last_review                  | Datetime      | object   | nyc       | Last review date for this airbnb                                                           |
| reviews_per_month            | Continuous    | float64  | nyc       | Number of reviews per month this airbnb received                                          |
| calculated_host_listings_count | Norminal      | int64   | nyc     | Number of the host properties                                     |
| availability_365                     | Norminal      | int64    | nyc     | Number of available days of this Airbnb within the year 


## Conclusion and Recommendations

|Regression Model|Training CV $R^2$ Score|Training CV RMSE Score|
|---|---|---|
|Baseline Model|-0.000|44|
|Linear Model|-4.100|637048016165039|
|Ridge Model|0.441|33|
|Lasso Model|0.442|33|

|Regression Model|Testing $R^2$ Score|Testing RMSE Score|
|---|---|---|
|Lasso Model|0.459|32|

Comparing between the models, Lasso regression model is the best model because it is best at predicting unseen data as well as giving the least estimated errors. However, the model is slightly underfit because it has high bias and low variance. We can consider removing more outliers from train dataset to lower RMSE.

Looking at coefficients, we found the best features to be used to predict the house price is mainly private room, followed by shared room, calculated host listing counts, and neighborhood such as Manhattan and Williamsburg. On the other hand, the worst features are neighborhood such as Graniteville, Rego Park, Jamaica Hills, and East New York. So, these features are the key features of the house that hosts or real estate developers should consider in order to make highest return from rental price. 

The model can be used on other city housing data as well since top features in the model should be similar to any other cities. However, the model can be improved by having many other features such as host ratings, type of amentities provided, free cancellation option, number of occupants, to get a better prediction on the rental price. 

Some further steps that we can consider are to include many more datetime features i.e. when the property was listed, whether interaction terms will improve the prediction, what are other outliers we can remove, and whether the prediction is still accurate when apply with other cities housing data. Also, we can further investigate NLP of reviews and recommendation system for future users



