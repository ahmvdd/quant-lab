# 02 — Hill estimator & tail risk

> **Question:** how much risk does a Gaussian Value-at-Risk hide on real equity returns?

## Method

1. Daily log-returns of an equity index (e.g. S&P 500, CAC 40) over 20+ years.
2. Sort losses, keep the k largest, estimate the tail index α with the Hill estimator:

$$\hat{\alpha}^{-1} = \frac{1}{k}\sum_{i=1}^{k} \ln\frac{L_{(i)}}{L_{(k+1)}}$$

3. Choose k with a Hill plot (stability region).
4. Compare VaR 99 % / 99.9 %: Gaussian vs. power-law tail.

## Results

_To be completed._

## Limitations

_To be completed — e.g. sensitivity to k, volatility clustering, i.i.d. assumption._
