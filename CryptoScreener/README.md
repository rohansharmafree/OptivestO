# Crypto 100 SMA Consolidation Screener

A static, browser-only screener for Binance Spot USDT pairs. It uses HTML, CSS and JavaScript, with no backend, API key, wallet connection or trading permissions.

## Files
- `index.html` — complete application
- `.nojekyll` — asks GitHub Pages to serve files without Jekyll processing

## Deploy on GitHub Pages
1. Create a GitHub repository, for example `crypto-sma-screener`.
2. Upload `index.html`, `.nojekyll`, and this README to the repository root.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select branch `main` and folder `/(root)`, then Save.
6. Wait for the Pages deployment and open the URL shown in Settings → Pages.

## Data source and request strategy
- Spot universe: `GET https://data-api.binance.vision/api/v3/exchangeInfo`
- Daily candles: `GET https://data-api.binance.vision/api/v3/klines?symbol=...&interval=1d&limit=130`
- 24-hour quote volume: `GET https://data-api.binance.vision/api/v3/ticker/24hr`
- The public market-data domain does not require an API key.
- A full scan uses one kline request per eligible pair. With hundreds or 1,000+ pairs, requests are sent with a small concurrency pool (default 5) and a small delay. HTTP 429/418 responses trigger backoff/retry.
- The scan runs in the open browser tab. Do not close or suspend the tab until it finishes.
- The app uses completed daily candles only, so the current unfinished daily candle is excluded.
- Chart rendering uses TradingView Lightweight Charts from a CDN.

## Metrics
- Absolute percent change in SMA100 over 10 days.
- Absolute percent change in SMA100 over 20 days.
- Range of SMA100 over the last 10 completed days, divided by current SMA100.
- High-low price range over the last 20 completed days, divided by latest close.
- A transparent heuristic score ranks the flattest / most compressed setups; it is not a probability or trading signal.

Thresholds are configurable in the UI. Initial defaults are 1% (10-day SMA change), 2% (20-day SMA change), 1.5% (10-day SMA range), and 15% (20-day price range).

## Important limitations
- This is a browser-only tool. CORS/API reachability is controlled by Binance and the user's network; if the browser blocks cross-origin requests, the app cannot bypass that without a proxy/backend.
- Rate limits are shared by public IP and may change. If you receive persistent rate-limit errors, reduce parallel requests or wait before retrying.
- Some Binance Spot pairs can be very illiquid, newly listed, or leveraged tokens. The default excludes likely leveraged tokens, but symbols are heuristic and should be checked.
- The chart link opens TradingView for manual review; it is not an embedded TradingView chart.
- This tool only screens technical patterns. It does not provide investment advice or execute trades.
