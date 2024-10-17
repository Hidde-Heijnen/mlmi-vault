### **2. Eigenvalues and Eigenvectors: Introduction**

**What are Eigenvalues and Eigenvectors?**

- **Eigenvectors** are special vectors that, when a matrix multiplies them, result in a scalar multiple of themselves.
- The scalar is called the **eigenvalue**.

**Mathematically:**

For a matrix $A$, a vector $\mathbf{v}$, and scalar $\lambda$:

$$
A \mathbf{v} = \lambda \mathbf{v}
$$

- $\mathbf{v}$ is the eigenvector.
- $\lambda$ is the eigenvalue corresponding to $\mathbf{v}$.

**Intuitive Understanding:**

- When you apply the transformation represented by $A$ to $\mathbf{v}$, the vector $\mathbf{v}$ doesn't change direction, only its magnitude scales by $\lambda$.

**Why are Eigenvalues and Eigenvectors Important?**

- They reveal the fundamental properties of a matrix.
- In data analysis, they help identify directions (eigenvectors) along which data varies the most (eigenvalues).

---

### **3. Orthogonality and Orthonormality**

**Orthogonality:**

- Two vectors are **orthogonal** if they are at a right angle (90 degrees) to each other.
- Mathematically, vectors $\mathbf{u}$ and $\mathbf{v}$ are orthogonal if their dot product is zero:

$$
\mathbf{u}^\top \mathbf{v} = 0
$$

**Orthonormality:**

- A set of vectors is **orthonormal** if all vectors are orthogonal to each other and each vector has a length (norm) of 1.

**Importance in Matrices:**

- An **orthonormal matrix** $U$ has columns that are orthonormal vectors.
- Properties of an orthonormal matrix:
  - $U^\top U = I$, where $I$ is the identity matrix.
  - $U^{-1} = U^\top$

---

### **4. Eigenvalue Decomposition of the Covariance Matrix**

**Symmetric Matrices:**

- A matrix $A$ is **symmetric** if $A^\top = A$.
- Covariance matrices are symmetric.

**Eigenvalue Decomposition:**

- Any symmetric matrix $A$ can be decomposed into:

$$
A = U \Lambda U^\top
$$

- $U$ is a matrix whose columns are the eigenvectors of $A$.
- $\Lambda$ is a diagonal matrix whose diagonal elements are the eigenvalues of $A$.
- $U^\top$ is the transpose of $U$.

**Properties:**

- Since $A$ is symmetric, its eigenvalues are **real numbers**.
- Eigenvectors can be chosen to be orthonormal.

## **Steps in Eigenvalue Decomposition:**

1. **Find Eigenvalues ($\lambda_i$):**

   - Solve the characteristic equation:

     $$
     \det(A - \lambda I) = 0
     $$

     - $\det$ denotes determinant.
     - $I$ is the identity matrix.

2. **Find Eigenvectors ($\mathbf{u}_i$):**

   - For each eigenvalue $\lambda_i$, solve:

     $$
     (A - \lambda_i I) \mathbf{u}_i = \mathbf{0}
     $$

3. **Form Matrices $U$ and $\Lambda$:**

   - $U$ is constructed by placing eigenvectors $\mathbf{u}_i$ as columns.
   - $\Lambda$ is a diagonal matrix with eigenvalues $\lambda_i$ on the diagonal.

---

### **5. Practical Example**

**Suppose we have a 2x2 Covariance Matrix:**

$$
A = \begin{bmatrix}
4 & 2 \\
2 & 3 \\
\end{bmatrix}
$$

**Step 1: Find Eigenvalues**

Solve $\det(A - \lambda I) = 0$:

$$
\begin{vmatrix}
4 - \lambda & 2 \\
2 & 3 - \lambda \\
\end{vmatrix} = 0
$$

Calculate determinant:

$$
(4 - \lambda)(3 - \lambda) - (2)(2) = 0
$$

Simplify:

$$
(4 - \lambda)(3 - \lambda) - 4 = 0
$$

Expand:

$$
(12 - 4\lambda - 3\lambda + \lambda^2) - 4 = 0
$$

Simplify:

$$
\lambda^2 - 7\lambda + 8 = 0
$$

Solve quadratic equation:

$$
\lambda = \frac{7 \pm \sqrt{(-7)^2 - 4 \times 1 \times 8}}{2}
$$

$$
\lambda = \frac{7 \pm \sqrt{49 - 32}}{2} = \frac{7 \pm \sqrt{17}}{2}
$$

Approximate eigenvalues:

$$
\lambda_1 \approx \frac{7 + 4.123}{2} \approx 5.561
$$

$$
\lambda_2 \approx \frac{7 - 4.123}{2} \approx 1.439
$$

**Step 2: Find Eigenvectors**

For each $\lambda_i$, solve $(A - \lambda_i I) \mathbf{u}_i = \mathbf{0}$.

For $\lambda_1 \approx 5.561$:

$$
\begin{bmatrix}
4 - 5.561 & 2 \\
2 & 3 - 5.561 \\
\end{bmatrix}
\mathbf{u}_1 = \mathbf{0}
$$

Simplify matrix:

$$
\begin{bmatrix}
-1.561 & 2 \\
2 & -2.561 \\
\end{bmatrix}
$$

Find $\mathbf{u}_1$ such that:

$$
-1.561 u_{11} + 2 u_{12} = 0 \\
2 u_{11} - 2.561 u_{12} = 0
$$

Solve for $u_{11}$ and $u_{12}$.

Repeat for $\lambda_2$.

**Step 3: Form $U$ and $\Lambda$**

- Normalise eigenvectors to have length 1.
- Construct $U$ and $\Lambda$ with the eigenvectors and eigenvalues.

---

### **7. Applications in Data Analysis**

**Principal Component Analysis (PCA):**

- PCA uses eigenvalue decomposition of the covariance matrix.
- Eigenvectors (principal components) represent directions of maximum variance.
- Eigenvalues indicate the amount of variance along each principal component.

**Data Compression:**

- By selecting top $k$ eigenvectors, we can reduce data dimensionality.
- Retain most of the variability in the data with fewer dimensions.

---

