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
   The likelihood describes the probability of observing $y$ given $d$, assuming a normal distribution centered at $d$ with variance $\sigma_y^2$.

---

**To find the posterior distribution $p(d|y)$:**

**Step 1: Write the Unnormalized Posterior**

Using Bayes' theorem (up to a proportionality constant since we can absorb constants into normalization):
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
Now, write the exponent with the grouped terms:
$$
p(d|y) \propto e^{-\left( \frac{d^2}{2}\left( \frac{1}{\sigma_y^2} + 1 \right) - \frac{yd}{\sigma_y^2} \right)}
$$
**Step 5: Rewrite in Standard Gaussian Form**
We can express the exponent in the standard quadratic form to identify the mean and variance of the posterior distribution.

Let:
- $A = \left( \frac{1}{\sigma_y^2} + 1 \right)$
- $B = \frac{y}{\sigma_y^2}$
The exponent becomes:
$$
p(d|y) \propto e^{-\left( \frac{A}{2}d^2 - Bd \right)}
$$
To rewrite this quadratic expression in terms of $(d - \mu_{d|y})^2$, we complete the square.

**Completing the Square:**
1. **Express the quadratic in $d$:**
$$
\frac{A}{2}d^2 - Bd = \frac{A}{2}\left( d^2 - \frac{2B}{A}d \right)
$$
2. **Complete the square inside the parentheses:**
$$
d^2 - \frac{2B}{A}d = \left( d - \frac{B}{A} \right)^2 - \left( \frac{B}{A} \right)^2
$$
3. **Substitute back:**
$$
\frac{A}{2}\left( \left( d - \frac{B}{A} \right)^2 - \left( \frac{B}{A} \right)^2 \right) = \frac{A}{2}\left( d - \frac{B}{A} \right)^2 - \frac{B^2}{2A}
$$
4. **Exclude constants from the exponent (since they do not affect the proportionality):**
$$
p(d|y) \propto e^{-\frac{A}{2}\left( d - \frac{B}{A} \right)^2}
$$
**Step 6: Identify Posterior Mean and Variance**
From the expression:
$$
p(d|y) \propto e^{-\frac{1}{2\sigma_{d|y}^2}\left( d - \mu_{d|y} \right)^2}
$$
We can equate:
1. **Variance:**
$$
\frac{1}{\sigma_{d|y}^2} = A = \frac{1}{\sigma_y^2} + 1
$$
$$
\Rightarrow \sigma_{d|y}^2 = \frac{1}{\frac{1}{\sigma_y^2} + 1} = \frac{\sigma_y^2}{1 + \sigma_y^2}
$$
2. **Mean:**
$$
\frac{\mu_{d|y}}{\sigma_{d|y}^2} = B = \frac{y}{\sigma_y^2}
$$
$$
\Rightarrow \mu_{d|y} = \sigma_{d|y}^2 \times \frac{y}{\sigma_y^2} = \left( \frac{\sigma_y^2}{1 + \sigma_y^2} \right) \left( \frac{y}{\sigma_y^2} \right) = \frac{y}{1 + \sigma_y^2}
$$
**Final Posterior Distribution:**
$$
p(d|y) = N\left( d; \mu_{d|y}, \sigma_{d|y}^2 \right)
$$
where
$$
\mu_{d|y} = \frac{y}{1 + \sigma_y^2}, \quad \sigma_{d|y}^2 = \frac{\sigma_y^2}{1 + \sigma_y^2}
$$

---

**Summary of Steps and Key Points:**

1. **Multiplying the Prior and Likelihood:** The unnormalised posterior is obtained by multiplying the prior $p(d)$ and the likelihood $p(y|d, \sigma_y^2)$.

2. **Combining Exponents:** The exponents of the prior and likelihood are combined into a single quadratic expression in $d$.

3. **Completing the Square:** By completing the square, we rewrite the quadratic expression to match the standard form of a Gaussian distribution, which allows us to identify the posterior mean $\mu_{d|y}$ and variance $\sigma_{d|y}^2$.

4. **Ignoring Constants:** Constants that do not depend on $d$ (like $y^2$ terms) are absorbed into the normalisation constant and do not affect the shape of the posterior distribution.

6. **Final Expression:** The posterior distribution $p(d|y)$ is a Gaussian distribution with the derived mean and variance.
#### Q2
**Given:**

From the previous derivation, we have:

- **Posterior Mean:** $\mu_{d|y} = \frac{y}{1 + \sigma_y^2}$
- **Posterior Variance:** $\sigma_{d|y}^2 = \frac{\sigma_y^2}{1 + \sigma_y^2}$

---

### **Measurement Noise Becomes Very Large ($\sigma_y^2 \rightarrow \infty$)**

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
### **Extra: Measurement Noise Becomes Very Small ($\sigma_y^2 \rightarrow 0$)**
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
### **Summary and Interpretation**
- **As $\sigma_y^2 \rightarrow \infty$:**
  - Measurement noise dominates, making $y$ unreliable.
  - The posterior distribution mirrors the prior.
  - **Posterior Mean:** $\mu_{d|y} \rightarrow 0$ (prior mean).
  - **Posterior Variance:** $\sigma_{d|y}^2 \rightarrow 1$ (prior variance).

- **As $\sigma_y^2 \rightarrow 0$:**
  - The measurement is highly precise.
  - The posterior distribution centers tightly around $y$.
  - **Posterior Mean:** $\mu_{d|y} \rightarrow y$.
  - **Posterior Variance:** $\sigma_{d|y}^2 \rightarrow 0$.

**Visual Representation:**

- **High Noise ($\sigma_y^2 \rightarrow \infty$):** Wide, flat posterior identical to the prior.
- **Low Noise ($\sigma_y^2 \rightarrow 0$):** Sharp peak at $d = y$, indicating high confidence in $y$.

---

### **Mathematical Insight**

- The **posterior variance** depends on the prior variance and measurement noise.
  - **Formula:** $\sigma_{d|y}^2 = \frac{\sigma_y^2}{1 + \sigma_y^2}$.
  - As $\sigma_y^2$ increases, $\sigma_{d|y}^2$ approaches the prior variance.
  - As $\sigma_y^2$ decreases, $\sigma_{d|y}^2$ approaches zero.

- The **posterior mean** balances the prior mean and measurement.
  - **Formula:** $\mu_{d|y} = \frac{y}{1 + \sigma_y^2}$.
  - High noise reduces $y$'s influence on the posterior mean.
  - Low noise makes $y$ the dominant factor in the posterior mean.

---

### **Practical Implications**

- **Reliability of Measurements:**
  - High measurement noise necessitates reliance on prior information.
  - Low measurement noise allows significant updates from the measurement.

- **Sensor Design:**
  - Understanding measurement noise is crucial for sensor design.
  - Reducing measurement noise enhances the quality of posterior estimates.

- **Bayesian Updating:**
  - The Bayesian framework adjusts the influence of new data based on its uncertainty.
  - Reliable data has a greater impact on the posterior distribution.

