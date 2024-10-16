$$p(\mathbf{z}_* | \mathbf{z}, \mathbf{x}_*, \mathbf{X}, \theta) = \int p(\mathbf{z}_* | \mathbf{x}_*, \mathbf{w}, \theta) p(\mathbf{w} | \mathbf{z}, \mathbf{X}, \theta) d\mathbf{w}$$

- we do not really care about the value of $\mathbf{w}$, we care about the new prediction $\mathbf{z}_*$ at location $\mathbf{x}_*$
- look at the marginal distribution, i.e. when we average out the latent variables or parameters
