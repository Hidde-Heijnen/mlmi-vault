## Bayesian decision theory
### Question
A data-scientist has computed a complex posterior distribution over a variable of interest, $x$, given observed data $y$, that is $p(x|y)$. They would like to return a point estimate of $x$ to their client. The client provides the data-scientist with a reward function $R(\hat{x},x)$ that indicates their satisfaction with a point estimate $\hat{x}$ when the true state of the variable is $x$.

  * Explain how to use _Bayesian Decision Theory_ to determine the optimal point estimate, $\hat{x}$.  
  * Compute the optimal point estimate $\hat{x}$ in the case when the reward function is the negative square error between the point estimate and the true value, $R(\hat{x},x) = -(\hat{x}-x)^2$. Comment on your result. 
  * Compute the optimal point estimate $\hat{x}$ in the case when the reward function is the negative absolute error between the point estimate and the true value, $R(\hat{x},x) = -|\hat{x}-x|$. Comment on your result.
### Answer
