# CIR Interest Rate Model

A from-scratch implementation of stochastic short-rate modelling on real yield curve data, built for Finance Club IIT Roorkee's Open Projects 2026.

The core challenge: given only the 3-month yield on any test day, reconstruct the entire yield curve.

## Models

*Base CIR* — single-factor mean-reverting diffusion, calibrated via MLE on the 3M yield time series. Closed-form bond pricing used to project all other maturities.

*Two-Factor CIR* (Longstaff-Schwartz, 1992) — decomposes the short rate into a fast factor (slope) and slow factor (level), allowing the model to independently control the short and long ends of the curve. Hidden states recovered during training via a 2×2 linear system; only the 3M yield consumed at test time.

## Performance

| Model | Pooled $R^2$ | Target |
|-------|-------------|--------|
| Base CIR | 0.800020 | — |
| Two-Factor CIR | 0.947365 | > 0.85 |

## Notebook layout


1. Data preprocessing
2. Base CIR — implementation, calibration, backtesting
3. Two-Factor CIR — extension and evaluation
4. Critical analysis and key questions


## Dependencies

numpy  pandas  scipy  scikit-learn  matplotlib
