

# sma5_bot

`sma5_bot` is a Python script that continuously receives tick-by-tick BTC/USDT price data from Binance. It computes a simple moving average (SMA) over the last 5 ticks and makes trading decisions based on the relationship between the last price and the SMA. The bot tracks trades, calculates profits, and prints trade details and metrics to the console.

## Features

- **Real-time Data**: Receives tick-by-tick BTC/USDT price data from Binance.
- **SMA Calculation**: Computes a 5-tick simple moving average.
- **Automated Trading**: Makes buy/sell decisions based on the price and SMA.
- **Trade Tracking**: Keeps track of trades and calculates net profit and metrics.
- **Console Output**: Prints trade details and metrics to the console.

## Requirements

- Python 3.x
- `websocket-client`
- `pandas`

You can install the required libraries using:
```sh
pip install websocket-client pandas
```

## Script Overview

### Imports

- **websocket**: A library for handling WebSocket connections.
- **json**: For parsing JSON messages.
- **pandas**: A powerful data analysis library used for handling the data.

### WebSocket Endpoint and Subscription Message

- **endpoint**: The Binance WebSocket API endpoint.
- **our_msg**: A JSON-formatted message to subscribe to the BTC/USDT ticker stream.

### DataFrame Setup

- **df**: An empty DataFrame to store price data.
- **in_position**: A boolean flag to indicate if a position is currently held.
- **buy_orders, sell_orders**: Lists to track buy and sell prices.
- **np, no_trade, np_per**: Variables to track net profit, number of trades, and net profit percentage.

### WebSocket Event Handlers

- **on_open Function**: Sends the subscription message when the WebSocket connection is opened.
- **on_message Function**:
  - Parses the incoming message, extracts the price, and creates a DataFrame row with the price and timestamp.
  - Updates the DataFrame with the latest 5 prices.
  - Calculates the 5-period SMA.
  - Buys when the last price is above the SMA and the bot is not in a position.
  - Sells when the last price is below the SMA and the bot is in a position.
  - Updates trading metrics (profit, number of trades, etc.) and prints the results.

### WebSocket Application Initialization

- Initializes the WebSocketApp with the specified endpoint and event handlers.
- Runs the WebSocket connection indefinitely, processing messages as they arrive.

## Usage

To run the bot, simply execute the script:
```sh
python sma5_bot.py
```

## Example Output

The bot will continuously print trading metrics to the console, including trade details, net profit, and the number of trades executed.
```sh
-----------------------------
bought for 66194.24
sell for 66198.58
profit: 4.3399999999965075
-----------------------------
net profit: 178.7100000000355
net profit percent: 0.26990751806082175
no. of trades: 198
-----------------------------
```
