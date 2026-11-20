# Trade calculator

Live app: https://ceofounder.github.io/trade-calculator/

Six inputs: security label (optional), price decimals, sell/bid, buy/ask, base price move percentage, and reward-to-risk ratio before spread (default 1 = 1:1). The label does not fetch quotes. Click Long or Short to show only that direction.

Base price move (% of mid-price, before spread) is editable and defaults to 1%. M = (bid + ask) / 2; D = M * entered percentage / 100; S = ask - bid. Assumes unchanged spread during the move.

Long enters at ask and exits at bid: SL = bid - D; TP = bid + D * RRR. Short enters at bid and exits at ask: SL = ask + D; TP = ask - D * RRR.

For either direction, risk per unit = D + S; reward per unit = D * RRR - S. The after-spread ratio is reward / risk, before fees and slippage. Targets that cannot cover the spread are rejected. A 1:1 ratio before spread is less than 1:1 after spread.

Example: bid 105.51, ask 106.32, M 105.915, D 1.05915, S 0.81. At RRR 1: long SL 104.45085 / TP 106.56915; short SL 107.37915 / TP 105.26085. Risk 1.86915; reward 0.24915 per unit after spread.

One responsive HTML file with plain CSS and JavaScript. No dependencies or build. Run `node test.cjs`. Invalid inputs, non-positive levels, insufficient targets and ambiguous rounding clear results.

No broker connection, order submission, quote lookup or storage. Positive-price instruments only. Display decimals do not set exchange tick size. Confirm broker trigger rules. Fees, slippage, funding, gaps and future spread changes are excluded.