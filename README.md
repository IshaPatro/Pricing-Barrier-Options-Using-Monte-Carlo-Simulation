# 📉 Monte Carlo Pricing of European Barrier Options

## Overview

This project prices **European barrier options** using **Monte Carlo simulation** under a **risk-neutral Geometric Brownian Motion (GBM)** framework. The primary focus is a **Down-and-Out Call**, with extensions to all major barrier structures (Up/Down, Knock-In/Knock-Out).

Barrier options are **path-dependent exotic derivatives** widely used in FX, equities, and commodities, offering lower premiums by conditioning payoffs on price behavior.

---

## Objective

- Price a **European Down-and-Out Call** via Monte Carlo  
- Generalize to all barrier variants  
- Visualize path dependency and barrier interaction  
- Analyze convergence and Monte Carlo error  

---

## Barrier Option Types

### Knock-Out Options
- Option ceases to exist if the barrier is touched  
- Lower cost, higher path risk  

### Knock-In Options
- Option activates only after the barrier is touched  
- Used for breakout-based strategies  

### Directional Variants (Call Options)

| Type | Market View |
|----|----|
| Up-and-Out | Bullish but capped |
| Down-and-Out | Bullish, confident no crash |
| Up-and-In | Bullish breakout |
| Down-and-In | Buy-the-dip activation |

---

## Model Assumptions

### Underlying Dynamics

The underlying asset follows GBM under the risk-neutral measure:

\[
dS_t = r S_t dt + \sigma S_t dW_t
\]

- Constant volatility and interest rate  
- Lognormal price dynamics  
- No arbitrage under risk-neutral pricing  

### Model Parameters

| Parameter | Value |
|----|----|
| Initial Price \(S_0\) | 620 |
| Strike \(K\) | 630 |
| Maturity \(T\) | 0.5 years |
| Volatility \(\sigma\) | 25% |
| Risk-Free Rate \(r\) | 3% |
| Barrier \(B\) | \(0.85S_0\) (down) / \(1.15S_0\) (up) |

---

## Monte Carlo Methodology

- Daily time discretization (252 trading days/year)  
- Full path simulation under GBM  
- Barrier monitored at every time step  
- Vanilla payoff computed at maturity  
- Knock-in / knock-out logic applied  
- Discounted expected payoff:

\[
\text{Price} = e^{-rT}\mathbb{E}[\text{Payoff}]
\]

---

## Visualization & Convergence

- Simulated price paths with barrier overlays  
- Clear distinction between surviving and knocked paths  
- Convergence analysis across increasing path counts  
- Standard error confirms \(O(1/\sqrt{N})\) Monte Carlo convergence  

---

## Why Barrier Options?

### Advantages
- Lower premiums than vanilla options  
- Targeted conditional exposure  
- Efficient risk structuring  

### Limitations
- Residual Monte Carlo error  
- Discrete barrier monitoring bias  
- Constant volatility assumption  
- No jumps or stochastic volatility  

---

## Key Takeaway

Monte Carlo simulation provides a **flexible and intuitive framework** for pricing path-dependent derivatives like barrier options, while clearly highlighting numerical and modeling trade-offs.

---

## Possible Extensions

- Brownian bridge barrier correction  
- Variance reduction techniques  
- Stochastic volatility (Heston)  
- Jump-diffusion models  
- Closed-form validation (Reiner–Rubinstein)  
