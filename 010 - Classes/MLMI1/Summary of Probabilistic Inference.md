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
