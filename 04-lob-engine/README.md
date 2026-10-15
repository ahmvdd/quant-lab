# 04 — Limit order book engine (C++)

> **Goal:** rebuild the full Nasdaq order book from raw ITCH 5.0 messages, simulate realistic execution, and evaluate a market-making strategy on a real trading day.

## Components

| Module | Description |
|--------|-------------|
| `itch/` | Zero-copy ITCH 5.0 binary parser |
| `book/` | L3 order book, price-time priority |
| `exchange/` | Execution simulator: queue position, latency, fees |
| `strategy/` | Avellaneda-Stoikov market maker |
| `bench/` | Throughput and latency benchmarks |
| `tests/` | Unit tests (GoogleTest) |

## Performance targets

| Metric | Target | Measured |
|--------|--------|----------|
| Messages / second (parse + book update) | > 10 M | |
| Book update latency p50 / p99 | < 100 ns / < 1 µs | |
| Full day replay | < 1 min | |

Measured values will be reported with CPU model, compiler and flags.

## Research questions

- How much of the quoted spread is lost to adverse selection?
- How sensitive is the strategy's PnL to latency and queue position?
- How does PnL decompose into spread capture, inventory and adverse selection?

## Build

```bash
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build -j
```

## Data

Nasdaq TotalView-ITCH 5.0 sample files (public). Files are not committed — see `data/README.md`.
