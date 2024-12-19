### Essentials of Lagrange Multipliers

Lagrange multipliers are a strategy for finding the local maxima and minima of a function subject to equality constraints. This method transforms a constrained optimization problem into a form that can be solved using the techniques of unconstrained optimization.

#### Basic Concept

Given a function \( f(\mathbf{x}) \) that we want to maximize or minimize subject to a constraint \( g(\mathbf{x}) = 0 \), the method of Lagrange multipliers introduces an auxiliary function called the Lagrangian:

$$
\mathcal{L}(\mathbf{x}, \lambda) = f(\mathbf{x}) + \lambda g(\mathbf{x})
$$

Here, \( \lambda \) is the Lagrange multiplier.

#### Steps to Solve Using Lagrange Multipliers

1. **Form the Lagrangian**: Combine the objective function and the constraint using a Lagrange multiplier.
2. **Take Partial Derivatives**: Compute the partial derivatives of the Lagrangian with respect to each variable and the Lagrange multiplier.
3. **Set Partial Derivatives to Zero**: Set each partial derivative equal to zero to form a system of equations.
4. **Solve the System of Equations**: Solve the system of equations to find the values of the variables and the Lagrange multiplier.

### Example: Minimizing and Maximizing the Objective Function

Consider the problem of minimizing and maximizing \( f(x, y) = x^2 + y^2 \) subject to the constraint \( g(x, y) = x + y - 1 = 0 \).

#### Minimizing \( f(x, y) = x^2 + y^2 \)

1. **Form the Lagrangian**:
   $$
   \mathcal{L}(x, y, \lambda) = x^2 + y^2 + \lambda (x + y - 1)
   $$

2. **Take Partial Derivatives**:
   $$
   \begin{aligned}
   \frac{\partial \mathcal{L}}{\partial x} &= 2x + \lambda = 0 \\
   \frac{\partial \mathcal{L}}{\partial y} &= 2y + \lambda = 0 \\
   \frac{\partial \mathcal{L}}{\partial \lambda} &= x + y - 1 = 0
   \end{aligned}
   $$

3. **Set Partial Derivatives to Zero**:
   $$
   \begin{aligned}
   2x + \lambda &= 0 \\
   2y + \lambda &= 0 \\
   x + y - 1 &= 0
   \end{aligned}
   $$

4. **Solve the System of Equations**:
   From the first two equations, we get \( 2x = 2y \) or \( x = y \). Substituting \( x = y \) into the third equation, we get \( 2x = 1 \) or \( x = \frac{1}{2} \). Therefore, \( y = \frac{1}{2} \).

   The solution is \( x = \frac{1}{2} \), \( y = \frac{1}{2} \), and \( \lambda = -1 \).

#### Maximizing \( f(x, y) = x^2 + y^2 \)

To maximize \( f(x, y) = x^2 + y^2 \) subject to the constraint \( x + y = 1 \), we need to recognize that the objective function is unbounded. As \( x \) and \( y \) increase without bound while satisfying \( x + y = 1 \), the value of \( x^2 + y^2 \) can go to infinity.

For example:
- If \( x = -1000 \) and \( y = 1001 \), then \( x + y = 1 \) and \( f(x, y) = (-1000)^2 + (1001)^2 = 1000000 + 1002001 = 2002001 \).
- As \( x \) and \( y \) continue to increase in magnitude while maintaining \( x + y = 1 \), \( f(x, y) \) will continue to increase without bound.

### Summary

- **Minimizing** \( f(x, y) = x^2 + y^2 \) subject to \( x + y - 1 = 0 \):
  - Solution: \( x = \frac{1}{2} \), \( y = \frac{1}{2} \), \( \lambda = -1 \)

- **Maximizing** \( f(x, y) = x^2 + y^2 \) subject to \( x + y - 1 = 0 \):
  - The problem is unbounded, and \( f(x, y) \) can go to infinity as \( x \) and \( y \) increase without bound while satisfying the constraint.

### Lagrange Multipliers for Different Constraints

Here is a summary of how to use Lagrange multipliers for different constraints in a table format:

| Objective | Constraint Type | Lagrangian Formulation | Lagrange Multiplier Condition |
|-----------|-----------------|------------------------|-------------------------------|
| Minimize  | \( g(\mathbf{x}) = 0 \) | \( \mathcal{L}(\mathbf{x}, \lambda) = f(\mathbf{x}) + \lambda g(\mathbf{x}) \) | \( \lambda \) can be any real number |
| Maximize  | \( g(\mathbf{x}) = 0 \) | \( \mathcal{L}(\mathbf{x}, \lambda) = -f(\mathbf{x}) + \lambda g(\mathbf{x}) \) | \( \lambda \) can be any real number |
| Minimize  | \( g(\mathbf{x}) \leq 0 \) | \( \mathcal{L}(\mathbf{x}, \lambda) = f(\mathbf{x}) + \lambda g(\mathbf{x}) \) | \( \lambda \geq 0 \) |
| Maximize  | \( g(\mathbf{x}) \leq 0 \) | \( \mathcal{L}(\mathbf{x}, \lambda) = -f(\mathbf{x}) + \lambda g(\mathbf{x}) \) | \( \lambda \leq 0 \) |
| Minimize  | \( g(\mathbf{x}) \geq 0 \) | \( \mathcal{L}(\mathbf{x}, \lambda) = f(\mathbf{x}) - \lambda g(\mathbf{x}) \) | \( \lambda \geq 0 \) |
| Maximize  | \( g(\mathbf{x}) \geq 0 \) | \( \mathcal{L}(\mathbf{x}, \lambda) = -f(\mathbf{x}) - \lambda g(\mathbf{x}) \) | \( \lambda \leq 0 \) |
| Minimize  | \( g(\mathbf{x}) < 0 \) | \( \mathcal{L}(\mathbf{x}, \lambda) = f(\mathbf{x}) + \lambda (g(\mathbf{x}) + \epsilon) \) | \( \lambda \geq 0 \) |
| Maximize  | \( g(\mathbf{x}) < 0 \) | \( \mathcal{L}(\mathbf{x}, \lambda) = -f(\mathbf{x}) + \lambda (g(\mathbf{x}) + \epsilon) \) | \( \lambda \leq 0 \) |
| Minimize  | \( g(\mathbf{x}) > 0 \) | \( \mathcal{L}(\mathbf{x}, \lambda) = f(\mathbf{x}) - \lambda (g(\mathbf{x}) - \epsilon) \) | \( \lambda \geq 0 \) |
| Maximize  | \( g(\mathbf{x}) > 0 \) | \( \mathcal{L}(\mathbf{x}, \lambda) = -f(\mathbf{x}) - \lambda (g(\mathbf{x}) - \epsilon) \) | \( \lambda \leq 0 \) |

