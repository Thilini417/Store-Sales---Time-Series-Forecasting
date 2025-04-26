This report presents our approach to predicting store sales using time series forecasting techniques. The primary goal was to develop an accurate machine learning model capable of forecasting sales for the test dataset. I utilized various models including XGBoost, and
LightGBM, and selected the best-performing one based on evaluation metrics.

Leaderboard Score: Best model achieved an RMSLE of 0.40786 on the leaderboard.

Solution Overview
Solution involved several key steps:
1. Data preprocessing and feature engineering: Here I used the Data cleaning and preprocessing as described in the section 3.
2. Exploratory Data Analysis (EDA) to understand trends, seasonality, and stationarity: First load the data set and merged as necessary. Then visualize the Time series component and
it will as Figure 2.1.
3. We have two methods to check data set stationarity. First one is the rolling mean and rolling standard deviation. Results of that shows
Figure 2.2. Next method was the Augmented Dickey Fuller test (ADF) Test According to that

Data set is stationary.
ADF Test Results:
ADF Statistic: -2.9316458403999253
p-value: 0.041789840054320446
Critical Values:
1%: -3.4342954463097706
5%: -2.8632826898390484
10%: -2.5676977663666714
Data is stationary (Reject H0)

According to the ADF results Dataset is stationarity. Therefore we don’t need to make it stationarity.

Implementation of different forecasting models, including statistical and machine learning models. The models I used described as in the Model training and evaluation
section.
As a Baseline Model used Naïve Forecast. It using the last observed sales value as a prediction. There I achieved as RMSLE Score as13.6196. Then I used ARIMA & SARIMA Models and
captured trends and seasonality in sales data. According to that I achieved ARIMA RMSLE:13.5615 and SARIMA RMSLE: 13.4938. Selecting the best model based on validation
performance and leaderboard score. But according to this they describe to use Machine learning for this task. Therefore used models as described in Model Training and evaluation.

Data Cleaning and Preprocessing
The dataset required various cleaning and preprocessing steps before modeling:
  Handling Missing Values: Forward-filling missing oil price values.
  Feature Engineering: Extracted time-based features such as day of the week, month, year,
and holidays.
  Encoding Categorical Variables: Used one hot encoding for categorical features like store
type and product family.
  Removing Special Characters: Cleaned column names to ensure compatibility with
LightGBM.
  Creating Lag Features: Introduced lag based and rolling window statistics for better
temporal dependencies

Model Training and Evaluation
XGBoost & LightGBM models are used time based features and lagged sales values. Performed time-series cross-validation. Applied hyper parameter tuning for optimal performance. Here I used GridSearchCV for the improvement the models. With that I achieved
  Avarage XGBoost RMSLE: 0.4188
  LightGBM RMSLE: 0.4359
According to the result best model was XGBoost. After I created the prediction with that modelto achieve above results in the leaderboard

Additional Evaluation Metrics
Beyond RMSLE, we considered following evaluation metrics which are RMSE, MSE, and R2.
Following table shows the comparison of values.

6. Alternative Solutions
Here I Used the XGBoost model is based on gradient boosting. Normally this is known for accuracy, speed and ability to handle large dataset.Random Forest model also can be get as an alternative. But it’s much slow than other algorithms.
As an alternative approach could involve Catboost model which is a gradient boosting algorithm. Normally this model will use when dataset contains many categorical data.Prophet which is from Facebook also can use as an alternative model which is specially design
for the time series forecasting for business applications. An alternative approach could involve deep learning techniques involved like Long Short term Memory (LSTM). It is better when a large dataset involved. These models excel at capturing
complex temporal dependencies and could potentially outperform traditional machine learning models with proper tuning and computational resources.
