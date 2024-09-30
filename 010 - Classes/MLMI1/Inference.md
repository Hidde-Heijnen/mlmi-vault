## Introduction
Inference is estimating unobserved variables from observed data. The purpose of inference is to make a decision, and in these cases how certain you are is even more critical. We will introduce probabilistic modelling and probabilistic inference for making these inferences.

#### Flavours of ML
The machine experiences a series of sensory inputs: $x_1, x_2, x_3, x_4, \dots$

- **Supervised Learning**:
  - The machine is also given the desired outputs $y_1, y_2, \dots$
  - Its goal is to learn to **produce the correct output given a new input**.$$\text{Input: } x_1, x_2, \dots \quad \text{Output: } y_1, y_2, \dots$$
	  - Regression: computer vision, weather, demand forecasting etc
	  - Classification: exactly the same as a regression problem, but the outputs are now discrete valued instead of real valued. You have $k$ classes with decisions boundaries 
- **Unsupervised Learning**:
  - The goal of the machine is to **build a model of** $x$ that can be used for reasoning, decision making, predicting things, communicating, etc.
$$\text{Model: } f(x_1, x_2, \dots) \quad \text{No labels or outputs provided.}$$
	  - Clustering (like spam filtering, network community detection, image segmentation): seeing what similar features similar data has. 
	  - Dimensionality Reduction: Summarize more complex things by the position on the manifold. Or as a preprocessing/feature learning: reducing computational complexity imporoving statistical efficiency. 
- **Reinforcement Learning**:
  - The machine can also produce actions $a_1, a_2, \dots$, which affect the state of the world, and receives rewards (or punishments) $r_1, r_2, \dots$
  - Its goal is to **learn to act in a way that maximizes rewards in the long term**.$$\text{Actions: } a_1, a_2, \dots \quad \text{Rewards: } r_1, r_2, \dots$$



