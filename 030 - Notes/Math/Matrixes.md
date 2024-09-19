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
  - Matrix multiplication is **distributive**: $(A+B)C = AC+BC$ , $C(A+B) = CA + CB$
  - If $A$, $B$  and $C$  are three matrices that are conformable for multiplication, then they follow the associative law: $(AB)C = A(BC)$
#### Powers of matrixes
$A^n$ is matrix $A$ multiplied with itself $n$ times. 
- $A$ needs to be a square matrix to be conformable with itself. 
- $A^0 = I$, the identity matrix of the same dimensions as $A$
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
- The **transpose** of a matrix $A$ (denoted as $A^T$) is obtained by swapping its rows with its columns:$$A^T = \begin{bmatrix} a_{11} & a_{21} \\ a_{12} & a_{22} \end{bmatrix}$$
- The main/principal/primary/leading/major diagonal is the collection of entries where a=j
- A matrix is **symmetric** if it is the same as his transpose
	- can only be square matrices. 
	- the inverse of both itself and the transpose is the same
	- sum of symmetric matrices is always symmetric. 
	- product is always defined, but not alwasys symmetric. 
$$(A^{\top})^{\top} = A$$
$$(AB)^{\top} = B^{\top}A^{\top}$$
$$(A + B)^{\top} = A^{\top} + B^{\top}$$
### Identity Matrix:
- The **identity matrix** $I$ is a square matrix with 1's on the diagonal and 0's elsewhere:
$$  I = \begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}$$
  - For any matrix $A$, $A \cdot I = A$ and $I \cdot A = A$.

If you multiply a matrix by the xth collumn of the identity matrix alone, you only get the xth collumn of the original matrix. Same for rows. 

If you mix the collumns of an identity matrix you call it a **permutation matrix** you can easily find the inverse of a permutation matrix by doing a transpose. 
### Determinant:
- The **determinant** of a square matrix $A$ (denoted $\det(A)$ or $|A|$) is a scalar value that provides important properties of the matrix (e.g., invertibility). 
- The absolute value of an nxn determinant can be interpreted as the volume of the n-dimensional parallelepiped spanned by the columns of the determinant. 
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
#### Special Matrices and Determinants

For certain matrices, such as triangular or diagonal matrices, we can compute determinants quickly using a few key properties:

1. **Identity Matrix**:  
   The determinant of an $n \times n$ identity matrix is 1.  $$ \det(I) = 1 $$
2. **Triangular or Diagonal Matrices**:  
   The determinant of a triangular or diagonal matrix is the product of the entries on the main diagonal.  
   For matrix $A$:  
$$ \det(A) = 4 \cdot 2 \cdot (-3) \cdot (-1) = 24 $$
   For matrix $B$:  $$ \det(B) = 3 \cdot 2 \cdot 4 \cdot 1 \cdot (-2) = -48 $$
3. **Transpose Property**:  
   The determinant of a matrix and its transpose are the same:   $$ \det(A^T) = \det(A) $$
#### Determinant of NxN Matrix
The **determinant** of an $N \times N$ matrix is a scalar value that provides important properties of the matrix, such as invertibility.
##### Calculating Determinants using Cofactors
To calculate the determinant, expand along any row or column using cofactors:
$$\det(A) = \sum (-1)^{i+j} \cdot a_{ij} \cdot \det(M_{ij})$$
Or  $$\det(A) = \sum a_{1j} \cdot C_{1j}$$where $M_{ij}$ is the minor of $a_{ij}$.
- Adding a multiple of one row or column to another row or column preserves the determinant. 
- switching two rows  or columns changes the sign of the determinant
- multiplying a row or column by a number, scales the determinant by that number
- multiplying a $n \times n$ by a scalar multiplies the determinant by that number to the power of $n$
	- $det(k\cdot A) = k^n \cdot det(A)$
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
  - Only square matrices can have an inverse
  - A matrix that has an inverse is called invertible/regular/nonsingular. Otherwise, the matrix doesn't have an inverse and is called non-invertible. A square matrix that is non-invertible is called singular.
$$AA^{-1} = I = A^{-1}A$$
$$(AB)^{-1} = B^{-1}A^{-1}$$
$$(A + B)^{-1} \neq A^{-1} + B^{-1}$$
#### Inverse of 2x2 matrix
$$
  A = \begin{bmatrix} a & b \\ c & d \end{bmatrix}
  $$
$$A^{-1} = \frac{1}{det(A)} \begin{bmatrix} d & -b \\ -c & d \end{bmatrix}$$
#### Inverse of a 3x3 Matrix using cofactor Method

To find the inverse of a $3 \times 3$ matrix $A$, follow these steps:
1. **Find the matrix of minors**: Calculate the minor of each element in the matrix.
2. **Find the cofactor matrix**: Multiply each minor by $(-1)^{i+j}$ to form the cofactor matrix.
3. **Find the adjugate**: Transpose the cofactor matrix to get the adjugate matrix.
4. **Calculate the determinant**: Compute the determinant of matrix $A$, denoted as $\det(A)$.
5. **Inverse formula**: The inverse is given by:
$$A^{-1} = \frac{1}{\det(A)} \cdot \text{adj}(A)$$where $\text{adj}(A)$ is the adjugate matrix.
### Example:
Given $A = \begin{bmatrix} 1 & 2 & 3 \\ 0 & 1 & 4 \\ 5 & 6 & 0 \end{bmatrix}$:
1. **Matrix of minors**:
$$
\begin{bmatrix} 
\det\begin{bmatrix} 1 & 4 \\ 6 & 0 \end{bmatrix} & \det\begin{bmatrix} 0 & 4 \\ 5 & 0 \end{bmatrix} & \det\begin{bmatrix} 0 & 1 \\ 5 & 6 \end{bmatrix} \\
\det\begin{bmatrix} 2 & 3 \\ 6 & 0 \end{bmatrix} & \det\begin{bmatrix} 1 & 3 \\ 5 & 0 \end{bmatrix} & \det\begin{bmatrix} 1 & 2 \\ 5 & 6 \end{bmatrix} \\
\det\begin{bmatrix} 2 & 3 \\ 1 & 4 \end{bmatrix} & \det\begin{bmatrix} 1 & 3 \\ 0 & 4 \end{bmatrix} & \det\begin{bmatrix} 1 & 2 \\ 0 & 1 \end{bmatrix} 
\end{bmatrix} = \begin{bmatrix} 
-24 & 20 & -5 \\
18 & -15 & -4 \\
-9 & 3 & 1 
\end{bmatrix}
$$
2. **Cofactor matrix**:
$$
\begin{bmatrix} 
-24 & -20 & -5 \\
-18 & -15 & 4 \\
d-9 & -3 & 1 
\end{bmatrix}
$$

3. **Adjugate matrix** (transpose of cofactor matrix):
$$
\text{adj}(A) = \begin{bmatrix} 
-24 & -18 & -9 \\
-20 & -15 & -3 \\
-5 & 4 & 1 
\end{bmatrix}
$$
4. **Determinant**: $\det(A) = 1(1 \cdot 0 - 4 \cdot 6) - 2(0 \cdot 0 - 4 \cdot 5) + 3(0 \cdot 6 - 1 \cdot 5) = -39$
5. **Inverse**:
$$
A^{-1} = \frac{1}{-39} \cdot \begin{bmatrix} 
-24 & -18 & -9 \\
-20 & -15 & -3 \\
-5 & 4 & 1 
\end{bmatrix}
$$

### Laplace expension
A cofactor expension (like we do to get the determinant), but you can use any row or collumn 
### Matrix Rank:
- The **rank** of a matrix is the maximum number of linearly independent rows or columns in the matrix. It determines the dimensionality of the matrix's row or column space.

### Symmetric Matrix:
- A matrix $A$ is **symmetric** if $A = A^T$, meaning the matrix is equal to its transpose:
- Must be square matrix
  $$A = \begin{bmatrix} a & b \\ b & c \end{bmatrix}$$$$A = \begin{bmatrix}
a & b & c \\
b & d & e \\
c & e & f
\end{bmatrix}$$
- Suppose $A$ is a symmetric matrix, then:
	- $-A$ is symmetric
	- $A^m$ is symmetric for any positive integer $m$
	- $A^{-1}$ is symmetric for nonsingular $A$
- $A + A^T$ is symmetric for **any** square matrix A
- $A^TA$ and $AA^T$ are symmetric for any matrix $A$ (doesn't have to be square) 
- If $A$ and $B$ are NxN symmetric matrices we have the following properties
	- $A + B$ is symmetric
	- The product $A \cdot B$ is **not** always symmetric
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

### Linear Transformations and Standard Matrix
A **linear transformation** $T: \mathbb{R}^n \to \mathbb{R}^m$ is a function that satisfies:
1. **Additivity**: $T(\mathbf{u} + \mathbf{v}) = T(\mathbf{u}) + T(\mathbf{v})$
2. **Homogeneity**: $T(c \mathbf{u}) = c T(\mathbf{u})$
#### Standard Matrix of a Linear Transformation
If $T: \mathbb{R}^n \to \mathbb{R}^m$ is a linear transformation, the **standard matrix** $A$ associated with $T$ is the matrix such that:
$$T(\mathbf{x}) = A \mathbf{x}$$
where $A = \begin{bmatrix} T(\mathbf{e}_1) & T(\mathbf{e}_2) & \cdots & T(\mathbf{e}_n) \end{bmatrix}$ and $\mathbf{e}_i$ are the standard basis vectors in $\mathbb{R}^n$.

In general, the standard matrix of the linear transformation $T$ in R2 (but works the same for higher dimensions):
$$\textbf{T}: \begin{bmatrix} x \\ y \end{bmatrix} \longrightarrow \begin{bmatrix} ax + by \\ cx + dy \end{bmatrix}$$
is $$T = \begin{bmatrix} a & b \\ c & d \end{bmatrix}.$$

#### Example
For $T: \mathbb{R}^2 \to \mathbb{R}^2$, if $T(\mathbf{e}_1) = \begin{bmatrix} 2 \\ 1 \end{bmatrix}$ and $T(\mathbf{e}_2) = \begin{bmatrix} -1 \\ 3 \end{bmatrix}$, the standard matrix is:
$$A = \begin{bmatrix} 2 & -1 \\ 1 & 3 \end{bmatrix}$$
Thus, $T(\mathbf{x}) = A \mathbf{x}$.

### Affine Transformations

An **affine transformation** is a function of the form:

$$ \mathbf{x} = A\mathbf{u} + \mathbf{b} $$

Where:
- $\mathbf{u}$ is a vector in the input space.
- $\mathbf{x}$ is a vector in the output space.
- $A$ is a matrix representing a linear transformation.
- $\mathbf{b}$ is a vector representing translation.

Affine transformations include translation, scaling, rotation, and shearing, and they preserve points, straight lines, and planes. 
- A linear transformation is a special case of an affine transformation when $\mathbf{b} = 0$. 
- For an affine transformation, $A$ is the matrix representation of the corresponding linear transformation.

Affine transformations can be expressed as a matrix multiplication plus a translation, while non-affine transformations contain terms like quadratic terms (e.g., $uv$), which make them nonlinear.
### Applications of Matrices:
- **Linear transformations**: Matrices represent transformations like rotations, scaling, and shearing in geometry.
- **Systems of linear equations**: Matrices are used to represent and solve multiple equations simultaneously.
- **Markov chains**: Matrices model transitions between states in a stochastic process.
- **Graph theory**: Adjacency matrices represent graphs where rows and columns correspond to vertices.
