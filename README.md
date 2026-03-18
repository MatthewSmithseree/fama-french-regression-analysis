# Fama-French-Carhart 4-Factor Regression Analysis

Regression analysis tool for evaluating fund performance using the **Carhart 4-Factor Model** (Fama-French 3 factors + Momentum).

## Factors

| Factor | Description |
|--------|-------------|
| **Mkt-RF** | Market excess return (market return minus risk-free rate) |
| **SMB** | Small Minus Big (size premium) |
| **HML** | High Minus Low (value premium) |
| **MOM** | Momentum (winners minus losers) |

## Features

- Regression of fund excess returns against the 4 Carhart factors
- Statistical significance testing (one-tailed and two-tailed p-values)
- Alpha decay analysis using exponential decay regression
- Cumulative alpha and fund alpha time-series plots
- Cumulative return comparison vs. benchmark (Russell 2000) with rolling volatility overlay
- Annualized Sharpe ratio for both fund and benchmark

## Setup

### Requirements

```
pandas
numpy
matplotlib
yfinance
statsmodels
scipy
pandas_datareader
requests
```

### Data Inputs

1. **Fund returns** — Excel file (`.xlsx`) with two columns: `Date` and `Return` (in decimals, not percentages).
2. **Fama-French factors** — Downloaded automatically from [Ken French's Data Library](https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html).
3. **Benchmark data** — Downloaded automatically from Yahoo Finance (default: `^RUT` Russell 2000).

### Configuration

Set the following parameters at the top of the notebook:

```python
monthly = True                  # True for monthly returns, False for daily
start_date = ""                 # Optional filter (yyyy-mm-dd)
end_date = ""                   # Optional filter (yyyy-mm-dd)
ticker = "^RUT"                 # Benchmark ticker (Yahoo Finance)
fund_data_path = "path/to/fund_returns.xlsx"
```

## Usage

Open `fama-french-cahart-regression-analysis.ipynb` and run all cells. The notebook will:

1. Load fund return data from the specified Excel file
2. Fetch Fama-French 3-factor and Momentum data
3. Run the 4-factor OLS regression and display a summary table
4. Test for alpha decay over time
5. Plot cumulative returns vs. benchmark with rolling volatility
