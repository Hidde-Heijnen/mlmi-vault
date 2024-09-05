### Explanation of Notation

#### **Binomial Coefficient**: $\binom{n}{k}$ or $C(n, k)$ or $nCk$
- The binomial coefficient represents the number of ways to choose $k$ successes from $n$ trials, without regard to order. It's calculated as:
  $$ \binom{n}{k} = \frac{n!}{k!(n-k)!} $$
#### **Permutation**: $P(n, k)$ or $nPk$
- The permutation represents the number of ways to arrange $k$ objects from $n$ total objects, where order matters. It's calculated as:
$$ P(n, k) = \frac{n!}{(n-k)!} $$
#### Finding the value of an observation, standard deviation or mean given a z-score
$$x = \overline{x} + z \cdot \sigma$$
---
## 1. **Binomial Distribution**
The binomial distribution models the number of successes in $n$ independent Bernoulli trials with the probability of success $p$.
- **Notation**: $X \sim \text{Binomial}(n, p)$
- **PMF** (Probability Mass Function):
  $$ P(X = k) = \binom{n}{k} p^k (1 - p)^{n - k}, \quad k = 0, 1, \dots, n $$
  where:
  - $\binom{n}{k}$ is the binomial coefficient.
  - $n$ is the number of trials.
  - $p$ is the probability of success on a given trial.
  - $k$ is the **exact** number of successes.

- **Mean**:
$$ \mu = n \cdot p $$
- **Variance**:
  $$ \sigma^2 = n \cdot p \cdot (1 - p) $$
---
## 2. **Poisson Distribution**
The Poisson distribution models the number of events in a fixed interval, with events occurring independently and at a constant rate.
- **Notation**: $X \sim \text{Poisson}(\lambda)$
- **PMF**:
  $$ P(X = k) = \frac{\lambda^k e^{-\lambda}}{k!}, \quad k = 0, 1, 2, \dots $$
  where:
  - $\lambda$ is the average number of occurrences.
  - $k$ is the number of occurrences.

- **Mean**:
$$ \mu = \lambda $$
- **Variance**:
$$ \sigma^2 = \lambda $$
---
## 3. **Normal (Gaussian) Distribution**
The normal distribution is continuous and symmetric about the mean, often used to model real-valued variables.
- **Notation**: $X \sim \mathcal{N}(\mu, \sigma^2)$
- **PDF** (Probability Density Function):
  $$ f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{(x - \mu)^2}{2\sigma^2}}, \quad x \in \mathbb{R} $$
  where:
  - $\mu$ is the mean.
  - $\sigma^2$ is the variance.

- **Mean**:
$$ \mu $$
- **Variance**:
$$ \sigma^2 $$
---
## 4. **Exponential Distribution**
The exponential distribution models the time between events in a Poisson process.
- **Notation**: $X \sim \text{Exponential}(\lambda)$
- **PDF**:
  $$ f(x) = \lambda e^{-\lambda x}, \quad x \geq 0 $$
  where:
  - $\lambda$ is the rate parameter.

- **Mean**:
$$ \mu = \frac{1}{\lambda} $$
- **Variance**:
$$ \sigma^2 = \frac{1}{\lambda^2} $$
---
## 5. **Uniform Distribution**
The uniform distribution models a scenario where all outcomes in a given range are equally likely.
- **Notation**: $X \sim \text{Uniform}(a, b)$
- **PDF**:
  $$ f(x) = \frac{1}{b - a}, \quad a \leq x \leq b $$
  where:
  - $a$ and $b$ are the lower and upper bounds.
- **Mean**:
$$ \mu = \frac{a + b}{2} $$
- **Variance**:
$$ \sigma^2 = \frac{(b - a)^2}{12} $$