# 📈 Pairs Trading & Statistical Arbitrage Strategy
Fully automated statistical arbitrage system to detect best candidates for Pair Trading automatically from given list of Stocks

## **Overview**
This project implements a **Pairs Trading Strategy** using **Statistical Arbitrage** techniques.  
Pairs Trading involves identifying two **historically correlated** assets, detecting deviations from their expected price behavior, and executing trades based on **mean reversion**.

The strategy is fully automated and consists of:
✅ **Cointegration Testing:** Finds the best stock pairs for trading.  
✅ **Z-Score Based Signal Generation:** Detects overbought/oversold conditions.  
✅ **Backtesting Engine:** Evaluates performance using historical data.  
✅ **Performance Metrics:** Computes Sharpe Ratio, Max Drawdown, and Win Rate.  

---

## **🔧 Features**
- **Cointegration Analysis:** Uses the **Engle-Granger test** to detect cointegrated stock pairs.
- **Dynamic Stock Selection:** Automatically selects the **best stock pair** for trading.
- **Trading Signal Generation:** Uses **Z-score thresholds** for long/short entry & exit.
- **Backtesting Engine:** Simulates strategy performance over historical data.
- **Performance Evaluation:** Calculates **Sharpe Ratio**, **Max Drawdown**, and **Win Rate**.

---

## **🛠️ Tech Stack**
- **Python** 🐍
- **Pandas & NumPy** (Data Analysis)
- **Statsmodels** (Cointegration Testing & Regression)
- **Matplotlib & Seaborn** (Data Visualization)
- **Yahoo Finance API** (Stock Data)
- **Backtrader/Zipline** (Backtesting Framework)

---

## **📌 Project Structure**
/pairs-trading-strategy 
│── /data # Data directory (if needed) 
│── pairs_trading.py # Core implementation of strategy 
│── cointegration_test.py # Cointegration testing module 
│── backtest.py # Backtesting engine 
│── utils.py # Helper functions 
│── README.md # Project documentation 
│── requirements.txt # Python dependencies 
│── pairs_trading.ipynb # Jupyter Notebook with full implementation


---

## **📖 How It Works**
### **1️⃣ Identify the Best Cointegrated Pair**
- Fetches **historical stock data** from Yahoo Finance.
- Computes **correlation** and **cointegration p-values** for multiple stock pairs.
- Selects the **most cointegrated pair** for trading.

### **2️⃣ Generate Trading Signals**
- Uses **Ordinary Least Squares (OLS) Regression** to compute **hedge ratio (β)**.
- Calculates the **spread** between the two assets.
- Applies **Z-score transformation** to detect mean reversion signals:
  - **Buy Spread (Long Position):** Z-score < -2
  - **Sell Spread (Short Position):** Z-score > +2
  - **Exit Position:** Z-score returns to 0

### **3️⃣ Backtest the Strategy**
- Simulates trading over historical data.
- Computes **cumulative returns** and plots performance.

### **4️⃣ Evaluate Performance**
- **Sharpe Ratio:** Measures risk-adjusted return.
- **Max Drawdown:** Evaluates worst historical loss.
- **Win Rate:** Calculates percentage of profitable trades.

---

## **💻 Installation**
```bash
# Clone the repository
git clone https://github.com/Poulami-Nandi/Arbitrage_PT.git
cd Arbitrage_PT

# Install dependencies
pip install -r requirements.txt
```
---

## **Usage**
```bash
from cointegration_test import CointegrationTester

# Define stock pairs to test
stock_pairs = [("GS", "MS"), ("JPM", "C"), ("AAPL", "MSFT")]

# Run cointegration test
tester = CointegrationTester(stock_pairs)
results = tester.test_cointegration()
tester.display_results()
```
---

## **Run pair trading strategy**
```bash
from pairs_trading import PairsTradingStrategy

# Use best cointegrated pair from test results
best_pair = tester.get_best_pair()

# Run trading strategy
strategy = PairsTradingStrategy(stock_1=best_pair[0], stock_2=best_pair[1])
strategy.fetch_data()
strategy.compute_spread_and_zscore()
strategy.generate_trading_signals()
strategy.backtest_strategy()
strategy.evaluate_performance()
```

---

## **Visualization/Example output**
- **Performance of the Pairs Trading Strategy Goldman Sachs and Morgan Stanly**
![Performance of the Pairs Trading Strategy Goldman Sachs and Morgan Stanly](https://github.com/Poulami-Nandi/Arbitrage_PT/blob/main/images/results/sample/GS_MS_Pair_trading.png)
- **Performance of the Pairs Trading Strategy Apple and Microsoft**
![Performance of the Pairs Trading Strategy Apple and Microsoft](https://github.com/Poulami-Nandi/Arbitrage_PT/blob/main/images/results/sample/aapl_msft_Pair_trading.png)
- **cointegration test results for stock pairs**
![cointegration_test_results_SP](https://github.com/Poulami-Nandi/Arbitrage_PT/blob/main/images/sample/cointegration_test_results_SP.png)
- **Performance of the Pairs Trading Strategy SPY and VOO**
![Performance of the Pairs Trading Strategy SPY and VOO](https://github.com/Poulami-Nandi/Arbitrage_PT/blob/main/images/sample/perf_PT_spy_voo.png)

---

## **🛠️ Next Improvements**
- 🔹 **Add Stop-Loss Mechanisms for risk management.**
- 🔹 **Optimize Trading Parameters using Machine Learning.**
- 🔹 **Deploy as a Live Trading Bot that generates signals for Pair Trading.**

---


## 📝 **References**
- Pairs Trading: Gatev, Goetzmann, and Rouwenhorst (2006)
- Cointegration Analysis: Engle & Granger (1987)
- Statistical Arbitrage: Avellaneda & Lee (2010)

---

## **📬 Contact & Contributions**
💡 Found this useful? Feel free to ⭐ star this repo and contribute!
For questions or contributions: 📧 nandi.poulami91@gmail.com
🌐 LinkedIn



