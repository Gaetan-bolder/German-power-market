# Quant Strategies in the EU Power & Gas Markets

Focus: German Power Market (2024) & NWE Gas Market (2023–2024)
This repository contains a full suite of market analysis and algorithmic trading strategies for the EU energy landscape. The work includes realistic market modeling, forecasting, regime detection, and trading simulations — tailored for interview use:

1. 🇩🇪 Germany Grid & Dunkelflaute Analysis
- Identification of Dunkelflaute periods (low renewable production).
- Impact analysis on Day-Ahead (DA), Continuous Intraday (CID), and Imbalance Prices (IP).
- Volatility comparison between normal and Dunkelflaute periods.

2. 🌍 Cross-Border Arbitrage Strategy – Markov Chain + Q-Learning
- Arbitrage between Germany and 10 neighboring countries.
- Markov modeling of price regimes (Germany vs Neighbor).
- Reinforcement Learning (Q-Learning) vs Manual strategy.
PnL Output:
RL Strategy: €15,616,663.00
Manual Strategy: €18,258,046.00

3. 🧠 Negative Price Arbitrage with Machine Learning (LightGBM)
- Predict negative DA price in Germany.
- Execute X-border arbitrage if foreign price > DE + cost.
- Classification Model Output:
Poland: €15,785,038.86
Switzerland: €11,378,268.64
Austria: €11,004,214.50
France: €14,948,026.98

4. 🔋 Renewable Analysis
- Negative price dynamics driven by solar/wind saturation.
- Duck curve visualizations (load net of RES).
- Correlation of solar output and price by season.

5. 📊 DA, CID, IP – Volatility Strategy (KAMA)
- Use Kaufman’s Adaptive Moving Average (KAMA) for smoother trend detection.
- Two strategies:
Slope-based directional signal (1 day)
Dual KAMA crossover (1 vs 10 days slopes)
- Applied to DA, CID, and IP power markets (80%+ hit ratio)

6. 🔮 LSTM Load Forecast + Prediction Trading
- Train-test split (Jan–Nov = train, Dec = test) result = RMSE:  10.60 €/MWh; MAE:   8.43 €/MWh; MdAE:  7.21 €/MWh
- Strategy 1: Directional forecast =) buy/sell DA base on my forecast - can be used to trade DA future market =) 1 year PnL is 5Mio.
- Strategy 2: Optuna-based signal optimization (volatility/cost adjusted) - need to tune a bit more the details

7. 🧠 LightGBM Classifier for DA–CID Spread
- Predict DA–CID price spread for arbitrage.
- Trade if prediction > cost.
Output:
Flow: 20 MWh
Total Cumulative PnL 1Y: €2.3Mio

8. ⚖️ Imbalance System Analysis
- Germany long/short system classification.
- Analyze IP vs DA/CID in stressed systems.

9. 📉 PCA on Imbalance Prices
- Principal Component Analysis on IP price behavior.
Result: First 4 components explain 88.36% of total variance - which is great as a source of indicators

10. 🔁 Regime-Based Trading (DBSCAN + KMeans + GMM Clustering)
- Cluster market regimes using PCA of DA–IP spreads.
- Two strategies:
Profitable Regime Only
Regime Switcher (Momentum in Low Vol, Mean-Reversion in High Vol)
PnL Range: €14k → €1.5M+

11. 🛠️ German and neighboring countries outages impact on CID & IP markets price for Q1 & Q2 2024
-   Determine the number of "Planned" and "Forced" outages and their relative percentages
-   Analyze how outages impact CID and IP prices/vol using distribution
-   Determine how much vol is created on both markets when a Forced outages is live
Enters a buy in the CID market at the start of a forced outage
Exits the position by selling in the IP market at various time offsets (profitable up to 200 minutes). 

12. 🔋 BESS Optimization (Battery Strategy for CID & IDA)
- Constraints modeled: Efficiency, cycles/day, degradation, spread filter, capacity
- Two strategies:
Manual spread optimization
Deep Q-Network (DQN) RL Agent
PnL Output:
Manual (1 year): €8,559,084.47
DQN (4 months): €700,000

13. ⚙️ Power Sell Strategy (Rebalancing for Power Plant)
- Strategies for excess power:
- TWAP (10-min, 20-min)
- XGBoost optimization
Output:
TWAP 10-min: €239,823.10
TWAP 20-min: €261,165.00
XGBoost: €434,167.20

14. 🔥 Gas Shock Detection Strategy (TTF)
- Use Yang-Zhang Volatility (robust to jumps).
- Detect shocks based on storage limits, LNG, geopolitics.
- Backtest post-shock behavior:
Day 1 = up
Day 2 = reversion

15. 🔄 Gas–Renewable Correlation & Signal (In Progress)
- Investigate correlation between TTF gas and solar/wind generation.
- Build trigger logic for trading signals on price/fundamentals dislocation.

🛠️ Tools & Frameworks Used
- Python: pandas, numpy, LightGBM, XGBoost, scikit-learn, Optuna, LSTM, Keras, PyTorch, Seaborn, Matplotlib
- Machine learning: classification, regression, clustering
- RL: Q-Learning, Deep Q-Networks (DQN)
- Power market modeling: flow constraints, cost filters, renewable dynamics

📌 NOTE
- All strategies are simulation-only, based on real market structure and behavior.
- This repo is for educational and interview preparation purposes (esp. quant & energy trading roles).

