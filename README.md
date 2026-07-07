# Retail Sales Time Series Forecasting

Time series forecasting project predicting weekly retail store sales 
using three joined data sources covering 45 stores, 99 departments, 
and 3 years of weekly sales history.

## Project Overview
I merged store information, sales history, and external features 
(temperature, fuel price, CPI, unemployment, holiday flags) into a 
single dataset and built three forecasting models. I applied 
chronological train/test splitting to avoid data leakage - a critical 
requirement for honest time series evaluation.

## Key Findings

| # | Theme | Finding |
|---|-------|---------|
| 1 | Seasonality | Strong November/December spike driven by holiday shopping |
| 2 | Holiday Impact | Holiday weeks generate measurably higher sales than non-holiday weeks |
| 3 | Store Type | Type A stores significantly outperform Type B and C on average weekly sales |
| 4 | Lag Features | Previous week sales and same week last year were the strongest predictors |
| 5 | Best Model | XGBoost achieved the lowest MAE and MAPE across all three models |
| 6 | Data Leakage | Chronological splitting is essential - random splitting would falsely inflate results |

## Models Compared
- **Linear Regression** - baseline model, struggles with non-linear seasonality
- **Random Forest** - captures non-linear patterns and feature interactions
- **XGBoost** - best performer, handles seasonality and lag features effectively

## Feature Engineering
I created the following time-based and lag features:
- Year, Month, Week, Quarter, Day of Year extracted from Date column
- Lag 1 week - previous week sales for the same store and department
- Lag 52 weeks - same week sales from the previous year
- Rolling 4 week mean - recent sales trend

## Data Sources
Three files merged on Store and Date:
- Sales data - weekly sales per store and department
- Store data - store type and size
- Features data - external economic indicators and holiday flags

## Tools Used
Python, pandas, numpy, matplotlib, seaborn, scikit-learn, XGBoost

## Dataset
[Retail Dataset - Kaggle](https://www.kaggle.com/datasets/manjeetsingh/retaildataset)
