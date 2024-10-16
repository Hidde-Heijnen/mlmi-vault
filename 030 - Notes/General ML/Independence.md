Often denoted as i.i.d. 

- **Likelihood**  
  $$p(y | \mathbf{x}, \mathbf{w}, \beta) = \mathcal{N}\left(y | \mathbf{w}^\top \mathbf{x}, \beta^{-1} \right)$$

- **Independence**  
  $$p(\mathbf{y} | \mathbf{X}, \mathbf{w}, \beta) = \prod_{n=1}^{N} \mathcal{N}\left( y_n | \mathbf{w}^\top \mathbf{x}_n, \beta^{-1} \right)$$

Assume each output to be independent given the input and the parameters. So if you give us an x, our model and our parameters (weights), the output will be the same regardless of our other inputs. And the order of the inputs will also not matter. 

Just assume it is independent, unless it is said not to (and then you probably get a covariance matrix or something where the top)
