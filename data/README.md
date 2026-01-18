# Data Directory

This directory contains datasets used for rough volatility analysis and Hurst parameter estimation.

## Data Files

The following datasets are used in this project:

- **`s&p.csv`**: S&P 500 historical price data (Date, High, Low, Close)
- **`oxfordman_realizedvolatilityindices.csv`**: Oxford-Man Institute realized volatility indices
- **`valeurs_sig_*.csv`**: Simulated volatility proxy values for different parameter settings
- **`valeurs_gros_bm.csv`**: Simulated Brownian motion paths
- **`valeurs_gros_fbm.csv`**: Simulated Fractional Brownian Motion paths (referenced in code)

## Data Sources

- **S&P 500**: Historical market data
- **Oxford-Man Realized Volatility**: Available from [Oxford-Man Institute](https://realized.oxford-man.ox.ac.uk/)

## Usage

To use the notebooks in this project:

1. Place your data files in this directory
2. Update the `data_path` variable in notebooks to point to `data/your_file.csv`
3. For simulated data generation, run `src/2006.py` which will generate FBM paths

## Note

Actual data files are excluded from version control via `.gitignore` to keep the repository lightweight. Users should obtain the datasets separately or generate them using the provided simulation code.
