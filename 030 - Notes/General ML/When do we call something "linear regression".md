We call a model "linear regression" when it is **linear in the parameters**, even if it involves non-linear transformations of the data. This means that the **parameters** appear in a way that directly scales the output, without being multiplied by each other or raised to powers.

To be **linear in parameters** means that for each parameter $w_j$, the output $y(\mathbf{x}, \mathbf{w})$ changes proportionally to $w_j$. So, increasing a parameter results in a proportional increase (or decrease) in the output, without involving combinations of parameters like $w_1w_2$ or $w_1^2$.

if adjusting a parameter $w_j$ results in  a proportional change in the output $y$ without altering the influence of other parameters, the model is likely linear in parameters. 

## Linear Regression Example:
The basic form of linear regression is:

$$
y(\mathbf{x}, \mathbf{w}) = w_0 + w_1 x_1 + \dots + w_D x_D = \mathbf{w}^\top \mathbf{x} + w_0
$$

This is linear in the parameters $w_0, w_1, \dots, w_D$, but $\mathbf{x}$ can take any values, so the function may be non-linear in the **data**.

### Generalised Basis Function:
A more general model with a basis function $\boldsymbol{\phi}(\mathbf{x})$:

$$
y(\mathbf{x}, \mathbf{w}) = w_0 + \sum_{j=1}^{M-1} w_j \phi_j(\mathbf{x}) = \mathbf{w}^\top \boldsymbol{\phi}(\mathbf{x})
$$

Here, the model is still linear in the parameters $\mathbf{w}$, even though $\boldsymbol{\phi}(\mathbf{x})$ can apply non-linear transformations to the data $\mathbf{x}$.

## Non-linear Example (Not Linear in Parameters):
We refer to a model as non-linear regression when it is non-linear in the parameters. This means that the parameters appear in the model equation in non-linear ways, such as being multiplied together, raised to a power, or inside a non-linear function like an exponential or logarithm.:

$$
y(\mathbf{x}, \mathbf{w}) = w_0 + w_1^2 x_1 + w_2 w_3 x_2
$$

Here, the output depends on products and powers of the parameters $w_1, w_2, w_3$, making the model **non-linear in parameters**, even though it might still be linear in the data $\mathbf{x}$.

The term "linear regression" refers to the linearity in parameters, not the linearity in the data or the output graph. A linear regression model can produce curves, waves, or any non-linear shapes when plotted against the input data if the model includes non-linear transformations of the inputs (like polynomial terms), but the parameters themselves enter the model linearly.

## Why this is important
- We are trying to optimise the parameters of the model, so these being linear allow for closed-form solutions and efficient algorithms like the normal equations or least squares.
- Linear models are often easier to interpret because the effect of each parameter is straightforward.