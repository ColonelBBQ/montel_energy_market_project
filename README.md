# Energy Price Forecasting with XGBoost

## Introduction
This project aims to predict **ElbasMaxPriceDKK** in the **Nord Pool Energy Market** using an XGBoost regression model. The objective is to determine whether machine learning can improve short-term electricity price forecasting compared to a simple baseline model (lagged price).

## Dataset
The dataset used for this project is **Nord Pool Energy Market Data**, sourced from Kaggle: [Link](https://www.kaggle.com/datasets/pythonafroz/nord-pool-energy-market-data?resource=download). While it may not fully match Montel's operations, it serves as a valuable proxy for exploring forecasting techniques.

### Key Features
- **HourUTC**: Timestamp of the energy price record.
- **SpotPriceDKK**: Day-ahead electricity price in DKK.
- **ElbasMaxPriceDKK**: The maximum intraday electricity price.
- **Lagged Features**: Previous hourly, daily, and weekly prices (e.g., lag_1, lag_24, lag_168).
- **Rolling Features**: 3-hour and 24-hour rolling averages of spot prices.
- **Holiday Indicators**: Whether the date is a holiday, the day before, or the day after a holiday.

## Model Implementation
The model follows these key steps:
1. **Data Preprocessing**
   - Convert timestamps to datetime format.
   - Handle missing values using backward fill.
   - Generate lag and rolling mean features.
   - Add holiday indicators using predefined holiday lists.

2. **Baseline Model (Naive Forecast)**
   - Uses the previous hour's price (`lag_1`) as the predicted value.
   - MAE and RMSE are calculated for comparison with the machine learning model.

3. **XGBoost Regression Model**
   - Trained on selected features to predict `ElbasMaxPriceDKK`.
   - Evaluated using MAE and RMSE against the baseline model.

## Future Improvements
- **Feature Engineering**: Incorporate more market indicators, weather data, and demand/supply signals.
- **Alternative Models**: Explore LightGBM, LSTMs, or hybrid models.
- **Probabilistic Forecasting**: Predict confidence intervals instead of point estimates.
