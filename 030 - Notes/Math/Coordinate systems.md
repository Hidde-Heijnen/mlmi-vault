In mathematics, a **coordinate system** is a system that uses one or more numbers, called **coordinates**, to uniquely determine the position of a point or other geometric element on a manifold such as Euclidean space.

## Cartesian Coordinate System

The **Cartesian coordinate system** is the most common coordinate system, typically represented in two dimensions by an $x$-axis and a $y$-axis, and in three dimensions with an additional $z$-axis.

A point in 2D is given as $(x, y)$ and in 3D as $(x, y, z)$.
### Distance Formula (2D)
$$
d = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}
$$

### Distance Formula (3D)
$$
d = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2 + (z_2 - z_1)^2}
$$

---
## Polar Coordinate System

In the **polar coordinate system**, a point in the plane is represented by two numbers: $r$, the distance from the origin, and $\theta$, the angle measured from the positive $x$-axis. The point is denoted as $(r, \theta)$.
### Conversion from Cartesian to Polar

To convert from Cartesian coordinates $(x, y)$ to polar coordinates $(r, \theta)$:
$$
r = \sqrt{x^2 + y^2}
$$
$$
\theta = \tan^{-1}\left(\frac{y}{x}\right)
$$
### Conversion from Polar to Cartesian
To convert from polar coordinates $(r, \theta)$ to Cartesian coordinates $(x, y)$:

$$
x = r \cos(\theta)
$$
$$
y = r \sin(\theta)
$$

---
## Cylindrical and Spherical Coordinate Systems

### Cylindrical Coordinates
In the **cylindrical coordinate system**, a point in 3D is represented by $(r, \theta, z)$ where $r$ and $\theta$ represent the polar coordinates in the $xy$-plane, and $z$ is the height.

- **Conversions**:
  - From Cartesian: $r = \sqrt{x^2 + y^2}$, $\theta = \tan^{-1}\left(\frac{y}{x}\right)$, $z = z$
  - From cylindrical to Cartesian: $x = r \cos(\theta)$, $y = r \sin(\theta)$, $z = z$

### Spherical Coordinates
In the **spherical coordinate system**, a point is represented by $(\rho, \theta, \phi)$ where:
- $\rho$ is the radial distance,
- $\theta$ is the azimuthal angle in the $xy$-plane,
- $\phi$ is the polar angle from the $z$-axis.

- **Conversions**:
  - Cartesian to Spherical: 
    - $\rho = \sqrt{x^2 + y^2 + z^2}$ 
    - $\theta = \tan^{-1}\left(\frac{y}{x}\right)$
    - $\phi = \cos^{-1}\left(\frac{z}{\rho}\right)$
  - Spherical to Cartesian: 
    - $x = \rho \sin(\phi) \cos(\theta)$
    - $y = \rho \sin(\phi) \sin(\theta)$
    - $z = \rho \cos(\phi)$
