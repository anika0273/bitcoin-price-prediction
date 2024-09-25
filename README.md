# Bitcoin Price Forecasting Project

## Overview

This project aims to forecast Bitcoin prices using time series analysis. By leveraging various statistical models, including AR, MA, ARMA, and ARIMA, we analyze historical price data to predict future trends. The primary goal is to assess the model's effectiveness and identify patterns in Bitcoin's price fluctuations.

## Table of Contents

1. [Data Collection](#data-collection)
2. [Data Preprocessing](#data-preprocessing)
3. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
4. [Modeling](#modeling)
   - [AR Model](#ar-model)
   - [MA Model](#ma-model)
   - [ARMA Model](#arma-model)
   - [ARIMA Model](#arima-model)
5. [Forecasting](#forecasting)
6. [Results and Evaluation](#results-and-evaluation)
7. [Conclusion](#conclusion)


## Data Collection

This dataset consists of monthly average closing prices of Bitcoin from Dec 2011 to March 2021.
Data Dictionary:
	- Timestamp: Date when the price was collected
	- Close: The closing price of Bitcoin

## Data Preprocessing

- The closing prices are log-transformed to stabilize variance and prepare for modeling.
- The data is split into training and testing datasets to evaluate model performance.

## Exploratory Data Analysis (EDA)

- Time series plots are generated to visualize price trends.
- Summary statistics and correlation analyses are performed to understand the relationships between different price metrics.

## Modeling

### AR Model

- An AutoRegressive (AR) model is implemented to predict Bitcoin prices based on its own past values.

### MA Model

- A Moving Average (MA) model is used, particularly with a focus on lagged values to capture trends.

### ARMA Model

- The ARMA model combines both AR and MA components to improve predictions by using both past prices and past forecast errors.

### ARIMA Model

- An ARIMA model is employed, with parameters p, d, and q set to account for seasonality and trends.
- The model is fit to the training data, and forecasts are generated for future prices.

## Forecasting

- The models forecast Bitcoin prices for the next 12 months.
- The forecasts are transformed back to the original price scale using the inverse log transformation.
- A new DataFrame is created with predicted values indexed by date.

## Results and Evaluation

- The original Bitcoin prices are plotted against the predicted values to visually assess model performance.
- Root Mean Squared Error (RMSE) is calculated to quantify prediction accuracy on both training and testing datasets.

```python
from sklearn.metrics import mean_squared_error

# Calculate RMSE for training data
error_train = mean_squared_error(predictions_ARMA, df_train, squared=False)

# Calculate RMSE for testing data
error_test = mean_squared_error(forecasted_ARMA, df_test, squared=False)
```

## Conclusion

The analysis revealed that while the models performed well on training data, they struggled to accurately predict prices during volatile periods in the testing data. The observed higher RMSE on test data indicates that the models may not sufficiently capture the large fluctuations characteristic of Bitcoin prices.

### Future Work

- Explore more complex models like SARIMA and SARIMAX to enhance forecasting accuracy.
- Incorporate external factors, such as market sentiment and macroeconomic indicators, to improve predictions.