# Comparison of Asset Pricing Factor Models

This project studies how well several factor models explain the monthly returns of US equity portfolios built by style and sector:

- CAPM
- Fama-French three-factor model (FF3)
- Carhart four-factor model (FF3 + momentum)
- Fama-French five-factor model (FF5)

The main objective is to assess whether adding factors such as size, value, momentum, profitability, or investment provides meaningful explanatory power beyond market risk alone.

## Notebook

The main notebook is available here:

[`Asset_Pricing_Factor_Models_Comparison.ipynb`](01_Asset_Pricing_Factor_Models_Comparison.ipynb)

It includes:

- retrieval of Fama-French and momentum factors;
- retrieval of monthly prices from Yahoo Finance;
- construction of six thematic sub-portfolios and one equal-weighted total portfolio;
- calculation of excess returns over the risk-free rate;
- a manual CAPM implementation using matrix algebra;
- OLS regressions with `statsmodels`;
- nested F-tests comparing the models;
- regression diagnostic visualizations;
- a rolling-window stability analysis using 24-month windows.

## Data and Study Period

Data is downloaded when the notebook is executed:

- Fama-French five factors and momentum via `pandas_datareader`;
- monthly closing prices via `yfinance`;
- configured study period: January 2016 to June 2026.

The data is not stored in this repository. Results may therefore change depending on the execution date, historical data revisions, and ticker availability.

## Portfolios

| Portfolio | Representative holdings |
|---|---|
| Growth | AAPL, MSFT, NVDA, META, GOOGL, AMZN |
| Value | JPM, WFC, XOM, CVX, F, VZ |
| Small_Mid | MHK, ALK, HAS, ZION, ETSY |
| Defensive | PG, KO, WMT, DUK, SO |
| Quality | JNJ, COST, ADP, MSCI |
| Cyclical | CAT, DE, FDX, MMM |
| Total_Portfolio | Equal-weighted average of all included stocks |

## Main Findings

The results reported in the notebook are **in-sample** results for the selected study period:

- moving from CAPM to FF3 generally produces the largest improvement in explanatory power;
- the momentum factor improves the models less consistently, with effects depending on the portfolio;
- profitability and investment factors add information mainly for defensive and quality-oriented portfolios;
- FF5 provides the best fit for the total portfolio in the reported analysis, with an $R^2$ of approximately 0.939.

These findings are not evidence of future performance and should not be interpreted as investment advice.

## Installation

Python 3.9 or later is recommended. Install the dependencies with:

```bash
pip install pandas numpy yfinance pandas-datareader plotly scikit-learn scipy statsmodels jupyter
```

## Running the Notebook

1. Clone or download the repository.
2. Install the dependencies.
3. Open the notebook in Jupyter Notebook, JupyterLab, or Visual Studio Code.
4. Run the cells in order.

An Internet connection is required to download the factor data and historical prices.

## Important: Charts on GitHub

The notebook generates charts with **Plotly** using interactive `fig.show()` outputs. The figures are not exported as image files or separate HTML files in this repository.

Therefore, **the interactive charts may not be visible or functional in GitHub's notebook preview**. GitHub generally displays the notebook's code, Markdown text, and some saved outputs, but it does not reliably support the JavaScript required by interactive Plotly visualizations.

To view the charts:

- clone or download the repository and run the notebook locally;
- open it with JupyterLab, Jupyter Notebook, or Visual Studio Code;
- optionally export the figures locally as HTML or image files if a shareable version is needed.

The charts also depend on live data retrieval. Simply viewing the notebook on GitHub does not re-run the cells or download the data automatically.

## Limitations

- Results are sensitive to the study period, stock selection, and downloaded data.
- The portfolios are educational constructions and do not necessarily represent investable indices.
- The analysis is mainly in-sample and does not provide out-of-sample validation.
- The econometric diagnostics could be extended, especially for autocorrelation, heteroskedasticity, residual normality, and parameter stability.
- Past returns do not guarantee future returns.

## References

- Sharpe, W. F. (1964), *Capital Asset Prices: A Theory of Market Equilibrium under Conditions of Risk*.
- Fama, E. F. & French, K. R. (1993), *Common Risk Factors in the Returns on Stocks and Bonds*.
- Carhart, M. M. (1997), *On Persistence in Mutual Fund Performance*.
- Fama, E. F. & French, K. R. (2015), *A Five-Factor Asset Pricing Model*.

## License and Intended Use

This project is provided for educational and personal research purposes. Check the terms of use of the data providers before any commercial reuse.
