# 20/50 EMA Crossover Strategy: Backtest Analysis & Deliverables

## 1. Overview
This repository / assignment pack contains the Pine Script implementation, backtest data extraction, trade log spreadsheet, and performance evaluation for a pure 20/50 Exponential Moving Average (EMA) Crossover strategy.

---

## 2. Strategy Logic & Rules
The strategy operates on systematic trend-following mechanics without discretionary intervention:
* Instrument / Timeframe: Tested via TradingView strategy engine.
* Indicators: 
  * Fast EMA = 20 periods
  * Slow EMA = 50 periods
* Entry Trigger (Long): 20 EMA crosses strictly above the 50 EMA (`ta.crossover(emaFast, emaSlow)`).
* Exit Trigger (Flat): 20 EMA crosses strictly below the 50 EMA (`ta.crossunder(emaFast, emaSlow)`).

---

## 3. Workflow & Technical Approach

### A. Pine Script Implementation (v5)
* Developed using TradingView Pine Script v5 with overlay mode.
* Parameterized fast and slow lengths with `input.int()` for adaptability.
* Automated round-trip execution via `strategy.entry()` and `strategy.close()`.

### B. Data Extraction & Normalization
* Strategy tester records spanning Trade #1 to Trade #47 were transcribed from execution logs.
* For each trade, the following data points were captured:
  * Trade ID
  * Entry Timestamp & Entry Price (INR)
  * Exit Timestamp & Exit Price (INR)
  * Net Realized PnL (INR)
  * Percentage Return: Return (%) = ((Exit Price - Entry Price) / Entry Price) * 100


---

## 4. Backtest Performance Summary (47 Trades)

| Metric | Result | Interpretation |
| :--- | :--- | :--- |
| Total Trades | 47 | High turnover across testing window |
| Winning Trades | 10 | Positive PnL executions |
| Losing Trades | 37 | False breakout / whipsaw exits |
| Win Rate | 21.28% | Classical low win-rate profile of lagging momentum |
| Net Realized PnL | -₹4,364.40 | Unprofitable after churning during consolidation |
| Largest Single Winner | +2.67% (+₹2,545.60) | Trade #27 (Aug 27, 2026 – Aug 28, 2026) |
| Largest Single Loser | -1.33% (-₹1,307.20) | Trade #30 (Aug 28, 2026 – Aug 31, 2026) |

---
