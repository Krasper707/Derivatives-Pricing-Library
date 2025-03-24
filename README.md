# Derivatives Pricing Library

## Overview
This repository implements various derivatives pricing models, including the **Black-Scholes Model** and **Monte Carlo Simulation** for European options. It also computes key **Greeks** to analyze option sensitivities.

## Features
- **Black-Scholes Model** for European Call and Put options
- **Calculation of Greeks** (Delta, Gamma, Vega, Theta, Rho)
- **Monte Carlo Simulation** for European options using Geometric Brownian Motion (GBM)
- **Vectorized implementation** for efficient computation

## Installation
Ensure you have Python installed, then install dependencies:
```bash
pip install numpy scipy
```

## Usage

### 1. Black-Scholes Pricing
```python
from black_scholes import black_scholes
import numpy as np

S = np.array([100, 105, 110])  # Current stock prices
K = 110  # Strike price
T = 1  # Time to expiration (1 year)
r = 0.05  # Risk-free rate (5%)
sigma = 0.2  # Volatility (20%)
q = 0.02  # Dividend yield (2%)

call_price, call_delta, call_gamma, call_vega, call_theta, call_rho = black_scholes(S, K, T, r, sigma, option_Type="Call", q=q)
put_price, put_delta, put_gamma, put_vega, put_theta, put_rho = black_scholes(S, K, T, r, sigma, option_Type="Put", q=q)

print("Call Option Price:", call_price)
print("Put Option Price:", put_price)
```

### 2. Monte Carlo Simulation for European Options
```python
from monte_carlo import monte_carlo_european

S0 = 100  # Initial stock price
num_simulations = 10000  # Number of simulations
num_steps = 252  # Daily time steps in a year

call_mc_price = monte_carlo_european(S0, K, T, r, sigma, option_type="Call", num_simulations=num_simulations, num_steps=num_steps)
put_mc_price = monte_carlo_european(S0, K, T, r, sigma, option_type="Put", num_simulations=num_simulations, num_steps=num_steps)

print("Monte Carlo Call Option Price:", call_mc_price)
print("Monte Carlo Put Option Price:", put_mc_price)
```

## Future Enhancements
- Implement **Antithetic Variates & Control Variates** for variance reduction
- Add **Heston & Merton Jump-Diffusion models** for more realistic pricing
- Extend Monte Carlo to compute **Greeks** using pathwise and likelihood ratio methods
- Implement **American option pricing** using Least-Squares Monte Carlo (LSM)

## License
This project is open-source under the MIT License.

