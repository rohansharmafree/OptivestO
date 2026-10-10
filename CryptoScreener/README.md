# Crypto 100 SMA Screener — Fixed v4

## Windows 11 local test
1. Extract the ZIP into a folder.
2. Double-click `start_local.bat`.
3. Keep the server command window open.
4. Visit http://127.0.0.1:8000/ in Chrome.

Do not open `index.html` directly as a file. The batch file starts Python's built-in HTTP server.

## What's fixed
The prior diagnostic build attempted to access loader elements (`loaderLine`, `loaderTitle`, `loaderDetail`, `loaderPct`) that were missing from the page. This caused `Cannot read properties of null (reading 'style')` before the Binance symbol request could complete. This version adds those elements and keeps error details visible.

## GitHub Pages
Upload/replace `index.html` in the repository folder published by GitHub Pages. Commit the change, wait for the Pages deployment, then hard-refresh the site (Ctrl+Shift+R). Keep `.nojekyll` in the published root if already used.

This is a static browser-only app. Binance API access can still depend on network and browser CORS behavior. A successful scan has not been verified until the pair count loads and the scan completes in your browser.
