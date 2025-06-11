# Enhanced LPPLS Mean Reversion Trading Strategy

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
