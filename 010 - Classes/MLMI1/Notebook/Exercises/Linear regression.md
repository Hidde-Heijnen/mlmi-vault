## 1. **Probabilistic models for regression**
---
### Question
A machine learner observes two separate regression datasets comprising scalar inputs and outputs $\{ x_n, y_n \}_{n=1}^N$ shown below.  
![[CleanShot 2024-10-11 at 17.39.38.png]]   
  * Suggest a suitable regression model, $p(y_n|x_n)$ for the dataset A. Indicate sensible settings for the parameters in your proposed model where possible. Explain your modelling choices.  
  * Suggest a suitable regression model, $p(y_n|x_n)$ for the dataset B. Indicate sensible settings for the parameters in your proposed model where possible. Explain your modelling choices. 
### Answer
> [!info] Goal
> This question teaches you how to build models that make sense, many people just say it's linear and don't account for the noise
#### A
Linear trend with a rough gradient of approximately 5 (draw a line for the mean, at $x=100$, $y=500$) and an intercept at $(0, 0)$. The noise appears Gaussian, but the standard deviation increases with $x$.

Thus, the suggested model is:
$$y_n(x) = 5x + \sigma(x)\epsilon_n$$
Where:
- $\epsilon_n \sim \mathcal{N}(0,1)$,
- $\sigma(x) = |x|$ (standard deviation grows linearly with $x$).
#### B
Sinusoidal trend with a true period of roughly 25 time steps, and heavy-tailed noise (outliers).

The model is given by:
$$y_n(x) = 2 + \sin\left(\frac{2\pi}{25}x\right) + \epsilon_n$$
Where:
- The amplitude of the sinusoid is approximately 1 (from 1 to 3).
- The mean is 2.
- $\epsilon_n \sim \text{Student-t}$, with:
  - mean 0,
  - variance approximately 1 (hard to specify),
  - degree of freedom parameter $\approx 2.1$ (accounts for heavy-tailed behaviour).
> [!info]- Sparse distributions 
> - **Heavy-Tailed Distributions**: Distributions like the Laplace have heavier tails compared to light-tailed distributions such as the Gaussian (normal) distribution.
> - **Data Characteristics**: Data often clusters tightly around the trend line but includes occasional large outliers due to the heavy tails.
> - **Kurtosis (Fourth Moment)**: The fourth moment, known as kurtosis (E[x⁴]), is sensitive to extreme values and helps identify the presence of heavy tails in a distribution.
## 2. **Maximum-likelihood learning for a simple regression model**
---
### Question
Consider a regression problem where the data comprise $N$ scalar inputs and outputs, $\mathcal{D} = \{ (x_1, y_1), ..., (x_N,y_N)\}$, and the goal is to predict $y$ from $x$. 
  
Assume a very simple linear model, $y_n = a x_n + \epsilon_n$, where the noise $\epsilon_n$ is iid Gaussian with zero mean and variance 1.
  * Provide an expression for the log-likelihood of the parameter $a$. 
  * Compute the maximum likelihood estimate for $a$. 

### Answer
#### A
$$ p\left( \left\{ y_n \right\}_{n=1}^N \mid a, \left\{ x_n \right\}_{n=1}^N \right) = \prod_{n=1}^N p\left( y_n \mid a, x_n \right) $$

Thus,
$$ \log p\left( \left\{ y_n \right\}_{n=1}^N \mid a, \left\{ x_n \right\}_{n=1}^N \right) = \sum_n \left[ -\frac{1}{2} \log 2\pi - \frac{1}{2} \left( y_n - a x_n \right)^2 \right] $$

$$ = -\frac{N}{2} \log 2\pi - \frac{1}{2} \sum_n \left( y_n - a x_n \right)^2 = \mathcal{L}(a) $$
#### B
$$ \frac{\partial \mathcal{L}(a)}{da} \Bigg|_{a_{ML}} = \sum_n x_n \left( y_n - a_{ML} x_n \right) = 0 $$

Thus,
$$ a_{\text{ML}} = \frac{\sum_n x_n y_n}{\sum_n x_n^2} $$

## 3. **Maximum-likelihood learning for multi-output regression** 
---
### Question

  A data-scientist has collected a regression dataset comprising $N$ scalar inputs ($\{x_n\}_{n=1}^N$) and $N$ scalar outputs ($\{y_n\}_{n=1}^N$). Their goal is to predict $y$ from $x$ and they have assumed a very simple linear model, $y_n = a x_n + \epsilon_n$.
  
  The data-scientist also has access to a second set of outputs ($\{z_n\}_{n=1}^N$) that are well described by the model $z_n = x_n + \epsilon'_n$.

  The noise variables $\epsilon_n$ and $\epsilon'_n$  are known to be iid zero mean correlated Gaussian variables
$$
  \begin{align}
p\left( \left[ \begin{array}{c} \epsilon_n\\ \epsilon'_n \end{array} \right ] \right) = \mathcal{N}\left( \left[ \begin{array}{c} \epsilon_n\\ \epsilon'_n \end{array} \right ]; \mathbf{0}, \Sigma \right)  \;\; \text{where} \;\; \; \Sigma^{-1} = \left[ \begin{array}{cc} 1 & 0.5 \\ 0.5 & 1 \end{array} \right ].  \nonumber
\end{align}
$$
  * Provide an expression for the log-likelihood of the parameter $a$. 
  * Compute the maximum likelihood estimate for $a$. 
  * Do the additional outputs $\{z_n\}_{n=1}^N$ provide useful additional information for estimating $a$? Explain your reasoning.

  The formula for the probability density of a multivariate Gaussian distribution of mean $\mu$ and covariance $\Sigma$ is given by
  $$
\begin{align}
\mathcal{N}(\mathbf{x};\mu,\Sigma) = \frac{1}{\sqrt{\text{det}(2 \pi \Sigma)}} \exp\left(-\frac{1}{2} (\mathbf{x} - \mathbf{\mu})^{\top} \Sigma^{-1}  (\mathbf{x} - \mathbf{\mu})\right). \nonumber
\end{align}
$$
### Answer
#### A
$$
\mathcal{L}(a) = \log p\left( \left\{ y_n \right\}_{n=1}^N, \left\{ z_n \right\}_{n=1}^N \mid \left\{ x_n \right\}_{n=1}^N, a \right) = \sum_{n=1}^N \log p\left( y_n, z_n \mid x_n, a \right)
$$

where

$$
p\left( y_n, z_n \mid a, x_n \right) = \mathcal{N} \left( \begin{bmatrix} y_n \\ z_n \end{bmatrix}; \begin{bmatrix} a x_n \\ x_n \end{bmatrix}, \Sigma = \begin{bmatrix} 1 & \tfrac{1}{2} \\ \tfrac{1}{2} & 1 \end{bmatrix}^{-1} \right)
$$

Thus,

$$
\mathcal{L}(a) = \sum_{n=1}^N -\tfrac{1}{2} \left( \begin{bmatrix} y_n \\ z_n \end{bmatrix} - \begin{bmatrix} a x_n \\ x_n \end{bmatrix} \right)^{\!\top} \begin{bmatrix} 1 & \tfrac{1}{2} \\ \tfrac{1}{2} & 1 \end{bmatrix} \left( \begin{bmatrix} y_n \\ z_n \end{bmatrix} - \begin{bmatrix} a x_n \\ x_n \end{bmatrix} \right) - \tfrac{N}{2} \log \left( \det(2\pi \Sigma) \right)
$$

simplifying, we get:

$$
\mathcal{L}(a) = -\tfrac{1}{2} \sum_{n=1}^N \left[ \left( y_n - a x_n \right)^2 + \left( y_n - a x_n \right)\left( z_n - x_n \right) + \left( z_n - x_n \right)^2 \right] - \tfrac{N}{2} \log \left( \det(2\pi \Sigma) \right)
$$

#### B
b)
$$ \frac{d \mathcal{L}(a)}{da} = \sum_n \left( y_n - a x_n \right) x_n + \frac{1}{2} \sum_n \left( z_n - x_n \right) x_n = 0 $$

$$ = \sum_n y_n x_n + \frac{1}{2} \sum_n z_n x_n - \frac{1}{2} \sum_n x_n^2 - a \sum_n x_n^2 $$

Thus,
$$ a = \frac{\left( \sum_n y_n x_n + \frac{1}{2} \sum_n z_n x_n \right)}{\sum_n x_n^2} \quad (\text{maximum likelihood estimate}) $$
#### C
The additional outputs change the maximum likelihood estimate of $a$. This means that they must provide useful information about $a$. They do this because the noise in $z_n$ is correlated with the noise in $y_n$, and so observing $z_n$ reveals information about the noise $\epsilon_n$ and allows more accurate identification of $a$.
