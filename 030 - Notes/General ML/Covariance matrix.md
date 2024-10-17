A **covariance matrix** $\Sigma$ captures the covariances between multiple random variables, describing variability and linear relationships in multivariate statistics and machine learning.

### Matrix Representation
The covariance matrix $\Sigma$ for random variables $X_1, X_2, \dots, X_n$ is defined as:
$$
\Sigma = \begin{pmatrix}
\sigma_{11} & \sigma_{12} & \dots & \sigma_{1n} \\
\sigma_{21} & \sigma_{22} & \dots & \sigma_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
\sigma_{n1} & \sigma_{n2} & \dots & \sigma_{nn}
\end{pmatrix}
$$
where $\sigma_{ij} = \text{Cov}(X_i, X_j) = \mathbb{E}[(X_i - \mu_i)(X_j - \mu_j)]$, and $\mu_i = \mathbb{E}[X_i]$.

### Key Properties
- **Symmetry**: $\Sigma$ is symmetric ($\sigma_{ij} = \sigma_{ji}$), allowing for orthogonal diagonalisation $\Sigma = Q \Lambda Q^\top$ where $\Lambda$ contains real eigenvalues.
- **Positive Semi-Definiteness**: For any vector $\mathbf{z} \in \mathbb{R}^n$, $\mathbf{z}^\top \Sigma \mathbf{z} \geq 0$. Diagonal elements (variances) are non-negative, and all eigenvalues are non-negative.
- **Invertibility**: $\Sigma$ is invertible if full-rank (all eigenvalues positive). Its inverse, the precision matrix $\Sigma^{-1}$, encodes conditional independence among variables.

### Mathematical Considerations
- **Eigen Decomposition**: $\Sigma = Q \Lambda Q^\top$ expresses the variance captured by different components, crucial for dimensionality reduction.
- **Rank and Determinant**: The rank reflects the number of independent variables. A non-zero determinant implies $\Sigma$ is invertible.
- **Trace**: The trace $\text{Tr}(\Sigma) = \sum_{i=1}^n \sigma_{ii}$ represents the total variance.
- **Mahalanobis Distance**: $D(\mathbf{x}) = \sqrt{(\mathbf{x} - \boldsymbol{\mu})^\top \Sigma^{-1} (\mathbf{x} - \boldsymbol{\mu})}$ accounts for correlations in measuring distance from the mean.

## Eigenvalue decomposition
Visual Understanding:
- The covariance matrix $\Sigma$ can be viewed as stretching and rotating space.
- Eigenvectors indicate the directions of stretching.
- Eigenvalues indicate how much stretching occurs in each direction.
### Conclusion
The covariance matrix $\Sigma$ is fundamental in understanding the relationships between variables in multivariate data. Its symmetric, positive semi-definite structure supports a wide range of mathematical and statistical applications, such as eigen decomposition, matrix inversion, and advanced machine learning techniques.

## Video
![](https://www.youtube.com/watch?v=RQKJBpaCCeo)