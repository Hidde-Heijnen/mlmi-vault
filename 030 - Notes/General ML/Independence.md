## Independence in Machine Learning

In machine learning, **independence** assumptions play a key role in simplifying probabilistic models. The most common assumption is that outputs are **independent and identically distributed (i.i.d.)**. This assumption allows us to model the joint likelihood of the data as a product of individual likelihoods.

### Conditional Independence

Given inputs \( \mathbf{x}_n \) and model parameters \( \theta \), the outputs \( y_n \) are **conditionally independent**. This means that, conditioned on the inputs and parameters, the outputs do not depend on each other:

\[
p(y_n \mid y_m, \mathbf{X}, \theta) = p(y_n \mid \mathbf{X}, \theta) \quad \text{for } n \neq m
\]

### Identically Distributed

The outputs are assumed to be drawn from the **same probability distribution** for each data point. This means that the likelihood function applies uniformly to all observations.

### General Likelihood

For a single observation, the likelihood of \( y \) given \( \mathbf{x} \) and parameters \( \theta \) is:

\[
p(y \mid \mathbf{x}, \theta) = f(y \mid \mathbf{x}, \theta)
\]

### Joint Likelihood under Independence

Assuming conditional independence, the joint likelihood of the entire dataset \( \mathbf{y} \) given the inputs \( \mathbf{X} \) and parameters \( \theta \) is the product of the individual likelihoods:

\[
p(\mathbf{y} \mid \mathbf{X}, \theta) = \prod_{n=1}^{N} f(y_n \mid \mathbf{x}_n, \theta)
\]

### Example: Gaussian Distribution

For a Gaussian distribution, the likelihood function for a single output is:

\[
p(y \mid \mathbf{x}, \theta) = \mathcal{N}\left( y \mid \mu(\mathbf{x}), \sigma^2 \right)
\]

And the joint likelihood under independence is:

\[
p(\mathbf{y} \mid \mathbf{X}, \theta) = \prod_{n=1}^{N} \mathcal{N}\left( y_n \mid \mu(\mathbf{x}_n), \sigma^2 \right)
\]

### Key Concepts

- **Conditional Independence**: Outputs are independent of each other given the inputs and parameters.
- **Identically Distributed**: Each output is drawn from the same distribution.
- **Simplification**: The independence assumption allows us to express the joint likelihood as a product of individual likelihoods, facilitating efficient model training and inference.
