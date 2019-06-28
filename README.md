# Sales-prediction
Prediction of sold units of S items ( 3 types) over specific period of time.

# Idea
Main idea was to enter into Time series type of data and play with posibilites of predicting future unit sales.

# Used models : 
1. ARIMA - time-series predicting model created from two components :
 * AR - auto regressive model
 * MA - moving average model
 
Combining those two models result is ARIMA model and goal is to create such model to have smallest possbile result of RSS.

* RSS is difference between MA(q) and MA(q-1) models.

Main components are :
1. p - correlation between prevoius time period and current
2. d - is the number of differencing required to make the time series stationary
3. Q - moving average

Through predicting time series data it is important to create stationary data from given dataset.

Data is stationary if:
* constant mean - average
* constant variance - distance from the mean
* autocovariance that does not depend on time

Stationarity was checked by Dickey-Fuller Test: This is one of the statistical tests for checking stationarity. Here the null hypothesis is that the time series is non-stationary. The test results comprise of a Test Statistic and some Critical Values for difference confidence levels. If the ‘Test Statistic’ is less than the ‘Critical Value’, we can reject the null hypothesis and say that the series is stationary.

Transformation of data to create stationary data : 
1. ake natural logarithm of data
2. substract moving average of data from data
3. create The exponential moving average (EMA) is a weighted average of the last n prices, where the weighting decreases exponentially with each previous price/period. In other words, the formula gives recent prices more weight than past prices
4. substract log data and ema
5. shifting data for some period of time and then substract it from real data


2. XGBoost Regressor
After implementing ARIMA model, I wanted to see is there possibility to create better model.

Boost?

 - Boosting is a sequential technique which works on the principle of an ensemble. It combines a set of weak learners and delivers improved prediction accuracy.
 * Hyperparamteres : 
     a) learning_rate: step size shrinkage used to prevent overfitting. Range is [0,1]
     b) max_depth: determines how deeply each tree is allowed to grow during any boosting round.
     c) subsample: percentage of samples used per tree. Low value can lead to underfitting.
     d) colsample_bytree: percentage of features used per tree. High value can lead to overfitting.
     e) n_estimators: number of trees you want to build.
     f) objective: determines the loss function to be used like reg:linear for regression problems, reg:logistic for classification problems with only decision, binary:logistic for classification problems with probability.
