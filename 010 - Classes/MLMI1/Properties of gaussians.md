**Prerequisites:**

- Basic knowledge of linear algebra (vectors, matrices, transpose, inverse, determinant).
- Understanding of probability density functions.
- Familiarity with the univariate Gaussian (normal) distribution.
- Knowledge of multivariate calculus (integration over multiple variables).

---
### Definition
A random vector $X \in \mathbb{R}^n$ is said to follow a multivariate normal (Gaussian) distribution with mean vector $M \in \mathbb{R}^n$ and covariance matrix $\Sigma \in \mathbb{R}^{n \times n}$, denoted as:

$$
X \sim \mathcal{N}(M, \Sigma) \quad \iff \quad p(x) = \mathcal{N}(x; M, \Sigma)
$$

The probability density function (pdf) is given by:
$$
p(x) = \frac{1}{\sqrt{ (2\pi)^n \det(\Sigma) }} \, e^{ -\frac{1}{2} (x - M)^\top \Sigma^{-1} (x - M) }
$$
or
$$
p(x) = \frac{1}{\sqrt{\det(2\pi\Sigma) }} \, e^{ -\frac{1}{2} (x - M)^\top \Sigma^{-1} (x - M) }
$$

**Explanation of Variables:**
- $X$: An $n$-dimensional random vector.
- $x$: A specific value in $\mathbb{R}^n$ where the pdf is evaluated.
- $M$: The mean vector, an $n$-dimensional column vector representing the expected value of $X$.
- $\Sigma$: The covariance matrix, an $n \times n$ symmetric positive-definite matrix capturing the variances and covariances between the elements of $X$.
- $\det(\Sigma)$: The determinant of $\Sigma$, ensuring the pdf integrates to 1.
- $(x - M)^\top$: The transpose of $(x - M)$, converting the column vector into a row vector.
- $\Sigma^{-1}$: The inverse of the covariance matrix.

---
### Moments

**Mean:**
The expected value (mean) of $X$ is:$$\mathbb{E}[X] = \int x \, p(x) \, dx = M$$
**Covariance:**
The covariance matrix of $X$ is:$$\mathbb{E}\left[ (X - M)(X - M)^\top \right] = \int (x - M)(x - M)^\top p(x) \, dx = \Sigma$$

---
### Properties

**Marginals are Gaussian:**
Given $X \sim \mathcal{N}(M, \Sigma)$ with partitions:

$$
X = \begin{bmatrix} X_1 \\ X_2 \end{bmatrix}, \quad M = \begin{bmatrix} M_1 \\ M_2 \end{bmatrix}, \quad \Sigma = \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix}
$$

Then, the marginal distributions of $X_1$ and $X_2$ are also Gaussian:
$$p(X_1) = \int p(x) \, dx_2 = \mathcal{N}(X_1; M_1, \Sigma_{11})$$
$$p(X_2) = \int p(x) \, dx_1 = \mathcal{N}(X_2; M_2, \Sigma_{22})$$
*Explanation:* The marginal distribution of a subset of variables from a multivariate Gaussian is Gaussian, with mean and covariance corresponding to the relevant subcomponents of $M$ and $\Sigma$.

---
### Conditionals are Gaussian
Using the same partitioning, the conditional distribution of $X_1$ given $X_2$ is Gaussian:
$$p(X_1 \mid X_2) = \mathcal{N}(X_1; M_{1|2}, \Sigma_{1|2})$$
**Where:**
- **Conditional Mean:**$$M_{1|2} = M_1 + \Sigma_{12} \Sigma_{22}^{-1} (X_2 - M_2)$$
- **Conditional Covariance:**$$\Sigma_{1|2} = \Sigma_{11} - \Sigma_{12} \Sigma_{22}^{-1} \Sigma_{21}$$
	- No need to to learn this identity, will be given if needed
*Explanation:* The conditional distribution remains Gaussian, with updated mean and covariance that account for the observed values of $X_2$.
---
### Alternative Representation
This form is useful for computing expectations of linear transformations of Gaussian variables quickly.

1. **Linear Transformation of Standard Normal Vector:**$$X = M + L \epsilon, \quad \epsilon \sim \mathcal{N}(0, I_n)$$
   - $L$: A matrix such that $\Sigma = L L^\top$ (e.g., Cholesky decomposition). 
	   - Or $\Sigma^{1/2}$: square root of the covariance matrix $\Sigma$ (i.e., a matrix that when multiplied by itself gives $\Sigma$.
   - $I_n$: The $n \times n$ identity matrix.
2. **Equivalent Probability Density Function:**$$p(X) = \mathcal{N}(X; M, \Sigma)$$
**Sketch Proof:**
- **Matching Moments:** The mean and covariance of $X$ computed from the transformation match $M$ and $\Sigma$.
- **Gaussianity:** Since $\epsilon$ is Gaussian and $X$ is a linear transformation of $\epsilon$, $X$ is also Gaussian.

---

**Product of Gaussian Densities:**
The product of two Gaussian densities yields an unnormalised Gaussian density:
$$
\mathcal{N}(x; M_1, \Sigma_1) \cdot \mathcal{N}(x; M_2, \Sigma_2) = c \cdot \mathcal{N}(x; M, \Sigma)
$$

**Where:**
- **Combined Precision Matrix:**$$\Sigma^{-1} = \Sigma_1^{-1} + \Sigma_2^{-1}$$
- **Combined Mean:**$$M = \Sigma \left( \Sigma_1^{-1} M_1 + \Sigma_2^{-1} M_2 \right)$$
- **Normalisation Constant ($c$):** A constant ensuring the equality holds, often omitted when focusing on proportionality.

*Explanation:* The inverse covariance matrices (precisions) add, and the mean is a precision-weighted average of $M_1$ and $M_2$.

**Derivation (Sketch):**
- **Completing the Square:** By combining exponents and rearranging terms, the product exponentiates to a quadratic form representing a Gaussian.
- **Normalisation:** The constant $c$ accounts for differences in normalisation factors due to the determinants.

---

**Additional Context:**
- **Affine Transformations:**
  If $Y = A X + b$, then:$$Y \sim \mathcal{N}(A M + b, A \Sigma A^\top)$$
- **Independence and Uncorrelatedness:**
  In a multivariate Gaussian, uncorrelated components (zero covariance) are independent.

- **Maximum Entropy:**
  The Gaussian distribution maximizes entropy among all distributions with a specified mean and covariance.

- **Applications:**
  - **Statistics:** Regression, hypothesis testing, principal component analysis.
  - **Machine Learning:** Gaussian processes, Bayesian inference.
  - **Signal Processing:** Kalman filters, state-space models.
---
**Key Takeaways:**

- The multivariate Gaussian distribution is central in probability and statistics due to its mathematical tractability and natural occurrence in the central limit theorem.
- Understanding its properties allows for simplified analysis of complex systems involving multiple random variables.
- The marginal and conditional distributions being Gaussian facilitate analytical solutions in many applications.

**Definition:**
$$ X \sim \mathcal{N}(M, \Sigma) \iff p(x) = \mathcal{N}(x; M, \Sigma) $$
	 - tell here about what the variables are (sigma is more dimensions than x or M)
$$ p(x) = \frac{1}{\sqrt{\det(2\pi\Sigma)}} e^{-\frac{1}{2}(x - M)^\top \Sigma^{-1} (x - M)} $$

**Moments:**

**Mean:**
$$ \mathbb{E}_{p(x)}[x] = \int x p(x) dx = M $$

**Covariance:**
$$ \mathbb{E}_{p(x)}[x x^T] - M M^T = \int (x - M)(x - M)^\top p(x) dx = \Sigma $$

**Marginals are Gaussian**

If $X \sim \mathcal{N}(M, \Sigma)$ where:
$$ X = \begin{bmatrix} X_1 \\ X_2 \end{bmatrix}, \quad M = \begin{bmatrix} M_1 \\ M_2 \end{bmatrix}, \quad \Sigma = \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix} $$

Then:
$$ p(X_1) = \int p(x) dx_2 = \mathcal{N}(X_1; M_1, \Sigma_{11}) $$
$$ p(X_2) = \int p(x) dx_1 = \mathcal{N}(X_2; M_2, \Sigma_{22}) $$

i.e. the marginals are Gaussians with mean and covariance given by corresponding elements of $M$ and $\Sigma$.

**Conditionals are Gaussian**

If $X \sim \mathcal{N}(M, \Sigma)$ where:
$$ X = \begin{bmatrix} X_1 \\ X_2 \end{bmatrix}, \quad M = \begin{bmatrix} M_1 \\ M_2 \end{bmatrix}, \quad \Sigma = \begin{bmatrix} \Sigma_{11} & \Sigma_{12} \\ \Sigma_{21} & \Sigma_{22} \end{bmatrix} $$

Then the conditional distribution is:
$$ p(X_1 | X_2) = \mathcal{N}(X_1; M_{1|2}, \Sigma_{1|2}) $$

Where:
$$ M_{1|2} = M_1 + \Sigma_{12} \Sigma_{22}^{-1} (X_2 - M_2) $$
$$ \Sigma_{1|2} = \Sigma_{11} - \Sigma_{12} \Sigma_{22}^{-1} \Sigma_{21} $$
**Alternative Representation**  
Useful for computing expectations of linear transforms of Gaussian variables quickly.

1.  
$$ X = M + \Sigma^{1/2} \epsilon, \quad \epsilon \sim \mathcal{N}(0, I) $$

2.  
$$ p(X) = \mathcal{N}(X; M, \Sigma) $$

**Sketch proof:**  
- The moments of (1) match those of (2).  
- $X$ produced from (1) must be multivariate Gaussian (proof in next section).

**Product of Gaussian Densities = Unnormalised Gaussian Density**

$$ \mathcal{N}(x; M_1, \Sigma_{11}) \, \mathcal{N}(x; M_2, \Sigma_{22}) = c \, \mathcal{N}(x; M, \Sigma) $$

Where:
$$ \Sigma^{-1} = \Sigma_{11}^{-1} + \Sigma_{22}^{-1} $$

$$ M = \left( \Sigma_{11}^{-1} + \Sigma_{22}^{-1} \right)^{-1} \left( \Sigma_{11}^{-1} M_1 + \Sigma_{22}^{-1} M_2 \right) $$

You don’t need to memorise these, but they can be derived by completing the square.
