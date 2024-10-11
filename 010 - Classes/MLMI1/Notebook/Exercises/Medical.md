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

Taking the derivative and solving for $\hat{x}$ gives:
$$\hat{x} = \int x \, p(x|y) \, dx = \mathbb{E}[x|y].$$
**Result**: The optimal estimate is the **posterior mean**:
$$\hat{x}^* = \mathbb{E}[x|y].$$
#### 3. Optimal Point Estimate for $R(\hat{x}, x) = -|\hat{x} - x|$

The reward function is the negative absolute error, giving the expected reward:

$$\text{Expected Reward}(\hat{x}) = -\int |\hat{x} - x| \, p(x|y) \, dx.$$

This is equivalent to minimizing the expected absolute error loss. The optimal $\hat{x}$ is the **posterior median**, satisfying:

$$P(x \leq \hat{x}|y) = 0.5.$$

**Result**: The optimal estimate is the **posterior median**:

$$\hat{x}^* = \text{Median}[x|y].$$

### Summary:

- **Negative Squared Error Reward**: Optimal estimate is the **posterior mean** $\mathbb{E}[x|y]$.
- **Negative Absolute Error Reward**: Optimal estimate is the **posterior median** $\text{Median}[x|y]$.

Bayesian Decision Theory systematically incorporates the uncertainty and reward preferences, leading to different optimal estimates depending on the reward or loss function.
