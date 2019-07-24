# Optimize Squeeze Trading Strategy with ANN
This is a project to optimize a squeeze trading strategy with a neural network made in keras

Squeeze strategy: This is a classical trading strategy that use a moving average of X periods (MA_X) and the standart deviatios of same period ( STD_X) so create a indicator that uses this formula:

# Superior Band = MA_X + (STD_X * 2)
# Inferior Band = MA_X - (STD_X * 2)

So is created a index to show the current volatility (Bp) that uses this formula:

# ((Superior Band - Inferior Band) / MA_X) * 100

If Bp in X periods is below Y value we can expect a volatility shock in t time ahead, so if Close price > Superior Band we can go in a long position, if close price < Inferior Band we can go in a short position.

But if we do a backtest in this strategy in  his classical way we become just market hostages, so to try get a better performance I use a Neural Network in PETR4.SA ( a bluechip in Brazilian Market of OIL sector), in VALE3.SA( a bluechip in Brazilian Market of Mining sector) and ITUB4.SA ( a bluechip in Brazilian Market of Banking industry)

The files of 1.0 version are the first try, I will seek new methods to improve this strategy 
# Objectives:

1: Test efficient market hypothesis
2: Check if is possible improve a classical trading strategy with machine learning
3: Create a open source template to backtest a trading strategy  with python to be used for any one with a basic level in python

# 1.0 Strategy:

# Inputs:
Last 30 periods returns, Bp, distance between close price and MA_20 and MA_200, MA_20 - MA_200, return of MA_20 and MA_200, OBV, candle body, candle range, returns' STD_20.
A Support Vector Regressor to forecast t+1...t+5 returns' STD_20 with Last 30 periods of returns' STD_20 ( A support vector autoregression method)

# Trading Signal:

The Neural Network output is  a sigmoid function with 1 = 100% of t+5 price > t price and 0 = 0%
If the current output is in <= First Quartile of train outputs is a signal of a Short position and if is > Third Quartile is a Long Position.

# Conclusion:

It's better trading in inverse signal of model,the efficient market hypothesis is rejected.

# 2.0 Strategy

Use same inputs of v1.0 

# Changes:

Use decile as signal to get a better performance and align with neural network output
Better comments in functions
See positives and negatives points per class
Print hit rate
Chart classical vs machine learning

# Conclusion

The performance is far better than v1.0 ;
Machine learning can improve hit rate;
The classical strategy have better returns even with larger drawdown.
