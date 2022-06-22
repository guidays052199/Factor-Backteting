# Factor-Backteting

The Factor Backtesting project is based on a strategy about 3 factors aborded in the following book to construct a filter for the assets and then backtest it.

The factors are based on the book:
> Berkin, Andrew.Your Complete Guide to Factor-Based Investing. BAM ALLIANCE Pres, 2016.

The 3 factors aborded in the project are as follow: 
  
  `Quality`: Here we want to get the stocks with good quality factors, as ROIC, ROE and so.
  
  `Value`: Here we are trying to get the best stocks with a huge upside, with low price to book indicators. If you want, you can use another indicator por value.
  
  `Momentum`: 12 past month returns excluding the most recent month. Here we do not look at the most recent month to robust our idea of returns and do not put in observation stocks that were perfoming poorly (lateralization) and then in the last month got a huge chance of performance.

## Calling the class for backtest

The Strategy aims to provide 2 main functions, the backtest and the plot of results. To use the functions, at first you have to call the class using the following command:

  `Strategy(prices, ineg, value, quality, initial_data, final_data,momentum_size, quality_size, position = 'short', mdomentum_lookback)`
 
 This function need 4 essentials parameters to work with additional optional parameteres:

  `prices`: the historical data of daily prices for the stocks
 
  `ineg`: historical data of negotiability index for the stocks. It will be used to set the universe of observation to the backtest.
  
  `value`: the historical daily data of the value factor chosen. It can be price/book, ev/ebitda etc...
  
  `quality`: the historical daily data of the quality factor chosen. It can be ROIC, ROE etc...
 
  `initial_data`: it is the initial data of observation for the backtest. Its optional, by default is '2000-02-28'.
  
   `final_data`: it is the final data of observation for the backtest. Its optional, by default is '2021-12-31'. Both data need to be passed in dt.datetime format.
   
   `quality_size`: it is the of stocks that you want to select from the universe. Since the universe of observation is 100, if you want to capture 30 stocks with the quality + value factor, you can put '0.3'
   
   `momentum_size`: it is the of stocks that you want to select from the universe. Since the universe of observation for momentum is selected by the quality + value filter, if you want 10 stocks at each moment in the past, you can put '0.3' again. 
   
   `position`: the position you want to backtest the strategy, long-only strategy will just buy the best selected stocks. Short/long strategy will buy the best and sell the worst stocks according to the filter defined.
   
   `momentum_lookback`: how many months you want to look in the past to define the momentum. Remembering that can not look at the most recent month. 
   
## Back Tester

After you called the class, you will have access to 2 main fuction, the first is the backtest, you can acess it by the following command:

  `strategy.Backtester(rebal)`
   
   
   
