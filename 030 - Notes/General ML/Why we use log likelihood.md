We use the log-likelihood instead of the likelihood for several reasons:

## 1. Products become sums
When dealing with independent and identically distributed (iid) data, the likelihood function often involves a product of probabilities. For example, the likelihood for a set of data points $\{x_1, x_2, \dots, x_n\}$ is:
$$ L(\theta) = \prod_{i=1}^{n} p(x_i | \theta) $$
   Taking the logarithm turns the product into a sum:
$$ \log L(\theta) = \sum_{i=1}^{n} \log p(x_i | \theta) $$
   This makes the calculations simpler and easier to handle in optimisation tasks.

## 2. Numerical stability
The likelihood function can result in very small numbers, especially when working with many data points or probabilities close to zero. For instance, multiplying many small probabilities can cause underflow. Taking the log converts these small products into sums of manageable values.

## 3. Simplifies exponentials
Many distributions, like the Gaussian (normal) distribution, involve exponentials. The probability density function of a Gaussian distribution is:

   $$ p(x | \mu, \sigma^2) = \frac{1}{\sqrt{2 \pi \sigma^2}} \exp\left(-\frac{(x - \mu)^2}{2 \sigma^2}\right) $$
   Taking the log of this simplifies the expression:$$ \log p(x | \mu, \sigma^2) = -\frac{1}{2} \log(2 \pi \sigma^2) - \frac{(x - \mu)^2}{2 \sigma^2} $$
   This simplification makes optimisation tasks like maximum likelihood estimation much more manageable.
