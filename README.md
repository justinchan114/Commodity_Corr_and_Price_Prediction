# Commodity_Correlation
## Introduction
This project aims to estimate the price of a commodity, with refence to the prices from other commodities that has high correlation.

## Data Set
Data set is from Kaggle, the "Commodity Futures Price History". It is available here: https://www.kaggle.com/datasets/mattiuzc/commodity-futures-price-history

## Methodology
### Exploratory Data Analysis
CSV files are read into pandas dataframes, and only Date and Closing Price of individual commodity is kept. They are combined into one df, and their daily log return was calculated. Heatmap is then plotted to have a quick look on the correlation between commodities.
