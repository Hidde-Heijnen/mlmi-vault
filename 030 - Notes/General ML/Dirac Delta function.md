---
link: https://en.wikipedia.org/wiki/Dirac_delta_function
---
### **Dirac Delta Function Overview**

- **Definition:** The Dirac delta function, denoted as $\delta(x)$, is a **generalised function** or **distribution**. It is zero everywhere except at $x = 0$, where it takes an infinitely large value such that:
  $$
  \int_{-\infty}^{\infty} \delta(x) \, dx = 1
  $$

- **Interpretation:** Represents an **idealised point mass** or **unit impulse**. In probability, it can be seen as a distribution with **zero variance**, concentrating all probability at one point.
- Make sure the delta function is within the integration limits, otherwise the integral is 0
### **Key Properties**

1. **Sifting Property**:
   $$
   \int_{-\infty}^{\infty} \delta(x - a) f(x) \, dx = f(a)
   $$
   This extracts the value of $f(x)$ at $x = a$.

2. **Scaling Property**:
   $$
   \delta(ax) = \frac{1}{|a|} \delta(x)
   $$
   where $a \neq 0$.

3. **Evenness**:
   $$
   \delta(x) = \delta(-x)
   $$
### **Integration with Dirac Delta**

- **Basic Integral:**
  $$
  \int_{-\infty}^{\infty} \delta(x) \, dx = 1
  $$

- **Sifting Property Applied:**
  $$
  \int_{-\infty}^{\infty} \delta(x - a) f(x) \, dx = f(a)
  $$
## Youtube videos
- https://www.youtube.com/watch?v=Y8y965ZAmQE