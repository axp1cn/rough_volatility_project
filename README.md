# Rough Volatility: Hurst Parameter Estimation

Estimation of the Hurst parameter for rough volatility models using wavelet-based methods and empirical analysis of financial time series.

## Context

This project implements and validates methods for estimating the Hurst exponent in rough volatility models, which are characterized by volatility paths with fractional Brownian motion (fBM) dynamics. The work demonstrates practical applications of rough volatility theory to real and simulated financial data.

## What It Demonstrates

- **Wavelet-based Hurst estimation**: Implementation of Haar wavelet decomposition for estimating the Hurst parameter from volatility paths
- **Fractional Brownian Motion simulation**: Generation of fBM paths with specified Hurst exponents for model validation
- **Multi-fractal analysis**: Application of structure function methods (ζ(q) analysis) to estimate roughness
- **Empirical validation**: Analysis of real financial data (S&P 500, Oxford-Man realized volatility) to test rough volatility hypotheses
- **Simulation studies**: Monte Carlo validation of estimation methods on synthetic data
- **Comparative analysis**: Evaluation of different volatility proxies (log returns, high-low spreads, realized volatility)

## Key Results

- Wavelet-based estimator implementation for Hurst parameter estimation
- Empirical evidence of rough volatility in financial markets (H < 0.5)
- Validation results on simulated data with known Hurst exponents
- Analysis reports available in `reports/Estimation_Parametre_Hurst.pdf`
- Notebook outputs showing structure function scaling and Hurst estimates

## Repository Layout

```
rough_volatility_project/
├── src/                    # Source code
│   └── 2006.py            # FBM simulation and Hurst estimation functions
├── notebooks/              # Jupyter notebooks for analysis
│   ├── simu_is_rough.ipynb      # Analysis of simulated volatility data
│   ├── logreturn_is_rough.ipynb # S&P 500 log return analysis
│   ├── oxford_is_rough.ipynb    # Oxford-Man realized volatility analysis
│   └── proxy_is_rough.ipynb     # High-low volatility proxy analysis
├── reports/                # Documentation and results
│   └── Estimation_Parametre_Hurst.pdf
├── data/                   # Data files (see data/README.md)
│   └── README.md          # Data description and sources
├── tests/                  # Unit tests (to be added)
├── requirements.txt        # Python dependencies
├── LICENSE                 # MIT License
└── README.md              # This file
```

## Quickstart

### Installation

```bash
# Clone the repository
git clone <repository-url>
cd rough_volatility_project

# Install dependencies
pip install -r requirements.txt
```

### Demo

Run a simple Hurst estimation on simulated data:

```bash
# Generate simulated fBM paths and estimate Hurst parameter
python src/2006.py
```

This will:
1. Generate Fractional Brownian Motion paths with H=0.8
2. Apply the wavelet-based estimator
3. Print estimated Hurst values

### Notebook Analysis

To explore the empirical analyses:

```bash
# Start Jupyter
jupyter notebook

# Open notebooks in notebooks/ directory:
# - simu_is_rough.ipynb: Simulated data analysis
# - logreturn_is_rough.ipynb: S&P 500 analysis
# - oxford_is_rough.ipynb: Realized volatility analysis
# - proxy_is_rough.ipynb: High-low proxy analysis
```

**Note**: Ensure data files are placed in the `data/` directory (see `data/README.md` for details).

## Method Overview

### Wavelet-Based Estimation

The core method uses Haar wavelets to decompose volatility paths and estimate the Hurst parameter:

1. **Volatility path construction**: From price data or simulations
2. **Wavelet decomposition**: Apply Haar wavelets at multiple scales
3. **Quadratic variation estimation**: Compute wavelet coefficients
4. **Hurst estimation**: Extract H from scaling behavior of wavelet coefficients

The estimator is based on the relationship:
```
H = -1/2 * log(Q(j+1)/Q(j)) / log(2)
```
where Q(j) is the quadratic variation at scale j.

### Structure Function Method

For empirical validation, the project uses structure functions:
- Compute m(q, Δ) = E[|log(σ_{t+Δ}) - log(σ_t)|^q]
- Estimate scaling exponent ζ(q) via regression
- Extract Hurst parameter from ζ(q) ≈ qH

## Notes / Limitations

- **Data availability**: Real datasets (S&P 500, Oxford-Man) are not included in the repository. Users must obtain them separately.
- **Computational complexity**: Wavelet-based methods can be computationally intensive for large datasets
- **Parameter sensitivity**: Estimation quality depends on appropriate choice of scale parameters (j, N)
- **Model assumptions**: Results assume rough volatility model structure; deviations may affect estimates
- **Sample size**: Estimation accuracy improves with longer time series

## References

- Gatheral, J., Jusselin, P., & Rosenbaum, M. (2018). The rough volatility paradigm. *Risk*, 31(3), 56-61.
- Fukasawa, M., Gatheral, J., & Rosenbaum, M. (2019). Volatility is rough. *Quantitative Finance*, 19(11), 1893-1903.
- Jusselin, P., & Rosenbaum, M. (2020). No-arbitrage implies power-law scaling in rough volatility models. *Mathematical Finance*, 30(3), 774-803.