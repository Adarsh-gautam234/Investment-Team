# Quant Strategy Assignment (Part B)

## Overview
This project implements and evaluates a mean-reversion trading strategy using the Relative Strength Index (RSI) along with a volatility filter. The objective is to design a robust strategy, optimize its parameters, and validate its performance across multiple assets.

---

## Data Processing
- Extracted OHLCV data for individual stocks from the dataset
- Cleaned data by:
  - Replacing invalid values (0 → NaN)
  - Forward-filling missing values
  - Removing non-positive and undefined values
- Ensured a continuous and reliable price series for analysis

---

## Strategy Design
The strategy is based on mean reversion:

- **Buy Signal (Entry):**
  - RSI < L (oversold condition)
  - Volatility < average volatility (stable market)

- **Sell Signal (Exit):**
  - RSI > H (overbought condition)

### Intuition
- RSI identifies potential reversal opportunities  
- Volatility filter avoids trading during unstable or high-risk conditions  

---

## Backtesting Framework
The strategy is implemented using the `vectorbt` library:
- Signals are converted into trades using `Portfolio.from_signals`
- Performance metrics such as Sharpe ratio are used for evaluation

---

## Parameter Optimization
A grid search was performed over:
- L (lower RSI threshold)
- H (upper RSI threshold)
- W (volatility window)

### Key Insight
Instead of selecting a single parameter combination with the highest Sharpe ratio, the focus was on identifying a **stable region** where performance remains consistent.

This helps avoid overfitting and ensures robustness.

---

## Multi-Stock Validation
The strategy was tested across multiple stocks:

- Strong performance observed in some stocks (e.g., C, E)
- Weak performance in others (e.g., B)

### Insight
- Strategy performs well in **mean-reverting markets**
- Underperforms in **trending or abnormal market conditions**

---

## Transaction Cost Analysis
Transaction costs were incorporated to simulate real-world trading:

- Frequent trading reduces net returns due to fees
- Small-profit trades often become unprofitable

### Insight
- Strategy must balance signal frequency and profitability  
- Over-trading is penalized in realistic conditions  

---

## Key Learnings
- Strategy performance depends on market behavior (mean-reverting vs trending)
- Stability of parameters is more important than peak performance
- Multi-asset validation is essential to avoid overfitting
- Transaction costs significantly impact real-world performance

---

## Conclusion
This project demonstrates a systematic approach to:
- Strategy design
- Parameter optimization
- Robustness validation

The emphasis was placed on building a **consistent and reliable strategy** rather than maximizing returns on a single dataset.
