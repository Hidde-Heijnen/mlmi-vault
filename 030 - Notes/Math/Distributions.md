### Explanation of Notation

#### **Binomial Coefficient**: $\binom{n}{k}$ or $C(n, k)$ or $nCk$
- The binomial coefficient represents the number of ways to choose $k$ successes from $n$ trials, without regard to order. It's calculated as:
  $$ \binom{n}{k} = \frac{n!}{k!(n-k)!} $$
#### **Permutation**: $P(n, k)$ or $nPk$
- The permutation represents the number of ways to arrange $k$ objects from $n$ total objects, where order matters. It's calculated as:
$$ P(n, k) = \frac{n!}{(n-k)!} $$
#### Finding the value of an observation, standard deviation or mean given a z-score
$$x = \overline{x} + z \cdot \sigma$$
### Covariance
- measures the degree to which two variables change together.
- For the sets $x = \{x_1, x_2,..., x_n\}$ and $y = \{y_1, y_2,..., y_n\}$ It is defined as:

  $$
  \text{Cov}(X, Y) = \frac{1}{n-1} \sum_{i=1}^{n} (X_i - \bar{X})(Y_i - \bar{Y})
  $$
  Or if drawn from a population (not sample data):
    $$
  \text{Cov}(X, Y) = \frac{1}{n} \sum_{i=1}^{n} (X_i - \bar{X})(Y_i - \bar{Y})
  $$
 where:
  - $X_i$ and $Y_i$ are individual sample points,
  - $\bar{X}$ and $\bar{Y}$ are the sample means of $X$ and $Y$,
  - $n$ is the number of data points.

- A positive covariance indicates that as one variable increases, the other tends to increase as well.
- A negative covariance indicates that as one variable increases, the other tends to decrease.
- A covariance of zero suggests no linear relationship between the variables.
- Variance is just Cov(x,x).
	- Variance measures the spread of a single data set x around its mean value. On the other hand, covariance measures of the relationship between two data sets x and y
	- The formula for *sample* **variance** is: $s^2 = \text{Var}(X) = \frac{1}{n-1} \sum_{i=1}^{n} (X_i - \bar{X})^2$	
	- The formula for *population* **variance** is: $\sigma^2 = \text{Var}(X) = \frac{1}{n} \sum_{i=1}^{n} (X_i - \bar{X})^2$	
	Where:
	- $X_i$ are the individual data points,
	- $\bar{X}$ is the mean of the data points,
	- $n$ is the number of data points.

### Linear correlation coefficient
- The **linear correlation coefficient** (denoted as $\rho$ for population or $r$ for samples) measures the strength and direction of a linear relationship between two variables.
- It is defined as:

  $$
  \rho(X, Y) = \frac{\text{Cov}(X, Y)}{\sigma_X \sigma_Y}
  $$
or 
  $$
  \rho = \frac{\text{S}_{xy}}{\sqrt{\text{S}_{xx} \cdot \text{S}_{yy}}}
  $$

  Where:
  - $\text{Cov}(X, Y)$ is the covariance between $X$ and $Y$,
  - $\sigma_X$ and $\sigma_Y$ are the standard deviations of $X$ and $Y$.
  - S is basically the Covariance without the 1/n in front of it. 

- **Properties**:
  - $\rho$ ranges from **-1** to **1**.
  - $\rho = 1$ indicates a perfect positive linear relationship.
  - $\rho = -1$ indicates a perfect negative linear relationship.
  - $\rho = 0$ suggests no linear relationship.

- **Strength of correlation**:
  - $|\rho| > 0.7$ suggests a **strong correlation**.
  - $0.3 < |\rho| \leq 0.7$ suggests a **moderate correlation**.
  - $|\rho| \leq 0.3$ suggests a **weak correlation**.



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
- **Standard deviation**
$$ SD[X] = \sqrt{n \cdot p \cdot (1 - p)} $$
- **Mean**:
$$ E[X] = \mu = n \cdot p $$
- **Variance**:
  $$ Var[X] =  \sigma^2 = n \cdot p \cdot (1 - p) $$
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