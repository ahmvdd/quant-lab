# quant-lab

Quantitative finance & market microstructure projects — from statistical models to a low-latency limit order book engine replaying real Nasdaq data.

Each project is self-contained, reproducible, and documented like a short research note: **question → method → results → limitations**. Results are reported honestly, including when a model or strategy fails.

---

## Projects

| # | Project | Topic | Stack | Status |
|---|---------|-------|-------|--------|
| 01 | [Ornstein-Uhlenbeck pairs trading](01-ornstein-uhlenbeck/) | Cointegration, mean reversion, half-life | Python | 🟡 In progress |
| 02 | [Hill estimator & tail risk](02-hill-tail-risk/) | Heavy tails, Gaussian VaR vs. power-law VaR | Python | ⚪ Planned |
| 03 | [Hawkes processes on order flow](03-hawkes-order-flow/) | Self-exciting point processes, MLE | Python | ⚪ Planned |
| 04 | [Limit order book engine](04-lob-engine/) | ITCH 5.0 parsing, price-time matching, latency | C++20 | ⚪ Planned |

**Flagship:** project 04 — a C++ engine that rebuilds the full Nasdaq order book from raw ITCH 5.0 messages, simulates queue position and latency, and runs a market-making strategy on top. Project 03 is used to calibrate realistic order flow for it.

---

## Roadmap

- [ ] **01** — OU model on a cointegrated pair (KO / PEP): Engle-Granger test, θ via OLS, half-life, entry/exit bands
- [ ] **02** — Hill tail index on equity index returns, VaR 99 % comparison
- [ ] **03** — Exponential-kernel Hawkes fit by MLE (O(N) recursion), branching ratio α/β
- [ ] **04a** — ITCH 5.0 parser + full L3 book reconstruction, throughput & latency benchmarks
- [ ] **04b** — Matching / exchange simulator with queue position, latency and fees
- [ ] **04c** — Avellaneda-Stoikov market maker, PnL decomposition (spread / inventory / adverse selection)

---

## Repository structure

```
quant-lab/
├── 01-ornstein-uhlenbeck/   # Pairs trading with an OU spread model
├── 02-hill-tail-risk/       # Tail index estimation and VaR
├── 03-hawkes-order-flow/    # Self-exciting models of trade arrivals
├── 04-lob-engine/           # C++ limit order book engine (CMake)
├── common/                  # Shared Python utilities (data loading, plotting)
├── data/                    # Local datasets (git-ignored)
└── requirements.txt
```

## Getting started

```bash
git clone https://github.com/ahmvdd/quant-lab.git
cd quant-lab
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
```

Each project folder has its own README with the exact steps to reproduce its results.

## Principles

- **Real data** whenever possible, with the source and date range documented.
- **Reproducible**: pinned dependencies, fixed random seeds, one command per result.
- **Honest results**: limitations and failure cases are part of the write-up.
- **Measured**: performance claims come with benchmarks and hardware details.

---

## Author

**Sayeh** — Master's student (CTO & Tech Lead, HETIC, Paris), developer focused on quantitative finance and low-latency systems.

Open to full-time opportunities in fintech, trading and quant development.
