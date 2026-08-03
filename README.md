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

Reconstructs per-wallet PnL from Polymarket on-chain trades, scores trader skill net of
variance, backtests skill-weighted forecasts against market price. Clean lab for it:
fills are wallet-attributable and markets resolve 0/1, so the labels are exact.

Python · three public APIs, no auth · data and backtests, no execution

---

### Notes

- TrueFill's learned policy loses to a five-line heuristic. It's in the README.
- Two of its stylized facts fail. Also in the README.
- One modelling improvement was pre-registered, failed its acceptance test, reverted.
- `make reproduce` regenerates every number and figure. None are typed by hand.

[bradca0.vercel.app](https://bradca0.vercel.app)
