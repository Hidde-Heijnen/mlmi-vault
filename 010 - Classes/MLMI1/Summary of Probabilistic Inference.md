Everything in probability and Bayesian inference follows from two fundamental rules:

- **Sum Rule** (Marginalisation):$$p(x) = \sum_y p(x, y)$$
	(or an integral for continuous distributions)
	- Allows computation of the marginal probability of $x$ by summing over all possible values of $y$

- **Product Rule**:$$p(x, y) = p(x) \, p(y \mid x)$$
	- Expresses the joint probability of $x$ and $y$ in terms of a marginal and a conditional probability.

From the product rule, we derive the **Bayes' Rule**, essential for updating probabilities with new evidence:$$p(y \mid z) = \frac{p(y) \, p(z \mid y)}{p(z)}$$
	- Enables the computation of the posterior probability $p(y \mid z)$ by relating it to the prior probability $p(y)$ and the likelihood $p(z \mid y)$.

## Learning:
Bayesian learning updates our beliefs about model parameters using observed data using bayes rule:
$$p(\theta \mid D, m) = \frac{p(D \mid \theta, m) \, p(\theta \mid m)}{p(D \mid m)}$$
- $m$: model
- $D$: data
- $\theta$: model parameters
- $p(\theta \mid D, m)$: **Posterior**; updated belief about parameters after observing data
	- The posterior combines prior beliefs and data evidence to update our knowledge about $\theta$.
- $p(D \mid \theta, m)$: **Likelihood**; probability of data given parameters; informs how likely the observed data is under $\theta$
- $p(\theta \mid m)$: **Prior**; initial belief about parameters before seeing data
- $p(D \mid m)$: **Marginal Likelihood** or **Evidence**; normalising constant ensuring probabilities sum to one; integrates over all possible $\theta$
### Prediction:
To make predictions about new data $x^*$:
$$
p(x^* \mid D, m) = \int p(x^* \mid \theta, m) \, p(\theta \mid D, m) \, d\theta
$$
- Calculates the **predictive distribution** by averaging over all possible parameters weighted by their posterior probabilities.
- Assumes $x^*$ is conditionally independent of $D$ given $\theta$.

### Model Comparison:
To compare different models based on observed data:
$$
p(m \mid D) = \frac{p(D \mid m) \, p(m)}{p(D)}
$$
- $p(m \mid D)$: posterior probability of model $m$ given data
	- Models with higher evidence $p(D \mid m)$ are considered more probable given the data.
- $p(D \mid m)$: **Evidence**; measures how well model $m$ explains the data
- $p(m)$: prior probability of model $m$
- $p(D)$: probability of data under all models; acts as a normalising constant

## Bayesian Decision Theory

The **expected conditional reward** (or utility) for an action $a$ is:
$$
R(a) = \sum_x R(a, x) \, p(x \mid D)
$$
- $R(a, x)$: reward for performing action $a$ in world state $x$
- $p(x \mid D)$: posterior probability of world state $x$ given data $D$

- Decision-making involves choosing the action $a$ that maximizes $R(a)$.

Alternatively, when considering losses:
- Compute the **expected loss** and select the action minimizing it.

### Key Insight:

Bayesian decision theory **separates inference and decision-making**:
- **Inference**: Compute the posterior distribution $p(x \mid D)$ to update beliefs about the world.
- **Decision-making**: Use the posterior to calculate expected rewards or losses and choose the optimal action.

- This separation allows for systematic and principled decisions under uncertainty.


Everything follows from two simple rules:
- **Sum rule**: $$p(x) = \sum_y p(x, y)$$
	(or integral for continuous distributions)
- **Product rule**: $$p(x, y) = p(x)p(y|x)$$
From the product rule we can make the **bayes rule**, which is useful when we want to ... $$p(y|z) = \frac{p(y)p(z|y)}{p(z)}$$
## Learning:


$$p(\theta | D, m) = \frac{p(D | \theta, m) p(\theta | m)}{p(D | m)}$$
- $m$: model
- $D$: data
- $\theta$: model parameters
- $p(\theta|D, m)$: **Posterior**;What we know about parameters after seeing the data
- $p(D|\theta, m)$: **likelihood**; what the data tells us. 
- $p(\theta | m)$: **prior**; probability of $\theta$ before seeing the data
- $p(D|m)$: normalising constant;

### Prediction:
$$p(x^* | D, m) = \int p(x^* | \theta, D, m) p(\theta | D, m) d\theta$$
  Often:
$$p(x^* | D, m) = \int p(x^* | \theta, m) p(\theta | D, m) d\theta$$
  (average of all possible predictions, weighted by posterior probability)

### Model Comparison:
$$p(m | D) = \frac{p(D | m) p(m)}{p(D)}$$
## Bayesian Decision Theory

The **expected conditional reward** is computed as:
$$R(a) = \sum_x R(a, x) p(x | D)$$
- $R(a, x)$: reward for carrying out action $a$ in world $x$
- $p(x | D)$: posterior probability of world state $x$ given data $D$
  (sum over all possible world states)

- Compute the action with the highest expected conditional reward.

### Key Insight:
Bayesian decision theory **separates inference and decision making**.
