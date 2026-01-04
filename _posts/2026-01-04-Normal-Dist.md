---
title: "So why does the Normal Distribution have a Pi in it?"
date: 2024-01-05
categories: [Mathematics, Calculus]
tags: [Integration, Gaussian, Probability]
use_math: true
mathjax: true
---

### What is the Normal Distribution?

The Gaussian (Normal) Distribution is the most important equation in statistics:

$$f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}(\frac{x-\mu}{\sigma})^2}$$

It describes everything from height distribution to sensor noise. This is due to the **Central Limit Theorem**, which states that under certian conditions the sample distribution of the sample mean is approximately normal *no matter* what the original population distribution was. The conditions are:

1) Random Sampling
   
2) Independent Samples
   
3) Samples come from identical distributions
   
4) Large Sample Size

This is why the Gaussian distrubution is everywhere. You don't need to know the complex shape of the original data source; as long as you have enough samples, you can treat the averages as a Bell Curve. This unlocks the ability to use standard statistical tools on almost any dataset in the world.

### The Problem: Normalization

For any probability distribution to be valid, the total area under the curve must equal exactly **1** (representing 100% probability).

The core of the bell curve is the function $e^{-x^2}$. To find the correct scaling factor (the number we put in front), we first need to find the area under this raw curve:

$$I = \int_{-\infty}^{\infty} e^{-x^2} dx$$

This is famous for being "unsolvable" using standard elementary calculus. 

### The Solution: Squaring the Integral

If we can't solve for $I$, let's solve for $I^2$. This allows us to multiply two copies of the integral together. We'll use $y$ for the second variable, effectively creating a 2D grid.

$$I^2 = \left( \int_{-\infty}^{\infty} e^{-x^2} dx \right) \left( \int_{-\infty}^{\infty} e^{-y^2} dy \right)$$

Combining them into a double integral:

$$I^2 = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} e^{-(x^2 + y^2)} dx dy$$

Visually, we have moved from finding the area under a 2D line to finding the volume under a 3D surface.



### Casting to Polar Coordinates

This is where the geometry comes in. The term $x^2 + y^2$ describes a circle ($r^2$). This hints that we should switch from Cartesian coordinates ($x, y$) to Polar coordinates ($r, \theta$).



1. **Substitute variables:** $x^2 + y^2 = r^2$
2. **Substitute the area element:** $dx dy \rightarrow r dr d\theta$ (The Jacobian)
3. **New Limits:**
* Radius ($r$) goes from $0$ to $\infty$.
* Angle ($\theta$) goes from $0$ to $2\pi$ (a full circle).

$$I^2 = \int_{0}^{2\pi} \int_{0}^{\infty} e^{-r^2} r dr d\theta$$

### Solving the Integral

The extra $r$ term (from the Jacobian) makes this integral solvable using simple u-substitution ($u = r^2$).

First, integrate with respect to $r$:
$$\int_{0}^{\infty} e^{-r^2} r dr = \left[ -\frac{1}{2} e^{-r^2} \right]_0^{\infty} = 0 - (-\frac{1}{2}) = \frac{1}{2}$$

Now, integrate that constant with respect to $\theta$:
$$I^2 = \int_{0}^{2\pi} \frac{1}{2} d\theta = \frac{1}{2}(2\pi) = \pi$$

So, $I^2 = \pi$. Taking the square root gives us the  result:

$$\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}$$

### **Mean ($\mu$)** and **Standard Deviation ($\sigma$)** in the Formula

We just proved that the area under $e^{-x^2}$ is $\sqrt{\pi}$. But in the real world, data isn't always centered at zero, and it isn't always the same width. We need to introduce **Mean ($\mu$)** and **Standard Deviation ($\sigma$)**.

Note: The case of ($\mu = 0$, $\sigma = 1$) has a special term, the *Standard Normal Distribution*



#### 1. Stretching the Curve ($\sigma$)
If we want to make the curve wider (higher variance), we scale the input $x$. In statistics, the convention is to use the exponent $-\frac{1}{2}(\frac{x}{\sigma})^2$.

If we let $u = \frac{x}{\sigma\sqrt{2}}$, then by the rules of calculus (u-substitution), $dx = \sigma\sqrt{2} du$.

When we plug this into our integral, that extra factor pops out:

$$\int_{-\infty}^{\infty} e^{-\frac{1}{2}(\frac{x}{\sigma})^2} dx = \sigma\sqrt{2} \underbrace{\int_{-\infty}^{\infty} e^{-u^2} du}_{\sqrt{\pi}} = \sigma\sqrt{2\pi}$$

Suddenly, the area under the curve is no longer $\sqrt{\pi}$, but $\sigma\sqrt{2\pi}$.

To force the area back to **1** (normalization), we must divide the whole function by this new amount. This is where the standardizing constant comes from:

$$\text{Constant} = \frac{1}{\sigma\sqrt{2\pi}}$$

#### 2. Shifting the Center ($\mu$)
Finally, we want to center the bell curve on our data's average ($\mu$).
In calculus, shifting a function left or right ($x \rightarrow x - \mu$) does **not** change the area under the curve. Therefore, we can simply plug in $(x - \mu)$ without changing the constant.

$$f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}$$

### Integrating Numerically with Python

We can use Python's `scipy.integrate` library to solve the integral numerically and see if it actually matches $\sqrt{\pi}$. For practical purposes, numerical integration is needed for the Gaussian distribution as the analytical trick above only works from $-\infty$ to $\infty$. For 2 specific numbers, we can only use numerical methods. This is how Z tables are created, the area to the right of any X value on the standard normal curve.

```python
import numpy as np
from scipy import integrate

# 1. Define the raw Gaussian function (e^-x^2)
def gaussian_raw(x):
return np.exp(-x**2)

# 2. Integrate it from -infinity to +infinity
result, error = integrate.quad(gaussian_raw, -np.inf, np.inf)

print(f"Numerical Result: {result:.10f}")
print(f"Expected (sqrt(pi)): {np.sqrt(np.pi):.10f}")

# Output:
# Numerical Result: 1.7724538509
# Expected (sqrt(pi)): 1.7724538509
```
