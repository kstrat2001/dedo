# Dark Energy Divergence Oscillator (DEDO)

### What makes The Universe grow at an accelerating pace?

### Dark Energy

### What makes The Economy grow at an accelerating pace?

### Debt

### Debt is the Dark Energy of The Economy.
_________________________________________________________________________________

I pronounce DEDO "Deed-oh", but variations are fine with me.

## To use the script, copy the source code into a new pine script in TradingView, and hit "add to chart".

**Note: The Pine Script version of DEDO is improved from the original formula, which used a constant all-time high calculation in the normalization factor. This was technically not as accurate for calculating liquidity pressure in historical data because it meant that historical prices were being tested against future liquidity factors. Now using Pine, the functions can be normalized for the bar at the time of calculation, so the liquidity factors are normalized per candle, not across the entire series, which feels like an improvement to me.**

## Thought Process:

It's all about the liquidity. What I started with is a correlation between major stock indices such as SPX and WRESBAL , a balance sheet metric on FRED

After September 2008, when QE was initiated, many asset valuations started to follow more closely with liquidity factors. This led me to create a function that could combine asset prices and liquidity in WRESBAL , in order to calculate their divergence and chart the signal in TradingView.

The original formula:
First, we don't want "non-QE" data. we only want data for the market affected by QE .
So, find SPX on the day of pre-QE: 1255.08 and subtract that from the 2022 top 4818.62 = 3563.54

With this post-QE SPX range, now you can normalize the price level simply by dividing by the range = ( SPX -1255.08)/3563.54)
Normalization produces values from 0 to 1 so that they can be compared with other normalized figures.

In order to test the 0 to 1 normalized SPX range measure against the liquidity number, WRESBAL , it's the same idea: normalize it using the max as the denominator and you get a 0 to 1 liquidity index:
( WRESBAL /4276000000000)

Subtract one from the other to get the divergence:
(( WRESBAL /4276000000000)-(( SPX -1255.08)/3563.54))*10

x10 to reduce decimal places, but this option is configurable in DEDO's input settings tab.

Positive values indicate there's ample liquidity to hold up price or even create bullish momentum in some cases. Negative values mean price levels are potentially extended beyond what liquidity levels can support.

**Note: many viewers of the charts on social media wanted the values to go down in alignment with price moving down, so inverting the chart is what I do with Option + I. I like the fact that negative values represent a deficit in liquidity to hold up price but that's just me.**

## Features

Now with Pine Script and some help from other liquidity focused accounts on TradingView , I was able to derive a script that includes central bank liquidity and Reverse Repo liquidity drain, all in one algorithm, with adjustable settings.

Central bank assets included in this version:
-JPY (Japan)
-CNY (China)
-UK (British Pound)
-SNB (Swiss National Bank)
-ECB (European Central Bank )

Central Bank assets can be adjusted to an allocation % so that the formula is adjusted for the market cap of the asset.

A handy table in the lower right corner displays useful information about the asset market cap, and percentage it represents in the liquidity pool.

Reverse repo soak is also an optional addition in the Input settings using the RRPONTSYD value from FRED . This value is subtracted from global liquidity used to determine divergence since it is swept away from markets when residing in the Fed's reverse repo facility.

There is an option to draw a line at the Zero bound. This provides a convenience so that the line doesn't keep having to be redrawn on every chart. The normalized equation produces a value that should oscillate around zero, as price/valuation grows past liquidity support, falls under it, and repeats in cycles.
