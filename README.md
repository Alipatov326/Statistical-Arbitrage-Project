# Stat Arb V & MA

A simple statistical arbitrage project comparing **Visa (V)** and **Mastercard (MA)** using a **pairs trading / mean reversion** framework.

This project:
- Downloads historical adjusted close prices for `V` and `MA`
- Estimates a hedge ratio using **OLS regression**
- Computes the **spread** between the two assets
- Standardizes the spread using a **Z-score**
- Identifies potential **entry** and **exit** signals
- Visualizes price behavior, spread distribution, and trading zones

---

## Overview

Visa and Mastercard are highly related companies in the payments sector, which makes them a common candidate pair for relative value analysis.

The strategy assumes that:
- the two assets move together over time,
- temporary deviations may occur,
- and those deviations may eventually revert back toward their historical relationship.

This notebook uses a simple linear regression approach to estimate that relationship and generate trading signals when the spread becomes unusually wide.

---

## Strategy Logic

### 1. Retrieve historical price data

The script downloads adjusted close prices for:
- `V` = Visa
- `MA` = Mastercard

using the `yfinance` library.

### 2. Estimate hedge ratio

An **OLS regression** is run with:
- `V` as the dependent variable
- `MA` as the independent variable

This produces:
- `beta` = hedge ratio
- `alpha` = intercept

### 3. Calculate spread

The spread is defined as:

```python
spread = V - (beta * MA + alpha)
