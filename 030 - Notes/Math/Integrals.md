## Polynomials
$\int x^n \, dx = \frac{x^{n+1}}{n+1} + C$

## Radicals
$\int \sqrt[m]{x^n} \, dx = \int x^{\frac{n}{m}} \, dx$

$= \frac{x^{\frac{n}{m}+1}}{\frac{n}{m} + 1} + C$

## Trigonometric functions
$\int \sin(x) \, dx = -\cos(x) + C$

$\int \cos(x) \, dx = \sin(x) + C$

$\int \tan(x) \, dx = -\ln|\cos(x)| + C$

$\int \tan(x) \, dx = \ln|\sec(x)| + C$

$\int \sec^2(x) \, dx = \tan(x) + C$

$\int \csc^2(x) \, dx = -\cot(x) + C$

$\int \sec(x) \tan(x) \, dx = \sec(x) + C$

$\int \csc(x) \cot(x) \, dx = -\csc(x) + C$

## Exponential functions
$\int e^x \, dx = e^x + C$

$\int a^x \, dx = \frac{a^x}{\ln(a)} + C$

## Integrals that are logarithmic functions
$\int \frac{1}{x} \, dx = \ln|x| + C$

Simplifying a $ln$ using the arbitrary constant. For any constant $C$ we can always write $C = ln K$ where $K$ is some other constant. Then, using the laws of logarithms, we can write
$$
\int \frac{1}{x} \, dx = \ln{|x|} + C
$$
$$
= \ln{|x|} + \ln{K}
$$
$$
= \ln{(K|x|)}
$$


$\int \ln(x) \, dx = x \ln(x) - x + C$

## Integrals that are inverse trigonometric functions
$$ \int \frac{1}{\sqrt{a^2 - x^2}} dx = \arcsin \left(\frac{x}{a}\right) + C $$
$$ \int \frac{1}{a^2 + x^2} dx = \frac{1}{a} \arctan \left(\frac{x}{a}\right) + C $$
## U substitution  

### (ax+b)
By using the substitution \( u = ax + b \), it's straightforward to show that

$$
\int (ax + b)^n \, dx = \frac{1}{a(n+1)} (ax + b)^{n+1} + C, \quad n \neq -1.
$$




