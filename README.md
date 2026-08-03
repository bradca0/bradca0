## Brad Cao

Interested in quant research, market microstructure, statistical inference, and reproducible experiments. Always excited to meet other really ambitious people!

---

### [TrueFill](https://github.com/bradca0/TrueFill) — queue position vs. your backtest

Most backtests fill your order the moment a trade prints at your price. Real exchanges
make you wait in a queue. I built an event-driven limit order book with exact
price-time priority to price that assumption.

**A strategy worth +214 ticks/episode under the standard assumption is worth +2.8 with
the queue modelled. 98.7% of the edge was the assumption, not the strategy.**

Market is synthetic but validated — 9/11 published stylized facts inside empirical
bands, measured with the agent switched off. Paired bootstrap CIs, Holm–Bonferroni,
deflated Sharpe charged for all 24 configs tried across development.

Python · NumPy · scikit-learn · 263 tests · 95.7% coverage · `mypy --strict` · CI

---

### [PolyEdge](https://github.com/bradca0/PolyEdge) — is prediction-market skill real or variance?

Rebuilds per-wallet PnL from Polymarket on-chain activity and validates it against the
exchange: **92% of positions match exactly**, 43 of 51 wallets reconcile perfectly. Scores
trader skill net of variance — population raw edge **+0.126 collapses to −0.095** once
shrunk, so the apparent edge is mostly luck.

Then backtests it point-in-time. **The signal does not beat the price**: Brier 0.2088 vs the
market's 0.2046, ROI −3.3% after costs. That's the result, reported as-is.

Python · three public APIs, no auth · data and backtests, no execution

---

### Notes

- TrueFill's learned policy loses to a five-line heuristic. It's in the README.
- Two of its stylized facts fail. Also in the README.
- One modelling improvement was pre-registered, failed its acceptance test, reverted.
- `make reproduce` regenerates every number and figure. None are typed by hand.

[bradca0.vercel.app](https://bradca0.vercel.app)
