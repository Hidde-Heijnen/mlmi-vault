In probability and statistics, **moments** are quantitative measures that describe various characteristics of a probability distribution. Moments provide insights into the shape, central tendency, dispersion, and other aspects of a distribution.

There are infinitely many moments for a distribution, corresponding to each positive integer $n$. However, the first four moments are the most commonly used:

---
### 1. First Moment – Mean ($\mu$)

- **Definition:** The first moment about the origin is the **expected value** or **mean** of the random variable.
- **Formula:** 

$$
\mu = E[X] = \int_{-\infty}^{\infty} x \, p(x) \, dx
$$

- **Interpretation:** Represents the **central location** or average value of the distribution.

---

### 2. Second Moment – Variance ($\sigma^2$)

- **Definition:** The second **central moment** measures the variability or spread of the distribution around the mean.
- **Formula:**

$$
\sigma^2 = E[(X - \mu)^2] = \int_{-\infty}^{\infty} (x - \mu)^2 \, p(x) \, dx
$$

- **Interpretation:** Indicates how much the values of the random variable deviate from the mean on average.

---

### 3. Third Moment – Skewness

- **Definition:** The third standardised moment measures the **asymmetry** of the distribution around the mean.
- **Formula:**

$$
\text{Skewness} = \gamma_1 = \frac{E[(X - \mu)^3]}{\sigma^3}
$$

- **Interpretation:**
  - **Positive Skewness ($\gamma_1 > 0$)**: Distribution has a longer right tail; more values are concentrated on the left.
  - **Negative Skewness ($\gamma_1 < 0$)**: Distribution has a longer left tail; more values are concentrated on the right.
  - **Zero Skewness ($\gamma_1 = 0$)**: Distribution is symmetric around the mean.

---

### 4. Fourth Moment – Kurtosis

- **Definition:** The fourth standardized moment measures the **"tailedness"** or **peakedness** of the distribution.
- **Formula:**

$$
\text{Kurtosis} = \gamma_2 = \frac{E[(X - \mu)^4]}{\sigma^4}
$$

- **Interpretation:**
  - **High Kurtosis ($\gamma_2 > 3$)**: Distribution has heavier tails and a sharper peak than a normal distribution (leptokurtic).
  - **Low Kurtosis ($\gamma_2 < 3$)**: Distribution has lighter tails and a flatter peak (platykurtic).
  - **Normal Kurtosis ($\gamma_2 = 3$)**: Distribution has tails similar to a normal distribution (mesokurtic).

**excess kurtosis**: a statistical measure that describes the shape of a distribution’s tails relative to a normal distribution. 
- Since the kurtosis of the normal distribution is 3, and another distribution is 4. the excess kurtosis would be $4-3=1$

---
### Higher-Order Moments
While the first four moments are most commonly used, higher-order moments can provide additional details about the distribution's shape:

- **Fifth Moment –** Relates to the distribution's tendency to produce extreme values on one side.
- **Sixth Moment and Beyond –** Provide increasingly nuanced information about the distribution's tails and shape but are rarely used in practice due to complexity and diminishing interpretability.

---

### Types of Moments

- **Raw Moments (Moments about the Origin):** Calculated as $E[X^n]$, provide information about the distribution relative to zero.
- **Central Moments:** Calculated as $E[(X - \mu)^n]$, focus on deviations from the mean.
- **Standardised Moments:** Central moments normalised by $\sigma^n$, allow for comparison between different distributions.

---

**Summary:**

- **First Moment (Mean):** Measures central tendency.
- **Second Moment (Variance):** Measures dispersion or variability.
- **Third Moment (Skewness):** Measures asymmetry.
- **Fourth Moment (Kurtosis):** Measures peakedness and tail weight.
- **Higher Moments:** Provide additional shape characteristics but are less commonly used.

---

**Note:** Not all distributions have finite moments of all orders. For distributions with heavy tails (e.g., Cauchy distribution), some higher-order moments may not exist.