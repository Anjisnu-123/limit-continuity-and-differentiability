# Understanding Limits and Continuity: Foundations of Calculus and Applications in Data Science

## Overview
Limits and continuity are fundamental concepts in calculus that play a critical role in both pure mathematics and applied fields like data science. This document covers key topics such as definitions, properties, methods of evaluating limits, the epsilon-delta definition, types of discontinuity, and practical applications in data science.

## Table of Contents
1. [Introduction](#introduction)
2. [Concepts of Limits](#concepts-of-limits)
3. [Properties of Limits](#properties-of-limits)
4. [Evaluating Limits](#evaluating-limits)
5. [One-Sided Limits](#one-sided-limits)
6. [Continuity of Functions](#continuity-of-functions)
7. [Types of Discontinuity](#types-of-discontinuity)
8. [Epsilon-Delta Definitions of Limits](#epsilon-delta-definitions-of-limits)
9. [Applications in Data Science](#applications-in-data-science)
10. [Case Study: Logistic Regression](#case-study-logistic-regression)
11. [Notes](#notes)

## Introduction
Limits are a foundational concept in calculus, allowing us to understand the behavior of functions as they approach specific points or infinity. Continuity, built upon limits, describes a function's behavior at every point in its domain without abrupt changes. These concepts are extensively applied in data science, particularly in statistical models and machine learning.

## Concepts of Limits
Limits help in understanding how a function behaves as it approaches a particular point. They are expressed using the notation `lim(x -> c) f(x)`.

### Key Definitions:
- **Definition and Notation**: The notation `lim(x -> c) f(x) = L` means that as `x` gets arbitrarily close to `c`, `f(x)` gets arbitrarily close to `L`.
- **One-Sided Limits**: Limits can be approached from the left (`lim(x -> c-) f(x)`) or the right (`lim(x -> c+) f(x)`).
- **Infinite Limits**: If a function grows without bound as it approaches a certain point, we describe it using infinite limits.
- **Limits at Infinity**: This describes the behavior of a function as `x` approaches positive or negative infinity.

### Examples:
- For `f(x) = 1/x`, `lim(x -> 0+) 1/x = +∞` and `lim(x -> 0-) 1/x = -∞`.

## Properties of Limits
Understanding the properties of limits is crucial for solving calculus problems:

- **Left-Hand and Right-Hand Limits**: These limits must be equal for a limit to exist at a point.
- **Infinite Limits**: Notation and definition for when limits grow infinitely.
- **Limit at Infinity**: Describes how a function behaves as the input grows infinitely large.

### Properties Include:
- **Sum/Difference**: `lim(x -> c) [f(x) + g(x)] = lim(x -> c) f(x) + lim(x -> c) g(x)`
- **Product**: `lim(x -> c) [f(x) * g(x)] = lim(x -> c) f(x) * lim(x -> c) g(x)`
- **Quotient**: `lim(x -> c) [f(x) / g(x)] = lim(x -> c) f(x) / lim(x -> c) g(x)` (if `lim(x -> c) g(x) ≠ 0`)
- **Composition**: `lim(x -> c) f(g(x)) = f(lim(x -> c) g(x))` if `f` is continuous at `lim(x -> c) g(x)`.

## Evaluating Limits
Different methods to evaluate limits include:

- **Direct Substitution**: Directly substituting `x = c` into `f(x)` when `f` is continuous at `c`.
- **Factoring**: Simplifying the expression by factoring to eliminate indeterminate forms.
- **Rationalization**: Multiplying by a conjugate to simplify complex expressions.
- **L'Hopital's Rule**: Used when the limit results in indeterminate forms like `0/0` or `∞/∞`.

## One-Sided Limits
One-sided limits are crucial in defining continuity and differentiability:

- **Left-Hand Limit**: `lim(x -> c-) f(x)`
- **Right-Hand Limit**: `lim(x -> c+) f(x)`
- **Importance**: These are particularly important in piecewise functions and understanding behavior at boundary points.

## Continuity of Functions
A function is continuous at a point `c` if:

- **The limit exists at `c`**: `lim(x -> c) f(x)`
- **The functional value exists**: `f(c)`
- **The limit equals the functional value**: `lim(x -> c) f(x) = f(c)`

### Visual Representation:
Graphs provide an intuitive understanding of where functions are continuous or discontinuous.

## Types of Discontinuity
There are several types of discontinuities to consider:

1. **Jump Discontinuity**: Sudden jumps in function values.
2. **Removable Discontinuity**: A hole in the graph where the function can be redefined to make it continuous.
3. **Infinite Discontinuity**: Vertical asymptotes where function values go to infinity.
4. **Oscillatory Discontinuity**: The function oscillates infinitely as it approaches a point.

<p style="color:red;">**Removable vs Non-Removable Discontinuities:** Removable can be "fixed" by redefining the function, while non-removable cannot.</p>

## Epsilon-Delta Definitions of Limits
The epsilon-delta definition provides the most rigorous way to define limits:

- **Epsilon Criterion (ε)**: For any `ε > 0`, there exists a `δ > 0`.
- **Delta Criterion (δ)**: If `0 < |x - c| < δ`, then `|f(x) - L| < ε`.

### Why is the Epsilon-Delta Definition Required?
<p style="color:red;">**Foundation for Calculus:** Provides a rigorous proof of limits for ensuring mathematical precision and intuition.</p>

### The Epsilon-Delta Definition of a Limit: Examples
- **Example**: Proving that `lim(x -> 2) (3x + 1) = 7` using epsilon-delta criteria.

## Applications in Data Science
Understanding limits and continuity is essential in data science, especially in the context of statistical and machine learning models:

- **Gaussian Distribution**: Limits help describe the behavior of probabilities in large samples.
- **Normal Distribution**: Understanding tail behavior and convergence.
- **Large Sample Theory**: Limits play a key role in the law of large numbers and central limit theorem.
- **Biometrica Tables**: Based on continuous probability distributions.

<p style="color:red;">**Note:** Assumption of linear regression models relies on the continuity of predictors and response variables.</p>

## Case Study: Logistic Regression
Logistic regression involves limits and continuity to model binary outcomes. The S-shaped curve (sigmoid) is continuous and differentiable, making it suitable for gradient-based optimization methods.

## Notes
<p style="color:red;">**Important Note:** The Tanh activation function cannot be used in hidden layers due to the vanishing gradient problem.</p>

## Conclusion
This document covers fundamental concepts of limits and continuity, essential for both calculus and data science. A deep understanding of these concepts allows for better modeling, analysis, and prediction in various applied fields.


