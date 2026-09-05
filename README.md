## Brad Cao

Interested in quant research, market microstructure, statistical inference, and reproducible experiments. Always excited to meet other really ambitious people!

---

### [orderbook-sim](https://github.com/bradca0/orderbook-sim) — queue position vs. your backtest

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

### [polymarket-pnl](https://github.com/bradca0/polymarket-pnl) — is prediction-market skill real or variance?

Rebuilds per-wallet PnL from Polymarket on-chain activity and validates it against the
exchange: **92% of positions match exactly**, 43 of 51 wallets reconcile perfectly. Scores
trader skill net of variance — population raw edge **+0.126 collapses to −0.095** once
shrunk, so the apparent edge is mostly luck.

Then backtests it point-in-time. **The signal does not beat the price**: Brier 0.2088 vs the
market's 0.2046, ROI −3.3% after costs. That's the result, reported as-is.

Python · three public APIs, no auth · data and backtests, no execution

---

### [threshold](https://github.com/bradca0/threshold) — bigger models get worse, then better

Everyone learns that bigger models overfit. Past a certain size they stop. I swept model
size through the interpolation threshold on MNIST and measured where the turn happens.

**Test error peaks at exactly `p = n` — 88.8% there against 24.4% at five times the size —
because the feature matrix goes nearly singular and the fitted weights blow up 313×.**
A measured bias–variance decomposition puts **90.0% of the peak on variance**, and a ridge
penalty tuned per model size removes it entirely (0.888 → 0.123).

Ensembling was supposed to help and doesn't, at the threshold exactly. The members' output
scales differ by 10.5× there against 1.1× beside it, so averaging is dominated by the
worst-conditioned one. That's measured, not hand-waved.

NumPy float64 · one decomposition per model, reused for every ridge and diagnostic ·
85 tests · 94% coverage · CI

---

### [induction-heads](https://github.com/bradca0/induction-heads) — switching off the part of GPT-2 that learns from context

An induction head looks back for the last time it saw the current token and predicts what
came next. I scored all 144 heads in GPT-2 Small, found them, and turned them off.

**Loss on a repeated random sequence goes from 0.23 to 7.83 nats with the top 4 ablated —
while ablating 4 matched control heads in the same layers leaves it at 0.27.** That's 86
standard errors of separation.

On aggregate in-context learning over natural prose the same ablation is much weaker
(t = 1.19, not decisive), and the repo says so rather than leading with the number that
looked better.

PyTorch · TransformerLens · verified against the reference HuggingFace models · CI

---

### Notes

- `orderbook-sim`'s learned policy loses to a five-line heuristic. It's in the README.
- Two of its stylized facts fail. Also in the README.
- One modelling improvement was pre-registered, failed its acceptance test, reverted.
- `threshold` predicted double descent would show up in a trained MLP too. It didn't, at
  that scale. The prediction was written down first, so the null result stands.
- Every number in all four is regenerated from committed JSON by a make target, and CI
  fails if the prose and the results drift apart. None are typed by hand.

[bradca0.vercel.app](https://bradca0.vercel.app)
