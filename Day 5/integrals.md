# Integrals and Numerical Integration: Comprehensive Theory and Code

## Table of Contents
1. [Definite Integrals](#definite-integrals)
2. [Indefinite Integrals](#indefinite-integrals)
3. [Fundamental Theorem of Calculus](#fundamental-theorem-of-calculus)
4. [Integration Techniques](#integration-techniques)
5. [Integration by Parts](#integration-by-parts)
6. [Area Under a Curve](#area-under-a-curve)
7. [Volume Calculation](#volume-calculation)
8. [Numerical Integration](#numerical-integration)
9. [Applications in Data Science](#applications-in-data-science)

## Definite Integrals

### Theory
A definite integral represents the area under a curve between two specific points. It is defined as:

∫[a to b] f(x) dx

where f(x) is the function, a is the lower limit, and b is the upper limit.

The definite integral has several important applications:
1. Calculating distances traveled
2. Determining areas of irregular shapes
3. Finding volumes of solids
4. Computing work done by a force
5. Analyzing consumer and producer surplus in economics

### Example: Calculating Area
Let's calculate the area under the curve y = x² from x = 0 to x = 2.

∫[0 to 2] x² dx = [x³/3]₀² = (8/3) - 0 = 8/3

### Code Implementation
```python
import sympy as sp

def definite_integral(expr, var, lower, upper):
    return sp.integrate(expr, (var, lower, upper))

# Example usage
x = sp.Symbol('x')
expr = x**2
result = definite_integral(expr, x, 0, 2)
print(f"The area under y = x² from 0 to 2 is: {result}")
```

## Indefinite Integrals

### Theory
An indefinite integral, also known as an antiderivative, is a function F(x) whose derivative is the integrand f(x). It is represented as:

∫ f(x) dx = F(x) + C

where C is an arbitrary constant of integration.

Indefinite integrals play a crucial role in solving differential equations and finding general solutions to various mathematical problems.

### Example: Finding an Antiderivative
Find the indefinite integral of f(x) = 2x.

∫ 2x dx = x² + C

### Code Implementation
```python
import sympy as sp

def indefinite_integral(expr, var):
    return sp.integrate(expr, var)

# Example usage
x = sp.Symbol('x')
expr = 2*x
result = indefinite_integral(expr, x)
print(f"The indefinite integral of 2x is: {result}")
```

## Fundamental Theorem of Calculus

### Theory
The Fundamental Theorem of Calculus (FTC) establishes the relationship between differentiation and integration. It consists of two parts:

1. First Fundamental Theorem of Calculus:
   If f(x) is continuous on [a, b], then the function F(x) = ∫[a to x] f(t) dt is continuous on [a, b] and differentiable on (a, b), and F'(x) = f(x).

2. Second Fundamental Theorem of Calculus:
   If f(x) is continuous on [a, b] and F(x) is any antiderivative of f(x), then:
   ∫[a to b] f(x) dx = F(b) - F(a)

This theorem allows us to evaluate definite integrals using antiderivatives, forming the basis for many integration techniques.

### Example: Applying the FTC
Evaluate ∫[0 to π] sin(x) dx using the Fundamental Theorem of Calculus.

Solution:
1. Find an antiderivative of sin(x): F(x) = -cos(x)
2. Apply the FTC: ∫[0 to π] sin(x) dx = F(π) - F(0) = (-cos(π)) - (-cos(0)) = 1 - (-1) = 2

### Code Implementation
```python
import sympy as sp

def apply_ftc(expr, var, lower, upper):
    F = sp.integrate(expr, var)
    return F.subs(var, upper) - F.subs(var, lower)

# Example usage
x = sp.Symbol('x')
expr = sp.sin(x)
result = apply_ftc(expr, x, 0, sp.pi)
print(f"The integral of sin(x) from 0 to π is: {result}")
```

## Integration Techniques

### Theory
Various techniques are used to solve integrals, including:

1. Substitution (u-substitution)
2. Integration by parts
3. Partial fraction decomposition

Each technique is suited for different types of integrands.

### Example: Integration by Substitution
Evaluate ∫ cos(2x) dx

Solution:
1. Let u = 2x, so du = 2dx
2. Rewrite the integral: ∫ cos(u) * (1/2)du
3. Integrate: (1/2) * sin(u) + C
4. Substitute back: (1/2) * sin(2x) + C

### Code Implementation
```python
import sympy as sp

def integration_by_substitution(expr, old_var, new_var, substitution):
    new_expr = expr.subs(old_var, substitution)
    new_expr *= sp.diff(substitution, new_var)
    result = sp.integrate(new_expr, new_var)
    return result.subs(new_var, old_var)

# Example usage
x = sp.Symbol('x')
u = sp.Symbol('u')
expr = sp.cos(2*x)
substitution = x/2
result = integration_by_substitution(expr, x, u, substitution)
print(f"The integral of cos(2x) is: {result}")
```

## Integration by Parts

### Theory
Integration by parts is based on the product rule of differentiation. The formula is:

∫ u dv = uv - ∫ v du

This technique is particularly useful for integrals involving products of functions.

### Example: Integrating x * ln(x)
Evaluate ∫ x * ln(x) dx

Solution:
1. Choose u = ln(x) and dv = x dx
2. Then du = (1/x) dx and v = x²/2
3. Apply the formula:
   ∫ x * ln(x) dx = (x²/2) * ln(x) - ∫ (x²/2) * (1/x) dx
4. Simplify:
   = (x²/2) * ln(x) - ∫ (x/2) dx
   = (x²/2) * ln(x) - (x²/4) + C

### Code Implementation
```python
import sympy as sp

def integration_by_parts(u, dv, x):
    v = sp.integrate(dv, x)
    du = sp.diff(u, x)
    return u*v - sp.integrate(v*du, x)

# Example usage
x = sp.Symbol('x')
u = sp.ln(x)
dv = x
result = integration_by_parts(u, dv, x)
print(f"The integral of x * ln(x) is: {result}")
```

## Area Under a Curve

### Theory
The area under a curve y = f(x) from x = a to x = b is given by the definite integral:

Area = ∫[a to b] f(x) dx

This concept forms the basis for many applications in physics, engineering, and economics.

### Example: Area Under a Parabola
Find the area under the parabola y = x² from x = 0 to x = 2.

Solution:
Area = ∫[0 to 2] x² dx
     = [x³/3]₀²
     = (8/3) - 0
     = 8/3

### Code Implementation
```python
import sympy as sp

def area_under_curve(expr, var, lower, upper):
    return sp.integrate(expr, (var, lower, upper))

# Example usage
x = sp.Symbol('x')
expr = x**2
result = area_under_curve(expr, x, 0, 2)
print(f"The area under y = x² from 0 to 2 is: {result}")
```

## Volume Calculation

### Theory
Integrals can be used to calculate volumes of solids of revolution. The disk method is one technique for this purpose.

For a solid formed by rotating the area between y = f(x) and the x-axis from x = a to x = b around the x-axis:

V = π ∫[a to b] [f(x)]² dx

### Example: Volume of a Sphere
Calculate the volume of a sphere with radius r.

Solution:
1. The curve is y = √(r² - x²) from -r to r
2. V = π ∫[-r to r] (r² - x²) dx
3. Evaluate: V = 4πr³/3

### Code Implementation
```python
import sympy as sp

def volume_of_revolution(expr, var, lower, upper):
    return sp.pi * sp.integrate(expr**2, (var, lower, upper))

# Example usage
r = sp.Symbol('r')
x = sp.Symbol('x')
expr = sp.sqrt(r**2 - x**2)
result = volume_of_revolution(expr, x, -r, r)
print(f"The volume of a sphere with radius r is: {result}")
```

## Numerical Integration

### Theory
Numerical integration techniques are used when analytical solutions are difficult or impossible to obtain. Two common methods are:

1. Trapezoidal Rule:
   ∫[a to b] f(x) dx ≈ (b-a)/2n * [f(a) + 2f(x₁) + 2f(x₂) + ... + 2f(xₙ₋₁) + f(b)]

2. Simpson's Rule:
   ∫[a to b] f(x) dx ≈ (b-a)/3n * [f(a) + 4f(x₁) + 2f(x₂) + 4f(x₃) + ... + 2f(xₙ₋₂) + 4f(xₙ₋₁) + f(b)]

### Example: Approximating π
Let's approximate the value of π using the integral of 4/(1+x²) from 0 to 1.

### Code Implementation
```python
import numpy as np

def f(x):
    return 4 / (1 + x**2)

def trapezoidal_rule(f, a, b, n):
    x = np.linspace(a, b, n+1)
    y = f(x)
    return (b-a)/n * (y[0]/2 + np.sum(y[1:-1]) + y[-1]/2)

def simpsons_rule(f, a, b, n):
    if n % 2 != 0:
        raise ValueError("n must be even")
    x = np.linspace(a, b, n+1)
    y = f(x)
    return (b-a)/(3*n) * (y[0] + 4*np.sum(y[1:-1:2]) + 2*np.sum(y[2:-1:2]) + y[-1])

# Example usage
a, b = 0, 1
n = 1000

print(f"Trapezoidal Rule approximation of π: {trapezoidal_rule(f, a, b, n)}")
print(f"Simpson's Rule approximation of π: {simpsons_rule(f, a, b, n)}")
print(f"Actual value of π: {np.pi}")
```

## Applications in Data Science

### Kernel Density Estimation (KDE)

#### Theory
KDE is a non-parametric way to estimate the probability density function of a random variable. It's used for data smoothing and to make inferences about the population.

The kernel density estimator is defined as:

f̂ₕ(x) = (1/nh) Σᵢ K((x - xᵢ) / h)

where K is the kernel function and h is the bandwidth.

#### Example: KDE for Bimodal Data

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
from scipy import integrate
area, _ = integrate.quad(kde, data.min(), data.max())
print(f"Area under KDE curve: {area}")
```

### Time Series Analysis: Moving Average

#### Theory
A moving average is a calculation used to analyze data points by creating a series of averages of different subsets of the full data set. It's often used in time series analysis to smooth out short-term fluctuations and highlight longer-term trends or cycles.

The simple moving average is calculated as:

SMA = (A₁ + A₂ + ... + Aₙ) / n

where A is the average in each period, and n is the number of periods.

#### Example: Smoothing a Noisy Signal

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

This comprehensive guide covers the theory and implementation of integral calculus and its applications in data science. Each section provides detailed explanations, mathematical formulas, and corresponding Python code to illustrate the concepts.
