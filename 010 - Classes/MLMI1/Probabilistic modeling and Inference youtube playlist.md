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
	- $x_n$ is the fixed varaible (the data), and $\lambda$ is the variable
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

**Step 4:** Use the definition of joint probability to express $p(x_n, s_n = k | \theta)$ as the product of the marginal and conditional probabilities:
$$= \sum_{n=1}^N \log \sum_{k=1}^K p(s_n = k | \theta) \, p(x_n | s_n = k, \theta)$$
*Explanation:* This separates the probability into the prior probability of belonging to component $k$ and the likelihood of observing $x_n$ given component $k$.

**Step 5:** Substitute the specific forms for $p(s_n = k | \theta)$ and $p(x_n | s_n = k, \theta)$:
$$= \sum_{n=1}^N \log \sum_{k=1}^K \pi_k \, \mathcal{N}(x_n; \mu_k, \sigma_k^2)$$
*Explanation:* Here, $\pi_k$ represents the mixing coefficients (priors for each component), and $\mathcal{N}(x_n; \mu_k, \sigma_k^2)$ is the Gaussian distribution for component $k$.

**Methods for Maximising the Likelihood:**

- **Method 1:** Direct gradient-based optimisation of the log-likelihood.
  - *Pros:* Generally faster convergence.
  - *Cons:* May be complex to implement due to the presence of sums inside logarithms.

- **Method 2:** Expectation-Maximization (EM) algorithm.
  - *Pros:* Simpler implementation for models with latent variables; widely used and extends to various generalizations.
  - *Cons:* Can be slower and may converge to local maxima.

**Notes:**
- **Direct Optimization** involves computing gradients of the log-likelihood with respect to $\theta$ and using optimization algorithms (e.g., gradient ascent).
- The **EM Algorithm** iteratively performs:
  1. **Expectation (E-step):** Compute the expected value of the latent variables given current parameters.
  2. **Maximization (M-step):** Update parameters to maximize the expected log-likelihood found in the E-step.

By understanding these steps, we can choose the appropriate method for maximizing the likelihood based on the problem's complexity and requirements.

(Given the data we’ve observed, which parameter value is most probable?)