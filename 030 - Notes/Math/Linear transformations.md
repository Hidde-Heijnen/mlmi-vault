A **linear transformation** is a function $T: V \to W$ between two vector spaces $V$ and $W$ (over the same field), which satisfies the following properties for all $u, v \in V$ and scalar $c$:

1. **Additivity (or Linearity)**:
   $$ T(u + v) = T(u) + T(v) $$

2. **Homogeneity (or Scalar Multiplication)**:
   $$ T(cu) = cT(u) $$

Linear transformations preserve the structure of vector addition and scalar multiplication in vector spaces.

In the plane, we know that a non-singular linear transformation maps a straight line onto a straight line. Similarly, a linear transformation maps a line segment onto another line segment.

## Matrix Representation

If $T: V \to W$ is a linear transformation and $V$ has dimension $n$, $W$ has dimension $m$, then there exists a matrix $A \in \mathbb{R}^{m \times n}$ such that for every vector $v \in V$:

$$ T(v) = A v $$

Here, $A$ is the matrix representation of $T$ with respect to the bases of $V$ and $W$.

## Non-Singular Linear Transformations

A linear transformation $T: V \to V$ is **non-singular** (or **invertible**) if there exists a linear transformation $T^{-1}: V \to V$ such that:

$$ T(T^{-1}(v)) = T^{-1}(T(v)) = v $$

This happens if and only if the matrix representation of $T$, say $A$, is invertible, i.e., $A$ has full rank and $\det(A) \neq 0$.

## Properties of Linear Transformations

- **Kernel**: The set of vectors in $V$ that map to the zero vector in $W$ under $T$, defined as:
  $$ \text{ker}(T) = \{v \in V : T(v) = 0\} $$
  The kernel of $T$ is a subspace of $V$.

- **Image**: The set of vectors in $W$ that can be expressed as $T(v)$ for some $v \in V$, defined as:
  $$ \text{im}(T) = \{T(v) : v \in V\} $$
  The image of $T$ is a subspace of $W$.

- **Rank-Nullity Theorem**: For a linear transformation $T: V \to W$, the sum of the dimension of the kernel and the dimension of the image equals the dimension of $V$:
  $$ \text{dim(ker}(T)) + \text{dim(im}(T)) = \text{dim}(V) $$

## Examples of Linear Transformations

1. **Identity Transformation**: $T(v) = v$ for all $v \in V$. The matrix representation is the identity matrix $I$.

2. **Scaling Transformation**: $T(v) = \lambda v$, where $\lambda$ is a scalar. The matrix representation is $\lambda I$.

3. **Rotation (in $\mathbb{R}^2$)**: A rotation by angle $\theta$ is represented by the matrix:
   $$
   A = \begin{bmatrix}
   \cos\theta & -\sin\theta \\
   \sin\theta & \cos\theta
   \end{bmatrix}
   $$

## Invertibility Conditions

A linear transformation $T: V \to V$ is invertible if:
- It is **bijective** (one-to-one and onto).
- The matrix $A$ representing $T$ is **non-singular** (i.e., $\det(A) \neq 0$).

If $T$ is invertible, then the inverse transformation $T^{-1}$ is also linear, and its matrix representation is $A^{-1}$, where $A$ is the matrix of $T$.
