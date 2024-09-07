### Vectors:
- A **vector** is a quantity that has both magnitude and direction, represented as:

  $$
  \mathbf{v} = \begin{bmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{bmatrix}
  $$

  where each $v_i$ is a component of the vector in the corresponding direction.

### Dot Product:
- The **dot product** (or scalar product) of two vectors $\mathbf{a}$ and $\mathbf{b}$ is a scalar value:

  $$
  \mathbf{a} \cdot \mathbf{b} = a_1b_1 + a_2b_2 + \cdots + a_nb_n = |\mathbf{a}| |\mathbf{b}| \cos(\theta)
  $$

  - Produces a scalar.
  - Measures how much one vector extends in the direction of another.
  - **Properties**: Commutative ($\mathbf{a} \cdot \mathbf{b} = \mathbf{b} \cdot \mathbf{a}$), distributive over addition.

### Cross Product:
- The **cross product** (or vector product) of two 3D vectors $\mathbf{a}$ and $\mathbf{b}$ is a vector:

  $$
  \mathbf{a} \times \mathbf{b} = \begin{vmatrix} \hat{i} & \hat{j} & \hat{k} \\ a_1 & a_2 & a_3 \\ b_1 & b_2 & b_3 \end{vmatrix} = (a_2b_3 - a_3b_2)\hat{i} - (a_1b_3 - a_3b_1)\hat{j} + (a_1b_2 - a_2b_1)\hat{k}
  $$

  - Produces a vector perpendicular to both $\mathbf{a}$ and $\mathbf{b}$.
  - **Magnitude**: $|\mathbf{a} \times \mathbf{b}| = |\mathbf{a}| |\mathbf{b}| \sin(\theta)$.
  - **Direction**: Follows the **right-hand rule**.

- When two vectors a and b are parallel (or collinear), them the angle between them is 0, and consequently their cross prod
### Magnitude of a Vector:
- The **magnitude** (or length) of a vector $\mathbf{v}$ is:

  $$
  |\mathbf{v}| = \sqrt{v_1^2 + v_2^2 + \cdots + v_n^2}
  $$

### Unit Vector:
- A **unit vector** has a magnitude of 1 and points in the same direction as the original vector:

  $$
  \hat{\mathbf{v}} = \frac{\mathbf{v}}{|\mathbf{v}|}
  $$

### Vector Addition & Subtraction:
- Vectors are added or subtracted component-wise:

  $$
  \mathbf{a} + \mathbf{b} = \begin{bmatrix} a_1 + b_1 \\ a_2 + b_2 \\ \vdots \\ a_n + b_n \end{bmatrix}
  $$

  $$
  \mathbf{a} - \mathbf{b} = \begin{bmatrix} a_1 - b_1 \\ a_2 - b_2 \\ \vdots \\ a_n - b_n \end{bmatrix}
  $$

### Scalar Multiplication:
- A vector $\mathbf{v}$ multiplied by a scalar $k$ scales each component:

  $$
  k\mathbf{v} = \begin{bmatrix} k v_1 \\ k v_2 \\ \vdots \\ k v_n \end{bmatrix}
  $$

### Orthogonal Vectors:
- Two vectors $\mathbf{a}$ and $\mathbf{b}$ are **orthogonal** (perpendicular) if:

  $$
  \mathbf{a} \cdot \mathbf{b} = 0$$