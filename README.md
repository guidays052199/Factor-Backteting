# Factor-Backteting

The Factor Backtesting project is based on a strategy about 3 factors aborded in the following book to construct a filter for the assets and then backtest it.

The factors are based on the book:
> Berkin, Andrew.Your Complete Guide to Factor-Based Investing. BAM ALLIANCE Pres, 2016.

The 3 factors aborded in the project are as follow: 
  
  `Quality`: Here we want to get the stocks with good quality factors, as ROIC, ROE and so.
  
  `Value`: Here we are trying to get the best stocks with a huge upside, with low price to book indicators. If you want, you can use another indicator por value.
  
  `Momentum`: 12 past month returns excluding the most recent month. Here we do not look at the most recent month to robust our idea of returns and do not put in observation stocks that were perfoming poorly (lateralization) and then in the last month got a huge chance of performance.

## Functions of the Back Test

The Strategy aims to provide 2 main functions, the backtest and the plot of results. To use the functions, at first you have to call the class using the following command:

  `Strategy(prices, ineg, p_vpa, ev_ebitda, initial_data = dt.datetime(2016,1,1), final_data = dt.datetime(2021,12,31), momentum_size = .2, quality_size = .5, position = 'short')`
