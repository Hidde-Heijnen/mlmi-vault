## **Understanding Marginal Likelihood**
The marginal likelihood of a model $M$ given data $D$ is defined as:

$$
P(D \mid M) = \int P(D \mid \theta, M) P(\theta \mid M) \, d\theta
$$

- $P(D \mid \theta, M)$: The likelihood of the data given parameters $\theta$ and model $M$.
- $P(\theta \mid M)$: The prior distribution of the parameters within model $M$.
- The integral sums over all possible parameter values, effectively averaging the likelihood across the parameter space weighted by the prior.
### **Model Comparison Using Marginal Likelihood**
---
When comparing different models, the marginal likelihood serves as a natural criterion because it balances model fit and complexity:

- **Model Fit**: Models that explain the data well will have higher likelihood values.
- **Model Complexity**: Models with more parameters or flexible structures can overfit the data. The marginal likelihood inherently penalises this because the integration over parameters averages out over the prior, favouring models that achieve good fit without unnecessary complexity.

By computing $P(D \mid M_1)$ and $P(D \mid M_2)$ for models $M_1$ and $M_2$, you can compare the models based on their evidence:

### **Bayes Factor**: 
 $$\frac{P(D \mid M_1)}{P(D \mid M_2)} = $$

The ratio provides a quantitative measure of the support for one model over another.

## **Comparing Different Model Structures vs. Parameter Sets**
---
- **Different Model Structures**: Using marginal likelihood is most meaningful when the models have different structures—for example, different numbers of parameters, different functional forms, or different underlying assumptions. The marginal likelihood accounts for both how well each model fits the data and their respective complexities.

- **Different Parameter Sets Within the Same Model**: If you're comparing different parameter values or estimates within the same model structure, the marginal likelihood is less informative. Since the marginal likelihood integrates over the parameter space, it does not provide a way to compare specific parameter sets directly. In this case, you might focus on the **posterior distribution** of the parameters or use criteria like the **maximum a posteriori (MAP)** estimate.

## **Practical Considerations and downsides**

- **Computational Complexity**: Calculating the marginal likelihood can be computationally intensive, especially for complex models (because of the integral). Techniques like **Bayesian Information Criterion (BIC)** or **Approximate Bayesian Computation (ABC)** can provide approximations.
- **Choice of Priors**: The marginal likelihood is sensitive to the choice of prior distributions. Informative priors can significantly influence the evidence, so it's important to choose priors carefully.
- **Preference for Simpler Models:** The inherent penalty for complexity can sometimes lead to favouring overly simplistic models that underfit the data.

## Videos
![](https://www.youtube.com/watch?v=T-kMpA4z-7k)