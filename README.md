# Hack The Burgh - VI
During a sleep depriving but rewarding weekend at **Hack the Burgh**, we set out to build an **automated trading bot**.
This challenge was set up by Optiver, and the goal was to find a trading strategy that would allow the bot to "out-trade" the competition.

Both me and my team had little to no knowledge of the FinTech world, and it was interesting to gain some insight into how latency (or rather, lack thereof) allows one trader to gain an edge over the others!

I'm very proud of what my team accomplished: apart from learning how to program an automated trading strategy, we ended up winning the Optiver challenge! 🥳 📈

# Project - Trading Bot for the Optiver Challenge

The Challenge is to create a trading algorithm to make money by buy and selling stocks on two indeces : S&P500 (SP) and Eurostoxx (ESX).

Our project is composed of three parts:

1) The trading algorithm itself
2) An SMS alert functionality to communicate profits and losses
3) A Web page for data visualization

## **1 - Algorithm**
We use the Ichimoku Cloud Indicator, a fairly safe and simple strategy especially for Microtrading.
The indicator is based on four components:
1) Conversion Line -> midpoint of the last 9 average prices
2) Base Line -> midpoint of the last 26 average prices
3) Leading Span A -> midpoint of Conversion Line and Base Line
4) Leading Span B -> midpoint of the last 52 average prices

**Trading Strategy**:
The Leading Spans consitute the boundaries of the "cloud". When Leading Span A is moving above Leading Span B it indicates an uptrend is gaining momentum. Conversly, Leading Span B above means a downward trend is taking place. A thin cloud shows indecision and a potentially weakening trend, whereas a wide one means it is a good time to start trading.

If the trend is Up and the Conversion Line falls below the Base Line, then it is time to buy stocks. Similarly, when the crossover of Conversion Line and Base Line happens in the opposite direction, it is time to sell.
To contain risk, we are allowing the bot to buy only two stocks on each market (four in total) for every "trading period".
![image](https://user-images.githubusercontent.com/47427204/75623153-5ad41e80-5b9f-11ea-9f65-9c83af4024e7.png)

## **2 - SMS alert**
The SMS alert system will send a notification to the user when a trade is closed, communicating losses and profit.

Some screenshots of the SMS functionality:
<table>
  <tr><td><img src="sms_0.png" height="450"/></td><td><img src="sms_1.jpg" height="450"/></td></tr>
</table>

## **3 - front-end**
1) `cd front_end/`
2) `python -m SimpleHTTPServer`
3) go to `0.0.0.0:8000`

The following shows an impression of what our front-end looks like.
The graphs show the mid-market prices for the SP and ESX instruments, respectively.
We plan to broadcast the trades our bot makes over SocketIO, which we can also show in the graphs as a scatterplot.
NB: currently, the front-end only shows static data. When we get the SocketIO integration set up, we hope that we can update the chart in real time.
![image](impression.png)

## Authors
[Mihail Yonchev](https://github.com/slaifan)  
[Nout Kleef](https://github.com/nout-kleef)  
[Vincenzo Incutti](https://github.com/enzo-inc)
