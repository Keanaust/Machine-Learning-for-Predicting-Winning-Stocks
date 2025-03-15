# MMA 823 - Optimal Portfolio Allocation & Simulation

## Project Overview
This project focuses on **constructing an optimal portfolio** with ETFs that perform well in a **war-risk scenario**. The portfolio is optimized by minimizing volatility and later simulated using **Geometric Brownian Motion (GBM)** to evaluate future risk and return.

---
## Part 1: Optimal Portfolio Allocation

### Objective
- Construct a portfolio using **historical data from Dec-2018 to Dec-2021**.
- **Minimize portfolio volatility** while ensuring:
  - Each ETF has a minimum weight of **1%**.
  - No ETF has more than **40%** allocation.
- Use **five ETFs**:
  - **IAU**: iShares Gold Trust ETF
  - **VDE**: Vanguard Energy ETF
  - **XLB**: Materials Sector SPDR ETF
  - **DBC**: Invesco DB Commodity Index Tracking Fund
  - **CQQQ**: China Technology Index ETF

### Implementation
1. **Data Collection**: Retrieved **monthly close prices** of the selected ETFs using `yfinance`.
2. **Returns & Risk Metrics**:
   - Computed **average returns**, **variance**, and **covariance matrix**.
   - Applied **Ordinary Least Squares (OLS)** regression for **CAPM Beta Estimation**.
3. **Portfolio Optimization**:
   - Used **Scipy optimization** to find the optimal weights minimizing portfolio volatility.
   - Ensured weight constraints were met.
4. **Performance Evaluation**:
   - Compared portfolio performance **vs. S&P 500 (Jan-2022 onwards)**.
   - Calculated **cumulative return, annualized return, and annualized volatility**.

### Key Findings
| Ticker | Avg. Monthly Return | Variance | Beta  |
|--------|--------------------|---------|------|
| CQQQ   | 1.59%              | 0.00581  | 1.28 |
| DBC    | 1.53%              | 0.00529  | 0.87 |
| IAU    | 1.06%              | 0.00183  | 0.34 |
| VDE    | **11.13%**         | **0.0153** | 1.67 |
| XLB    | 1.99%              | 0.00834  | 1.12 |

- **VDE** had the **highest return** but also the **highest risk**.
- **IAU** had the **lowest volatility**, making it a stable hedge asset.
- **Optimal portfolio weights** were found and visualized in a pie chart.

---
## Part 2: Portfolio Simulation

### Objective
- Use **Geometric Brownian Motion (GBM)** to simulate the portfolio’s future performance.
- **Forecast period**: **Jan-2023 to Jan-2025**.
- **Simulations**: 1000 Monte Carlo paths with **weekly time steps**.

### Implementation
1. **Constructed the variance-covariance matrix**.
2. **Applied Cholesky decomposition** to model correlated asset movements.
3. **Generated 1000 simulated paths** to predict potential future outcomes.
4. **Analyzed simulation results**:
   - Created a **histogram of simulated end values**.
   - Compared **actual portfolio performance vs. simulated range**.
   - Identified whether actual returns were a **tail event** in the simulated distributions.

### Key Insights
- **Expected portfolio value** at the end of **2025** falls between **95 and 135**.
- **Extreme tail events** were observed where **portfolio values dropped below 85**.
- **Actual performance in 2023-2024** was compared to simulated projection

