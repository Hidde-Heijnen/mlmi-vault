### Matrices:
- A **matrix** is a rectangular array of numbers arranged in rows and columns. It is denoted as:
  $$
  A = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn} \end{bmatrix}
  $$

  - An **$m \times n$ matrix** has $m$ rows and $n$ columns.
### Matrix Addition and Subtraction:
- Matrices of the same dimensions are added or subtracted element-wise:
  $$
  A + B = \begin{bmatrix} a_{11} + b_{11} & a_{12} + b_{12} \\ a_{21} + b_{21} & a_{22} + b_{22} \end{bmatrix}
  $$
### Scalar Multiplication:
- A matrix can be multiplied by a scalar $k$ by multiplying each element by $k$:
  $$kA = \begin{bmatrix} k \cdot a_{11} & k \cdot a_{12} \\ k \cdot a_{21} & k \cdot a_{22} \end{bmatrix}$$
### Matrix Multiplication:
- For matrices **$A$** (size $m \times n$) and **$B$** (size $n \times p$), their product **$C = A \cdot B$** is a matrix of size $m \times p$:
$$C_{ij} = \sum_{k=1}^{n} a_{ik} \cdot b_{kj}$$
  - The number of columns in $A$ must equal the number of rows in $B$.
  - Matrix multiplication is **not commutative**: $A \cdot B \neq B \cdot A$.
#### Matrix-Vector Multiplication
##### Dot Product Method
To multiply a matrix $A$ by a vector $\mathbf{x}$, calculate the dot product of each row in $A$ with $\mathbf{x}$.
Given:
$$
A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}, \quad \mathbf{x} = \begin{bmatrix} e \\ f \end{bmatrix}
$$
Multiply each row:
$$
A\mathbf{x} = \begin{bmatrix} a \cdot e + b \cdot f \\ c \cdot e + d \cdot f \end{bmatrix}
$$

##### Alternative: Linear Combination
Another method is to express the multiplication as a linear combination of the matrix columns scaled by the vector entries. For $A = \begin{bmatrix} a & c \\ b & d \end{bmatrix}$ and $\mathbf{x} = \begin{bmatrix} e \\ f \end{bmatrix}$:
$$
A\mathbf{x} = e \begin{bmatrix} a \\ b \end{bmatrix} + f \begin{bmatrix} c \\ d \end{bmatrix} = \begin{bmatrix} ea + fc \\ eb + fd \end{bmatrix}
$$
### Transpose of a Matrix:
- The **transpose** of a matrix $A$ (denoted as $A^T$) is obtained by swapping its rows with its columns:
  $$A^T = \begin{bmatrix} a_{11} & a_{21} \\ a_{12} & a_{22} \end{bmatrix}$$
### Identity Matrix:
- The **identity matrix** $I$ is a square matrix with 1's on the diagonal and 0's elsewhere:
$$  I = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}$$
  - For any matrix $A$, $A \cdot I = A$ and $I \cdot A = A$.
### Determinant:
- The **determinant** of a square matrix $A$ (denoted $\det(A)$ or $|A|$) is a scalar value that provides important properties of the matrix (e.g., invertibility). 
#### For a 2x2 matrix:
  $$\det(A) = \begin{vmatrix} a & b \\ c & d \end{vmatrix} = ad - bc$$
#### 3x3 matrix: 
That is, if $A = \begin{bmatrix} a & b & c \\ d & e & f \\ g & h & i \end{bmatrix}$, then
$$\begin{vmatrix}
a & b & c \\
d & e & f \\
g & h & i
\end{vmatrix} = a\begin{vmatrix}
e & f \\
h & i
\end{vmatrix} - b\begin{vmatrix}
d & f \\
g & i
\end{vmatrix} + c\begin{vmatrix}
d & e \\
g & h
\end{vmatrix}$$
$$ = a(ei - fh) - b(di - fg) + c(dh - eg).$$
#### Determinant of NxN Matrix
The **determinant** of an $N \times N$ matrix is a scalar value that provides important properties of the matrix, such as invertibility.
##### Calculating Determinants using Cofactors
To calculate the determinant, expand along any row or column using cofactors:
$$\det(A) = \sum (-1)^{i+j} \cdot a_{ij} \cdot \det(M_{ij})$$
Or  $$\det(A) = \sum a_{1j} \cdot C_{1j}$$where $M_{ij}$ is the minor of $a_{ij}$.
### Minor of NxN Matrix
The **minor** $M_{ij}$ is the determinant of the submatrix formed by removing the $i$-th row and $j$-th column from matrix $A$.

Given matrix $A$:
$$A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 9 \end{bmatrix}$$
The minor $M_{11}$ is the determinant of the $2 \times 2$ matrix formed by removing the 1st row and 1st column:
$$
M_{11} = \det\begin{bmatrix} 5 & 6 \\ 8 & 9 \end{bmatrix} = (5 \cdot 9 - 6 \cdot 8) = -3
$$
### Cofactor of NxN Matrix
The **cofactor** $C_{ij}$ is the minor $M_{ij}$ multiplied by $(-1)^{i+j}$:
$$
C_{ij} = (-1)^{i+j} \cdot M_{ij}
$$

### Inverse Matrix:
- The **inverse** of a square matrix $A$ (denoted $A^{-1}$) is a matrix such that:  $$
  A \cdot A^{-1} = A^{-1} \cdot A = I $$
  - A matrix is invertible if and only if $\det(A) \neq 0$.
  - A matrix that has an inverse is called invertible. Otherwise, the matrix doesn't have an inverse and is called non-invertible. A square matrix that is non-invertible is called singular.
#### Inverse of 2x2 matrix
$$
  A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}
  $$
$$A^{-1} = \frac{1}{det(A)} \begin{bmatrix} d & -b \\ -c & d \end{bmatrix}$$
#### Inverse of a 3x3 Matrix using cofactor Method

### Matrix Rank:
- The **rank** of a matrix is the maximum number of linearly independent rows or columns in the matrix. It determines the dimensionality of the matrix's row or column space.

### Symmetric Matrix:
- A matrix $A$ is **symmetric** if $A = A^T$, meaning the matrix is equal to its transpose:
  $$
  A = \begin{bmatrix} a & b \\ b & c \end{bmatrix}
  $$
### Diagonal Matrix:
- A **diagonal matrix** is a square matrix in which all off-diagonal elements are zero:
  $$
  D = \begin{bmatrix} d_1 & 0 \\ 0 & d_2 \end{bmatrix}
  $$
### Trace:
- The **trace** of a square matrix $A$ is the sum of its diagonal elements:
$$
  \text{Tr}(A) = \sum_{i=1}^{n} a_{ii}
$$ ### Eigenvalues and Eigenvectors:
- For a square matrix $A$, if there exists a scalar $\lambda$ (called an **eigenvalue**) and a non-zero vector $\mathbf{v}$ (called an **eigenvector**) such that:

  $$
  A \mathbf{v} = \lambda \mathbf{v}
  $$

  - $\lambda$ is the eigenvalue, and $\mathbf{v}$ is the corresponding eigenvector.
  - **Eigenvalues** provide important information about the matrix, such as stability and behavior in transformations.

### Orthogonal Matrix:
- A matrix $A$ is **orthogonal** if its transpose is equal to its inverse:

  $$
  A^T = A^{-1}
  $$

  - For orthogonal matrices, multiplying them by their transpose yields the identity matrix: $A \cdot A^T = I$.
  - The rows and columns of an orthogonal matrix are orthonormal vectors (i.e., they have unit length and are perpendicular).

### Block Matrix:
- A **block matrix** is a matrix divided into smaller matrices (called blocks or submatrices):

  $$
  A = \begin{bmatrix} A_{11} & A_{12} \\ A_{21} & A_{22} \end{bmatrix}
  $$

  - Block matrices are useful in simplifying complex matrix operations.

### Row Echelon Form:
- A matrix is in **row echelon form** if:
  - All non-zero rows are above rows of all zeros.
  - The leading entry (pivot) of each non-zero row is to the right of the leading entry in the row above it.
  - All entries in a column below a pivot are zeros.
  - Reduced Row Echelon Form is when the leading entry is a 1 of each non zero row. 

### Gaussian Elimination:
- **Gaussian elimination** is a method for solving systems of linear equations by transforming the matrix into row echelon form using row operations:
  - Swapping rows.
  - Multiplying a row by a non-zero scalar.
  - Adding/subtracting a multiple of one row to another row.

### LU Decomposition:
- **LU decomposition** expresses a matrix $A$ as the product of a lower triangular matrix $L$ and an upper triangular matrix $U$:

  $$
  A = LU
  $$

  - It is used to solve linear systems and invert matrices efficiently.

### Applications of Matrices:
- **Linear transformations**: Matrices represent transformations like rotations, scaling, and shearing in geometry.
- **Systems of linear equations**: Matrices are used to represent and solve multiple equations simultaneously.
- **Markov chains**: Matrices model transitions between states in a stochastic process.
- **Graph theory**: Adjacency matrices represent graphs where rows and columns correspond to vertices.
