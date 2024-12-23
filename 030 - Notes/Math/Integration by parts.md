Integration by parts is a technique to evaluate integrals involving the product of functions, based on the product rule of differentiation.

---
## Formula

The integration by parts formula is:
$$
\int u \, dv = u v - \int v \, du
$$
- $u$: differentiable function of $x$
- $dv$: remaining part of the integrand
- $du$: derivative of $u$ ($du = u' \, dx$)
- $v$: integral of $dv$ ($v = \int dv$)

---
## Derivation (from the Product Rule)
The product rule for differentiation:
$$
\frac{d}{dx}[u(x) \cdot v(x)] = u(x) \cdot v'(x) + u'(x) \cdot v(x)
$$
Rewriting this:
$$
u(x) \cdot v'(x) = \frac{d}{dx}[u(x) \cdot v(x)] - u'(x) \cdot v(x)
$$
Integrating both sides:
$$
\int u \, dv = u v - \int v \, du
$$
---
## Steps for Integration by Parts
1. **Choose $u$ and $dv$:**
   - Pick $u$ such that its derivative simplifies the expression.
   - Let $dv$ be the remaining part of the integrand.

2. **Find $du$ and $v$:**
   - Differentiate $u$ to get $du$.
   - Integrate $dv$ to get $v$.

3. **Substitute in the Formula:**
   - Plug $u$, $v$, $du$, and $dv$ into the formula.

4. **Simplify and Integrate:**
   - Evaluate the remaining integral.

---
## Choosing $u$ and $dv$
A useful mnemonic: **LIATE** (in order of preference for $u$):
1. **L**ogarithmic ($\ln x$)
2. **I**nverse trigonometric ($\arctan x$)
3. **A**lgebraic ($x^2$)
4. **T**rigonometric ($\sin x$)
5. **E**xponential ($e^x$)

---
## Examples
### Example 1
Evaluate $\int x e^x \, dx$:

1. Choose $u = x$, $dv = e^x \, dx$.
2. Compute $du = dx$, $v = e^x$.
3. Apply the formula:
   $$
   \int x e^x \, dx = x e^x - \int e^x \, dx = x e^x - e^x + C
   $$
4. Simplify:
   $$
   = e^x (x - 1) + C
   $$
### Example 2 
Evaluate $\int \ln x \, dx$.

1. Choose $u = \ln x$, $dv = dx$.
2. Compute $du = \frac{1}{x} \, dx$, $v = x$.
3. Apply the formula:
   $$
   \int \ln x \, dx = x \ln x - \int 1 \, dx = x \ln x - x + C
   $$
### Example 3

Evaluate $\int e^x sin(x)dx$

1. Choose $u = \sin(x)$, $dv = e^xdx$
2. Compute $du = \cos(x)dx$, $v = e^x$
3. $\int e^x sin(x)dx = e^x\sin(x) - \int e^x\cos(x)dx$

Now we can do it again on the right part of the solution
4. Choose $u = \cos(x)$, $dv=e^xdx$
5. Compute $du = -\sin(x)dx$, $v=e^x$
6. $\int e^x sin(x)dx = e^x\sin(x) - e^x\cos(x) - \int e^x \sin(x)dx$
Now we can move this final integral from the right to the left and get
7. $2\int e^x sin(x)dx = e^x\sin(x) - e^x\cos(x)$
8. $\int e^x sin(x)dx = \frac{e^x\sin(x) - e^x\cos(x)}2 + C$

---
### Summary

Integration by parts simplifies the process of integrating products of functions by leveraging the product rule. Proper selection of $u$ and $dv$ is key, and sometimes multiple iterations are required.

## Videos
![](https://www.youtube.com/watch?v=sWSLLO3DS1I)