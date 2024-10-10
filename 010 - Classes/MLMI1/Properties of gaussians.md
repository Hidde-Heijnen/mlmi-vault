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
