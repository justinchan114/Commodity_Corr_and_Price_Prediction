# Commodity Correlation and Price Prediction
## Introduction
This project aims to estimate the price of a commodity, with refence to the prices from other commodities that has high correlation in the same period.

## Data Set
Data set is from Kaggle, the "Commodity Futures Price History". It is available here: https://www.kaggle.com/datasets/mattiuzc/commodity-futures-price-history

## Methodology
### Exploratory Data Analysis
CSV files are read into pandas dataframes, and only Date and Closing Price of individual commodity is kept. They are combined into one df, and their daily log return was calculated. After disposing missing data, heatmap is then plotted to have a quick look on the correlation between commodities.

### Train test split
We will then separate the data into train test split. Data before 2009 and after 2020 is disposed, due to missing data and abnormal high variance (pandemic in 2020). As such, we will use data from 2010-2017 for training, 2018 for validation, 2019 for testing.

### Finding correlation to Crude Oil (WTI)
Correlation between Crude Oil and other commodities were compared, and it is found that Brent Crude Oil, Heating Oil has the highest correlation to Crude Oil (WTI), as such their prices would be used to estimate Crude Oil's price.

### Model Training
A tensorflow neural network is used to predict Crude Oil's price. The input is Heating Oil and Brent Crude Oil price, that has been feature engineered, whereas the output Crude Oil's price.</br>
GridSearchCV from sklearn was used to select the best hyperparameters for model, including no. of hidden layers and no. of nodes (due to limited computing power, only a few hyperparameter combination was tested).</br>
Different rolling period was also compared to find the best windowed data.

## Conclusion
In this project we have successfully predicted the price of Crude Oil, based on the price of Heating Oil and Brent Crude Oil from the same period, with a R^2 score of ~0.83. It is noted that rolling of daily close price (of 5 days and 10 days) did not improve the performance. We may need to further analyze price of a shorter period (say minutes or seconds) to observe more correlation between commodities. As Brent Crude Oil and Crude Oil (WTI) is one of the most liquid commodities in market, they have very high market efficiency and prices reactions should be within minutes, if not seconds.
