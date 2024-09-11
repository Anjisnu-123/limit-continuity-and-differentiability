# Understanding Limits and Continuity: Foundations of Calculus and Applications in Data Science

## Overview
This document provides a comprehensive overview of limits and continuity, key concepts in calculus with applications in data science. It covers fundamental definitions, properties, and methods of evaluating limits, as well as the epsilon-delta definition and its importance.

## Table of Contents
1. [Introduction to Limits and Continuity](#introduction-to-limits-and-continuity)
2. [Concepts of Limits](#concepts-of-limits)
    - Definition, Notation
    - One-Sided Limits
    - Infinite Limits and Limits at Infinity
3. [Properties of Limits](#properties-of-limits)
4. [Evaluating Limits](#evaluating-limits)
5. [One-Sided Limits](#one-sided-limits)
6. [Continuity of Functions](#continuity-of-functions)
7. [Types of Discontinuity](#types-of-discontinuity)
8. [Epsilon-Delta Definitions of Limits](#epsilon-delta-definitions-of-limits)
9. [Applications in Data Science](#applications-in-data-science)
10. [Case Study: Logistic Regression](#case-study-logistic-regression)
11. [Notes](#notes)

## Introduction to Limits and Continuity
Limits and continuity form the foundation of calculus. They are crucial in understanding changes and approximations in various fields, including data science. 

## Concepts of Limits
Limits are used to describe the behavior of a function as it approaches a particular point. Key concepts include:

- **Definition and Notation**: The limit of a function `f(x)` as `x` approaches a value `c` is denoted as `lim(x -> c) f(x)`.
- **One-Sided Limits**: Limits can be approached from the left (`lim(x -> c-) f(x)`) or the right (`lim(x -> c+) f(x)`).
- **Infinite Limits**: When limits grow without bound as `x` approaches a certain value.
- **Limits at Infinity**: Describes the behavior of `f(x)` as `x` grows indefinitely large.

## Properties of Limits
Mathematical definitions of limits, including:

- **Left-Hand and Right-Hand Limits**
- **Infinite Limits**
- **Limit at Infinity**

Properties include:

- **Sum/Difference**: `lim(x -> c) [f(x) + g(x)] = lim(x -> c) f(x) + lim(x -> c) g(x)`
- **Product**: `lim(x -> c) [f(x) * g(x)] = lim(x -> c) f(x) * lim(x -> c) g(x)`
- **Quotient**: `lim(x -> c) [f(x) / g(x)] = lim(x -> c) f(x) / lim(x -> c) g(x)`, provided `lim(x -> c) g(x) ≠ 0`
- **Composition**: `lim(x -> c) f(g(x)) = f(lim(x -> c) g(x))` if `f` is continuous at `lim(x -> c) g(x)`.

## Evaluating Limits
Methods to evaluate limits include:

- **Direct Substitution**
- **Factoring**
- **Rationalization**
- **L'Hopital's Rule**: Used when the limit results in an indeterminate form.

## One-Sided Limits
Definition and notation:

- **Left-Hand Limit**: `lim(x -> c-) f(x)`
- **Right-Hand Limit**: `lim(x -> c+) f(x)`

Importance in calculus: One-sided limits are essential when dealing with piecewise functions or functions that are not defined over the entire domain.

## Continuity of Functions
A function is continuous if:

- **The limit exists at a point `c`.**
- **The functional value `f(c)` exists.**
- **The limit of the function as `x` approaches `c` is equal to `f(c)`.**

Visual representation and definition of continuity at a point:

- **Equality of limits and functional values.**
- **Visual representation of continuity.**

## Types of Discontinuity
There are several types of discontinuities:

- **Jump Discontinuity**
- **Removable Discontinuity**
- **Infinite Discontinuity**
- **Oscillatory Discontinuity**

Distinguishing between **removable** and **non-removable discontinuities** is crucial for understanding function behavior.

## Epsilon-Delta Definitions of Limits
The epsilon-delta definition provides a rigorous mathematical foundation for limits:

- **Epsilon Criterion (ε)**: For every `ε > 0`, there exists a `δ > 0`.
- **Delta Criterion (δ)**: Such that if `0 < |x - c| < δ`, then `|f(x) - L| < ε`.

### Why is the Epsilon-Delta Definition Required?
To provide a formal proof of limits that can be applied across various mathematical contexts, ensuring rigor in calculus.

### The Epsilon-Delta Definition of a Limit: Examples
Detailed examples to illustrate the application of epsilon-delta definitions in proving limits.

## Applications in Data Science
Understanding limits and continuity is vital for:

- **Gaussian Distribution**: Limits help describe how data behaves in large samples.
- **Normal Distribution**
- **Biometric Data Tables**

These concepts are particularly useful in **regression analysis** and **machine learning algorithms**.

## Case Study: Logistic Regression
An example of how limits and continuity principles are applied in logistic regression models in data science.

## Notes
<p style="color:red;">**Important:** Assumption of linear regression is crucial when considering the continuity of functions.</p>
<p style="color:red;">**Note:** The Tanh activation function cannot be used in hidden layers due to the vanishing gradient problem.</p>

## Conclusion
This document provides a foundation for understanding the concepts of limits and continuity in both mathematics and data science contexts. 

