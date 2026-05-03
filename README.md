# Quant Strategy Assignment (Part B)

## Overview
This project implements a rule-based mean-reversion trading strategy using the Relative Strength Index (RSI) along with a volatility filter. The goal is to evaluate and optimize the strategy using historical data and assess its robustness across multiple assets.

---

## Strategy Design
The strategy is based on the following principles:
- Buy when RSI indicates oversold conditions (RSI < L)
- Sell when RSI indicates overbought conditions (RSI > H)
- Apply a volatility filter to avoid trading during unstable market periods

---

## Parameter Optimization
A grid search was performed over parameters:
- L (lower RSI threshold)
- H (upper RSI threshold)
- W (volatility window)

Instead of selecting a single best parameter set, the focus was on identifying a stable region where performance remains consistent. This helps avoid overfitting.

---

## Backtesting Framework
The strategy was implemented using the `vectorbt` library, which allows efficient vectorized backtesting. Performance was evaluated using metrics such as Sharpe ratio.

---

## Multi-Stock Validation
To ensure robustness, the strategy was tested across multiple stocks. Results showed:
- Strong performance on some stocks (mean-reverting behavior)
- Weak performance on others (trending behavior)

This indicates that the strategy is not universally applicable and depends on market characteristics.

---

## Transaction Cost Analysis
Transaction costs were incorporated to simulate real-world trading conditions. It was observed that:
- Performance decreases when fees are included
- Strategies with frequent trading are more sensitive to costs

---

## Key Insights
- Mean-reversion strategies work better in non-trending markets
- Parameter stability is more important than peak performance
- Multi-asset testing is essential to avoid overfitting
- Real-world factors like transaction costs significantly impact profitability

---

## Conclusion
The project demonstrates a systematic approach to strategy design, optimization, and validation. Emphasis was placed on robustness and consistency rather than maximizing returns on a single dataset.
