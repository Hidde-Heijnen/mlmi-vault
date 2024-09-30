---
aliases:
  - MLMI playlist summary
link: https://www.youtube.com/playlist?list=PLyXv258Xt2PRhkou67NwiQD9OmiNMzdfa
---
## Books
- Machine Learning: a Probabilistic Perspective - Kevin Patrick Murphy
- Pattern Recognition and Machine Learning - Christopher Bishop
- Bayesian Reasoning and Machine Learning - David Barber
- Information Theory, Inference and Learning Algorithms - David JC MacKay

**Inference problem**: A problem where you have to **estimate unknown variables** from **known variables** 
- Known variables are sometimes called **observed variables**
- unknown variables are sometimes called **unobserved (or latent/hidden) variables**

1. **"right answer" to any inference problem is a probability distribution**
		Instead of just returning a single point estimate of the unobserved variables of the model, you return how plausible that variable is with a distribution. So plausibility of unobserved variables given observed variables. $p(u|o)$
2. **plausibility computed using the sum and product rules of probability**
		**Sum rule**: $p(y) = \int p(y,z) dz$
			If you have a joint probability of y and z, and you want to compute just the probability of y, you have to sum out all of the z variables (for continuous functions you need to integrate, for discrete values: $p(y) = \sum_{z} p(y,z)$)
			We call the $p(y)$ the **marginal probability** of y and $p(y,z)$ the **joint probability of y and z**
		**Product rule**: $p(y,z) = p(z)p(y|z) = p(y)p(z|y)$
		Using these two rules is the only way to perform consistent inferences. If we don't use these rules things like order will start to matter and our answer will be different. We should take into account all evidence (can't leave out some data), and if you can reason in more than one way, then each must lead to the same answer. equivalent states of knowledge imply same plausibility assignment. 
		Cox(1946)
		**Bayes' rule**: $p(y|z) = \frac{p(y)p(z|y)}{p(z)}$ is derived from the product rule 
			$p(y)$ is the prior distribution, and it is what we knew before we see any data
			$p(z|y)$ is what the data tells us (likelihood of parameters)
			$p(y|z)$ is the plausibility after observing data (posterior)
			$p(z)$ is more of a normalising constant


### Summarising the posterior distribution
1. MAP (Maximum a posteriori): $\lambda_{MAP} = \arg \max p(\lambda | \{x_n\}_{n=1}^N)$ + Error-bars (for example the full width of the distribution at the half maximum point FWHM)
2. Gaussian approximation: Make a gaussian with a particular mean and variance to match the posterior 
3. Samples from posterior distribution: Samples can be interpreted as typical values of the hidden variables, and there are more samples from the peak than tails. And the samples can be used to calculate for example the mean and uncertainties in that value (like variance). 

### Summary of probabilistic approach
1. write down the probability of everything (**joint distribution**)
$$p(\{x_n\}_{n=1}^N, \lambda) = p(\lambda) p(\{x_n\}_{n=1}^N | \lambda)$$
2. use Bayes' rule (product rule) to form the **posterior distribution**
$$p(\lambda | \{x_n\}_{n=1}^N) = \frac{1}{p(\{x_n\}_{n=1}^N)} p(\lambda) p(\{x_n\}_{n=1}^N | \lambda)$$
	- Has a normalising constant, a prior and the likelihood of the parameters. 
	- $x_n$ is the fixed variable (the data), and $\lambda$ is the variable
	- Sometimes called inverse problem
3. summarise the posterior e.g. via the **maximum a posteriori** (MAP) estimate
$$\lambda^{MAP} = \arg \max_{\lambda} p(\lambda | \{x_n\}_{n=1}^N) = \arg \max_{\lambda} p(\lambda) p(\{x_n\}_{n=1}^N | \lambda) $$
- or **maximum likelihood** estimate is recovered when using a wide uniform prior distribution
$$\lambda^{ML} = \arg \max_{\lambda} p(\{x_n\}_{n=1}^N | \lambda)$$
	- If you use wide uniform prior distribution MAP will actually correlate to the maximum likelihood distribution
	- Maximum likelihood estimate focusses on optimizing on the data, and doesn't involve the prior. So doesn't involve any prior knowledge we have about or hidden variables or that it is a uniform distribution. 

### Bayesian Decision Theory
- **Posterior probabilities**:
  - The posterior probabilities of possible actions are computed given some observation or condition. For example:$$p(a = 1 | b = 1) = \frac{1}{2}, \quad p(a = 0 | b = 1) = \frac{1}{2}$$
- **Rewards**:
  - The rewards associated with different actions and outcomes (states) are represented as a matrix:$$\begin{bmatrix}
  R(a = 0, t = 0) & R(a = 0, t = 1) \\
  R(a = 1, t = 0) & R(a = 1, t = 1)
  \end{bmatrix}
  =
  \begin{bmatrix}
  10 & 7 \\
  3 & 5
  \end{bmatrix}$$
- **Conditional Reward**:
  - The conditional reward $R(t)$ is calculated by summing over all possible actions $a$, weighted by the posterior probabilities of those actions:$$R(t) = \sum_{a} R(a, t) p(a | b = 1)$$
  - This shows how we can separate **inference** (determining the posterior probability) and **decision making** (choosing an action to maximize expected reward).

- **Example**: 
  - **Conditional reward for not treating** ($t = 0$):
$$R(t = 0) = R(a = 0, t = 0) p(a = 0 | b = 1) + R(a = 1, t = 0) p(a = 1 | b = 1) = 6 \frac{1}{2}$$
  - **Conditional reward for treating** ($t = 1$):
$$R(t = 1) = R(a = 0, t = 1) p(a = 0 | b = 1) + R(a = 1, t = 1) p(a = 1 | b = 1) = 6$$
### Dutch Book Theorem
- The theorem assumes that you are willing to accept bets with odds proportional to the strength of your beliefs.
  - Example: if your belief $b(x) = 0.9$, you will accept a bet where:
    - If $x$ is true, you win $\geq 1$ dollar.
    - If $x$ is false, you lose $9$ dollars.

- **Implication**:
  - If your beliefs do not satisfy the rules of probability theory (such as the sum and product rules), there exists a set of simultaneous bets (called a "Dutch Book") that you will accept. This guarantees that you will lose money, regardless of the outcome.

- **Protection**:
  - The only way to avoid a Dutch Book scenario is to ensure that your beliefs are **coherent**; in other words, they must satisfy the rules of probability theory.

### Flavours of Machine Learning
The machine experiences a series of sensory inputs: $x_1, x_2, x_3, x_4, \dots$

- **Supervised Learning**:
  - The machine is also given the desired outputs $y_1, y_2, \dots$
  - Its goal is to learn to **produce the correct output given a new input**.$$\text{Input: } x_1, x_2, \dots \quad \text{Output: } y_1, y_2, \dots$$
  - Regression: computer vision, weather, demand forecasting etc
  - Classification: exactly the same as a regression problem, but the outputs are now discrete valued instead of real valued. 
	  - Object recognition, speech recognition, face recognition, grouping etc. 
	  - x classes, with decision boundaries. 
- **Unsupervised Learning**:
  - The goal of the machine is to **build a model of** $x$ that can be used for reasoning, decision making, predicting things, communicating, etc.
$$\text{Model: } f(x_1, x_2, \dots) \quad \text{No labels or outputs provided.}$$
  - Clustering (like spam filtering, network community detection, image segmentation): seeing what similar features similar data has. 
  - Dimensionality Reduction: Summarize more complex things by the position on the manifold. Or as a preprocessing/feature learning: reducing computational complexity imporoving statistical efficiency. 
- **Reinforcement Learning**:
  - The machine can also produce actions $a_1, a_2, \dots$, which affect the state of the world, and receives rewards (or punishments) $r_1, r_2, \dots$
  - Its goal is to **learn to act in a way that maximizes rewards in the long term**.$$\text{Actions: } a_1, a_2, \dots \quad \text{Rewards: } r_1, r_2, \dots$$
## Clustering
Two points belonging to the same cluster are generally more similar to each-other than two points in different clusters. 
- The model takes a set of datapoints and a number of clusters that it has to find, and it will assign the data to that numbers of clusters. 
-  Unsupervised learning problem (no labels or rewards)
- **Notation:** 
$$\mathcal{D} = \{ \mathbf{x}_1, \dots, \mathbf{x}_N \} \rightarrow \mathbf{s} = \{ s_1, \dots, s_N \}$$
	where $D = \text{dim}(\mathbf{x}_n)$ and $s_n \in \{ 1, \dots, K \}$
		D is dataset, and for each datapoint x, return a scalar s to which cluster it belongs. 

### K means algorithm
Input: $D = \{x_1, \dots, x_N\}, \ x_n \in \mathbb{R}^D$

Initialise: $m_k \in \mathbb{R}^D$ for $k = 1 \dots K$                                                       (m is cluster centres, randomly)
Repeat:
	For $n = 1 \dots N$:                         Assignment step:
	  $s_n = \arg \min_k \|x_n - m_k\|$        (for each point measure which the closest cluster centre is)
	 For $k = 1 \dots K$:                         (Update step)
	  $m_k = \text{mean}(x_n : s_n = k)$        (update cluster centres with the mean of allocated datapoints)
Until convergence ($s_n$ fixed).         The sn's don't change anymore

- If no points assigned to cluster, do not change the centre. 
- Is K-means guaranteed to converge for any dataset D? Or could one or more cluster centres diverge or oscillate?
	- each step of the algorithm is reducing the energy, and the energy cannot go below zero, at some point we have to reach a local minimum. 
#### K-means as Optimisation
Let $s_{n,k} = 1$ if data point $n$ is assigned to cluster $k$ and $0$ otherwise.
**Note**: $\sum_{k=1}^{K} s_{n,k} = 1$
**Cost**:$$C(\{s_{n,k}\}, \{m_k\}) = \sum_{n=1}^{N} \sum_{k=1}^{K} s_{n,k} \| x_n - m_k \|^2$$K-means tries to minimise the cost function $C$ with respect to $\{s_{n,k}\}$ and $\{m_k\}$, subject to $\sum_k s_{n,k} = 1$ and $s_{n,k} \in \{0,1\}$.

**K-means sequentially**:
- Minimises $C$ with respect to $\{s_{n,k}\}$, holding $\{m_k\}$ fixed.
- Minimises $C$ with respect to $\{m_k\}$, holding $\{s_{n,k}\}$ fixed.
$C$ is a Lyupanov function => K-means converges, but finding the global optimum is an NP-hard problem. 
#### K-means problems
![[CleanShot 2024-09-20 at 12.19.48.png]]
- Strange results when clusters have very different shapes
	- initialisation doesn't fix this. 
	- you could weight the horizontal direction more than the vertical one, but this won't scale to other datasets. 
- Returns hard assignments
	- Maybe soft assignments are better if we are less sure to which cluster they belong.   
- Initialisation delicate
	- k++ means algorithm: spreads out initial centres.  

### Probabilistic approach to clustering
(Given the data we’ve observed, which parameter value is most probable?)
#### Mixture of Gaussians: Generative Model
The mixture of Gaussians (MoG) is a probabilistic model that assumes data is generated from a mixture of $K$ Gaussian distributions, each with its own mean and covariance.

- Cluster membership ($s_n$) determines which Gaussian generates the data point $x_n$.
- The responsibilities ($\pi_k$) represent the probability that a data point belongs to cluster $k$.
- Maximum likelihood estimation is used to optimize the parameters, finding the best-fitting Gaussians for the observed data.
##### Parameters
- **$\theta$ (parameters)**: $\theta = \{ \pi_k, \mu_k, \Sigma_k \}_{k=1}^{K}$
  - $\pi_k$: Mixing coefficients (e.g., $\pi_1 = \frac{1}{2}$, $\pi_2 = \frac{1}{4}$, $\pi_3 = \frac{1}{4}$)
  - $\mu_k$: Mean vectors for each Gaussian component.
  - $\Sigma_k$: Covariance matrices for each Gaussian component.
##### Process for each data point $x_n$, for $n = 1, 2, \dots, N$ (i.i.d.):
1. **Sample cluster membership**:
   - $p(s_n = k | \theta) = \pi_k$
   - The prior probability for $x_n$ to belong to cluster $k$ follows a *Categorical distribution*, with $\sum_{k=1}^{K} \pi_k = 1$.

2. **Sample data value given cluster membership**:
   - $p(x_n | s_n = k, \theta) = \mathcal{N}(x_n; \mu_k, \Sigma_k)$
   - Data points are drawn from a Gaussian distribution (with parameters $\mu_k$ and $\Sigma_k$) specific to the cluster $k$.
##### Clustering procedure:
1. **Parameter estimation**:
   Learn parameters $\theta$ (cluster weights $\pi_k$, means $\mu_k$, and covariances $\Sigma_k$) using maximum likelihood:$$ \theta_{\text{ML}} = \arg \max_\theta \log p(\{x_n\}_{n=1}^N | \theta) $$
2. **Cluster inference**:
   Infer cluster membership for each data point based on the estimated parameters:$$ p(s_n = k | x_n, \theta_{\text{ML}}) $$
   - This will give probabilities how likely it is to come from a curtain cluster.  
##### Different Ways of Maximising the Likelihood
In machine learning, we often want to find the parameters $\theta$ that make the observed data most likely under our model. Maximising the log-likelihood is the standard way to do this. 
$$\log p(\{x_n\}_{n=1}^N | \theta) = \log \prod_{n=1}^N p(x_n|\theta) = \sum_{n=1}^N \log p(x_n|\theta) = \sum_{n=1}^N \log \sum_{k=1}^K p(x_n, s_n = k|\theta)$$
$$= \sum_{n=1}^N \log \sum_{k=1}^K p(s_n = k|\theta) p(x_n | s_n = k, \theta) = \sum_{n=1}^N \log \sum_{k=1}^K \pi_k \mathcal{N}(x_n; \mu_k, \sigma_k^2)$$
We start with the log-likelihood of the observed data $\{x_n\}_{n=1}^N$ given the parameters $\theta$:
$$\log p(\{x_n\}_{n=1}^N | \theta)$$
**Step 1:** Assume that the data points are independent, allowing us to express the joint probability as a product over all data points:
$$= \log \prod_{n=1}^N p(x_n | \theta)$$
*Explanation:* Independence simplifies the joint probability of the data into a product of individual probabilities.

**Step 2:** Apply the logarithm property $\log a b = \log a + \log b$ to convert the product into a sum:
$$= \sum_{n=1}^N \log p(x_n | \theta)$$
*Explanation:* This transformation makes the expression more tractable for optimisation, as sums are easier to handle than products.

**Step 3:** Recognise that each $p(x_n | \theta)$ can be represented as a sum over latent variables (e.g., mixture components), using the sum rule. We're summing out all the possible clusters the datapoint xn could've come from:
$$= \sum_{n=1}^N \log \sum_{k=1}^K p(x_n, s_n = k | \theta)$$
*Explanation:* We introduce latent variables $s_n$ indicating the component membership of each data point in a mixture model.

**Step 4:** Use the definition of joint probability (product rule ) to express $p(x_n, s_n = k | \theta)$ as the product of the marginal and conditional probabilities:
$$= \sum_{n=1}^N \log \sum_{k=1}^K p(s_n = k | \theta) \, p(x_n | s_n = k, \theta)$$
*Explanation:* This separates the probability into the prior probability of belonging to component $k$ and the likelihood of observing $x_n$ given component $k$.

**Step 5:** Substitute the specific forms for $p(s_n = k | \theta)$ and $p(x_n | s_n = k, \theta)$:
$$= \sum_{n=1}^N \log \sum_{k=1}^K \pi_k \, \mathcal{N}(x_n; \mu_k, \Sigma_k)$$
*Explanation:* Here, $\pi_k$ represents the mixing coefficients (priors for each component/how likely it is to come from each cluster before seeing the data), and $\mathcal{N}(x_n; \mu_k, \sigma_k^2)$ is the Gaussian distribution for component $k$. These were already defined above, so we're just substituting them in. 

**Methods for Maximising the Likelihood:**

- **Method 1:** Direct gradient-based optimisation of the log-likelihood.
  - *Pros:* Generally faster convergence.
  - *Cons:* May be complex to implement due to the presence of sums inside logarithms.

- **Method 2:** Expectation-Maximisation (EM) algorithm.
  - *Pros:* Simpler implementation for models with latent variables; widely used and extends to various important generalisations.
  - *Cons:* Can be slower and may converge to local maxima.

**Notes:**
- **Direct Optimisation** involves computing gradients of the log-likelihood with respect to $\theta$ and using optimisation algorithms (e.g., gradient ascent).
- The **EM Algorithm** iteratively performs:
  1. **Expectation (E-step):** Compute the expected value of the latent variables given current parameters.
  2. **Maximisation (M-step):** Update parameters to maximise the expected log-likelihood found in the E-step.

By understanding these steps, we can choose the appropriate method for maximising the likelihood based on the problem's complexity and requirements.
### Kullback-Leibler (KL) Divergence

The Kullback-Leibler divergence measures the difference between two probability distributions, $P_1(z)$ and $P_2(z)$. It quantifies the inefficiency or "surprise" when using $Q$ to approximate $P$. It is basically a distance measure between two distributions. It is calculated using:

$$KL(p_1(z) || p_2(z)) = \sum_{z \in \mathcal{Z}} p_1(z) \log \frac{p_1(z)}{p_2(z)}$$

- **$z \in \mathcal{Z}$**: This denotes that the sum is taken over all possible values that $z$ can take.
- **$p_1(z)$**: The probability from the true distribution, $P_1$.
- **$p_2(z)$**: The probability from the approximate distribution, $P_2$.
#### Key Points:
- **KL divergence** measures the extra information needed when $Q$ is used instead of $P$.
- If $P = Q$, KL divergence is zero.
- Greater differences between $P$ and $Q$ lead to a higher KL divergence, implying more inefficiency in $Q$.
- **Gibb's inequality**: $KL(p_1(z) || p_2(z)) \geq 0$, with equality when $p_1(z) = p_2(z)$.
	- Proof via **Jensen's inequality** or **differentiation** (refer to MacKay, pg. 35).
- It is called a divergence and not the distance for a reason, because of the asymmetry
	- $KL(p || q) \neq KL(q || p)$
	- ![[CleanShot 2024-09-28 at 14.30.44@2x.png]]

#### Example: Bernoulli Distribution
In this example, we use a Bernoulli distribution with possible outcomes $z = {0,1}$. 
##### Probabilities for $P_1$ and $P_2$:
- $P_1(z=0) = 1 - \pi$, $P_1(z=1) = \pi$
- $P_2(z=0) = 1 - \rho$, $P_2(z=1) = \rho$

##### KL Divergence of $P_1$ from $P_2$:
$$KL(P_1 || P_2) = (1 - \pi) \log \frac{1 - \pi}{1 - \rho} + \pi \log \frac{\pi}{\rho}$$
##### KL Divergence of $P_2$ from $P_1$:
$$KL(P_2 || P_1) = (1 - \rho) \log \frac{1 - \rho}{1 - \pi} + \rho \log \frac{\rho}{\pi}$$
### EM algorithm
- [Very good youtube video for general understanding](https://youtube.com/playlist?list=PLBv09BD7ez_7beI0_fuE96lSbsr_8K8YD&si=oQLMWXZhpFtj2dqD)
- EM is used for maximum-likelihood parameter learning in **many latent variable models**.
- Leads to extensions like **approximate variational inference**.
- Basic process
	- Start with $k$ randomly placed Gaussians $(\mu_a, \Sigma_a), (\mu_b, \Sigma_b), \dots, (\mu_k, \Sigma_k)$
	  - For each point: $P(c \mid x_i)$ = does it look like it came from component $c$?
	  - Adjust $(\mu_a, \Sigma_a), (\mu_b, \Sigma_b), \dots, (\mu_k, \Sigma_k)$ to fit points assigned to each component

For generality, we simplify notation: let $\mathbf{x} = \{x_n\}_{n=1}^N$ and $\mathbf{s} = \{s_n\}_{n=1}^N$, so:
$$ \log p(\{x_n\}_{n=1}^N | \theta) = \log p(\mathbf{x} | \theta) = \log \sum_{\mathbf{s}} p(\mathbf{x}, \mathbf{s} | \theta) $$
![[CleanShot 2024-09-28 at 14.45.18@2x.png]]
- We can rewrite (1) to (2) and we use this free-energy instead of just log-likelihood
![[CleanShot 2024-09-29 at 10.04.00@2x.png]]
#### Steps

- **Initialisation**: Start with random parameters $\theta_0$ and $q_0$. Iterate next steps $1...T$ Times
1. **E-step (Optimisation)**: For fixed $\theta_{n}$, maximise the lower bound $\mathcal{F}(q(s), \theta_n)$ with respect to $q(s)$, equivalent to maximising the log likelihood (because the log likelihood is not dependent on $q(s)$ and we minimise the KL divergence):$$ q_{n+1} = \arg \max_q \mathcal{F}(q(s), \theta_n) = p(s|x, \theta_n) $$
2. **M-step (Maximisation)**: For fixed $q_{n+1}(s)$, maximise $\mathcal{F}(q_{n+1}(s), \theta)$ with respect to $\theta$, thereby maximising the free energy:
   $$ \theta_{n+1} = \arg \max_\theta \mathcal{F}(q_{n+1}(s), \theta) $$
   The objective function in M step becomes (we will show how we derive that from the original function):
$$
F(q(s), \theta) = \sum_s q(s) \log \left( p(x|s, \theta) p(s|\theta) \right) - \sum_s q(s) \log q(s)
$$
#### Different math form
- The formula below is easier to calculate for the M-step, and we show how it follows from the first formula we learned about. 
	- This is better because in the M step we fix $q$ and optimise the parameters, and the part after the minus sign is not dependent on the parameters at all (This second step is called the **entropy of $q(s)$**).  
		- the second term is the entropy of $q(s)$, independent of $\theta$, so the M step is

$$
\theta_t = \arg max_{\theta} \sum_s q_t(s) \log \left( p(x|s, \theta)p(s|\theta) \right).
$$

	- Furthermore $p(s|\theta) = \pi_k$ is given by our model, the a priori probability of coming of each of our clusters.  
	- Additionally $p(\mathbf{x}|s,\theta)$ is just the gaussian distribution $\mathcal{N}(x_i,\mu_k, \Sigma_k)$, we can basically just plug in the model inside the first log. 
$$\mathcal{F}(q(s),\theta) = \sum_s q(s) \log (p(\mathbf{x}|s,\theta)p(s|\theta)) - \sum_s q(s) \log q(s),$$
(Applied the product rule inside the logarithm: 
$$= \sum_s q(s) \log p(\mathbf{x},s|\theta) - \sum_s q(s) \log q(s)$$
(Applied the product rule again: $p(\mathbf{x},s|\theta) = p(\mathbf{x}|\theta)p(s|\mathbf{x},\theta)$ by the definition of conditional probability)
$$= \sum_s q(s) \log [p(\mathbf{x}|\theta)p(s|\mathbf{x},\theta)] - \sum_s q(s) \log q(s)$$
(Factored out $\log p(\mathbf{x}|\theta)$ from the first sum as it doesn't depend on $s$, and rearranged terms)
$$= \left(\sum_s q(s)\right) \log p(\mathbf{x}|\theta) + \sum_s q(s) \log\left[\frac{p(s|\mathbf{x},\theta)}{q(s)}\right]$$
($\sum_s q(s) = 1$ because $q(s)$ is a probability distribution over $s$, so it must sum to 1. The ratio is inverted to match KL divergence form)
$$\mathcal{F}(q(s),\theta) = \log p(\mathbf{x}|\theta) - KL\left(q(s) \parallel p(s|\mathbf{x},\theta)\right)$$
The final step recognises the KL divergence formula: $KL(P\parallel Q) = \sum_x P(x) \log\frac{P(x)}{Q(x)}$. 


