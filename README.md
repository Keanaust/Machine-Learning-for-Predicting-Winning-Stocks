# Optimal Portfolio Allocation and Simulation

## Project Overview
This repository contains an analysis of optimal portfolio allocation and simulation for a war-resistant investment strategy. The project is divided into two main parts:
1. **Optimal Portfolio Allocation:** Constructing a portfolio optimized for a war scenario using ETFs.
2. **Portfolio Simulation:** Simulating portfolio performance using Geometric Brownian Motion (GBM).

---
## Part 1: Optimal Portfolio Allocation

### **Objective**
Construct a portfolio that minimizes volatility while adhering to the following constraints:
- Use the following ETFs:
  - **IAU**: iShares Gold Trust ETF
  - **VDE**: Vanguard Energy ETF
  - **XLB**: Materials Sector SPDR ETF
  - **DBC**: Invesco DB Commodity Index Tracking Fund
  - **CQQQ**: China Technology Index ETF
- **Constraints:**
  - Each ETF weight must be **≥ 1%**.
  - No ETF can exceed **40%** weight.
- **Optimization Goal:** Minimize portfolio volatility using historical variance-covariance data.
- **Historical Data Period:** Dec-2018 to Dec-2021.

### **Findings**
#### **1. Average Monthly Returns**
| Ticker | Average Monthly Return |
|--------|------------------------|
| CQQQ   | 0.015903               |
| DBC    | 0.015297               |
| IAU    | 0.010587               |
| VDE    | 0.111318               |
| XLB    | 0.019979               |

- **VDE (0.111318)** has the highest return.
- **IAU (0.010587)** has the lowest return.

#### **2. Variance (Risk)**
| Ticker | Variance |
|--------|---------|
| CQQQ   | 0.005813 |
| DBC    | 0.005295 |
| IAU    | 0.001826 |
| VDE    | 0.015297 |
| XLB    | 0.008336 |

- **VDE (0.015297)** is the most volatile.
- **IAU (0.001826)** is the least volatile.

#### **3. Beta Estimation (CAPM Model)**
- Beta values measure sensitivity to market movements.
- Using OLS regression, we estimated the beta for each ETF.

#### **4. Portfolio Optimization**
- Applied constraints to minimize portfolio volatility.
- **Generated optimal ETF weight allocation** (see pie chart in results).

#### **5. Performance Evaluation (Jan-2022 Onwards)**
- Compared portfolio returns against the S&P 500.
- **Key performance metrics:**
  - **Cumulative return**
  - **Annualized return**
  - **Annualized volatility**

---
## Part 2: Portfolio Simulation

### **Objective**
Simulate the optimized portfolio's performance using **Geometric Brownian Motion (GBM)** to assess potential future returns and risks.

### **Implementation Steps**
1. **Computed the variance-covariance matrix from Dec-2018 to Dec-2021.**
2. **Simulated portfolio performance using GBM with Cholesky Decomposition.**
3. **Simulation Parameters:**
   - **Simulation Period:** Jan-2023 to Jan-2025
   - **Frequency:** Weekly
   - **Paths:** 1000
   - **Initial Portfolio Value:** 100
4. **Generated a histogram of simulated end values.**
5. **Compared actual performance to simulated scenarios.**
   - Analyzed whether actual returns were a tail event within the simulated distribution. (see chart in script).

