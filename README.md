## Brad Cao

Quantitative research — market microstructure, statistical inference, and
reproducible experiments. I care most about the gap between a number that looks
good and a number that survives being attacked.

---

### [lobsim](https://github.com/bradca0/lobsim) — what queue position does to a market-making backtest

Most backtests fill your resting order the moment a trade prints at your price.
Real exchanges don't work that way: you sit in a queue and trade only after
everything ahead of you has traded or cancelled. I built an event-driven limit
order book with exact price-time priority to measure what that assumption is
worth.

**A market-making strategy worth +214 ticks per episode under the standard
assumption is worth +2.8 once the queue is modelled — a 98.7% collapse on
identical order flow.**

The market is synthetic but validated, not assumed: 9 of 11 published stylized
facts land inside their empirical target bands, measured with the trading agent
switched off. Evaluation uses paired bootstrap confidence intervals,
Holm–Bonferroni correction, and a deflated Sharpe ratio charged for every
configuration tried across development — not just the ones that survived.

`Python` · `NumPy` · `scikit-learn` · 263 tests · 95.7% coverage · `mypy --strict` · CI

---

### [pm-signal-research](https://github.com/bradca0/pm-signal-research) — is prediction-market skill real, or variance?

Reconstructs per-wallet PnL from Polymarket's on-chain trade data, scores trader
skill net of variance, and backtests skill-weighted resolution forecasts against
market price. Prediction markets are an unusually clean laboratory for this:
fills are wallet-attributable and markets resolve to 0 or 1, so both the skill
estimates and the forecasts have exact labels rather than proxies.

`Python` · three public APIs, no auth · data and backtests only, no execution

---

### How I work

**Measure the assumption, don't argue about it.** lobsim exists because "queue
position matters" is easy to assert and worth putting a number on.

**Report what failed.** lobsim's learned policy loses to a five-line heuristic,
two of its stylized facts fail, and one modelling improvement was pre-registered,
measured, failed its acceptance test, and reverted. All of it is in the README.
Work that only shows its wins isn't checkable.

**Make it reproducible or it didn't happen.** `make reproduce` regenerates every
number and figure in lobsim's README from scratch; none of them are typed by hand.

---

[bradca0.vercel.app](https://bradca0.vercel.app)
