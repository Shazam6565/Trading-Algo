# Executed three S&P 500 algorithmic trading strategies using Python, pandas, NumPy, and Matplotlib, covering Equal-weight index fund creation, Momentum, and Value investing to attempt improved portfolio performance through diverse financial theories.

# Equal-Weight S&P 500 Index Fund Script

## Introduction

This document outlines a Python script designed to facilitate the creation of an equal-weight S&P 500 index fund. The S&P 500 serves as a leading indicator for U.S. equities, representing the market's best performance. Unlike traditional funds that weight investments by market capitalization, this script aims to distribute investments evenly across all constituents of the S&P 500.

## Getting Started

### Library Imports

The script utilizes several open-source software libraries for numerical computing, data manipulation, HTTP requests, Excel file creation, and mathematical functions. These include:

- NumPy
- Pandas
- Requests
- XlsxWriter
- Math

### Importing Stock List

The S&P 500 constituents are dynamic and change over time. For this exercise, a static list of stocks is used, which should be downloaded and placed in a designated directory for access by the script.

### Acquiring API Token

Market data is fetched using the IEX Cloud API, requiring an API token for access. It's recommended to store this token securely in a `secrets.py` file within the same directory as the script.

## Script Functionality

### Making API Calls

The script structures API calls to IEX Cloud to retrieve necessary stock information, such as market capitalization and stock price.

### Parsing API Data

Data retrieved from API calls is parsed to extract relevant information, preparing it for further processing and analysis.

### Data Organization

A pandas DataFrame is employed to organize stock data, acting like a spreadsheet to store ticker symbols, stock prices, market capitalizations, and the calculated number of shares to buy for each stock.

### Batch API Calls

To enhance performance, the script utilizes batch API calls, reducing the total number of HTTP requests. This approach not only speeds up the data retrieval process but may also reduce costs associated with API usage.

### Calculating Shares to Buy

The script calculates the number of shares to buy for each stock based on the total value of the user's investment portfolio. This ensures an equal-weight distribution of the investment across all S&P 500 constituents.

### Output Formatting

The final step involves formatting and exporting the calculated data to an Excel file using the XlsxWriter library. This file provides a clear and accessible recommendation for trades, tailored to the size of the user's investment portfolio.

## Conclusion

This Python script offers a comprehensive solution for investors looking to create an equal-weight S&P 500 index fund. From fetching up-to-date stock information to calculating investment distribution and exporting actionable insights, the script simplifies the investment process, making it accessible to a wide range of users, including recruiters seeking to understand the project's functionality and potential impact.

# Quantitative Momentum Strategy

## Introduction

This document details a Python script for implementing a quantitative momentum investing strategy. Momentum investing involves investing in stocks that have shown an increase in price the most. The strategy focuses on selecting the 50 stocks with the highest price momentum from the S&P 500 and calculates recommended trades for an equal-weight portfolio of these stocks.

## Getting Started

### Library Imports

The script relies on several key Python libraries for data manipulation, HTTP requests, numerical computing, and Excel file writing. These libraries include Pandas, Numpy, Requests, XlsxWriter, Math, and Scipy for statistical functions.

### Importing Stock List and API Token

To fetch stock data, the script uses a list of S&P 500 stocks and an API token from IEX Cloud. Ensure you have the `sp_500_stocks.csv` file and a valid IEX Cloud API token stored securely.

## Script Functionality

### Fetching Momentum Data

The first step involves making API calls to IEX Cloud to retrieve one-year price returns for each stock. This data is crucial for identifying high-momentum stocks.

### Building the DataFrame

The script constructs a DataFrame to hold stock tickers, prices, one-year price returns, and a placeholder for the number of shares to buy. This DataFrame is populated by making batch API calls to improve efficiency, fetching data for up to 100 stocks per request.

### Identifying High-Momentum Stocks

To focus on high-momentum stocks, the script sorts the DataFrame by one-year price return in descending order and selects the top 50 stocks. This subset represents the high-momentum stocks for the investment strategy.

### Calculating Shares to Buy

The script calculates the number of shares to buy for each stock in the high-momentum portfolio based on the total value of the user's investment portfolio. This ensures an equal-weight investment across all selected stocks.

### Enhancing the Momentum Strategy

To refine the strategy, the script also considers the quality of momentum by looking at price returns over different time frames: one month, three months, six months, and one year. Stocks are scored based on their momentum percentile ranks across these time frames, and an overall High-Quality Momentum (HQM) Score is calculated.

### Selecting the Best Momentum Stocks

The top 50 stocks with the highest HQM Scores are selected for the investment portfolio. This approach aims to identify stocks with "slow and steady" momentum, indicative of high-quality momentum.

### Output Formatting and Excel Export

Finally, the script formats the output and exports the investment recommendations to an Excel file using the XlsxWriter library. The Excel file includes detailed information on each selected stock, such as price, momentum scores, and the calculated number of shares to buy.

## Conclusion

This Python script provides a comprehensive approach to implementing a quantitative momentum investing strategy. By selecting stocks with high momentum and considering the quality of momentum, the strategy aims to construct a balanced, equal-weight portfolio of high-momentum stocks from the S&P 500, providing clear and actionable investment recommendations through a well-organized Excel output.

# Quantitative Value Strategy

## Introduction

This documentation outlines the Python script for a quantitative value-investing strategy. This strategy focuses on selecting the 50 stocks with the best value metrics from the S&P 500, aiming for an equal-weight portfolio of these stocks.

## Library Imports

The script utilizes several Python libraries for numerical computing, data manipulation, HTTP requests, and Excel file creation. These libraries include NumPy, Pandas, Requests, XlsxWriter, Math, and SciPy's stats module.

## Importing Stock List & API Token

The script begins by importing a list of S&P 500 stocks and an API token for accessing financial data through the IEX Cloud API. This step is crucial for retrieving up-to-date stock information and valuation metrics.

## Making the First API Call

The initial API call fetches the price-to-earnings (P/E) ratio for a given stock symbol. This ratio is a fundamental component of the value strategy, as it helps identify undervalued stocks.

## Executing Batch API Calls & Building the DataFrame

To efficiently gather data for all S&P 500 stocks, the script executes batch API calls. This approach minimizes the number of requests sent and speeds up data retrieval. The information collected includes not just the P/E ratio but also price-to-book (P/B), price-to-sales (P/S), enterprise value to EBITDA (EV/EBITDA), and enterprise value to gross profit (EV/GP) ratios.

## Handling Missing Data

Not all stocks have complete data for the required metrics. The script handles missing data by either dropping those stocks from consideration or imputing missing values with averages. This step ensures the robustness of the strategy.

## Calculating the RV Score

The script calculates a composite "Robust Value" (RV) Score for each stock, based on its percentile ranking across all value metrics considered. The RV Score helps identify stocks that are most undervalued across multiple metrics, rather than focusing on a single valuation dimension.

## Selecting the 50 Best Value Stocks

Based on the RV Scores, the script selects the top 50 stocks that represent the best value within the S&P 500. This subset forms the basis for the investment strategy.

## Calculating Shares to Buy

Similar to the momentum strategy, the value strategy script calculates the number of shares to buy for each stock to maintain an equal-weight portfolio. This calculation is based on the total investment amount and the current stock prices.

## Exporting to Excel

The final step involves formatting the output and exporting the calculated investment recommendations to an Excel file. The file includes detailed information for each of the 50 selected value stocks, including valuation metrics and the number of shares to buy.

## Conclusion

This Python script provides a methodical approach to implementing a quantitative value investing strategy, focusing on identifying undervalued stocks within the S&P 500. By considering multiple valuation metrics and calculating an RV Score, the strategy aims to select stocks with the best potential for value appreciation, offering investors a clear guide to constructing a value-focused, equal-weight portfolio.
