# Retirement Model

This Retirement Model helps you understand how far your money will take you into retirement based on historical data.

## Overview

The current state of the model demonstrates holding all assets in an S&P 500 index fund. The `$^SPX` is used as it has more extensive historical data than `$VOO` or other ETFs. You can choose any range of time throughout history and any capital gains tax bracket. This model allows you to apply these parameters to the amount of capital you invested and currently have, showing how much money you could spend per year and how it would affect your overall asset base.

## Features

- **Historical Data Analysis**: Utilize historical data from the S&P 500 index to project retirement funds.
- **Customizable Time Range**: Select any range of time throughout history for analysis.
- **Capital Gains Tax Bracket**: Choose any capital gains tax bracket to apply to your investments.
- **Investment Simulation**: Apply the model to your invested capital to see potential yearly spending and asset performance.
- **Visual Representation**: Charts at the bottom represent how your money would perform relative to the S&P 500, with red lines indicating when sales take place.

## Code Description

The `liquidate_portfolio` function simulates the liquidation of a portfolio over a specified number of years, taking into account capital gains tax and annual withdrawals. The function uses historical data from the S&P 500 index to model the portfolio's performance.

### Function: `liquidate_portfolio`

#### Parameters:
- `invested`: Initial amount of capital invested.
- `value`: Current value of the portfolio.
- `tax_rate`: Capital gains tax rate.
- `year`: The starting year for the simulation.
- `years`: The number of years over which the portfolio will be held after liquidation.
- `ticker`: The stock ticker symbol for the S&P 500 index (e.g., `^SPX`).

#### Process:
1. **Download Historical Data**: Fetches historical closing prices for the S&P 500 index from the specified start year to the current date.
2. **Calculate Initial Asset Value**: Adjusts the portfolio value for capital gains tax.
3. **Buy Shares**: Buys shares of the S&P 500 index at the beginning of the specified year.
4. **Annual Liquidation**: Each year, sells a portion of the shares to cover expenses (3% of the asset value) and adjusts the remaining shares.
5. **Store Results**: Records the dates and portfolio values after each annual liquidation.
6. **Final Asset Value**: Calculates the final asset value at the end of the specified period.

#### Output:
- `dates`: List of dates when the portfolio value was recorded.
- `values`: List of portfolio values corresponding to the recorded dates.

### Example Usage

```python
dates, values = liquidate_portfolio(invested=1000000, value=7000000, tax_rate=0.2, year=1994, years=30, ticker='^SPX')
