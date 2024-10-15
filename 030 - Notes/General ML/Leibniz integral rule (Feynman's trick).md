---
link: https://en.wikipedia.org/wiki/Leibniz_integral_rule
---
## Feynman's Trick (Differentiation Under the Integral Sign)

Feynman's trick allows complex integrals to be simplified by introducing a parameter and differentiating the integral with respect to that parameter.

### Leibniz's Integral Rule

Leibniz's rule formalises when you can interchange differentiation and integration:

$$
\frac{d}{d\theta} \int_{a}^{b} f(x, \theta) \, dx = \int_{a}^{b} \frac{\partial f(x, \theta)}{\partial \theta} \, dx
$$

### Conditions for Use

1. **Continuity**: $f(x, \theta)$ is continuous in both $x$ and $\theta$ over the domain.
2. **Partial Derivative**: $\frac{\partial f(x, \theta)}{\partial \theta}$ exists and is continuous.
3. **Integrability**: The integral $\int_{a}^{b} \frac{\partial f(x, \theta)}{\partial \theta} \, dx$ must converge.
4. **Constant Limits**: $a$ and $b$ are constants. If they depend on $\theta$, apply:
   $$
   \frac{d}{d\theta} \int_{a(\theta)}^{b(\theta)} f(x, \theta) \, dx = f(b(\theta), \theta) \frac{db}{d\theta} - f(a(\theta), \theta) \frac{da}{d\theta} + \int_{a(\theta)}^{b(\theta)} \frac{\partial f(x, \theta)}{\partial \theta} \, dx
   $$

### When It Fails

- **Discontinuities** in $f(x, \theta)$ or $\frac{\partial f(x, \theta)}{\partial \theta}$.
- **Non-integrable** partial derivatives.
- **Variable limits** not accounted for correctly.
- **Singularities** at the endpoints.

### Practical Guidelines

- Ensure continuity and integrability before applying the rule.
- Adjust for variable limits where necessary.
- Validate the final result, comparing with known solutions.

### Example Use Case

For integrals like $ \int_{0}^{\infty} e^{-ax} \, dx$, differentiating with respect to $a$ simplifies the problem.

### Example to Avoid

If $f(x, \theta)$ is discontinuous or its derivative is non-convergent, the rule may not apply.


## Videos
![](https://www.youtube.com/watch?v=YO38MCdj-GM)