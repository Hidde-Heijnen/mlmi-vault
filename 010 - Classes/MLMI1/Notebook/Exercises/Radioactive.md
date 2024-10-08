## 1. Inference in a Gaussian model
### Question
A noisy depth sensor measures the distance to an object an unknown distance $d$ metres away. The depth can be assumed, _a priori_, to be distributed according to a standard Gaussian distribution $p(d) = \mathcal{N}(d;0,1)$. The depth sensor returns $y$ a noisy measurement of the depth, that is also assumed to be Gaussian $p(y|d,\sigma_y^2) = \mathcal{N}(y;d,\sigma_y^2)$.

  * Q1: Compute the posterior distribution over the depth given the observation, $p(d|y,\sigma_y^2)$.   
  * Q2: What happens to the posterior distribution as the measurement noise becomes very large $\sigma_y^2 \rightarrow \infty$? Comment on this result. 

  The formula for the probability density of a Gaussian distribution of mean $\mu$ and variance $\sigma^2$ is given by $$  \begin{align}
\mathcal{N}(x;\mu,\sigma^2) = \frac{1}{\sqrt{2 \pi \sigma^2}} \exp\left(-\frac{1}{2 \sigma^2} (x - \mu)^2 \right). \nonumber
\end{align}$$
### Answer
#### Q1
**Given:**

1. **Prior Distribution:**$$
   p(d) = N(d; 0, 1) = \frac{1}{\sqrt{2\pi}} e^{-\frac{1}{2}d^2}
   $$
   The prior for $d$ is a standard normal distribution with mean $0$ and variance $1$.

2. **Likelihood Function:**
   $$
   p(y|d, \sigma_y^2) = N(y; d, \sigma_y^2) = \frac{1}{\sqrt{2\pi\sigma_y^2}} e^{-\frac{(y - d)^2}{2\sigma_y^2}}
   $$
   The likelihood describes the probability of observing $y$ given $d$, assuming a normal distribution centred at $d$ with variance $\sigma_y^2$.

---

**To find the posterior distribution $p(d|y)$:**

Since we our likelihood is a normal distribution, and our prior is as well, we know that our posterior will also be a normal distribution. This is because this is a [[Conjugate priors|Conjugate prior combination]]

**Step 1: Write the Unnormalised Posterior**
Using Bayes' theorem (up to a proportionality constant since we can absorb constants into normalisation):
$$
p(d|y) \propto p(y|d, \sigma_y^2) \times p(d)
$$

Substitute the expressions for $p(y|d, \sigma_y^2)$ and $p(d)$:
$$
p(d|y) \propto e^{-\frac{(y - d)^2}{2\sigma_y^2}} \times e^{-\frac{1}{2}d^2}
$$
**Step 2: Combine Exponents**
Combine the exponents into a single expression:
$$
p(d|y) \propto e^{-\left( \frac{(y - d)^2}{2\sigma_y^2} + \frac{d^2}{2} \right)}
$$
**Step 3: Expand the Squared Term**
Expand $(y - d)^2$:
$$
(y - d)^2 = y^2 - 2yd + d^2
$$
Substitute back into the exponent:
$$
p(d|y) \propto e^{-\left( \frac{y^2 - 2yd + d^2}{2\sigma_y^2} + \frac{d^2}{2} \right)}
$$
**Step 4: Simplify the Exponent**
Separate the terms and combine like terms:
1. **Group $d^2$ terms:**
$$
\frac{d^2}{2\sigma_y^2} + \frac{d^2}{2} = \frac{d^2}{2}\left( \frac{1}{\sigma_y^2} + 1 \right)
$$
2. **Group $yd$ term:**

$$
-\frac{2yd}{2\sigma_y^2} = -\frac{yd}{\sigma_y^2}
$$
3. **Constant term (independent of $d$) can be ignored for proportionality:**
$$
-\frac{y^2}{2\sigma_y^2}
$$
	 This is because we could just move it into a different exponent and put it in the normalising constant we ignored. 
	 
Now, write the exponent with the grouped terms:
$$
p(d|y) \propto e^{-\left( \frac{d^2}{2}\left( \frac{1}{\sigma_y^2} + 1 \right) - \frac{yd}{\sigma_y^2} \right)}
$$
**Step 5: Rewrite Gaussian Form**
We can express the exponent in the standard quadratic form to identify the mean and variance of the posterior distribution.$$\mathcal{N}(d;\mu_{d|y},\sigma_{d|y}^2) = e^{-\frac{1}{2\sigma_{d|y}^2} \left( d - \mu_{d|y} \right)^2}
= e^{-\frac{1}{2} \left( \frac{d^2}{\sigma_{d|y}^2} - 2 d \frac{\mu_{d|y}}{\sigma_{d|y}^2} + \frac{\mu_{d|y}^2}{\sigma_{d|y}^2} \right)}$$
We can ignore the constant here as well:
$$e^{-\frac{1}{2} \left( \frac{d^2}{\sigma_{d|y}^2} - 2 d \frac{\mu_{d|y}}{\sigma_{d|y}^2} \right)}$$
Now let's compare with our formula from above, we can see that we can match the coefficients to each other. 
$$
e^{-\frac{1}{2} \left[ d^2 \left(\frac{1}{\sigma_{y}^2} + 1\right) - \frac{2dy}{\sigma_{y}^2}\right]}$$
We want to solve for:
$$ e^{-\frac{1}{2} \left( \frac{d^2}{\sigma_{d|y}^2} - 2 d \frac{\mu_{d|y}}{\sigma_{d|y}^2} \right)} =
e^{-\frac{1}{2} \left[ d^2 \left(\frac{1}{\sigma_{y}^2} + 1\right) - \frac{2dy}{\sigma_{y}^2}\right]}$$
The take $ln$ of both sides and multiply both sides by $-2$ to get
$$d^2\frac{1}{\sigma_{d|y}^2} - 2d \frac{\mu_{d|y}}{\sigma_{d|y}^2} =
d^2 \left(\frac{1}{\sigma_{y}^2} + 1\right) - 2d\frac{y}{\sigma_{y}^2}$$
**Match $d^2$ coefficient**
$$\frac{1}{\sigma_{d|y}^2} = \frac{1}{\sigma_{y}^2} + 1 = \frac{1+\sigma_{y}^2}{\sigma_{y}^2}$$
Flip both sides
$$\sigma_{d|y}^2 = \frac{\sigma_{y}^2}{1+\sigma_{y}^2}$$
**Match the other coefficient $2d$, fill in $\sigma_{d|y}^2$, and solve for $\mu_{d|y}$**
$$ \frac{\mu_{d|y}}{\sigma_{d|y}^2} = \frac{\mu_{d|y}}{(\frac{\sigma_{y}^2}{1+\sigma_{y}^2})} = \frac{y}{\sigma_{y}^2}$$
$$ = \frac{\mu_{d|y}(1+\sigma_{y}^2)}{\sigma_{y}^2} = \frac{y}{\sigma_{y}^2}$$
$$ = \mu_{d|y}(1+\sigma_{y}^2) = y$$
$$ \mu_{d|y} = \frac{y}{1+\sigma_{y}^2}$$



**Final Posterior Distribution:**
$$
p(d|y) = N\left( d; \mu_{d|y}, \sigma_{d|y}^2 \right)
$$
where
$$
\mu_{d|y} = \frac{y}{1 + \sigma_y^2}, \quad \sigma_{d|y}^2 = \frac{\sigma_y^2}{1 + \sigma_y^2}
$$
#### Q2
**Given:**

From the previous derivation, we have:

- **Posterior Mean:** $\mu_{d|y} = \frac{y}{1 + \sigma_y^2}$
- **Posterior Variance:** $\sigma_{d|y}^2 = \frac{\sigma_y^2}{1 + \sigma_y^2}$

---

##### **Measurement Noise Becomes Very Large ($\sigma_y^2 \rightarrow \infty$)**

**Step 1: Evaluate the Posterior Variance**
As $\sigma_y^2 \rightarrow \infty$: $$\sigma_{d|y}^2 = \frac{\sigma_y^2}{1 + \sigma_y^2}$$Divide numerator and denominator by $\sigma_y^2$:$$\sigma_{d|y}^2 = \frac{1}{\frac{1}{\sigma_y^2} + 1} \rightarrow \frac{1}{0 + 1} = 1$$
	The posterior variance $\sigma_{d|y}^2$ approaches **1**, which is the variance of the prior distribution $p(d)$.

**Step 2: Evaluate the Posterior Mean**
As $\sigma_y^2 \rightarrow \infty$:$$\mu_{d|y} = \frac{y}{1 + \sigma_y^2} \rightarrow \frac{y}{\infty} = 0$$**Interpretation:**
- The posterior mean $\mu_{d|y}$ approaches **0**, the mean of the prior distribution $p(d)$.

**Conclusion:**
- **When the measurement noise is very large**, the measurement $y$ becomes extremely unreliable.
- The posterior distribution $p(d|y)$ **reverts to the prior distribution** $p(d)$.
- This occurs because the measurement provides **no new information** beyond prior beliefs.
---
##### **Extra: Measurement Noise Becomes Very Small ($\sigma_y^2 \rightarrow 0$)**
**Step 1: Evaluate the Posterior Variance**
As $\sigma_y^2 \rightarrow 0$:$$\sigma_{d|y}^2 = \frac{\sigma_y^2}{1 + \sigma_y^2} \rightarrow \frac{0}{1 + 0} = 0$$
**Interpretation:**
- The posterior variance $\sigma_{d|y}^2$ approaches **0**, indicating our uncertainty about $d$ vanishes.

**Step 2: Evaluate the Posterior Mean**
As $\sigma_y^2 \rightarrow 0$:$$\mu_{d|y} = \frac{y}{1 + \sigma_y^2} \rightarrow \frac{y}{1 + 0} = y$$**Interpretation:**
- The posterior mean $\mu_{d|y}$ approaches **$y$**, the value of the measurement.

**Conclusion:**
- **When the measurement noise is very small**, the measurement $y$ is highly reliable.
- The posterior distribution $p(d|y)$ becomes **concentrated at $d = y$**.
- This indicates that the measurement **overrides our prior beliefs** due to its high precision.
---
##### **Summary and Interpretation**
- **As $\sigma_y^2 \rightarrow \infty$:**
  - Measurement noise dominates, making $y$ unreliable.
  - The posterior distribution mirrors the prior.
  - **Posterior Mean:** $\mu_{d|y} \rightarrow 0$ (prior mean).
  - **Posterior Variance:** $\sigma_{d|y}^2 \rightarrow 1$ (prior variance).

- **As $\sigma_y^2 \rightarrow 0$:**
  - The measurement is highly precise.
  - The posterior distribution centres tightly around $y$.
  - **Posterior Mean:** $\mu_{d|y} \rightarrow y$.
  - **Posterior Variance:** $\sigma_{d|y}^2 \rightarrow 0$.
## 2. Bayesian inference for a biased coin

### Question
A sequence of coin tosses are observed from a biased coin $$\begin{align} x_{1:N}= \{ 0,1,1,0,1,1,1,1,0\} \end{align} $$
where $x_n=1$ indicates flip $n$ was a head and $x_n=0$ indicates that it was tails. An experimenter would like to estimate the coin's probability of landing heads, $\rho$, from these data. 

The experimenter assumes that the coin flips are drawn independently from a Bernoulli distribution $p(x_n|\rho) = \rho^{x_n} (1-\rho)^{1-x_n}$ and uses a prior distribution of the form   $$\begin{align}
p(\rho|n_0,N_0) = \frac{1}{Z(n_0,N_0)}\rho^{n_0} (1-\rho)^{N_0-n_0}. \nonumber
\end{align}$$
Here $n_0$ and $N_0$ are parameters set by the experimenter to encapsulate their prior beliefs.  $Z(n_0,N_0)$ returns the normalising constant of the distribution as a function of the parameters, $n_0$ and $N_0$.

  a) Compute the posterior distribution over the bias $p(\rho | x_{1:N},n_0,N_0 )$. 
  b) Compute the __maximum a posteriori__ (MAP) estimate for the bias. 
  c) Provide an intuitive interpretation for the parameters of the prior distribution, $n_0$ and $N_0$. For what setting of $n_0$ and $N_0$ does the MAP estimate become equal to the maximum-likelihood estimate? 
### Answers
#### a)

Apply bayes rule, and we can separate the data into a product, because they're independent
$$ p(\rho \mid x_{1:N}, n_0, N_0) \propto p(\rho \mid n_0, N_0) \prod_{n=1}^{N} p(x_{n} \mid \rho) $$
Apply definitions:
$$ = \frac{1}{Z(n_0, N_0)} \rho^{n_0} (1-\rho)^{N_0 - n_0} \prod_{n=1}^{N} \rho^{x_n} (1-\rho)^{1 - x_n} $$
We can express this as:
$$ = \frac{1}{Z(n_0, N_0)} \rho^{n_0} (1-\rho)^{N_0 - n_0} \rho^{\sum_n x_n} (1-\rho)^{N - \sum_n x_n} $$
Simplifying:
$$ = \frac{1}{Z(n_0, N_0)} \rho^{n_0 + n } (1-\rho)^{N_0 + N - n_0 - n} $$
Where:
$$ n = \sum_n x_n \quad \text{(i.e., the number of 1's in the dataset)} $$
Thus:
$$ p(\rho \mid x_{1:N}, n_0, N_0) = \frac{1}{Z(n', N')} \rho^{n'} (1-\rho)^{N' - n'} $$
Where:
$$ n' = n_0 + n, \quad N' = N_0 + N $$

This is a Beta distribution (because of the normalising constant in front of it, and the arbitrary values it's fine that it is not in the $\alpha - 1$ form) and is conjugate to the likelihood, meaning the posterior has the same form.

#### b)
We want to find $\rho_{\text{MAP}} = \underset{\rho}{\mathrm{arg\max}} \;\; p(\rho) p(\{ x_n \}_{n=1}^N | \rho )= \underset{\rho}{\mathrm{arg\max}} \;\; p(\rho | \{ x_n \}_{n=1}^N)$
To make it easier we will take the log (this doesn't change the maximum)

We have $p(\rho | \{ x_n \}_{n=1}^N)$ from above

$$\log p(\rho | \textbf{x}, n_0, N_0) = log(\frac{1}{Z(n', N')} \rho^{n'} (1-\rho)^{N' - n'})$$
$$= log(\frac{1}{Z(n', N')}) + log( \rho^{n'}) +log((1-\rho)^{N' - n'})$$
$$= log(\frac{1}{Z(n', N')}) + n'\log( \rho) +(N' - n')\log(1-\rho)$$
$$= log(1) - log(Z(n', N')) + n'\log( \rho) +(N' - n')\log(1-\rho)$$
$$= - log(Z(n', N')) + n'\log( \rho) +(N' - n')\log(1-\rho)$$
Now we take the derivative
$$
\frac{d}{d\rho} \log p(\rho | \textbf{x}, n_0, N_0) = \frac{n'}{\rho_{MAP}} - \frac{N'-n'}{1-\rho}
$$


#### C
- $N_0$ = # of pseudo data points seen before real data
- $n_0$ = # of 1's in pseudo data

**maximum likelihood estimation** $\rho_{\text{ML}} = \underset{\rho}{\mathrm{arg\max}} \;\; p(\{ x_n \}_{n=1}^N | \rho )$
**maximum a posteriori estimation** $\rho_{\text{MAP}} = \underset{\rho}{\mathrm{arg\max}} \;\; p(\rho) p(\{ x_n \}_{n=1}^N | \rho )$
They are the same when our prior is one

in this case our prior is:
$$\frac{1}{Z(n_0, N_0)} \rho^{n_0} (1-\rho)^{N_0 - n_0}$$
This is only equal to one when $n_0 = N_0 = 0$