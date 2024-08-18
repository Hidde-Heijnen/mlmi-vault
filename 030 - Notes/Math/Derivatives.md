## Derivative Rules

### Power Rule

$\frac{d}{dx}(x^n) = nx^{n-1}$

#### Examples

- $\frac{d}{dx}(x^2) = 2x$

### Constant Rule



$\frac{d}{dx}(c) = 0$

#### Examples

- $\frac{d}{dx}(5) = 0$

### Sum Rule

$\frac{d}{dx}(f(x) + g(x)) = \frac{d}{dx}(f(x)) + \frac{d}{dx}(g(x))$

#### Examples

- $\frac{d}{dx}(3x^2 + 2x) = 6x + 2$

### Product Rule

$\frac{d}{dx}(f(x)g(x)) = f'(x)g(x) + f(x)g'(x)$

#### Examples

- $\frac{d}{dx}(x^2 \cdot x) = 2x \cdot x + x^2 \cdot 1 = 3x^2$

### Quotient Rule

$\frac{d}{dx}\left(\frac{f(x)}{g(x)}\right) = \frac{f'(x)g(x) - f(x)g'(x)}{g(x)^2}$

#### Examples

- $\frac{d}{dx}\left(\frac{x^2}{x}\right) = \frac{2x \cdot x - x^2 \cdot 1}{x^2} = 1$

### Chain Rule

$\frac{d}{dx}(f(g(x))) = f'(g(x)) \cdot g'(x)$

#### Examples

- $\frac{d}{dx}(\sin(x^2)) = \cos(x^2) \cdot 2x$

### Exponential Rule

$\frac{d}{dx}(e^x) = e^x$

#### Examples

- $\frac{d}{dx}(e^{2x}) = 2e^{2x}$

### Logarithmic Rule

$\frac{d}{dx}(\ln(x)) = \frac{1}{x}$

#### Examples

- $\frac{d}{dx}(\ln(x^2)) = \frac{2}{x}$

### Trigonometric Functions Rule

$\frac{d}{dx}(\sin(x)) = \cos(x)$

$\frac{d}{dx}(\cos(x)) = -\sin(x)$

$\frac{d}{dx}(\tan(x)) = \sec^2(x)$

#### Examples

- $\frac{d}{dx}(\sin(x^2)) = \cos(x^2) \cdot 2x$
- $\frac{d}{dx}(\cos(x^3)) = -\sin(x^3) \cdot 3x^2$
- $\frac{d}{dx}(\tan(x)) = \sec^2(x)$

### Inverse Trigonometric Functions Rule

$\frac{d}{dx}(\sin^{-1}(x)) = \frac{1}{\sqrt{1-x^2}}$

$\frac{d}{dx}(\cos^{-1}(x)) = -\frac{1}{\sqrt{1-x^2}}$

$\frac{d}{dx}(\tan^{-1}(x)) = \frac{1}{1+x^2}$

#### Examples

- $\frac{d}{dx}(\sin^{-1}(x)) = \frac{1}{\sqrt{1-x^2}}$
- $\frac{d}{dx}(\cos^{-1}(2x)) = -\frac{2}{\sqrt{1-(2x)^2}} = -\frac{2}{\sqrt{1-4x^2}}$
- $\frac{d}{dx}(\tan^{-1}(x^2)) = \frac{2x}{1+x^4}$

### General Exponential Rule

$\frac{d}{dx}(a^x) = a^x \ln(a)$

#### Examples

- $\frac{d}{dx}(2^x) = 2^x \ln(2)$
- $\frac{d}{dx}(3^{2x}) = 3^{2x} \cdot 2 \ln(3)$

### General Logarithmic Rule

$\frac{d}{dx}(\log_a(x)) = \frac{1}{x \ln(a)}$

#### Examples

- $\frac{d}{dx}(\log_2(x)) = \frac{1}{x \ln(2)}$
- $\frac{d}{dx}(\log_3(x^2)) = \frac{2}{x \ln(3)}$

### Constant Multiple Rule

$\frac{d}{dx}(cf(x)) = c \frac{d}{dx}(f(x))$

#### Examples

- $\frac{d}{dx}(5x^3) = 5 \cdot 3x^2 = 15x^2$

## Partial derivative
**Just remember to treat all other variables as if they are constants.**

Partial derivatives are used specifically for functions of multiple variables when you are interested in the rate of change of the function with respect to one of the variables, while keeping the other variables constant. You can think of it as a slice of the function. In general, when dealing with functions of multiple variables, the appropriate tool to use is the partial derivative.

In multivariable calculus, partial derivatives are used to find local maxima, minima, and saddle points of functions of several variables using methods such as the gradient and Hessian matrix.
