---
aliases:
  - MLMI playlist summary
link: https://www.youtube.com/playlist?list=PLyXv258Xt2PRhkou67NwiQD9OmiNMzdfa
---

**Inference problem**: A problem where you have to **estimate unknown variables** from **known variables** 
- Known variables are sometimes called **observed variables**
- unknown variables are sometimes called **unobserved (or latent/hidden) variables**

1. **"right answer" to any inference problem is a probability distribution**
		Instead of just returning a single point estimate of the unobserved variables of the model, you return how plausible that variable is with a distribution. So plausibility of unobserved variables given observed variables. $p(u|o)$
2. **plausibility computed using the sum and product rules of probability**
		**Sum rule**: $p(y) = \int p(y,z) dz$
			If you have a joint probability of y and z, and you want to compute just the probability of y, you have to sum out all of the z variables (for continious functions you need to integrate, for discrete values: $p(y) = \sum_{z} p(y,z)$)
			We call the $p(y)$ the **marginal probability** of y and $p(y,z)$ the **joint probability of y and z**
		**Product rule**: $p(y,z) = p(z)p(y|z) = p(y)p(z|y)$
		Using these two rules is the only way to perform consistent inferences. If we don't use these rules things like order will start to matter and our answer will be different. Cox(1946)
		**Bayes' rule**: $p(y|z) = \frac{p(y)p(z|y)}{p(z)}$ is derived from the product rule 
			$p(y)$ is the prior distribution, and it is what we knew before we see any data
			$p(z|y)$ is what the data tells us (likelihood of parameters)
			$p(y|z)$ is the plausibility after observing data (posterior)
			$p(z)$ is more of a normalizing constant
1.  