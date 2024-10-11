## Bayesian decision theory
### Question
A data-scientist has computed a complex posterior distribution over a variable of interest, $x$, given observed data $y$, that is $p(x|y)$. They would like to return a point estimate of $x$ to their client. The client provides the data-scientist with a reward function $R(\hat{x},x)$ that indicates their satisfaction with a point estimate $\hat{x}$ when the true state of the variable is $x$.

  * Explain how to use _Bayesian Decision Theory_ to determine the optimal point estimate, $\hat{x}$.  
  * Compute the optimal point estimate $\hat{x}$ in the case when the reward function is the negative square error between the point estimate and the true value, $R(\hat{x},x) = -(\hat{x}-x)^2$. Comment on your result. 
  * Compute the optimal point estimate $\hat{x}$ in the case when the reward function is the negative absolute error between the point estimate and the true value, $R(\hat{x},x) = -|\hat{x}-x|$. Comment on your result.
### Answer
#### 1. Determine the Optimal Point Estimate $\hat{x}$
Bayesian Decision Theory helps determine the optimal point estimate $\hat{x}$ for a variable $x$ given observed data $y$ and a reward function $R(\hat{x}, x)$. The goal is to maximise the expected reward, calculated as:
$$\text{Expected Reward}(\hat{x}) = \int R(\hat{x}, x) \, p(x|y) \, dx.$$
The optimal point estimate $\hat{x}^*$ maximises the expected reward:

$$\hat{x}^* = \arg\max_{\hat{x}} \int R(\hat{x}, x) \, p(x|y) \, dx.$$
Alternatively, with a loss function $L(\hat{x}, x) = -R(\hat{x}, x)$, the goal becomes minimising the expected loss:
$$\hat{x}^* = \arg\min_{\hat{x}} \int L(\hat{x}, x) \, p(x|y) \, dx.$$
#### 2. Optimal Point Estimate for $R(\hat{x}, x) = -(\hat{x} - x)^2$

The reward function is the negative squared error, leading to the following expected reward:

$$\text{Expected Reward}(\hat{x}) = -\int (\hat{x} - x)^2 \, p(x|y) \, dx.$$

This is equivalent to minimising the expected squared error loss:

$$\text{Expected Loss}(\hat{x}) = \int (\hat{x} - x)^2 \, p(x|y) \, dx.$$

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
