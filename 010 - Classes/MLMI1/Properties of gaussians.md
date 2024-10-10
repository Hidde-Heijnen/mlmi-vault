**Definition:**
$$ X \sim \mathcal{N}(M, \Sigma) \iff p(x) = \mathcal{N}(x; M, \Sigma) $$
$$ p(x) = \frac{1}{\sqrt{(2\pi)^d \det(\Sigma)}} e^{-\frac{1}{2}(x - M)^T \Sigma^{-1} (x - M)} $$

**Moments:**

**Mean:**
$$ \mathbb{E}_{p(x)}[x] = \int x p(x) dx = M $$

**Covariance:**
$$ \mathbb{E}_{p(x)}[x x^T] - M M^T = \int (x - M)(x - M)^T p(x) dx = \Sigma $$
