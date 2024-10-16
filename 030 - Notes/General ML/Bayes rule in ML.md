$$ p(\theta | \mathcal{D}) =
 \frac{p(\mathcal{D} | \theta)p(\theta)}
 {\int p(\mathcal{D} | \theta)p(\theta)d\theta} $$
- $\theta$: our model parameters
- $\mathcal{D}$: our data
- $p(\mathcal{D}|\theta)$
	- **Likelihood**: How much **evidence** is there in the data for a specific parameter set
- $p(\theta)$
	- **Prior**: What are my beliefs of the parameters before seeing the data
- $p(\theta|\mathcal{D})$
	- **Posterior**: What is my **updated** belief of the parameters after having seen data
- $\int p(\mathcal{D} | \theta)p(\theta)d\theta = p(\mathcal{D})$
	- **Evidence**: What is my belief about the data over all the different parameters sets
	- Consists of integrating over two parts
		- $p(\mathcal{D} | \theta)$: Just our likelihood again
		- $p(\theta)d\theta$: You can think of $d\theta$ as an infinitely small part of theta, and then balances it with the probability of that theta. So theta's that are very probable become really big and things that are not likely become small. 
		- The integral sums over all possible parameter values, effectively averaging the likelihood across the parameter space weighted by the prior.
			- The marginal likelihood inherently penalises this because the integration over parameters averages out over the prior

We often use the evidence to compare models, downsides of this is that it is heavily dependent on the prior that we pick, even if the prior doesn't impact our posterior that much. 

## Adding our model
The above definition is a simplified version of the bayes rule, in reality every one of these probabilities is dependant on the structure of our model. 

$$ p(\theta | \mathcal{D}, M) =
 \frac{p(\mathcal{D} | \theta, M)p(\theta | M)}
 {\int p(\mathcal{D} | \theta, M)p(\theta | M)d\theta} $$
