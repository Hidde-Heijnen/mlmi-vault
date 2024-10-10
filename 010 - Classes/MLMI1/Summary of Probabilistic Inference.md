Everything follows from two simple rules:
- **Sum rule**: $$p(x) = \sum_y p(x, y)$$
	(or integral for continuous distributions)
- **Product rule**: $$p(x, y) = p(x)p(y|x)$$
From the product rule we can make the **bayes rule**, which is useful when we want to ... $$p(y|z) = \frac{p(y)p(z|y)}{p(z)}$$
## Learning:


$$p(\theta | D, m) = \frac{p(D | \theta, m) p(\theta | m)}{p(D | m)}$$
- $m$: model
- $D$: data
- $\theta$
- $p(\theta|D, m)$
- $p(D|\theta, m)$: likelihood of the data $D$ in model $m$ (model parameters)
- $p(\theta | m)$: prior probability of $\theta$

### Prediction:
$$p(x^* | D, m) = \int p(x^* | \theta, D, m) p(\theta | D, m) d\theta$$
  Often:
$$p(x^* | D, m) = \int p(x^* | \theta, m) p(\theta | D, m) d\theta$$
  (average of all possible predictions, weighted by posterior probability)

### Model Comparison:
$$p(m | D) = \frac{p(D | m) p(m)}{p(D)}$$
