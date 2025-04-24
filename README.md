# Pyhton script focusing on German power market (2024 period) and NWE gas (2023 & 2024 period)

This repository contains projects related to:
- Germany grid/dunkelfaute analysis (when it appends, how the DA,CID and IP markets are impacted during this period)
- X-border arbitrage strategy between DE and neighboring countries using Markov chain modeling & Reinforcemnt learning (Q-Learning) - not optimized.
Output = Cumul PnL RL Strategy: €15,616,663.00 & Manual Strategy: €18,258,046.00
- X-border arbitrage strategy focusing on negative price between DE and neighboring countries. Use of LightGBM model to classify possible DA negative price in DE and then use this classification for arbitrage.
Output = very good classification model : Poland €115785038.86; Switzerland €111378268.64; Austria €111004214.50, France €14948026.98 etc etc
- Renewable analysis (negative power price, duck curve, power split)
- Wholesale market analysis using Kaufman’s Adaptive Moving Average (KAMA) for DA, CID and IP DE markets using Slope strategy and dual KAMA strategy. 
- Germany DA power prices forecasting using LSTM model (training set from Jan to Nov/24 - test set Dec/24). Created two strategies base on prediction vs reality:
1st directional view
2nd optuna optimization using Vol and Cost constraints.
- Germany arbitrage between DA–CID spread prediction strategy using LightGBM model classifier.
Output : For a flow of 20MWh - The total cumulative PnL is €2,377,913.00
- Imbalance system analysis (long vs short system) - IP vs DA & CID markets.
- PCA analysis on IP
Output : The first four principal components explain 88.63% of the variance.
- Trading strategies base on Kmeans & GMM regimes clustering base on the spread between IP and DA markets:
1st Profitable Regime Only (Profit Cluster Strategy)
If cluster = profitable and Spread (IP - DA) > 0 → Buy (+1)
If cluster = profitable and Spread (IP - DA) < 0 → Sell (-1)
Else → No trade (0)
2nd Regime Switcher Based on Volatility
If Low-Volatility Cluster:Trade with momentum:Buy if Spread > 0, Sell if Spread < 0
If High-Volatility Cluster:Trade with mean reversion:Sell if Spread > 0, Buy if Spread < 0
Else → No trade (0)
Output : Lowest PnL is €140k and highest is 1.5Mio.
- BESS optimization for CID and IDA markets with real parameters (charge/discharge efficiency, time limit, limited cycle per day, trading fee "illiquid market cost", Max capacity, Minimun spread to enter the trade, battery degradation cost)
Output : Manual optimization base on specific spread (no future cheating) PnL €8,559,084.47 for 1 year; PnL Reinforcement learning base on deep Q-network (DQN) for 5 months is max €700K.
- Optimization of power sell strategy for power plant "rebalacing excess of power generation" - either buy using TWAPs (TWAP 10-min, TWAP 20-min) or via XGboost model optimization for the DE CID market.
Output : TWAP 10-min Total PnL: €239,823.10; TWAP 20-min Total PnL: €261,165.00; XGBoost ML Strategy Total PnL: €434,167.20
- Gas market analysis : analysis when TTF gas price face a shock (positive or negative base on storage levels limit, geopolitical events, Extreme weather, or LNG flows) base on Yang-Zhang Volatility for accurate shock detection based on recent volatility patterns (20 days MA for 2std dev signal). After a shock, the next day saw usually a positive average return and the second day after a shock a negative return.
- Gas vs renewable power generation correlation and finding trading signal --- working on it--


All these strats have quite realistic market behaviors/limitations. 


This repo is for practice only on EU power/gas market. 

