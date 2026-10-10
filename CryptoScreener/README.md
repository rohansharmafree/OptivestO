# Crypto 100 SMA Screener — Local Test + GitHub Pages

## 1) Test locally on Windows first

1. Extract the ZIP into a normal folder, for example `C:\crypto-screener`.
2. Open that folder in File Explorer.
3. Click the address bar, type `cmd`, and press Enter.
4. Run this command in Command Prompt:

   ```bat
   py -m http.server 8000
   ```

5. Keep the Command Prompt window open and visit **http://localhost:8000** in Chrome.
6. Wait for the Binance connection status. Do not double-click `index.html` to open it as a `file://` URL; use the local web server above.

## 2) Test Binance separately

Open https://data-api.binance.vision/api/v3/ping in the same browser. A successful response is `{}`.

- If it does not load, the PC/network cannot reach this Binance public market-data host.
- If it loads but the screener reports a network/CORS error, check browser extensions, firewall/antivirus HTTPS filtering, or try another network.

## 3) GitHub Pages

Upload `index.html` and `.nojekyll` to the repository root, commit, and wait for GitHub Pages to publish. Then hard-refresh with `Ctrl+Shift+R`.

## Notes

- No API key is needed; public Binance market data is used.
- The page tries multiple Binance public API endpoints, but browser-only JavaScript cannot bypass a network block or a server's CORS policy.
- The default is one filter: SMA 100, 30-minute timeframe, 10-bar lookback, max change 1%. Add additional filters only after the first connection/scan works.
- Legacy fixed SMA thresholds and duplicate default controls were removed. The custom filter builder is the only moving-average condition editor.
