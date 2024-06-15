# sma5_bot
This script continuously receives tick-by-tick BTC/USDT price data from Binance, computes a simple moving average over the last 5 ticks, and makes trading decisions based on the relationship between the last price and the SMA. It keeps track of the trades, calculates profits, and prints trade details and metrics to the console.

# Imports
websocket: A library for handling WebSocket connections.
json: For parsing JSON messages.
pandas: A powerful data analysis library used for handling the data.

# WebSocket Endpoint and Subscription Message
endpoint: The Binance WebSocket API endpoint.
our_msg: A JSON-formatted message to subscribe to the BTC/USDT ticker stream.

# DataFrame Setup
df: An empty DataFrame to store price data.
in_position: A boolean flag to indicate if a position is currently held.
buy_orders, sell_orders: Lists to track buy and sell prices.
np, no_trade, np_per: Variables to track net profit, number of trades, and net profit percentage.

# WebSocket Event Handlers
on_open Function
Sends the subscription message when the WebSocket connection is opened.

# on_message Function
Parses the incoming message, extracts the price, and creates a DataFrame row with the price and timestamp.
Updates the DataFrame with the latest 5 prices.
Calculates the 5-period SMA.
Buys when the last price is above the SMA and the bot is not in a position.
Sells when the last price is below the SMA and the bot is in a position.
Updates trading metrics (profit, number of trades, etc.) and prints the results.

# WebSocket Application Initialization
Initializes the WebSocketApp with the specified endpoint and event handlers.
Runs the WebSocket connection indefinitely, processing messages as they arrive.
