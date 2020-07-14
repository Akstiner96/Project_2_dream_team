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

4. We searched for the best short term sma trading strategy by constraining the backtesting library to only look at strategies using smas between 1 and 200.  The best it could find was a short 2, long 13 sma crossover. While this
strategy beat the S&P500 over the last three years it did terribly over 20 years. 

![2_13_SMA_20_years.png](Images/2_13_SMA_20_years.png)

So this is not an all-weather SMA strategy. Maybe it is more of a late bull market, high volatility market strategy where one is concerned with sharp downdrafts and wants to exit as soon as possible while still trading the 
volatility. It may also be a strategy that works when the government is rolling out stimulus, creating
volatility. It did navigate the latest coronavirus bear market well by selling near the top and buying back in near the bottom.  
 






We computed betas, standard deviations, correlations, sharpe ratios, daily return plots and frequency distributions for each sector. We calculated how much a $10,000 investment would have grown over time. Finally, we calculated a 95% confidence interval for the next 30 days. 

Daily returns

![daily_return.png](Images/daily_return.png)

Monte Carlo

![monte_carlo.png](Images/monte_carlo.png)

Freq distribution

![freq_dist.png](Images/freq_dist.png)


After the Monte Carlo analysis we used two python libraries to look deeper:

1. *PyPortfoliOpt*

With PyPortfoliOpt we calculated covariances and expected returns and ran the 11 sectors through an optimizer to find a max sharpe ratio portfolio. We then compared this portfolio to an equally weighted portfolio of the sector etfs. 

2. *Backtesting.py*

Next we used Backtesting.py with the goal of developing the best moving average crossover strategy for each sector. Two moving averages for each sector were analyzed - one short term and one long term. The trading strategy tested was: Buy - when the short term goes through the long term on an upswing.  Sell - when the short term goes through long term on a downswing. Backtesting.py found the best moving averages to use for each sector.

**RESULTS**

1. Sharpe ratio analysis showed Consumer Staples, Health Care and Technology sectors as the sectors with the highest ratios and  Financials and Energy with the lowest. 

![sharpe.png](Images/sharpe.png)

2. A correlation matrix showed Energy and Real Estate as sectors with the lowest correlations to other sectors. Technology and Material had higher correlations with other sectors. 
 
![correlations.png](Images/correlations.png)

3. Over the long-term there is variability in returns suggesting good sector selection can increase performance. 

Poor performance -Energy

![energy.png](Images/energy.png)

Good performance - Technology

![tech.png](Images/tech.png)

4. Monte Carlo analysis confidence intervals allowed us to define a trading range for a $10,000 investment over the next 30 days with a 95% probability. For example, a 10,000 investment in the Real Estate sector is expected to be 8245 to 12,542 in 30 days. Real Estate had the highest range. The sector with the lowest range was Consumer Staples (9210 to 11,112). 

All of the sectors fall in the range 8200 to 12,542 and in general more upside means more downside risk which makes it difficult to say that one sector looks best. The use of 30 day Monte Carlo results depends on the investor's perspective. If one is focused on preserving assets then Consumer Staples has the least downside from a Monte Carlo perspective. If one is focused on the upside then Real Estate would be the sector to choose (although downside risk would be higher). In this way Monte Carlo can help manage risk of a porfolio. 

Although beyond our scope, Monte Carlo could also be used to create sector models with Monte Carlo analysed inputs (for example, oil price for energy) to make the 30 day forecasts more accurate. 

5. Backtesting produced trading strategies for four sectors (Industrials, Technology, Financials, Energy) that beat a buy and hold portfolio return. We could not find a trading strategy to beat buy and hold for the other 7 sectors. 

Industrials

![industrials_backtest.png](Images/industrials_backtest.png)


Technology

![tech_backtest.png](Images/tech_backtest.png)


Financials

![financials_backtest.png](Images/financials_backtest.png)

Energy

![energy_backtest.png](Images/energy_backtest.png)

6. PyPortfolioOpt was used to calculate expected returns and covariance to optimize the 11 sectors and find a portfolio with the highest sharpe ratio. 

The max sharpe ratio portfolio was:

1. 26% Technology
2. 34% Consumer Staples
3. 22% Utilities
4. 18% Health Care

![optimized.png](Images/optimized.png)

This portfolio completely eliminated 7 sectors from the portfolio. (One caveat - PyPortfolioOpt has several methods to calculate expected returns and covariances. Different combinations of methods can produce different results. It also possible to constrain the optimization to have a min and max percent in each sector. We ran an unconstrained portfolio so the optimization was free to take sectors to a zero weighting.) 

Compared to an equally weighted portfolio the optimized portfolio outperformed. However, it is possible this outperformance comes from data mining/overfitting the data. 

![optimize_equal.png](Images/optimize_equal.png)


This portfolio has four sectors. Backtesting showed that only in Technology could we beat a buy and hold strategy with a crossover trading strategy (10 sma, 95 sma). One possible improvement on the optimized portfolio would be to buy and hold Consumer Staples, Utilities, and Health Care in the recommend weights while implementing a 10 day sma/95 day sma trading strategy in technology. 






















