## Introduction
Inference is estimating unobserved variables from observed data. The purpose of inference is to make a decision, and in these cases how certain you are is even more critical. We will introduce probabilistic modelling and probabilistic inference for making these inferences.

#### Flavours of ML
The machine experiences a series of sensory inputs: $x_1, x_2, x_3, x_4, \dots$

- **Supervised Learning**:
	- Also given correct outputs $y_1, y_2, \dots$
	- Its goal is to learn to **produce the correct output given a new input**.
	  - Regression
	  - Classification: same as a regression problem, but the outputs discrete instead of real. 
		  - You have $k$ classes with decisions boundaries 
- **Unsupervised Learning**:
	- No label or outputs given, just data
	- The goal is to **build a model of** $x$ that can be used for prediction.
		- Clustering: seeing what similar features similar data has. 
		- Dimensionality Reduction: Summarise more complex things by the position on the manifold. Or as a preprocessing/feature learning: reducing computational complexity improving statistical efficiency. 
- **Reinforcement Learning**:
	- The machine can also produce actions $a_1, a_2, \dots$, which affect the state of the world, and receives rewards (or punishments) $r_1, r_2, \dots$
	- Its goal is to **learn to act in a way that maximises rewards in the long term**.$$\text{Actions: } a_1, a_2, \dots \quad \text{Rewards: } r_1, r_2, \dots$$

## Probabilistic approach
 $p(\cdot)$ will be used to denote the probability density functions (discrete values) and $P(\cdot)$ will be used to denote probability mass functions (continuous random variables, distributions etc).
### Probabilistic Inference
Two key ideas for probabilistic inference:
1. The solution is a probability distribution over all possible settings of unknown variables, given observed data.
2. Use the sum and product rules to compute the solution.

**Sum rule**: $P(y) = \int p(y, z) \, dz$  or $p(y) = \sum_{z} P(y,z)$
**Product rule**: $p(y, z) = p(z)p(y|z) = p(y)p(z|y)$
**Bayes' rule**: $p(y|z) = \frac{p(y)p(z|y)}{p(z)}$  
	- **Posterior distribution** $p(y|z)$: what we know after seeing the data.
	- **Prior distribution** $p(y)$: what we knew before seeing the data.
	- **Likelihood** $p(z|y)$: what the data told us.
	Sometimes written as $p(y|z) \propto p(y)p(z|y)$ when $p(z)$ normalises. undefined for $p(z)=0$
	


