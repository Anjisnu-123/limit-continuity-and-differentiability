# Integrals and Numerical Integration: Detailed Code Examples

This document provides comprehensive code examples for various integral calculations and numerical integration techniques, with a focus on Python implementation.

## Table of Contents
1. [Basic Integration](#basic-integration)
2. [Numerical Integration](#numerical-integration)
3. [Volume Calculation](#volume-calculation)
4. [Applications in Data Science](#applications-in-data-science)

## Basic Integration

First, let's implement some basic integration techniques using SymPy, a symbolic mathematics library for Python.

```python
import sympy as sp

# Define symbolic variables
x, y, z = sp.symbols('x y z')

# Basic indefinite integral
def indefinite_integral(expr):
    return sp.integrate(expr, x)

# Basic definite integral
def definite_integral(expr, lower, upper):
    return sp.integrate(expr, (x, lower, upper))

# Example usage
expr1 = x**2 + 2*x + 1
expr2 = sp.sin(x)

print("Indefinite integral of x^2 + 2x + 1:")
print(indefinite_integral(expr1))

print("\nDefinite integral of sin(x) from 0 to pi:")
print(definite_integral(expr2, 0, sp.pi))
```

## Numerical Integration

Now, let's implement numerical integration techniques: the trapezoidal rule and Simpson's rule.

```python
import numpy as np
from scipy import integrate

def f(x):
    return x**2  # Example function: f(x) = x^2

# Trapezoidal Rule
def trapezoidal_rule(f, a, b, n):
    x = np.linspace(a, b, n+1)
    y = f(x)
    return (b-a)/n * (y[0]/2 + np.sum(y[1:-1]) + y[-1]/2)

# Simpson's Rule
def simpsons_rule(f, a, b, n):
    if n % 2 != 0:
        raise ValueError("n must be even")
    x = np.linspace(a, b, n+1)
    y = f(x)
    return (b-a)/(3*n) * (y[0] + 4*np.sum(y[1:-1:2]) + 2*np.sum(y[2:-1:2]) + y[-1])

# Example usage
a, b = 0, 1  # Integration limits
n = 1000    # Number of subintervals

print(f"Trapezoidal Rule: {trapezoidal_rule(f, a, b, n)}")
print(f"Simpson's Rule: {simpsons_rule(f, a, b, n)}")

# Compare with SciPy's quad function
result, error = integrate.quad(f, a, b)
print(f"SciPy quad: {result}")

# Manual implementation of trapezoidal rule
def manual_trapz(x, y):
    return np.sum((x[1:] - x[:-1]) * (y[1:] + y[:-1])) / 2

x = np.linspace(a, b, n+1)
y = f(x)
print(f"Manual Trapezoidal: {manual_trapz(x, y)}")

# Using NumPy's trapz function
print(f"NumPy Trapz: {np.trapz(y, x)}")

# Manual implementation of Simpson's rule
def manual_simpson(x, y):
    h = (x[-1] - x[0]) / (len(x) - 1)
    return h/3 * (y[0] + y[-1] + 4*np.sum(y[1:-1:2]) + 2*np.sum(y[2:-2:2]))

print(f"Manual Simpson: {manual_simpson(x, y)}")
```

## Volume Calculation

Let's implement volume calculation for a solid of revolution using the disk method.

```python
import numpy as np
from scipy import integrate

def disk_method(f, a, b, n=1000):
    def integrand(x):
        return np.pi * f(x)**2
    
    return integrate.quad(integrand, a, b)[0]

# Example: Volume of a sphere
def hemisphere(x):
    return np.sqrt(1 - x**2)

radius = 1
volume = 2 * disk_method(hemisphere, 0, radius)  # Multiply by 2 for full sphere
print(f"Volume of sphere with radius {radius}: {volume}")
print(f"Exact volume: {4/3 * np.pi * radius**3}")
```

## Applications in Data Science

### Kernel Density Estimation

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

# Generate sample data
np.random.seed(0)
data = np.concatenate([np.random.normal(0, 1, 1000), 
                       np.random.normal(4, 1.5, 1000)])

# Compute KDE
kde = stats.gaussian_kde(data)

# Plot results
x = np.linspace(data.min(), data.max(), 100)
plt.figure(figsize=(10, 6))
plt.hist(data, bins=50, density=True, alpha=0.5)
plt.plot(x, kde(x), 'r-')
plt.title("Kernel Density Estimation")
plt.xlabel("Value")
plt.ylabel("Density")
plt.show()

# Calculate area under KDE curve (should be approximately 1)
area, _ = integrate.quad(kde, data.min(), data.max())
print(f"Area under KDE curve: {area}")
```

### Cumulative Distribution Function (CDF)

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

# Generate sample data
np.random.seed(0)
data = np.random.normal(0, 1, 1000)

# Compute KDE
kde = stats.gaussian_kde(data)

# Compute CDF
x = np.linspace(data.min(), data.max(), 1000)
cdf = np.array([kde.integrate_box_1d(-np.inf, x_i) for x_i in x])

# Plot results
plt.figure(figsize=(10, 6))
plt.plot(x, cdf)
plt.title("Cumulative Distribution Function")
plt.xlabel("Value")
plt.ylabel("Cumulative Probability")
plt.show()
```

### Time Series Analysis: Moving Average

```python
import numpy as np
import matplotlib.pyplot as plt

def moving_average(data, window):
    return np.convolve(data, np.ones(window), 'valid') / window

# Generate sample time series data
np.random.seed(0)
t = np.linspace(0, 10, 1000)
signal = np.sin(t) + 0.1 * np.random.randn(1000)

# Compute moving average
ma_10 = moving_average(signal, 10)
ma_50 = moving_average(signal, 50)

# Plot results
plt.figure(figsize=(12, 6))
plt.plot(t, signal, label='Original Signal')
plt.plot(t[9:], ma_10, label='10-point MA')
plt.plot(t[49:], ma_50, label='50-point MA')
plt.title("Time Series Moving Average")
plt.xlabel("Time")
plt.ylabel("Value")
plt.legend()
plt.show()
```

This code provides detailed implementations of various integral calculations and numerical integration techniques, including applications in data science. Each section includes explanations and visualizations where appropriate.
