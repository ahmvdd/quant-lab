# 03 — Hawkes processes on order flow

> **Question:** what fraction of trades is triggered by other trades rather than by external information?

## Model

Exponential-kernel Hawkes process:

$$\lambda(t) = \mu + \sum_{t_i < t} \alpha\, e^{-\beta (t - t_i)}$$

- **μ** — baseline (exogenous) intensity
- **α / β** — branching ratio: share of endogenous, self-excited events

## Method

1. Timestamped trades from real market data (Nasdaq ITCH, reused in project 04).
2. Maximum likelihood estimation using the O(N) recursive formulation of the log-likelihood.
3. Goodness of fit: time-rescaling theorem + QQ-plot of residual inter-arrival times.
4. Use the fitted process to generate synthetic order flow for the LOB engine.

## Results

_To be completed._
