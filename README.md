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

  ```
  Strategy(prices, ineg, value, quality, initial_data, final_data,momentum_size, quality_size, position , momentum_lookback)
  ```
 
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

   ```
   strategy.BackTester(rebal)
   ```
   
   `rebal`: this is the rebalancing period for the strategy, by default it is monthly. You can put 2 months, 3 months etc...
 
   With this command:
   
   ```
   strategy.BackTester("1M")
   ```
   
   You can get the following output:
   
|Strategy Profit |	Strategy | Cumulative Profit |	IBrX Returns |	IBrX Cumulative Returns |
| -------------  | ------------- | ------------- | ------------- | ------------------------ | 
|2016-02-01 |	0.006554 |	1.006554 |	0.017635 |	0.931825 |
|2016-02-02 |	-0.022484 |	0.983923 |	-0.034878 |	0.899325 | 
|2016-02-03 |	0.004744 |	0.988591 |	0.014814 |	0.912648 |
|2016-02-04 |	0.015136 |	1.003554 |	0.029424 |	0.939502 |
|2016-02-05 |	0.001758 |	1.005318 |	0.002612 |	0.941956 |
|...|	...|	...|	...|	...|
|2022-01-25 |	0.008416 |	6.787400 |	0.022650 |	2.805304 |
|2022-01-26 |	0.003166 |	6.808889 |	0.011423 |	2.837349 |
|2022-01-27 |	0.001390 |	6.818351 |	0.014389 |	2.878177 |
|2022-01-28 |	0.000890 |	6.824421 |	-0.004619 |	2.864881 |
|2022-01-31 |	0.003190 |	6.846194 |	0.016814 |	2.913051 |


  With you want to rebalance you portfolio at each 2 monthd, you put the following command:
  
  ```
  strategy.BackTester("2M")
  ```
  
  Getting the following output:
  
|Strategy Profit |	Strategy Cumulative Profit |	IBrX Returns |	IBrX Cumulative Returns |
| ------------- | ------------- | ------------- | ------------------------ | 
|2016-02-29 |  	0.024106 | 	1.024106 |	0.023227 | 	0.973170 | 
|2016-03-01 | 	0.016129 | 	1.040624 |	0.023797 | 	1.019084 | 
|2016-03-02 | 	0.010566 | 	1.051619 |	0.015548 | 	1.034929 | 
|2016-03-03 | 	0.033011 | 	1.086334 |	0.045296 | 	1.081807 | 
|2016-03-04 | 	0.008034 | 	1.095062 |	0.028804 | 	1.112968 | 
|...|	...|	...|	...|	...|
|2021-12-23 |	-0.004611 |	4.847014 |	-0.005231  |	2.757947 |
|2021-12-27 | 0.005126  |	4.871861 |	0.008300   |	2.780838 |
|2021-12-28 |	-0.001066 |	4.866669 |	0.000022   |	2.780898 |
|2021-12-29 |	-0.000995 |	4.861825 |	-0.011912. |	2.747772 |
|2021-12-30 |	0.010324  |	4.912020 |	0.016351   |	2.792702 |
   
## Plot Results

The others function defined aims to provide the results plotted in a graph comparing to the benchmark, that you can access by the following command:

  ```
  strategy.PlotStrategyResults()
  ```
     
Getting, for example, the following output:

![output](https://user-images.githubusercontent.com/94725904/175137998-215bdffc-9f13-4385-9491-408e490e1326.png)

## Returns



   
