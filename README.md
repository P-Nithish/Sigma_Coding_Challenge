# **Sigma Internship Coding Challenge**

## Getting Started
-  Installed QuantRocket using Docker.
-  Went through tutorials to understand basic platform capabilities.
-  Utilized Quantrocket to pull the price data (daily close prices only) for Apple stock (sid=‘AAPL’) for the year 2023 (01-01-2023 to 12-31-2023).

## Objective
The objective of this project is to build a simple model to make decisions on certain days using pre-specified logic and maximize V(N).

## Logic
- **Returns**: r(d) = (p(d) - p(d-1))/p(d-1)
- **State classification**:
  - if r(d) >= 0.1, s(d) = +1
  - else if r(d) > -0.1, s(d) = 0
  - else, s(d) = -1
- **Portfolio Value**:
  - if s(d+1) = 1 & s(d) = 0, then V(d+1) = V(d) + 1
  - else if s(d+1) = -1 & s(d) = 0, then V(d+1) = V(d) -1
  - else V(d+1) = V(d)

## Implementation
1. Calculate the daily returns based on the closing prices.
2. Classify the states (Bull, Flat, Bear) based on the defined thresholds.
3. Determine the optimal buy points according to the given logic.
4. Calculate the transition distribution based on the state transitions.
5. Implement the model to maximize the portfolio value (V(N)).

## DataFrame
The DataFrame "df" consists of the following:
- **close_price**: The closing price of the stock for each date.
- **Returns**: The daily returns of the stock.
- **State**: The classified state for each day (-1 for Bear, 0 for Flat, 1 for Bull).
- **State_name**: The corresponding state name (Bear, Flat, Bull).
- **Portfolio**: The portfolio value calculated based on the given rules.

## Output
- **Optimal Buy Indices**: [6, 8, 12, 16, 21, 28, 30, 41, 50, 52, 59, 61, 69, 79, 85, 88, 94, 100, 103, 108, 110, 113, 117, 120, 123, 133, 142, 160, 164, 177, 187, 191, 207, 209, 212, 216, 218, 232, 234, 238]
- **Maximum Portfolio Value V(N)**: 40
