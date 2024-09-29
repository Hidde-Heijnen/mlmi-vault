**1. Probability Basics**
- Total Probability: $$P(A) = \sum_{i} P(A \cap B_i) = \sum_{i} P(A|B_i)P(B_i)$$
- Bayes' Theorem: $$P(A|B) = \frac{P(B|A)P(A)}{P(B)}$$
- Conditional Probability: $$P(A|B) = \frac{P(A \cap B)}{P(B)}$$
- Law of Total Expectation: $$\mathbb{E}[X] = \mathbb{E}[\mathbb{E}[X|Y]]$$

**2. Random Variables**
- Expectation: $$\mathbb{E}[X] = \sum_x xP(X=x)$$
- Variance: $$\text{Var}(X) = \mathbb{E}[X^2] - (\mathbb{E}[X])^2$$
- Covariance: $$\text{Cov}(X,Y) = \mathbb{E}[(X - \mathbb{E}[X])(Y - \mathbb{E}[Y])]$$
- Correlation: $$\text{Corr}(X,Y) = \frac{\text{Cov}(X,Y)}{\sigma_X \sigma_Y}$$

**3. Common Distributions**
- Bernoulli: $$P(X=x) = p^x(1-p)^{1-x}, \, x \in \{0,1\}$$
- Binomial: $$P(X=k) = \binom{n}{k} p^k(1-p)^{n-k}$$
- Gaussian: $$f(x|\mu,\sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)$$
- Poisson: $$P(X=k) = \frac{\lambda^k e^{-\lambda}}{k!}$$
- Exponential: $$f(x|\lambda) = \lambda e^{-\lambda x}, \, x \geq 0$$

**4. Joint and Marginal Distributions**
- Joint Distribution: $$P(A \cap B) = P(A|B)P(B)$$
- Marginal Distribution: $$P(A) = \sum_{B} P(A \cap B)$$

**5. Maximum Likelihood Estimation (MLE)**
- MLE: $$\hat{\theta}_{\text{MLE}} = \arg\max_\theta \prod_{i=1}^n P(x_i|\theta)$$
- Log-likelihood: $$\ell(\theta) = \sum_{i=1}^n \log P(x_i|\theta)$$

**6. KL Divergence**
- KL Divergence: $$D_{KL}(P||Q) = \sum_x P(x) \log\frac{P(x)}{Q(x)}$$

**7. Mutual Information**
- Mutual Information: $$I(X;Y) = \sum_{x,y} P(x,y) \log \frac{P(x,y)}{P(x)P(y)}$$
