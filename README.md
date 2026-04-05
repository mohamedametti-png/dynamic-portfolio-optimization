# 📈 Dynamic Trading with Transaction Costs
Dynamic portfolio optimization with transaction costs: from Markowitz failure to execution-aware trading using alpha decay.

## Overview

This project implements a dynamic portfolio optimization strategy with transaction costs, following the framework of Garleanu & Pedersen (2013).

We show that while a classical Markowitz strategy performs poorly in the presence of transaction costs, a dynamic trading policy that accounts for signal persistence significantly improves performance.

---

## Key Results

| Strategy | Gross Sharpe | Net Sharpe | Turnover | Transaction Costs |
|----------|-------------|-----------|----------|------------------|
| Markowitz | ~0.30 | ~-0.32 | ~184k | ~77k |
| Dynamic | **~0.94** | **~0.76** | **~16k** | **~600** |

---

## Key Insight

> The issue is not the signal — it is the trading strategy.

The static Markowitz portfolio over-trades and destroys alpha through transaction costs.

A dynamic strategy that trades gradually toward an optimal target:
- reduces turnover
- lowers transaction costs
- improves net performance

---

## Methodology

### Signal Model

We estimate expected returns using a cross-sectional regression:

$$
\mathbb{E}_t[r_{t+1}] = B f_t
$$

where features include multi-horizon signals.

---

### Transaction Costs

We model quadratic transaction costs:

$$
TC_t = \frac{\lambda}{2} \Delta x_t^\top \Sigma \Delta x_t
$$

---

### Dynamic Trading Strategy

Instead of fully rebalancing:

$$
x_t = x_t^{\text{Markowitz}}
$$

we use:

$$
x_t = x_{t-1} + \kappa (aim_t - x_{t-1})
$$

where:
- $\kappa = a / \lambda$
- $aim_t$ accounts for signal persistence

---

## Results Visualization

Example: Gold position

- Markowitz: highly volatile
- Dynamic: smooth and stable

(see figures/)

---

## Repository Structure

- `notebook/` — main implementation
- `figures/` — plots
- `src/` — modular code (optional extension)

---

## Future Work

- Hyperparameter optimization ($\kappa$, $\lambda$)
- Rolling retraining
- Risk constraints
- Multi-asset extensions

---

## Author

Mohamed Ametti
