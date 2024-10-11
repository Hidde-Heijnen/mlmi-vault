## Bayesian decision theory
### Question
A data-scientist has computed a complex posterior distribution over a variable of interest, $x$, given observed data $y$, that is $p(x|y)$. They would like to return a point estimate of $x$ to their client. The client provides the data-scientist with a reward function $R(\hat{x},x)$ that indicates their satisfaction with a point estimate $\hat{x}$ when the true state of the variable is $x$.

  * Explain how to use _Bayesian Decision Theory_ to determine the optimal point estimate, $\hat{x}$.  
  * Compute the optimal point estimate $\hat{x}$ in the case when the reward function is the negative square error between the point estimate and the true value, $R(\hat{x},x) = -(\hat{x}-x)^2$. Comment on your result. 
  * Compute the optimal point estimate $\hat{x}$ in the case when the reward function is the negative absolute error between the point estimate and the true value, $R(\hat{x},x) = -|\hat{x}-x|$. Comment on your result.
### Answer
#### 1. Determine the Optimal Point Estimate $\hat{x}$
> [!info]
> Here we use $\int$ as a definite integral with the $-\infty$ lower and $\infty$ bounds

Bayesian Decision Theory helps determine the optimal point estimate $\hat{x}$ for a variable $x$ given observed data $y$ and a reward function $R(\hat{x}, x)$. We have a reward function that compares the real value $x$ with the value we want to find $\hat{x}$. But we don't know the real value of $x$, so we find an estimate based on our evidence $y$, and sum over all these possible $x$ The goal is to maximise the expected reward, calculated as:
$$\text{Expected Reward}(\hat{x}) = \int R(\hat{x}, x) \, p(x|y) \, dx.$$
The optimal point estimate $\hat{x}^*$ maximises the expected reward:

$$\hat{x}^* = \arg\max_{\hat{x}} \int R(\hat{x}, x) \, p(x|y) \, dx.$$
Alternatively, with a loss function $L(\hat{x}, x) = -R(\hat{x}, x)$, the goal becomes minimising the expected loss:
$$\hat{x}^* = \arg\min_{\hat{x}} \int L(\hat{x}, x) \, p(x|y) \, dx.$$
#### 2. Optimal Point Estimate for $R(\hat{x}, x) = -(\hat{x} - x)^2$
The reward function is the negative squared error, leading to the following expected reward:$$\text{Expected Reward}(\hat{x}) = -\int (\hat{x} - x)^2 \, p(x|y) \, dx.$$Find optimum (take out the $-1$ of the integral):
$$
-\frac{d}{d\hat{x}} \int (x - \hat{x})^2 p(x|y) dx = 0
$$
We can move the differentiation inside of the integral, since the bounds of the integral don't depend on the thing we're differentiating over ($\hat{x}$)
$$
- \int \frac{d}{d\hat{x}} (x - \hat{x})^2 p(x|y) dx = 0
$$
$$
- \int -2 (x - \hat{x}) p(x|y) dx = 0
$$
$$
2 \int (x - \hat{x}_*) p(x|y) dx = 0
$$
**Divide both sides by 2**:$$\int (x - \hat{x}_*) p(x|y) \, dx = 0.$$
**Expand the integral**:$$\int x p(x|y) \, dx - \int \hat{x}_* p(x|y) \, dx = 0.$$
**Take $\hat{x}_*$ outside the integral** (since it's a constant with respect to $x$):$$\int x p(x|y) \, dx - \hat{x}_* \int p(x|y) \, dx = 0.$$
**Recognise that the integral of the probability density function over its entire domain is 1**:
$$\int p(x|y) \, dx = 1.$$
**Simplify the equation**:   $$\int x p(x|y) \, dx - \hat{x}_* = 0.$$**Solve for $\hat{x}_*$**:$$\hat{x}_* = \int x p(x|y) \, dx.$$
Thus, the posterior mean minimises the expected squared error.

**Result**: The optimal estimate is the **posterior mean**:
$$\hat{x}^* = \mathbb{E}[x|y].$$
> [!question]- Why is this the posterior mean?
>  - Posterior Distribution  $p(x|y)$: This is a probability density function that describes the probability of $x$ given the observed data $y$. It is a function of $x$.
>  - Integrating $x \, p(x|y)$: When you multiply $x$ by its probability density $p(x|y)$ and integrate over all possible $x$, you are calculating the expected value (or mean) of $x$ under the posterior distribution.
#### Optimal Point Estimate for $R(\hat{x}, x) = -|\hat{x} - x|$
The reward function is the negative absolute error, so the expected reward is:
$$
\text{Expected Reward}(\hat{x}) = -\int |\hat{x} - x| \, p(x|y) \, dx.
$$
We aim to **maximise** the expected reward with respect to $\hat{x}$.

Find $\hat{x}^*$ such that:
$$
- \frac{d}{d\hat{x}} \int |\hat{x} - x| \, p(x|y) \, dx = 0.
$$
We can interchange the differentiation and integration:
$$
- \int \frac{d}{d\hat{x}} |\hat{x} - x| \, p(x|y) \, dx = 0.
$$

$$
- \int \frac{d}{d\hat{x}} |\hat{x} - x| \, p(x|y) \, dx = 0.
$$
---
#### Step 4: Substitute Back into the Integral

Now substitute this back into the integral:

$$
- \int \text{sign}(\hat{x} - x) \, p(x|y) \, dx = 0.
$$

---

#### Step 5: Split the Integral

The sign function divides the integral:

$$
- \left( \int_{-\infty}^{\hat{x}} p(x|y) \, dx - \int_{\hat{x}}^{\infty} p(x|y) \, dx \right) = 0.
$$

---

#### Step 6: Use the Cumulative Distribution Function

Let $F(\hat{x}|y)$ denote the CDF of $x$ given $y$. Then:

$$
F(\hat{x}|y) = \int_{-\infty}^{\hat{x}} p(x|y) \, dx, \quad 1 - F(\hat{x}|y) = \int_{\hat{x}}^{\infty} p(x|y) \, dx.
$$

Substitute into the equation:

$$
- \left( 2F(\hat{x}|y) - 1 \right) = 0.
$$

---

#### Step 7: Solve for $\hat{x}^*$
Setting the equation to zero:
$$
F(\hat{x}^*|y) = \frac{1}{2}.
$$
Thus, $\hat{x}^*$ is the **posterior median**.
> [!info]- Why is this the posterior median?
> - **Definition**: The median divides the distribution into two equal halves.
> - **CDF Interpretation**: $F(\hat{x}|y) = P(x \leq \hat{x}|y)$.
> - **Equating to 0.5**: Ensures a 50% chance that $x \leq \hat{x}$ and $x > \hat{x}$, defining the median.
> - **Minimising Absolute Error**: The median minimises the expected absolute deviation under the posterior.

---

**Summary**: The optimal point estimate for the negative absolute error reward function is the **posterior median**.

##### Full solution

### Summary:

- **Negative Squared Error Reward**: Optimal estimate is the **posterior mean** $\mathbb{E}[x|y]$.
- **Negative Absolute Error Reward**: Optimal estimate is the **posterior median** $\text{Median}[x|y]$.
- This exercise shows the benefit of bayesian methods, in the way that you don't have to change your 
