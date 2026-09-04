Overview
This project implements a statistical arbitrage (pairs trading) strategy between Visa (V) and Mastercard (MA) stocks. It uses OLS regression to compute a hedge ratio between the two assets, calculates the price spread, and normalizes it into a Z-score to identify mean-reversion trading opportunities.

When the spread deviates significantly from its historical mean (Z-score beyond ±2.0), the script flags potential entry signals for a long/short pairs trade. It also visualizes price relationships, spread distribution, trading opportunity zones, and mean-reversion exit points.

Features
•	Downloads historical price data for V and MA via Yahoo Finance (yfinance)
•	Calculates hedge ratio using OLS linear regression (statsmodels)
•	Computes and normalizes the price spread (Z-score)
•	Generates buy/sell signals based on Z-score thresholds (±2.0)
•	Visualizations:
  - Z-score time series with threshold lines
  - Dual-axis price comparison chart (V vs. MA)
  - Z-score distribution histogram
  - Trading opportunity zones (shaded regions)
  - Mean-reversion exit points
•	Summary statistics table of trading days by signal zone (Sell / Buy / Neutral)

Requirements
•	Python 3.8+
•	Dependencies:
  - numpy
  - pandas
  - yfinance
  - statsmodels
  - matplotlib
  - seaborn

Install with:
pip install numpy pandas yfinance statsmodels matplotlib seaborn

Usage
1.	Clone or download the script.
2.	Run it in a Jupyter Notebook, Google Colab, or any Python environment that supports display() (or replace display() calls with print() if running as a plain .py script).
3.	Adjust the configuration section as needed:
tickers = ['V', 'MA']
start_date = '2023-01-01'
end_date = datetime.now().strftime('%Y-%m-%d')
4.	Run all cells/sections sequentially — the script will:
   - Fetch price data
   - Fit the hedge ratio
   - Plot the Z-score and trading signals
   - Print recent trade signals and summary statistics

Note: This script uses display(), which is native to Jupyter/Colab environments. If running as a standalone .py file, replace display(...) with print(...).

Trading Logic

Condition	Signal
Z-score > 2.0	SELL V / BUY MA
Z-score < -2.0	BUY V / SELL MA
Z-score returns to 0	Exit position (mean reversion)

Output Summary
•	Red zones: Short V, Long MA
•	Green zones: Long V, Short MA
•	Blue 'x' markers: Trade exit points (spread reverted to mean)
•	A summary table reports the number and percentage of trading days spent in each signal zone.

Disclaimer
This project is for educational and research purposes only. It does not constitute financial advice. Past performance and backtested signals do not guarantee future results. Always conduct your own due diligence before trading.

License
Specify your preferred license (e.g., MIT, Apache 2.0) here.

