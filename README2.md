# Project 2 Dream Team 


**PROCESS**

We completed a survey of several trading strategies. We used the Backtesting Library to search for outperforming
simple moving average crossover strategies. We then confirmed with our own backtesting code. We also examined bollinger bands, various buy and sell rules, and sentiment data. 

We used Alpaca and Apha Vantage to pull in 20 years of data. We used sentiment data from 1987 pulled from the AAII website. AAII conducts a weekly survey of its members regarding their bullishness or bearishness and makes the data available to the public via its website. 

1. The backtesting library and our own backtesting showed a short 215 and long 225 moving average as the best performing sma strategy over 20 years. Much of the outperformance vs buy and hold occurred because of a good sell signal just before 2008 bear market. However, the strategy outperformed using only the last 5 years of data as well (does not include 2008 bear market). 

  

![215_225_SMA.png](Images/215_225_SMA.png)

This strategy had a higher annual return, lower volatility, and higher sharpe ratio than the S&P500.

![215_225_stats.png](Images/215_225_stats.png)


2. We also used the backtesting library to improve upon the convential 50/150 SMA strategy. We obtained better performance with a 57/130 SMA strategy. 

    A backtest showed a 135% return for the 57/130 strategy while a backtest using the 50/150 strategy showed a 87% return. So we were able to improve upon the 50/150 strategy. However, both strategies underperformed the buy and hold return of the S&P 500. Much of the underperformance was due to the Coronavirus bear market. 

3. We tested a 10 month SMA strategy using month end data. The strategy is to sell when the S&P500 goes below the 10 month SMA and buy when the S&P500 rises above the 10 month SMA. Buy and sell signals are only made at month end. 
Month-end data from January 1950 was downloaded from Yahoo Finance. The strategy did not beat a buy and hold.
Next, data from January 1990 was used and the backtest run again. This time the strategy outperformed Buy and
Hold. 
 
![10_mo_SMA.png](Images/10_mo_SMA.png)

This strategy is notable for its performance during big bear markets.

2000 Bear Market, sell and buy signals

![10_mo_SMA_2000bear.png](Images/10_mo_SMA_2000bear.png)

2008 Bear Market, sell and buy signals

![10_mo_SMA_2008bear.png](Images/10_mo_SMA_2008bear.png)

4. We searched for the best short term sma trading strategy by constraining the backtesting library to only look at strategies using smas between 1 and 200.  The best it could find was a short 2, long 13 sma crossover. While this strategy beat the S&P500 over the last three years it did terribly over 20 years. 
 

![2_13_SMA_20_years.png](Images/2_13_SMA_20_years.png)

So this is not an all-weather SMA strategy. Maybe it is more of a late bull market, high volatility market strategy where one is concerned with sharp downdrafts and wants to exit as soon as possible while still trading the volatility. 
It may also be a strategy that works when the government is rolling out stimulus, creating
volatility. It did navigate the latest coronavirus bear market well by selling near the top and buying back in near the bottom.  
 
5. We also looked at AAII sentiment data, more specifically the Bull-Bear Spread column shown below. It is simply the difference between the bullish and bearish column. When the Bull-Bear spread was 2 standard deviations above its mean we took that as a sign of excessive optimism (sell signal) and when the spread was 2 standard deviations
below its mean that was considered excessive pessimism (buy signal.) (We later changed this to 1.8 standard deviations to generate more signals.) We were unable to come up with a good trading strategy using these signals because the sell signals were inconsistent. However, the buy signals (pessimism) worked better. One possible use of the buy signals could be to combine them with a sma strategy.  

![AAII_data.png](Images/AAII_data.png)


Here is the 10 month sma strategy combined with excessive pessimism for the 2000 bear market. You would buy and sell using the SMA crossovers and use pessimism as confirming evidence at the bottom. Green triangles are pessimism signals.  

![10_mo_sma_w_pessimism.png](Images/10_mo_sma_w_pessimism.png)

In the 2008 bear market, pessimism was above 1.8 standard deviations all the way down. However, there was one 3 standard deviation signal at the bottom which would have been confirming when the S&P crossed through the 10 month sma on the upside. 

![10_sma_2008_w_pessimism.png](Images/10_sma_2008_w_pessimism.png)

So in 2000, you would sell at top on the sma sell signal, wait for a cluster of pessimism and a sma buy signal, then enter.

In 2008, you would sell near top on sma sell signal, ignore clusters of pessimism until you get sma buy signal,  then enter, confirmed by clusters of pessimism and one 3 standard deviation pessimism signal. 

In 2020, we just had a cluster of pessimism followed by a sma buy signal so the market should continue up?

 ![10_mo_SMA_2020bear.png](Images/10_mo_SMA_2020bear.png)


































