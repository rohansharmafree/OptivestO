# Delta India Crypto SMA Screener

## Windows 11 local test
1. Extract the ZIP into a folder.
2. Double-click `start_local.bat`.
3. Keep the server command window open.
4. Visit http://127.0.0.1:8000/ in Chrome.

Do not open `index.html` directly as a file. The batch file starts Python's built-in HTTP server.

## Universe and filtering
- Loads live products from the public Delta Exchange India products API across all product categories.
- Extracts unique underlying asset symbols, then intersects them with active Binance Spot USDT pairs.
- Uses Binance candles and preserves the older SMA/EMA change method: absolute percentage difference between the current moving average and its value `lookback` bars earlier.
- Downloads only the candle history needed for the largest MA length + lookback on each selected timeframe, with a small buffer.
- Shares one candle request per coin/timeframe even when multiple filters use that timeframe.

## Notes
- Delta product availability can change. The universe is refreshed on startup and when Scan is clicked.
- A Delta-listed asset is only scanned when an active Binance Spot USDT pair with the same base-asset symbol exists. Assets without an exact ticker match are excluded rather than guessed.
- Both public APIs must permit browser cross-origin requests for this static site to work. If the Delta API is blocked by CORS on your network, a small proxy/backend would be required.

## GitHub Pages
Replace `index.html` in the published repository root, commit, wait for deployment, and hard-refresh with Ctrl+Shift+R. Keep `.nojekyll` in the published root.
