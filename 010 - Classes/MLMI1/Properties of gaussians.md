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
