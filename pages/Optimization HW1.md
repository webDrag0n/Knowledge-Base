- #Homework
- Course Code: DDA5002
  Name: Lin Zexin
  Student ID: 120010061
- ## Q1
- ### (a) **Discontinuous function, compact set X**
- **Optimal solution example**:  
  \( f(x) = \begin{cases} 
      0 & \text{if } x = 0, \\
      1 & \text{if } x \neq 0, 
      \end{cases} \)
  and \( X = [-1, 1] \).  
  Optimal solution: \( x = 0 \).
- **No optimal solution example**:  
  \( f(x) = \frac{1}{x} \), \( X = [0, 1] \setminus \{0\} \).  
  No optimal solution exists.
- ### (b) **Continuous function, X is not closed**
- **No optimal solution example**:  
  \( f(x) = x^2 \), \( X = (0, 1) \).  
  No optimal solution exists.
- ### (c) **Linear function, X is not bounded**
- **No optimal solution example**:  
  \( f(x) = x \), \( X = \mathbb{R} \).  
  No optimal solution exists.
- ### (d) **Nonlinear function, X is compact**
- **Optimal solution example**:  
  \( f(x) = x^2 \), \( X = [-1, 1] \).  
  Optimal solution: \( x = 0 \).
- ### (e) **Linear function, X is not closed**
- **No optimal solution example**:  
  \( f(x) = x \), \( X = (0, 1) \).  
  No optimal solution exists.
- ### (f) **Linear function, X is compact**
- **Optimal solution example**:  
  \( f(x) = x \), \( X = [0, 1] \).  
  Optimal solution: \( x = 0 \).
- ## Q2
- Sure, here are the simplified proofs:
- ### (a) **True**  
  If the feasible region is bounded and the objective function is continuous, by the Extreme Value Theorem, the objective function must attain a minimum (or maximum) at some point in the feasible region.
- ### (b) **False**  
  Consider \( \min f(x) = x \) subject to \( x \geq 0 \). The feasible region is unbounded, but the optimal solution is \( x = 0 \), which gives the minimum objective value.
- ### (c) **True**  
  All global optimal solutions must give the same objective function value because they represent the minimum (or maximum) of the objective over the entire feasible region.
- ### (d) **False**  
  Adding a new constraint can change the feasible region. If the previous optimal solution doesn’t satisfy the new constraints, it may no longer be optimal.
- ### (e) **True**  
  Since the objective is \( [f(x)]^2 \), and the minimum value of a square is 0, if \( f(x^*) = 0 \), then \( x^* \) is optimal.
- ### (f) **False**  
  A discontinuous objective function can still have an optimal solution if the feasible region is closed and bounded. For example, a step function can have an optimal solution at a specific point.
- ### (g) **False**  
  Changing the constraint can affect the optimal value. In some cases, the optimal objective value can increase, not necessarily decrease or stay the same.
- ## Q3
- ### (a) Lagrangian Relaxation
  
  \[
  L(x, \lambda) = x^2 + 1 + \lambda \left( (x-2)(x-4) \right)
  \]
- ### (b) Solution to Lagrangian Relaxation
  
  \[
  \frac{\partial L(x, \lambda)}{\partial x} = 2x + \lambda(2x - 6) = 0
  \]
  \[
  x = \frac{3\lambda}{1 + \lambda}
  \]
- ### (c) Dual Problem
  
  \[
  g(\lambda) = \inf_x L(x, \lambda)
  \]
  \[
  \text{Maximize } g(\lambda) \quad \text{subject to} \quad \lambda \geq 0
  \]
- ## Q4
- ### (a) Lagrangian Relaxation
  
  \[
  L(x, \lambda) = x^\top W x + \sum_{i=1}^{n} \lambda_i (x_i^2 - 1)
  \]
- ### (b) Solution to Lagrangian Relaxation
  
  \[
  \frac{\partial L(x, \lambda)}{\partial x} = 2W x + 2 \text{diag}(\lambda) x = 0
  \]
  \[
  (W + \text{diag}(\lambda)) x = 0
  \]
- ### (c) Lower Bound
  
  \[
  g(\lambda) = \inf_x L(x, \lambda)
  \]
  \[
  \text{Maximize } g(\lambda) \quad \text{subject to} \quad \lambda \geq 0
  \]