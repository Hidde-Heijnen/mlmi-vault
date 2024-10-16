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
- $\int p(\mathcal{D} | \theta)p(\theta)d\theta) = p(\mathcal{D})$
	- **Evidence**: What is my belief about the data over all the different parameters sets
