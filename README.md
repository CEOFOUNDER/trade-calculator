# Trade calculator

Live: https://ceofounder.github.io/trade-calculator/

Enter security label, price decimals, sell/bid, buy/ask, risk distance (% of mid-price), and reward/risk ratio. Select Long or Short. Security is a label, not a quote lookup.

Mid-price M = (bid + ask) / 2. Planned risk D = M * percentage / 100. Planned reward = D * RRR. Both are measured from executable entry to closing quote AFTER spread, before fees and slippage.

Long entry = ask, closing quotes = bid: SL = ask - D; TP = ask + D * RRR.
Short entry = bid, closing quotes = ask: SL = bid + D; TP = bid - D * RRR.

Do not add spread twice. A stop distance at or inside the current spread is rejected. At bid 105.51 / ask 106.32, 1% and RRR 1: long SL 105.26085 / TP 107.37915; short SL 106.56915 / TP 104.45085. Both risk and reward are 1.05915 per unit after spread.

Compact layout. Floating window uses Document Picture-in-Picture in supported desktop browsers. Keep the opener tab open; closing the floating window returns the calculator and inputs to the tab. Unsupported browsers display instructions.

One HTML file; no dependencies or broker connection. Run node test.cjs. Invalid inputs and ambiguous display rounding clear results. Display decimals do not set exchange tick size; displayed values are rounded. Fees, slippage, gaps and funding are excluded. No orders are submitted.
