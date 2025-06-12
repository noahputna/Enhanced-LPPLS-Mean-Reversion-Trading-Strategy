# Enhanced LPPLS Mean Reversion Trading Strategy
Capstone Project as part of Algorithmic Trading (FNCE30010) at The University of Melbourne.
## Authors
- Noah Putna
- Viktor Myszko
- Joseph Williams

## Overview
This project investigates whether the inclusion of bubble prediction signals using the Log-Periodic Power Law Singularity (LPPLS) model can enhance the performance of short-term mean reversion trading strategies. We evaluate the strategy's effectiveness across different market conditions by backtesting across two distinct periods: 2005-2010 and 2016-2021.

## Objectives
- Evaluate short-term mean reversion strategies on US equities.
- Identify the weaknesses in reversal-based approaches during bull markets.
- Incorporate LPPLS-based bubble diagnostics to dynamically adjust strategy behaviour.
- Test multiple strategy variants with and without LPPLS filtering.

## Background
Mean Reversion assumes that asset prices tend to return to their long-term average. Despite earlier arguments for market randomness (Fama, 1965), subsequent literature (Fama & French, 1988; Rosenberg et al., 1998) supports reversion over both long and short horizons.

## Strategy Summary
### Base Strategy
Inspired by Groot, Guij, and Zhou (2011):
- Long: 10 worst-performing stocks of the previous week.
- Short: 10 best-performing stocks of the previous month.
- Weekly rebalancing, tested using QuantConnect (2000-2022).
- **Base performance (2000-2022)** :
  - CAGR: 22%
  - Sharpe Ratio: 0.82

### Identified Pitfalls
- Weak performance in strong bull markets (e.g., 2016-2021).
- High contrarian risk during downturns.
- Liquidity and cost assumptions.

## LPPLS Integration
The LPPLS model predicts bubbles through:
1. Faster-than-exponential growth.
2. Accelerated price oscillations.
3. Mean-reverting residuals.

These signals help dynamically adjust the trading approach, particularly during unsustainable market surges or corrections.

## Strategy Variants
**Group A - Changing Aggression**
- Adjust leverage based on LPPLS signal.

**Group B - Seek Bubble Risk**
- Hold S&P 500 until bubble is detected, then switch to mean reversion.

**Group C - Avoid Bubble Risk**
- Use mean reversion until bubble is detected, then switch to S&P 500.

## Key Results
| **Strategy**                                                 | **Period**  | **Return** | **Sharpe** |
| ------------------------------------------------------------ | ----------- | ---------- | ---------- |
| Aggresive w/ LPPLS (bubble signal)                           | 2005 - 2010 | 65.2%      | 1.64%      |
| Aggresive w/ LPPLS (bubble signal)                           | 2016 - 2021 | 1.8%       | 0.18%      |
| Short-term reversal (baseline)                               | 2016 - 2021 | 3%         | 0.20%      |
| Hold S&P 500 -> switch to reversal when LPPLS signals bubble | 2016 - 2021 | 6.86%      | 0.37%      |
| Reversal -> switch to S&P 500 when LPPLS signals bubble      | 2016 - 2021 | 11.9%      | 0.59       |

-  Leverage-based models enhanced performance in volatile periods (2005-2010).
- LPPLS switching improved Sharpe ratio significantly for 2016-2021 (from 0.2 to 0.58).
- No negative bubble signals were detected in 2016-2021, limiting signal opportunities.

## Discussion
- LPPLS models show promise in adapting strategy behaviour based on market conditions.
- Effective in filtering out weak performance phases of reversal strategies.
- Useful particularly when short-term reversals underperform due to extended trend persistence.
