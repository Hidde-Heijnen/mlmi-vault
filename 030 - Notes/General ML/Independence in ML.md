# Independence in Machine Learning

In machine learning, it's common to assume that data points are **independent and identically distributed (i.i.d.)**. This assumption simplifies modelling by allowing us to treat each data point separately when calculating probabilities, making computations more manageable.

## Independence
---
Two random variables $Y_n$ and $Y_m$ are **independent** if knowing the value of one provides no information about the other:
$$
p(y_n, y_m) = p(y_n) \cdot p(y_m) \quad \text{for } n \neq m
$$
In other words, the occurrence of $y_n$ does not affect the probability of $y_m$.

With independence alone, we can write the joint probability as a product. However, if the variables are not identically distributed, each $p(y_n)$ might be different. This complicates modelling because we cannot generalise a single probability distribution across all data points.

## Identically Distributed
---
Variables are **identically distributed** if they share the same probability distribution:
$$
p(y_n) = p(y_m) \quad \text{for all } n, m
$$
This implies that each data point is drawn from the same underlying distribution. But without independence, the variables can be dependent. Dependency implies that knowing one variable gives information about another, preventing us from expressing the joint probability as a simple product

## Independent and Identically Distributed (i.i.d.)
---
Combining both concepts:

- **Independent**: Each data point is independent of the others.
- **Identically Distributed**: Each data point follows the same probability distribution.

The **i.i.d. assumption** allows us to model the joint probability of data as the product of individual probabilities:
$$
p(\mathbf{y}) = \prod_{n=1}^{N} p(y_n)
$$

## Conditional Independence
---
In many machine learning models, especially supervised learning, outputs $y_n$ are assumed to be **conditionally independent** given the inputs $\mathbf{X}$ and model parameters $\theta$. This means:
$$
p(y_n \mid y_m, \mathbf{X}, \theta) = p(y_n \mid \mathbf{X}, \theta) \quad \text{for } n \neq m
$$
Here, each output $y_n$ is independent of other outputs $y_m$ when we know the inputs and parameters. 

This allows us to write the **conditional joint probability** as a product:
$$
p(\mathbf{y} \mid \mathbf{X}, \theta) = \prod_{n=1}^{N} p(y_n \mid \mathbf{X}, \theta)
$$
However, if we're interested in the **marginal joint probability** $p(\mathbf{y})$, conditional independence alone doesn't help because the conditioning variables $\mathbf{X}$ and $\theta$ are not accounted for:
$$
p(\mathbf{y}) \neq \prod_{n=1}^{N} p(y_n)
$$
## Key Concepts

- **Independence**: Data points do not influence each other; no conditions are applied.
- **Identically Distributed**: All data points come from the same probability distribution.
- **Conditional Independence**: Outputs are independent of each other given certain conditions (inputs and parameters).
- **i.i.d. Assumption**: Combines independence and identical distribution, simplifying calculations.
