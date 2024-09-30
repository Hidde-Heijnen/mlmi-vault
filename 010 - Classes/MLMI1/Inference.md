## Introduction
Inference is estimating unobserved variables from observed data. The purpose of inference is to make a decision, and in these cases how certain you are is even more critical. We will introduce probabilistic modelling and probabilistic inference for making these inferences.

#### Flavours of ML
The machine experiences a series of sensory inputs: $x_1, x_2, x_3, x_4, \dots$

- **Supervised Learning**:
	- Also given correct outputs $y_1, y_2, \dots$
	- Its goal is to learn to **produce the correct output given a new input**.
	  - Regression
	  - Classification: same as a regression problem, but the outputs discrete instead of real. 
		  - You have $k$ classes with decisions boundaries 
- **Unsupervised Learning**:
	- No label or outputs given, just data
	- The goal is to **build a model of** $x$ that can be used for prediction.
		- Clustering: seeing what similar features similar data has. 
		- Dimensionality Reduction: Summarise more complex things by the position on the manifold. Or as a preprocessing/feature learning: reducing computational complexity improving statistical efficiency. 
- **Reinforcement Learning**:
	- The machine can also produce actions $a_1, a_2, \dots$, which affect the state of the world, and receives rewards (or punishments) $r_1, r_2, \dots$
	- Its goal is to **learn to act in a way that maximises rewards in the long term**.$$\text{Actions: } a_1, a_2, \dots \quad \text{Rewards: } r_1, r_2, \dots$$

## Probabilistic approach
 $p(\cdot)$ will be used to denote the probability density functions (discrete values) and $P(\cdot)$ will be used to denote probability mass functions (continuous random variables, distributions etc).
### Probabilistic Inference
Two key ideas for probabilistic inference:
1. The solution is a probability distribution over all possible settings of unknown variables, given observed data.
2. Use the sum and product rules to compute the solution.

- **Forward model:** Moves from unknown variables to the observed variables
	- We do this by first sampling a value for the unknown parameter from the prior distribution, then generating data from the likelihood based on that parameter.
- **Inverse modelling (inference)**: moves from the observed variables to the unknown


**Sum rule**: $p(y) = \int p(y, z) \, dz$  or $P(y) = \sum_{z} P(y,z)$
**Product rule**: $p(y, z) = p(z)p(y|z) = p(y)p(z|y)$
**Bayes' rule**: $p(y|z) = \frac{p(y)p(z|y)}{p(z)}$  
	- **Posterior distribution** $p(y|z)$: what we know after seeing the data.
	- **Prior distribution** $p(y)$: what we knew before seeing the data.
	- **Likelihood** $p(z|y)$: what the data told us.
	Sometimes written as $p(y|z) \propto p(y)p(z|y)$ when $p(z)$ normalises. undefined for $p(z)=0$


### Radioactive decay example
Our decay is supposed to be modelled like: $p( x_n | \lambda ) = \frac{1}{Z(\lambda)} \exp\left(- x_n/\lambda \right)$
	 - $Z(\lambda)$ is a normalisation coefficient
	 - $\lambda$ decay constant
	 - $x_n$ distance

We cannot be sure of $\lambda$, so we would rather have a distribution based on our data $p(\lambda|\{ x_n \}_{n=1}^N)$
$$p(\lambda | \{ x_n \}_{n=1}^N) = \frac{ 1}{p(\{ x_n \}_{n=1}^N )} p(\lambda) p(\{ x_n \}_{n=1}^N | \lambda ) \propto p(\lambda) \prod_{n=1}^N p( x_n | \lambda )$$
	- $p(\{ x_n \}_{n=1}^N | \lambda )$ is our model of the observed data (likelihood)
	- $p(\lambda)$ is our prior (so a realistic estimate beforehand)

Now let's substitute in the expression for the model $p( x_n | \lambda ) = \frac{1}{Z(\lambda)} \exp\left(- x_n/\lambda \right)$ into Bayes' rule
$$
p(\lambda | \{ x_n \}_{n=1}^N) \propto p(\lambda) \prod_{n=1}^N \left( \frac{1}{Z(\lambda)} \exp\left(- x_n/\lambda \right)\right) = p(\lambda)  \frac{1}{Z(\lambda)^N} \exp\left(-\frac{1}{\lambda} \sum_{n = 1}^{N} x_n \right)
$$
	Notice then that we do not need to store all of the individual datapoints $\{ x_n \}_{n=1}^N$ to evaluate the posterior. Rather, we only require the mean $\hat{\mu} = \frac{1}{N}\sum_{n=1}^N x_n$ and $N$. These are called **sufficient statistics**.

**Understanding the likelihood**

The posterior is a distribution over $\lambda$. This means that in order to understand its behaviour we need to understand how $p( x_n | \lambda )$ behaves as a function of $\lambda$. Let's make a familiar plot of the density of $x$ given $\lambda$ that is $p( x | \lambda )$ as a function of $x$ for three different settings of the decay constant.

#### Summarising the posterior distribution
1. MAP (Maximum a posteriori): $\lambda_{MAP} = \arg \max p(\lambda | \{x_n\}_{n=1}^N)$ + Error-bars (for example the full width of the distribution at the half maximum point FWHM)
2. Gaussian approximation: Make a gaussian with a particular mean and variance to match the posterior 
3. Samples from posterior distribution: Samples can be interpreted as typical values of the hidden variables, and there are more samples from the peak than tails. And the samples can be used to calculate for example the mean and uncertainties in that value (like variance). 

#### How should we predict where the next decay event will occur?

Prediction is a fundamental part of science and engineering. The probabilistic approach says:
1. that the answer to this question is the probability of the location next decay event $x^\star$ given the observed data $\{x_n\}_{n=1}^N$, that is $p(x^\star \lvert \{x_n\}_{n=1}^N)$. This is known as the predictive distribution.
2. that the predictive distribution can be computed using the rules of probability
$$\begin{align}
p(x^\star \lvert \{x_n\}_{n=1}^N) &= \int p(x^\star,\lambda \lvert \{x_n\}_{n=1}^N) \text{d} \lambda \;\;\; \text{(sum rule)}\\
%
& = \int p(x^\star \lvert  \lambda, \{x_n\}_{n=1}^N) p(\lambda | \{x_n\}_{n=1}^N) \text{d} \lambda \;\;\; \text{(product rule)}\\ 
%
& = \int p(x^\star \lvert  \lambda) p(\lambda | \{x_n\}_{n=1}^N) \text{d} \lambda \;\;\; \text{(modelling assumptions)}\\ 
\end{align}$$
	The last line follows from that fact that if we know $\lambda$ then, under the model we are assuming, the data set $\{x_n\}_{n=1}^N$ provides no additional information about $x^\star $.

The predictive distribution has an intuitive form: it takes the prediction we would make if we knew $\lambda$, $p(x^\star \lvert  \lambda)$, weights it by the probability under the posterior $p(\lambda | \{x_n\}_{n=1}^N)$, and sums this quatity over all settings of $\lambda$. For this reason the probabilistic predictive distribution above is sometimes called the **posterior predictive**.

Here's the posterior predictive distribution in our case:


