## 1. **Probabilistic models for regression**
---
### Question
A machine learner observes two separate regression datasets comprising scalar inputs and outputs $\{ x_n, y_n \}_{n=1}^N$ shown below.  
![[CleanShot 2024-10-11 at 17.39.38.png]]   
  * Suggest a suitable regression model, $p(y_n|x_n)$ for the dataset A. Indicate sensible settings for the parameters in your proposed model where possible. Explain your modelling choices.  
  * Suggest a suitable regression model, $p(y_n|x_n)$ for the dataset B. Indicate sensible settings for the parameters in your proposed model where possible. Explain your modelling choices. 
### Answer
#### A
Linear trend with a rough gradient of approximately 5 and an intercept at $(0, 3)$. The noise appears Gaussian, but the standard deviation increases with $x$.

Thus, the suggested model is:
$$y_n(x) = 5x + \sigma(x)\epsilon_n$$
Where:
- $\epsilon_n \sim \mathcal{N}(0,1)$,
- $\sigma(x) = 1 \times x$ (standard deviation grows linearly with $x$).
#### B
Sinusoidal trend with a true period of roughly 25 time steps, and heavy-tailed noise (outliers).

The model is given by:

$$y_n(x) = 2 + \sin\left(\frac{2\pi}{25}x\right) + \epsilon_n$$

Where:
- The amplitude of the sinusoid is approximately 1.
- The mean is 2.
- $\epsilon_n \sim \text{Student-t}$, with:
  - mean 0,
  - variance approximately 1 (hard to specify),
  - degree of freedom parameter $\approx 2.1$ (accounts for heavy-tailed behaviour).

*Again, it's a good one to dismiss.*


## 2. **Maximum-likelihood learning for a simple regression model**
---
### Question
  Consider a regression problem where the data comprise $N$ scalar inputs and outputs, $\mathcal{D} = \{ (x_1, y_1), ..., (x_N,y_N)\}$, and the goal is to predict $y$ from $x$. 
    
  Assume a very simple linear model, $y_n = a x_n + \epsilon_n$, where the noise $\epsilon_n$ is iid Gaussian with zero mean and variance 1.

  * Provide an expression for the log-likelihood of the parameter $a$. 
  * Compute the maximum likelihood estimate for $a$. 

### Answer

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