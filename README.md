# timeseries
# Retail Demand Forecasting — Time Series & Concept Drift

This project focuses on forecasting product demand in a retail context using time series analysis and machine learning. The goal is to evaluate how different forecasting strategies perform under **regime changes** and **concept drift**, which naturally occur in retail due to promotions, pricing, seasonality, and market dynamics.

---

##  Objective

Forecast monthly *Units Sold* for a retail product and compare:

1. **Static forecasting models**
2. **Adaptive forecasting models**
3. Behavioral response to **concept drift**

---

## Dataset

Source: Kaggle — Retail Store Inventory Dataset  
Structure: Daily data across multiple stores and products (multi-series)  
Time span: 2 years  
Granularity for forecasting: Product × Month

---

##  Methods & Models

### **Exploratory Analysis**
- Trend & seasonality analysis
- Distribution & variance
- Sku-level analysis
- Stationarity (ADF)
- ACF & PACF
- Detection of data leakage (Demand Forecast column)

### **Static Forecasting Models**
- Naive
- SARIMA
- XGBoost Regression (with exogenous features)

### **Adaptive Forecasting (Rolling Window)**
(used to handle concept drift)
- Rolling-Naive
- Rolling-XGBoost

---

##  Evaluation Metrics

- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)
- SMAPE (Symmetric Mean Absolute Percentage Error)

---

##  Key Findings

- The dataset exhibits **concept drift** and a **regime shift** near the end of the horizon.
- Static models degrade significantly under drift.
- Rolling retraining reduces error and improves adaptability.
- **Rolling-XGBoost achieved the best performance**, benefiting from exogenous variables.

> **Insight:** Forecasting in retail is not purely autoregressive — context matters (pricing, promotions, calendar effects, competition).

---

##  Tech Stack

- Python
- Pandas / NumPy
- Statsmodels (SARIMA)
- XGBoost
- Scikit-Learn
- Matplotlib / Seaborn

---

##  Results (Brief)

Performance improved significantly when using **adaptive** vs **static** forecasting.

Static SMAPE (approx):
- Naive: ~46.9%
- SARIMA: ~40.5%
- XGBoost: ~58.3%

Adaptive SMAPE (approx):
- Rolling-Naive: ~28.1%
- Rolling-XGBoost: ~25.7%




