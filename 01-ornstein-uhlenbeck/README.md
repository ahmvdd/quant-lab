# 01 — Ornstein-Uhlenbeck pairs trading

> **Question:** does the price spread between two economically linked stocks revert to its mean — and how fast?

## Model

The spread follows an Ornstein-Uhlenbeck process:

$$dX_t = \theta(\mu - X_t)\,dt + \sigma\,dW_t$$

- **θ** — speed of mean reversion
- **μ** — long-run mean of the spread
- **σ** — volatility of the spread
- **Half-life** = ln(2) / θ — time for a deviation to shrink by half

In discrete time, the OU process is an AR(1): regressing ΔX on X_{t-1} by OLS gives θ directly.

## Steps

1. **Data** — 5 years of daily adjusted closes for KO and PEP (`yfinance`).
2. **Cointegration** — Engle-Granger test (`statsmodels.tsa.stattools.coint`). Stop here if the pair is not cointegrated.
3. **Hedge ratio** — OLS of log(KO) on log(PEP) → spread X_t.
4. **OU estimation** — OLS of ΔX_t on X_{t-1} → θ, μ, σ, half-life.
5. **Signals** — z-score of the spread, entry at |z| > 2, exit at z ≈ 0.
6. **Backtest** — simple PnL with transaction costs, in-sample vs. out-of-sample split.
7. **Write-up** — results and limitations below.

## Results

_To be completed._

| Metric | Value |
|--------|-------|
| Engle-Granger p-value | |
| Hedge ratio β | |
| θ (per day) | |
| Half-life (days) | |
| Out-of-sample Sharpe (after costs) | |

## Limitations

_To be completed — e.g. hedge ratio stability over time, regime changes, look-ahead bias._

## Reproduce

```bash
jupyter notebook ou_pairs.ipynb
```
