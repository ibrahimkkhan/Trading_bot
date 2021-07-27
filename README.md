# Trading_bot
This project implements algorithms that are use my technical traders to analyze price action. The first algorithm detects Support and Resistance levels of a stock. Below I describe how a trader can use the service followed by a high level description of the code.

## Why Support and Resistance levels?
Support and Resistance levels are price ranges that usually witness a reversal in trends. This is why they are also called *key levels*. If the price rises and then inverts its trend moving down, the highest point it has reached is called **resistance**. If the price has gone down and then starts rising, the lowest price value is called **support**. We refer to the two as *level* but they are actually a *price range* or *price area* rather than an exact level. These areas show high level of activity as day and swing traders often trade around these trading areas. 

Key levels are very important because many interesting events may occur near these inversion levels. For example, the market can bounce again allowing mean-reversion strategies to win or it can break the key level, making things better for breakout traders.
There’s a rule of thumb that says that the more times a key level has been tested (i.e. the market has bounced near it many times), the higher the importance of the level.

## Why technique do I use?
For this project, I am using a technique called the **4-bar fractal technique**. A *fractal* is a candlestick pattern made by 5 candles. The third candle has the lowest low price, the previous candles have decreasing lows and the next candles have increasing lows. By this pattern, the low of the third candle is the support level. The same concept applies to resistance levels, where the third candle has the highest high of the five ones.

## Now let's talk code!
### Libraries
I use the following libraries:
* `pandas` - helps with data maniputlaiton and analysis
* `numpy` - helps deal with large multi-dimensional arrays and matrices 
* `matplotlib` - for plotting 
* `yfinance` - for stock data
* `mpl_finance` - for drawing candlestick patterns

### High Level Description
* I start by importing the libraries and initializing the plotting environment. 
* I create a `list` that will contain the support and resistance levels we find. Each level is represented as a `tuple`. The frist element of the tuple is the index of the *signal candle* and the second element is the *price value*.
* I define a function `plot_all()` that plots the prices and the levels together. 
*The resulting plot in `plot_all()` has all the levels I need but more work is needed! I am looking for price areas rather than levels so I would need to start filtering the **noise**. I can clean this noise modifying the function that detects key levels. If a level is near another one, it will be discarded. Two levels are near if their is less than the average candle size in our chart*.
* So, I define a parameter that uses every price value in the price history to see if it is near some previously discovered key level and filter accordingly.
* I use `plot_all()` to plot the final filtered graph and *Voila! I have the areas I needed!* The levels are clearer with no overlay and I can easily observe the ranges where a stock's price jumps.








