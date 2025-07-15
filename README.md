# Lagged Macro Predictors for VNQ Return Forecasting

This project explores the predictive relationship between **lagged macroeconomic indicators** and the quarterly returns of **VNQ**, the Vanguard Real Estate ETF. Using **Lasso regression (LassoCV)** on time-lagged macro factors, we aim to forecast REIT performance and analyze signal quality.

While a simple threshold-based trading overlay is implemented for backtesting, the primary focus remains on **prediction accuracy and factor importance**.

---

## Highlights

**Lagged Macro Features:**  
Incorporates GDP growth, Fed Funds Rate, CPI, housing affordability, credit spreads, and more — with lags identified via Granger causality.  

**Stationarity & Preprocessing:**  
ADF tests ensure stationary series, and non-stationary variables are differenced.

**Predictive Modelling:**  
- Expanding-window **LassoCV** for feature selection and forecasting
- Evaluation via correlation (R), RMSE, and residual analysis

**Exploratory Backtest:**  
Applies a σ-threshold trading overlay and Treasury allocation for capital preservation. (Caution: for demonstration only)

---

## Key Results

| Metric        | Best σ-Threshold | VNQ ETF |
|---------------|-------------------|---------|
| **CAGR**      | +8.51%            | +0.39%  |
| **Sharpe**    | 0.75              | 0.11    |
| **Calmar**    | 1.40              | —       |
| **Max Drawdown** | 6.4%           | -       |

The predictive model achieves a correlation (R) of **0.53** between predicted and actual returns.

---

## Methods

###  Data Sourcing
- **Macro Factors:** FRED & Yahoo Finance
- **REIT ETF (VNQ):** Yahoo Finance

### Feature Engineering
- Lag identification via **Granger causality tests**
- Construction of a **Real Estate Premium (REP)** based on debt-to-equity splits

### Modelling
- Expanding-window **LassoCV** regression
- Prediction evaluation: Correlation (R), RMSE

### Exploratory Strategy
- σ-threshold based position sizing
- Treasury yield allocation during neutral signals
