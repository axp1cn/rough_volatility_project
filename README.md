# Rough Volatility: Hurst Parameter Estimation

Hurst exponent estimation methods for rough volatility models, using both simulated fractional Brownian motion paths and real financial volatility proxies.

## What’s inside
- Wavelet-based Hurst estimation using Haar wavelet decomposition on volatility paths
- Fractional Brownian motion (fBM) simulation to validate estimators on synthetic data with known H
- Structure function / scaling analysis (ζ(q)) to estimate roughness
- Empirical checks on real datasets (S&P 500 and Oxford-Man realized volatility) and comparisons across volatility proxies
- Report with results and methodology in `reports/Estimation_Parametre_Hurst.pdf`

## Contributors
Axel Pincon

## References
- Gatheral, Jim, Thibault Jaisson, and Mathieu Rosenbaum (2018), *Volatility is Rough*
- Jusselin, Paul, and Mathieu Rosenbaum (2020), *No-arbitrage implies power-law market impact and rough volatility*

MIT license, feel free to use and adapt with attribution.
