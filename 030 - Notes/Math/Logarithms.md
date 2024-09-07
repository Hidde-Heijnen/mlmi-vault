### Logarithms:
- A **logarithm** is the inverse operation of exponentiation. The logarithm of a number $x$ with base $b$ is the exponent to which $b$ must be raised to obtain $x$:
  
  $$
  \log_b(x) = y \ \text{if and only if} \ b^y = x
  $$

  - $b$ is the **base**.
  - $x$ is the **argument**.
  - $y$ is the **logarithm** (or exponent).

### Common Logarithms:
- **Common logarithm**: $\log_{10}(x)$ (logarithm with base 10).
- **Natural logarithm**: $\ln(x)$ (logarithm with base $e$, where $e \approx 2.718$).

### Law of Logarithms:
1. **Product Rule**:
   - The logarithm of a product is the sum of the logarithms:

     $$
     \log_b(xy) = \log_b(x) + \log_b(y)
     $$

2. **Quotient Rule**:
   - The logarithm of a quotient is the difference of the logarithms:

     $$
     \log_b\left(\frac{x}{y}\right) = \log_b(x) - \log_b(y)
     $$

3. **Power Rule**:
   - The logarithm of a power is the exponent times the logarithm of the base:

     $$
     \log_b(x^n) = n \cdot \log_b(x)
     $$

4. **Change of Base Formula**:
   - To change the base of a logarithm:

     $$
     \log_b(x) = \frac{\log_c(x)}{\log_c(b)}
     $$

   - Commonly used to convert to natural logarithms or base 10 logarithms:

     $$
     \log_b(x) = \frac{\ln(x)}{\ln(b)} = \frac{\log_{10}(x)}{\log_{10}(b)}
     $$

### Special Logarithmic Values:
- $\log_b(1) = 0$ for any base $b$, since $b^0 = 1$.
- $\log_b(b) = 1$, since $b^1 = b$.

### Natural Logarithms:
- The **natural logarithm**, denoted $\ln(x)$, uses the base $e$ (Euler's number):
  
  $$
  \ln(x) = \log_e(x)
  $$

- **Properties**:
  - $\ln(e) = 1$ because $e^1 = e$.
  - $\ln(1) = 0$ because $e^0 = 1$.

### Exponential and Logarithmic Relationship:
- **Inverse property**: Exponentials and logarithms are inverses of each other.
  - $b^{\log_b(x)} = x$
  - $\log_b(b^x) = x$

### Solving Logarithmic Equations:
- To solve equations involving logarithms, use the laws of logarithms to combine terms and isolate the logarithmic expression. Then, exponentiate both sides to solve for the unknown.

### Graph of Logarithmic Functions:
- The graph of $y = \log_b(x)$ is a curve that:
  - Passes through $(1, 0)$ (since $\log_b(1) = 0$).
  - Is asymptotic to the y-axis (approaches negative infinity as $x$ approaches 0).
  - Increases as $x$ increases for $b > 1$.

### Applications of Logarithms:
- **Growth and decay**: Logarithms are used in modeling exponential growth (e.g., population growth) and decay (e.g., radioactive decay).
- **pH scale**: The pH scale in chemistry is a logarithmic scale, defined as $pH = -\log_{10}[\text{H}^+]$.
- **Richter scale**: Earthquake magnitude is measured logarithmically on the Richter scale.
