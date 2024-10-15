
## **Linearity of Integration**
- **Single Variable**: $\int [a \cdot f(x) \pm b \cdot g(x)]\,dx = a \int f(x)\,dx \pm b \int g(x)\,dx$
- **Multivariable**: $\int [a \cdot f(\mathbf{x}) \pm b \cdot g(\mathbf{x})]\,d\mathbf{x} = a \int f(\mathbf{x})\,d\mathbf{x} \pm b \int g(\mathbf{x})\,d\mathbf{x}$

---
## **Constants Factoring**
- **Single Variable**: $\int a \cdot f(x)\,dx = a \int f(x)\,dx$
- **Multivariable**: $\int a \cdot f(\mathbf{x})\,d\mathbf{x} = a \int f(\mathbf{x})\,d\mathbf{x}$

---

## **Splitting the Integral**
- **Single Variable**: If $c$ is between $a$ and $b$: 
$$ \int_a^b f(x)\,dx = \int_a^c f(x)\,dx + \int_c^b f(x)\,dx $$
- **Multivariable**: For disjoint regions $D_1$ and $D_2$: 
$$ \int_{D_1 \cup D_2} f(\mathbf{x})\,d\mathbf{x} = \int_{D_1} f(\mathbf{x})\,d\mathbf{x} + \int_{D_2} f(\mathbf{x})\,d\mathbf{x} $$

---

#### 4. **Differentiation Under the Integral Sign**
- **Single Variable**: If $f(x, y)$ and $\partial f/\partial y$ are continuous:
$$ \frac{d}{dy} \left( \int_a^b f(x, y)\,dx \right) = \int_a^b \frac{\partial f(x, y)}{\partial y}\,dx $$
- **Multivariable**: If $f(\mathbf{x}, y)$ and $\partial f/\partial y$ are continuous:
$$ \frac{d}{dy} \left( \int_D f(\mathbf{x}, y)\,d\mathbf{x} \right) = \int_D \frac{\partial f(\mathbf{x}, y)}{\partial y}\,d\mathbf{x} $$

---

#### 5. **Change of Variables**
- **Single Variable**: For $u = g(x)$:
$$ \int f(x)\,dx = \int f(g^{-1}(u)) \cdot \frac{du}{dx}\,du $$
- **Multivariable**: For $\mathbf{u} = \mathbf{g}(\mathbf{x})$:
$$ \int_D f(\mathbf{x})\,d\mathbf{x} = \int_{D'} f(\mathbf{g}^{-1}(\mathbf{u})) \left| \det \left( \frac{\partial \mathbf{x}}{\partial \mathbf{u}} \right) \right| d\mathbf{u} $$

---

#### 6. **Fubini's Theorem (Interchanging Order of Integration)**
If $f(x, y)$ is continuous over $[a, b] \times [c, d]$:
$$ \int_a^b \left( \int_c^d f(x, y)\,dy \right) dx = \int_c^d \left( \int_a^b f(x, y)\,dx \right) dy $$

---

#### 7. **Integration by Parts**
- **Single Variable**: $\int u(x)\,dv(x) = u(x) \cdot v(x) - \int v(x)\,du(x)$
- **Multivariable (Vector Fields)**: $\int_D (\nabla \cdot \mathbf{F})\,d\mathbf{x} = \int_{\partial D} \mathbf{F} \cdot d\mathbf{S}$

---

#### 8. **Fundamental Theorem of Calculus**
- **Single Variable**: $\frac{d}{dx} \left( \int_a^x f(t)\,dt \right) = f(x)$
- **Multivariable (Gradient Theorem)**: $\int_{\mathbf{a}}^{\mathbf{b}} \nabla f(\mathbf{x}) \cdot d\mathbf{x} = f(\mathbf{b}) - f(\mathbf{a})$

---

#### 9. **Interchanging Limit and Integration (Dominated Convergence)**
If $\{ f_n \}$ converges to $f$ and is dominated by an integrable function $g$:
$$ \lim_{n \to \infty} \int f_n(x)\,dx = \int \lim_{n \to \infty} f_n(x)\,dx = \int f(x)\,dx $$

---

#### 10. **Multiple Integrals over Product Domains**
If $f(\mathbf{x}, \mathbf{y}) = f_1(\mathbf{x}) \cdot f_2(\mathbf{y})$:
$$ \int_{D_x} \int_{D_y} f(\mathbf{x}, \mathbf{y})\,d\mathbf{y}\,d\mathbf{x} = \left( \int_{D_x} f_1(\mathbf{x})\,d\mathbf{x} \right) \left( \int_{D_y} f_2(\mathbf{y})\,d\mathbf{y} \right) $$

---

#### 11. **Probability Density Function (PDF) Properties**
- **Normalisation**: $\int_{-\infty}^{\infty} p(x)\,dx = 1$
- **Expectation**: $\mathbb{E}[X] = \int_{-\infty}^{\infty} x \cdot p(x)\,dx$

