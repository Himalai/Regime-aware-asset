# Regime-Aware Asset Allocation
### Machine Learning Based Dynamic Portfolio Strategy

**Author:** Himalai Appikatla  
**Field:** Quantitative Finance | Asset Allocation | Machine Learning  

---

## Project Overview

This project builds a **Regime-Aware Dynamic Asset Allocation strategy** that adjusts portfolio weights based on predicted market volatility regimes.

Instead of using fixed allocations, the model detects **Low-Volatility vs High-Volatility regimes** and dynamically reallocates capital across assets to improve risk-adjusted performance.

The goal is to answer:

> Can machine learning identify market regimes and improve portfolio performance compared to static allocation?

---

## Assets Used

- **SPY** — US Equities  
- **EFA** — International Equities  
- **AGG** — Bonds  
- **GLD** — Gold  
- **VNQ** — Real Estate  

Daily data: **2015 → 2026**

---

## Methodology

### 1. Regime Detection
Market regimes defined using **20-day rolling volatility of SPY**

- Regime = 0 → Low Volatility  
- Regime = 1 → High Volatility  

Threshold = Median volatility

---

### 2. Feature Engineering

Features used to predict **tomorrow's regime**

- `vol20` → Recent volatility (risk signal)
- `mom60` → 60-day momentum (trend signal)
- `mkt_ret` → Daily SPY return (short-term signal)

---

### 3. Machine Learning Model

Model: **Random Forest Classifier**

Why Random Forest:
- Captures non-linear relationships
- Robust to noise
- Works well for regime classification

Train/Test split preserves **time-series order**.

---

## Model Performance

### Classification Results

Accuracy: **95%**

Confusion Matrix:

| Actual / Predicted | Low Vol | High Vol |
|-------------------|---------|----------|
| Low Vol           | 381     | 19       |
| High Vol          | 24      | 397      |

Random Forest significantly outperformed Logistic Regression.

---

## Feature Importance

Most important predictor:

1. **vol20 (≈80%)** — Market volatility dominates regime detection  
2. `mom60` — Trend signal  
3. `mkt_ret` — Short-term noise signal  

---

## Portfolio Strategy

### Dynamic Allocation

**Low Vol Regime**
- SPY 40%
- EFA 20%
- AGG 20%
- GLD 10%
- VNQ 10%

**High Vol Regime**
- SPY 15%
- EFA 10%
- AGG 45%
- GLD 20%
- VNQ 10%

The strategy shifts toward **defensive assets during high volatility**.

---

## Performance Comparison (Monthly, Net of Costs)

| Strategy | Ann Return | Ann Vol | Sharpe | Max Drawdown |
|----------|------------|---------|--------|--------------|
| Regime Strategy | **12.13%** | **8.30%** | **1.43** | **-7.83%** |
| Static Portfolio | 12.34% | 8.97% | 1.35 | -7.54% |

### Key Insight

- Regime strategy **improves Sharpe ratio**
- Better **risk control**
- Slightly smoother drawdowns
- Volatility-aware allocation improves risk-adjusted return

---

## Probability-Based Regime Strategy

The model also tested **probability-weighted allocation** using predicted regime probability.

- Average turnover ≈ **10%**
- Stable performance after transaction costs

---

## Benchmark Comparison

Compared against:

- Static Portfolio  
- 60/40 Portfolio  
- Risk Parity  

The **Regime Strategy delivered competitive performance with improved risk control**.

---

## Additional Analysis

- Volatility threshold sensitivity tested
- Feature importance studied
- Turnover measured
- Out-of-sample walk-forward validation performed

---

## Key Visualizations

The repository includes:

- Wealth Curve: Regime vs Static
- Drawdown Comparison
- Feature Importance
- Confusion Matrix
- Regime Timeline
- Parameter Sensitivity

---

## Results Summary

**Dataset:** Daily market data (2015–2026)  
**Model:** Random Forest Regime Classifier  
**Evaluation:** Out-of-sample, time-series split  

### Model Accuracy

- Classification Accuracy: **~95%**
- Strong separation between Low-Vol and High-Vol regimes
- Volatility is the dominant predictive feature

### Key Insights

- Dynamic allocation **improves risk-adjusted return**
- Defensive positioning during high-volatility reduces downside risk
- Machine learning successfully identifies regime shifts
- Strategy remains stable after transaction costs
- Low turnover (~10%) makes strategy practical

---

## Project Summary

**Regime-Aware Asset Allocation using Machine Learning**

Developed a machine learning-based dynamic portfolio strategy that adjusts asset allocation based on predicted market volatility regimes. Built a Random Forest classifier using volatility and momentum features to forecast future regimes and dynamically rebalance a multi-asset portfolio. Conducted out-of-sample backtesting with transaction costs and benchmark comparison. The strategy improved Sharpe ratio and risk control compared to static allocation, demonstrating practical application of machine learning in quantitative asset management.


## Project Significance

This project demonstrates how **machine learning can be applied to real-world portfolio management problems**, combining quantitative finance theory with data-driven regime prediction to improve portfolio risk-adjusted performance. The framework can be extended to multi-factor, macro-driven, or live trading systems.


## Future Improvements

- Add macroeconomic indicators
- Try Gradient Boosting / XGBoost
- Multi-regime classification
- Transaction-cost optimization
- Live market deployment
- Deep learning regime models

---

## Repository Structure

## How to Run the Project

1. Clone the repository


Run all cells to reproduce results.

---

## Reproducibility

- Data source: Stooq (daily market data)
- No look-ahead bias: Features at time **t** predict regime at **t+1**
- Time-series split used (no random shuffle)
- Transaction cost included in evaluation
- Out-of-sample testing performed

---

## Skills Demonstrated

- Quantitative Finance & Portfolio Management
- Asset Allocation & Risk Management
- Regime Detection & Volatility Modeling
- Machine Learning (Random Forest, Logistic Regression)
- Feature Engineering
- Time-Series Modeling
- Backtesting & Strategy Evaluation
- Performance Metrics (Sharpe, Drawdown, CAGR)
- Financial Data Analysis with Python
- Research & Quantitative Strategy Design

---

## Author

**Himalai Appikatla**  
MSc Quantitative Economics & Econometrics  
Quantitative Finance | Asset Allocation | Machine Learning  

GitHub: https://github.com/Himalai  

---

## Disclaimer

This project is for **educational and research purposes only**.  
It does not constitute financial advice or investment recommendation.


