**1. Probability Basics**
- Sum Rule (Marginalization): $$P(A) = \sum_{B} P(A \cap B) = \sum_{B} P(A, B)$$
- Product Rule: $$P(A \cap B) = P(A|B)P(B) = P(A,B)$$
- Bayes' Theorem: $$P(A|B) = \frac{P(B|A)P(A)}{P(B)}$$
- Conditional Probability: $$P(A|B) = \frac{P(A \cap B)}{P(B)}$$
- Law of Total Probability: $$P(A) = \sum_{i} P(A|B_i)P(B_i)$$
- Law of Total Expectation: $$\mathbb{E}[X] = \mathbb{E}[\mathbb{E}[X|Y]]$$
- **Law of Large Numbers**:
  - *Weak Law*: $$\overline{X}_n \xrightarrow{P} \mu$$
  - *Strong Law*: $$\overline{X}_n \xrightarrow{\text{a.s.}} \mu$$
- **Central Limit Theorem**:
  $$\sqrt{n}(\overline{X}_n - \mu) \xrightarrow{D} N(0, \sigma^2)$$
- **Jensen's Inequality**:
  For a convex function \( f \):
  $$f(\mathbb{E}[X]) \leq \mathbb{E}[f(X)]$$
- **Markov's Inequality**:
  For a non-negative random variable \( X \):
  $$P(X \geq a) \leq \frac{\mathbb{E}[X]}{a}$$
- **Chebyshev's Inequality**:
  $$P(|X - \mathbb{E}[X]| \geq k\sigma) \leq \frac{1}{k^2}$$

**2. Random Variables**
- Expectation: $$\mathbb{E}[X] = \sum_x xP(X=x)$$
- Variance: $$\text{Var}(X) = \mathbb{E}[X^2] - (\mathbb{E}[X])^2$$
- Covariance: $$\text{Cov}(X,Y) = \mathbb{E}[(X - \mathbb{E}[X])(Y - \mathbb{E}[Y])]$$
- Correlation: $$\text{Corr}(X,Y) = \frac{\text{Cov}(X,Y)}{\sigma_X \sigma_Y}$$
- **Moment Generating Function (MGF)**:
  $$M_X(t) = \mathbb{E}[e^{tX}]$$
- **Characteristic Function**:
  $$\phi_X(t) = \mathbb{E}[e^{itX}]$$

**3. Common Distributions**
- **Discrete Distributions**:
  - Bernoulli: $$P(X=x) = p^x(1-p)^{1-x}, \, x \in \{0,1\}$$
  - Binomial: $$P(X=k) = \binom{n}{k} p^k(1-p)^{n-k}$$
  - Poisson: $$P(X=k) = \frac{\lambda^k e^{-\lambda}}{k!}$$
  - **Geometric**: $$P(X=k) = p(1-p)^{k-1}$$
- **Continuous Distributions**:
  - Gaussian (Normal): $$f(x|\mu,\sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}} \exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)$$
  - **Multivariate Gaussian**:
    $$f(\mathbf{x}|\boldsymbol{\mu}, \Sigma) = \frac{1}{(2\pi)^{k/2}|\Sigma|^{1/2}} \exp\left(-\frac{1}{2} (\mathbf{x}-\boldsymbol{\mu})^\top \Sigma^{-1} (\mathbf{x}-\boldsymbol{\mu})\right)$$
  - Exponential: $$f(x|\lambda) = \lambda e^{-\lambda x}, \, x \geq 0$$
  - Gamma: $$f(x|\alpha,\beta) = \frac{\beta^\alpha x^{\alpha -1} e^{-\beta x}}{\Gamma(\alpha)}, \, x \geq 0$$
  - Beta: $$f(x|\alpha,\beta) = \frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)} x^{\alpha -1} (1 - x)^{\beta -1}, \, 0 \leq x \leq 1$$
  - **Dirichlet**:
    $$f(\mathbf{x}|\boldsymbol{\alpha}) = \frac{\Gamma\left(\sum_{i=1}^K \alpha_i\right)}{\prod_{i=1}^K \Gamma(\alpha_i)} \prod_{i=1}^K x_i^{\alpha_i -1}, \quad \sum_{i=1}^K x_i = 1$$
  - **Student's t-Distribution**:
    $$f(x|\nu) = \frac{\Gamma\left(\frac{\nu +1}{2}\right)}{\sqrt{\nu \pi}\, \Gamma\left(\frac{\nu}{2}\right)} \left(1 + \frac{x^2}{\nu}\right)^{-\frac{\nu+1}{2}}$$

**4. Joint and Marginal Distributions**
- Joint Distribution: $$P(A \cap B) = P(A|B)P(B)$$
- Marginal Distribution: $$P(A) = \sum_{B} P(A \cap B)$$
- Conditional Distribution: $$P(X|Y)$$
- **Chain Rule for Probabilities**:
  $$P(X_1, X_2, ..., X_n) = P(X_1)P(X_2|X_1)P(X_3|X_1,X_2)\cdots P(X_n|X_1,...,X_{n-1})$$

**5. Maximum Likelihood Estimation (MLE)**
- MLE: $$\hat{\theta}_{\text{MLE}} = \arg\max_\theta \prod_{i=1}^n P(x_i|\theta)$$
- Log-likelihood: $$\ell(\theta) = \sum_{i=1}^n \log P(x_i|\theta)$$
- **Properties of MLE**:
  - Consistency: $$\hat{\theta}_{\text{MLE}} \xrightarrow{P} \theta_0$$
  - Asymptotic Normality: $$\sqrt{n}(\hat{\theta}_{\text{MLE}} - \theta_0) \xrightarrow{D} N(0, I^{-1}(\theta_0))$$
- **Fisher Information**:
  $$I(\theta) = -\mathbb{E}\left[ \frac{\partial^2}{\partial \theta^2} \log P(X|\theta) \right]$$
- **Cramér-Rao Lower Bound**:
  $$\text{Var}(\hat{\theta}) \geq \frac{1}{I(\theta)}$$

**6. Bayesian Inference**
- **Prior Distribution**: $$P(\theta)$$
- **Likelihood**: $$P(X|\theta)$$
- **Posterior Distribution**: $$P(\theta|X) = \frac{P(X|\theta)P(\theta)}{P(X)}$$
- **Evidence (Marginal Likelihood)**: $$P(X) = \int P(X|\theta)P(\theta) d\theta$$
- **Maximum A Posteriori (MAP) Estimation**:
  $$\hat{\theta}_{\text{MAP}} = \arg\max_\theta P(\theta|X)$$
- **Conjugate Priors**:
  - Example: For Binomial likelihood, Beta prior is conjugate.
- **Posterior Predictive Distribution**:
  $$P(x_{n+1}|X) = \int P(x_{n+1}|\theta) P(\theta|X) d\theta$$

**7. KL Divergence and Information Theory**
- **Entropy**: $$H(X) = -\sum_x P(x) \log P(x)$$
- **Cross-Entropy**: $$H(P, Q) = -\sum_x P(x) \log Q(x)$$
- **KL Divergence**: $$D_{KL}(P||Q) = \sum_x P(x) \log\frac{P(x)}{Q(x)}$$
- **Mutual Information**: $$I(X;Y) = \sum_{x,y} P(x,y) \log \frac{P(x,y)}{P(x)P(y)}$$
- **Conditional Entropy**: $$H(X|Y) = -\sum_{x,y} P(x,y) \log P(x|y)$$
- **Chain Rule for Entropy**: $$H(X,Y) = H(X|Y) + H(Y)$$

**8. Markov Chains**
- **Definition**: A stochastic process where the future state depends only on the current state.
- **Transition Matrix**: $$P_{ij} = P(X_{n+1} = j | X_n = i)$$
- **Stationary Distribution**: $$\pi = \pi P$$
- **Detailed Balance Condition**: $$\pi_i P_{ij} = \pi_j P_{ji}$$

**9. Markov Decision Processes (MDPs)**
- **Components**:
  - States \( S \)
  - Actions \( A \)
  - Transition Probabilities \( P(s'|s,a) \)
  - Reward Function \( R(s,a) \)
- **Policy**: $$\pi(a|s)$$
- **Value Function**: $$V^\pi(s) = \mathbb{E}\left[ \sum_{t=0}^\infty \gamma^t R(s_t,a_t) | s_0 = s \right]$$
- **Bellman Equation**:
  $$V^\pi(s) = \sum_a \pi(a|s) \left[ R(s,a) + \gamma \sum_{s'} P(s'|s,a) V^\pi(s') \right]$$

**10. Monte Carlo Methods**
- **Monte Carlo Integration**:
  $$\int f(x) dx \approx \frac{1}{N} \sum_{i=1}^N f(x_i)$$
- **Markov Chain Monte Carlo (MCMC)**:
  - **Metropolis-Hastings Algorithm**
  - **Gibbs Sampling**

**11. Variational Inference**
- **Evidence Lower Bound (ELBO)**:
  $$\log P(X) \geq \mathbb{E}_{q(\theta)} [\log P(X,\theta)] - \mathbb{E}_{q(\theta)} [\log q(\theta)]$$
- **Objective**:
  Maximize ELBO w.r.t. \( q(\theta) \)

**12. Expectation-Maximization (EM) Algorithm**
- **E-step**: Compute expected log-likelihood using current parameter estimates.
- **M-step**: Maximize this expected log-likelihood to update parameters.

**13. Concentration Inequalities**
- **Hoeffding's Inequality**:
  $$P\left( \left| \overline{X}_n - \mu \right| \geq \epsilon \right) \leq 2 \exp\left( -\frac{2n\epsilon^2}{(b - a)^2} \right)$$
- **Chernoff Bound**:
  $$P(X \geq a) \leq \inf_{t > 0} \frac{\mathbb{E}[e^{tX}]}{e^{ta}}$$

**14. Stochastic Processes**
- **Definition**: A collection of random variables \( \{X_t\}_{t \in T} \) indexed by time or space.
- **Examples**:
  - Random Walks
  - Poisson Processes
  - Brownian Motion

**15. Probability Density Functions and Transformations**
- **Probability Density Function (PDF)**: $$f_X(x)$$
- **Cumulative Distribution Function (CDF)**: $$F_X(x) = P(X \leq x)$$
- **Change of Variables**:
  $$f_Y(y) = f_X(g^{-1}(y)) \left| \frac{d}{dy} g^{-1}(y) \right|$$

**16. Random Vectors and Multivariate Distributions**
- **Joint PDF**: $$f_{\mathbf{X}}(\mathbf{x})$$
- **Covariance Matrix**:
  $$\Sigma = \mathbb{E}[(\mathbf{X} - \boldsymbol{\mu})(\mathbf{X} - \boldsymbol{\mu})^\top]$$
- **Properties of Multivariate Normal Distribution**:
  - Marginals and conditionals are also normal.

**17. Statistical Hypothesis Testing**
- **Null Hypothesis (\( H_0 \))** vs **Alternative Hypothesis (\( H_1 \))**
- **Test Statistic**: A function of the sample data.
- **p-value**: Probability of observing data as extreme as the sample.
- **Type I Error**: Rejecting \( H_0 \) when it's true.
- **Type II Error**: Failing to reject \( H_0 \) when \( H_1 \) is true.
- **Confidence Intervals**

**18. Bootstrap Methods**
- **Resampling Technique**: Drawing samples with replacement.
- **Purpose**: Estimate the sampling distribution of a statistic.

**19. Bias-Variance Tradeoff**
- **Decomposition**:
  $$\text{Expected Loss} = \text{Bias}^2 + \text{Variance} + \text{Irreducible Error}$$

**20. Hidden Markov Models (HMMs)**
- **Components**:
  - Hidden states
  - Observations
  - Transition probabilities
  - Emission probabilities
- **Algorithms**:
  - **Forward Algorithm**: Computes probability of observed sequence.
  - **Viterbi Algorithm**: Finds most probable state sequence.
  - **Baum-Welch Algorithm**: Parameter estimation for HMMs.

**21. Entropy and Information Gain in Machine Learning**
- **Entropy in Decision Trees**:
  $$H(S) = - \sum_{i} p_i \log_2 p_i$$
- **Information Gain**:
  $$IG(S, A) = H(S) - \sum_{v \in \text{Values}(A)} \frac{|S_v|}{|S|} H(S_v)$$

**22. Additional Inequalities**
- **Cauchy-Schwarz Inequality**:
  $$|\langle X, Y \rangle| \leq \|X\| \|Y\|$$
- **Holder's Inequality**
- **Minkowski's Inequality**

**23. Advanced Topics**
- **Concentration Measures**:
  - **Variance Bounding**: Using Chebyshev's inequality.
  - **Tail Bounds**: Using inequalities like Markov's and Chernoff's.
- **Stochastic Optimization**:
  - **Stochastic Gradient Descent (SGD)**
- **Empirical Risk Minimization**:
  $$\min_{\theta} \frac{1}{n} \sum_{i=1}^n L(y_i, f(x_i; \theta))$$

**24. Probability Generating Functions**
- **Definition**:
  $$G_X(s) = \mathbb{E}[s^{X}]$$
- **Use**: Summarize all probabilities of a discrete random variable.

This expanded summary includes fundamental and advanced probability concepts relevant for a Master's level understanding in Machine Learning. It encompasses essential theorems, inequalities, distributions, estimation techniques, Bayesian inference, information theory, stochastic processes, and statistical methods that are foundational for machine learning algorithms and statistical modeling.