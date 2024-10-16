---
link: https://en.wikipedia.org/wiki/Leibniz_integral_rule
---
## Feynman's Trick (Differentiation Under the Integral Sign)

Feynman's trick allows complex integrals to be simplified by introducing a parameter and differentiating the integral with respect to that parameter.

## Leibniz's Integral Rule
Leibniz's rule formalises when you can interchange differentiation and integration:

$$
\frac{d}{d\theta} \int_{a}^{b} f(x, \theta) \, dx = \int_{a}^{b} \frac{\partial f(x, \theta)}{\partial \theta} \, dx
$$

### Conditions for Use

1. **Continuity**: $f(x, \theta)$ is continuous in both $x$ and $\theta$ over the domain.
2. **Partial Derivative**: $\frac{\partial f(x, \theta)}{\partial \theta}$ exists and is continuous.
3. **Integrability**: The integral $\int_{a}^{b} \frac{\partial f(x, \theta)}{\partial \theta} \, dx$ must converge.
4. **Constant Limits**: $a$ and $b$ are constants. 
	- If they depend on $\theta$, apply:
	  $$
   \frac{d}{d\theta} \int_{a(\theta)}^{b(\theta)} f(x, \theta) \, dx = f(b(\theta), \theta) \frac{db}{d\theta} - f(a(\theta), \theta) \frac{da}{d\theta} + \int_{a(\theta)}^{b(\theta)} \frac{\partial f(x, \theta)}{\partial \theta} \, dx
   $$

### When It Fails

- **Discontinuities** in $f(x, \theta)$ or $\frac{\partial f(x, \theta)}{\partial \theta}$. can prevent the rule from applying, particularly in models involving non-smooth activation functions.
- **Non-integrable** partial derivatives, which can occur in complex probabilistic models, make the rule inapplicable.
- **Singularities** at the endpoints of integrals can also break the conditions required for Leibniz's rule.

## Videos
You can also just introduce a variable so you can do a partial derivative over it:
![](https://www.youtube.com/watch?v=YO38MCdj-GM)