We call a model "linear regression" when it is **linear in the parameters**, even if it involves non-linear transformations of the data. This means that the **parameters** appear in a way that directly scales the output, without being multiplied by each other or raised to powers.

To be **linear in parameters** means that for each parameter $w_j$, the output $y(\mathbf{x}, \mathbf{w})$ changes proportionally to $w_j$. So, increasing a parameter results in a proportional increase (or decrease) in the output, without involving combinations of parameters like $w_1w_2$ or $w_1^2$.

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
Contrast this with a model that is **non-linear in parameters**, such as a polynomial model where the parameters are squared or multiplied together:

$$
y(\mathbf{x}, \mathbf{w}) = w_0 + w_1^2 x_1 + w_2 w_3 x_2
$$

Here, the output depends on products and powers of the parameters $w_1, w_2, w_3$, making the model **non-linear in parameters**, even though it might still be linear in the data $\mathbf{x}$.
