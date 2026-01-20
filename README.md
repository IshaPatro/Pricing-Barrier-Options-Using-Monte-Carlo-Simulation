# Monte Carlo Pricing of European Barrier Options

## Overview

This project prices **European barrier options** using **Monte Carlo simulation** under a **risk-neutral Geometric Brownian Motion (GBM)** framework. The primary focus is a **Down-and-Out Call**, with extensions to all major barrier structures (Up/Down, Knock-In/Knock-Out).

Barrier options are **path-dependent exotic derivatives** widely used in FX, equities, and commodities, offering lower premiums by conditioning payoffs on price behavior.

---

## Objective

- Price a European Down-and-Out Call using Monte Carlo simulation  
- Support Up/Down barriers and Knock-In / Knock-Out structures  
- Visualize path dependency and barrier interaction  
- Analyze convergence and Monte Carlo error  

---

## Barrier Option Types

### Knock-Out Options
- Option ceases to exist if the barrier is touched  
- Lower premium, higher path risk  

### Knock-In Options
- Option activates only after the barrier is touched  
- Used for breakout-based strategies  

### Directional Variants (Call Options)

| Type | Market View |
|------|-------------|
| Up-and-Out | Bullish but capped |
| Down-and-Out | Bullish, confident no crash |
| Up-and-In | Bullish breakout |
| Down-and-In | Buy-the-dip activation |

---

## Model Assumptions

### Underlying Dynamics

- Asset prices follow a continuous-time stochastic process  
- Risk-neutral drift ensures no-arbitrage pricing  
- Prices remain strictly positive  
- Volatility and interest rates are constant  

---

### Model Parameters

| Parameter | Value |
|----------|-------|
| Initial Price (S0) | 620 |
| Strike (K) | 630 |
| Maturity (T) | 0.5 years |
| Volatility | 25% |
| Risk-Free Rate | 3% |
| Barrier (B) | 0.85 × S0 (down) / 1.15 × S0 (up) |

---

## Monte Carlo Methodology

- Daily time discretization (252 trading days per year)  
- Full price path simulation under GBM  
- Barrier monitored at every time step  
- Payoff evaluated at maturity  
- Knock-in / knock-out logic applied  
- Option price computed as the discounted average payoff  

---

## Visualization & Convergence

- Simulated price paths with barrier overlays  
- Clear distinction between surviving and knocked paths  
- Convergence analysis across increasing path counts  
- Standard error decreases as the number of paths increases  

---

## Why Barrier Options?

### Advantages
- Lower premiums than vanilla options  
- Targeted conditional exposure  
- Efficient risk structuring  

### Limitations
- Monte Carlo sampling error  
- Discrete barrier monitoring bias  
- Constant volatility assumption  
- No jumps or stochastic volatility  

---

## Key Takeaway

Monte Carlo simulation provides a flexible and intuitive framework for pricing path-dependent derivatives like barrier options, while clearly highlighting numerical and modeling trade-offs.

---

## Possible Extensions

- Brownian bridge correction for barrier bias  
- Variance reduction techniques  
- Stochastic volatility models  
- Jump-diffusion dynamics  
- Closed-form validation against analytical results  
