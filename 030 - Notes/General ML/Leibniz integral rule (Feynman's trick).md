---
link: https://en.wikipedia.org/wiki/Leibniz_integral_rule
---
**Feynman's Trick (Differentiation Under the Integral Sign)**

Feynman's trick, also known as differentiating under the integral sign, is a technique that allows you to compute complex integrals by introducing a parameter and differentiating the integral with respect to that parameter. This method can simplify the integral or make it solvable when it might not be otherwise.

**Leibniz's Integral Rule**

Leibniz's integral rule formalises the conditions under which you can interchange differentiation and integration. It provides the foundation for differentiating under the integral sign.

---
## **When You Can Use It**

To safely differentiate under the integral sign, the following conditions must be met:

1. **Continuity of the Function $f(x, \theta)$:**
   - The function $f(x, \theta)$ must be continuous with respect to both the variable of integration $x$ and the parameter $\theta$ over the domain of integration.
2. **Existence and Continuity of Partial Derivative $\frac{\partial f}{\partial \theta}$:**
   - The partial derivative $\frac{\partial f(x, \theta)}{\partial \theta}$ must exist and be continuous with respect to $x$ and $\theta$ over the domain.
3. **Integrability of the Partial Derivative:**
   - The integral of the partial derivative $\int_{a}^{b} \frac{\partial f(x, \theta)}{\partial \theta} \, dx$ must exist (i.e., it must converge).
4. **Independent Limits of Integration:**
   - The limits of integration $a$ and $b$ are constants and do not depend on the parameter $\theta$. If they do depend on $\theta$, additional terms involving the derivatives of the limits must be included.

---
## **Mathematical Expression**
Under the above conditions, Leibniz's integral rule states:

$$
\frac{d}{d\theta} \int_{a}^{b} f(x, \theta) \, dx = \int_{a}^{b} \frac{\partial f(x, \theta)}{\partial \theta} \, dx
$$
---

##  **Variable Limits Depending on $\theta$:**
   - When the limits of integration are functions of $\theta$, you need to modify the differentiation accordingly:
   $$
     \frac{d}{d\theta} \int_{a(\theta)}^{b(\theta)} f(x, \theta) \, dx = f(b(\theta), \theta) \frac{db}{d\theta} - f(a(\theta), \theta) \frac{da}{d\theta} + \int_{a(\theta)}^{b(\theta)} \frac{\partial f(x, \theta)}{\partial \theta} \, dx
     $$

 - If $f(x, \theta)$ or its derivative is not well-behaved at the variable limits, the rule may fail.
- If there are other parameters in the function that affect its continuity or integrability, ensure they also meet the necessary conditions.

---
### **Examples When It's Appropriate**

- **Evaluating Parameter-Dependent Integrals:**

  - Integrals like $\int_{0}^{\infty} e^{-ax} \, dx$, where $a$ is a parameter, can be differentiated with respect to $a$ to find related integrals.

- **Solving Difficult Integrals:**

  - When direct integration is complex, introducing a parameter and differentiating under the integral sign can simplify the problem.

---

### **Examples When to Avoid It**

- **Discontinuous Functions:**

  - If $f(x, \theta)$ has a jump discontinuity or is undefined at points within the integration range.

- **Non-Convergent Integrals:**

  - If integrating $\frac{\partial f}{\partial \theta}$ leads to divergence, the technique fails.

---

**Conclusion**

You can use Feynman's trick or Leibniz's integral rule when:

- The function and its partial derivative are continuous over the domain.
- The partial derivative is integrable over the domain.
- The limits of integration are constants (or you correctly account for variable limits).

Avoid using it when these conditions are not met, as it may lead to incorrect results or unsolvable integrals.

## Videos
![](https://www.youtube.com/watch?v=YO38MCdj-GM)