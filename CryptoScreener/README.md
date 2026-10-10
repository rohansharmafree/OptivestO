# Crypto 100 SMA Screener — local test and GitHub Pages

## Test locally on Windows
1. Extract this ZIP. The `index.html` file and `start_local.bat` must be in the same folder.
2. Double-click `start_local.bat`.
3. Keep the **Crypto Screener Server** command window open. Open `http://127.0.0.1:8000/`.
4. If the browser reports connection refused, read the server command window. The server did not start. The batch file will say if Python is missing.

Python is required for this local server. Install it from https://www.python.org/downloads/windows/ and select **Add python.exe to PATH** during installation.

## GitHub Pages deployment
Upload/replace these files directly in the **repository root** (not inside another folder): `index.html`, `.nojekyll`. Commit the change and wait for GitHub Pages to redeploy, then hard-refresh with Ctrl+Shift+R. Check that the deployed page shows the new single-filter layout and automatically attempts to load the Binance Spot USDT universe on page load.

## Binance connection
The screener uses Binance public market-data endpoints and requires no API key. Opening https://data-api.binance.vision/api/v3/ping and seeing `{}` confirms the endpoint is reachable as a webpage, but does not by itself prove JavaScript fetch/CORS requests work from the screener. If the page reports an API error, capture the exact message and browser DevTools Console (F12 → Console).
