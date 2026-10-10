# Crypto 100 SMA Screener (Progress + Custom Filters)

Static browser-only site for GitHub Pages.

## Deploy
Upload `index.html`, `.nojekyll`, and `README.md` to the repository root. Commit the new `index.html`, then hard-refresh the deployed page (Ctrl+Shift+R).

## Features
- Animated connection/scanning loader with pair count, percent complete, and error count.
- Fallback between Binance public market-data hosts (`data-api.binance.vision` and `api.binance.com`).
- Select 1–5 custom filters; each filter configures SMA or EMA, moving-average length, lookback days, and maximum percent change.
- Optional price-range filter, volume threshold, exclusion of likely leveraged tokens, sortable results, CSV export, and candle chart.
- Uses completed daily candles only.

If both Binance hosts fail, the loader shows a specific connection, timeout, HTTP, or CORS/network error. A static page cannot bypass CORS or regional network restrictions without a backend/proxy.
