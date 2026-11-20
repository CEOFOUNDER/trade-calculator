# Trade calculator

A standalone web form with no dependencies, accounts, market data requests or broker connection. Open `index.html` in a browser, or publish the repository root with GitHub Pages to use it from any computer. Inputs remain in the page only.

Enter the sell/bid and buy/ask quotes, a stop-loss distance percentage and reward-to-risk ratio (RRR, default 1). Midpoint is `(bid + ask) / 2`; spread percentage uses that midpoint. The percentages specify planned per-unit price gain/loss using the midpoint as a base, measured from each executable entry price.

Long enters at ask and exits at bid: SL = ask − midpoint × SL%, TP = ask + midpoint × SL% × RRR. Short enters at bid and exits at ask: SL = bid + midpoint × SL%, TP = bid − midpoint × SL% × RRR. Entry spread is included through quote sides and must not be added twice.

For bid 105.51 and ask 106.32, midpoint = 105.915 and spread = 0.81 (0.764764% of midpoint). At 1% SL and TP, unrounded levels are long SL 105.26085 / TP 107.37915 and short SL 106.56915 / TP 104.45085.

Supports positive-price instruments only. Decimal places control display precision, not exchange tick size. Confirm broker trigger conventions and tradability. Slippage, fees, funding, gaps and future spread changes are excluded. No orders are placed.

## Architecture

One responsive HTML file containing CSS and plain JavaScript. No installation or build is required. The calculation function rejects invalid and crossed quotes and non-positive exit levels. A warning highlights stops inside the current spread.

Choose LONG or SHORT explicitly; only the selected panel appears. TP distance is derived as stop-loss distance × RRR. Unsafe spread stops, invalid inputs and collapsed rounded levels clear the results. Run checks with: node test.cjs.

Live app: https://ceofounder.github.io/trade-calculator/