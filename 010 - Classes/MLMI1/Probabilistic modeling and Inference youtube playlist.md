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