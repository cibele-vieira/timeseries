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

The experimental results show that adaptive models, especially the Rolling-XGBoost approach, achieved superior performance in scenarios with concept drift. By continuously retraining the model using recent data (rolling window strategy), the solution maintained lower forecasting errors over time compared to static models.

From a business perspective, this brings several direct benefits:

• Greater forecast accuracy in dynamic environments, where demand patterns change due to seasonality, promotions or market shifts.
• Reduced risk of stockouts and overstock, improving inventory balance and operational efficiency.
• Faster adaptation to behavioral changes, minimizing financial losses caused by outdated models.
• More reliable demand signals to support planning, procurement and logistics decisions.

Although the project was developed in an analytical environment, the proposed architecture can be extended to a production-ready pipeline, including automated data ingestion, periodic retraining, forecast generation and dashboard integration for decision-makers. Combined with model versioning and monitoring practices, this approach supports governance, traceability and long-term model sustainability.




