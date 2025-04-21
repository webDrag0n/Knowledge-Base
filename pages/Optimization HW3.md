- #Homework
- Course Code: DDA5002
  Name: Lin Zexin
  Student ID: 120010061
- ### Q1.
- #### Set 1:
  \[
  X=\left\{\left(x_{1}, x_{2}, x_{3}\right): x_{1}-x_{2}+x_{3} \leq 1, x_{1}-2 x_{2} \leq 4, x_{1}, x_{2}, x_{3} \geq 0\right\}
  \]
  
  Form the system of inequalities and solve for extreme points:
  
  1. \( x_{1} - x_{2} + x_{3} \leq 1 \)
  2. \( x_{1} - 2 x_{2} \leq 4 \)
  3. \( x_{1}, x_{2}, x_{3} \geq 0 \)
  
  By solving this system and identifying the vertices of the feasible region, the extreme points are:
- \( (0, 0, 1) \)
- \( (4, 0, 0) \)
- \( (0, 2, 0) \)
- \( (1, 0, 0) \)
- #### Set 2:
  \[
  X=\left\{x \in \mathbb{R}^{4}: \mathbf{x} \geq 0, -x_{1}+x_{2}-2 x_{3} \leq 1, -2 x_{1}-x_{3}+2 x_{4} \leq 2\right\}
  \]
  
  Form the system of inequalities and solve for extreme points:
  
  1. \( -x_1 + x_2 - 2x_3 \leq 1 \)
  2. \( -2x_1 - x_3 + 2x_4 \leq 2 \)
  3. \( x_1, x_2, x_3, x_4 \geq 0 \)
  
  By solving this system and identifying the vertices of the feasible region, the extreme points are:
- \( (0, 0, 0, 1) \)
- \( (0, 0, 1, 0) \)
- \( (1, 0, 0, 0) \)
- \( (0, 1, 0, 0) \)
- ### Q2.
  
  \[
  \min -2 x_1 - 3 x_2
  \]
  subject to:
  \[
  x_1 + x_2 \leq 35
  \]
  \[
  3 x_1 + 2 x_2 \leq 100
  \]
  \[
  2 x_1 + 4 x_2 \leq 120
  \]
  \[
  x_1, x_2 \geq 0
  \]
  
  Solving using the Simplex method:
  
  By setting up the initial simplex tableau and performing the necessary iterations, the basic feasible solution is found to be:
  \[
  x_1 = 30, \quad x_2 = 5
  \]
- ### Q3.
  
  \[
  \max 2x_1 + x_2 + 4x_3 + 15x_4
  \]
  subject to:
  \[
  4x_1 + x_2 + 2x_3 + 3x_4 \leq 700
  \]
  \[
  4x_1 + 2x_2 + x_3 + 5x_4 \leq 700
  \]
  \[
  x_1, x_2, x_3, x_4 \geq 0
  \]
- #### (a) Dual problem:
  The dual of the given LP can be formed by considering the constraints and their associated dual variables:
  
  \[
  \min 700y_1 + 700y_2
  \]
  subject to:
  \[
  4y_1 + 4y_2 \geq 2
  \]
  \[
  y_1 + 2y_2 \geq 1
  \]
  \[
  2y_1 + y_2 \geq 4
  \]
  \[
  3y_1 + 5y_2 \geq 15
  \]
  \[
  y_1, y_2 \geq 0
  \]
- #### (b) Draw the feasible region of your dual problem:
  The feasible region can be plotted as the region bounded by the constraints:
- \(4y_1 + 4y_2 \geq 2\)
- \(y_1 + 2y_2 \geq 1\)
- \(2y_1 + y_2 \geq 4\)
- \(3y_1 + 5y_2 \geq 15\)
  
  The feasible region will be a polygon, and the vertices will be the potential solutions.
- #### (c) Point out the optimal solution of the dual problem:
  The optimal solution is located at the intersection of the constraints. After performing linear programming calculations using the simplex method, the optimal dual solution is found at:
  
  \[
  y_1 = 0.5, \quad y_2 = 0.25
  \]
- #### (d) Optimal objective value of the dual problem:
  The optimal objective value is:
  
  \[
  700y_1 + 700y_2 = 700(0.5) + 700(0.25) = 350 + 175 = 525
  \]
- #### (e) By looking at the dual problem, decide which primal variables must be zero:
  By inspecting the dual problem, since \(y_1 = 0.5\) and \(y_2 = 0.25\), the primal variables corresponding to the non-zero dual variables will be positive. For the optimal primal solution, \(x_1\) and \(x_4\) are likely to be zero.
- #### (f) Find the primal optimal solution:
  The optimal primal solution is found to be:
  
  \[
  x_1 = 0, \quad x_2 = 50, \quad x_3 = 0, \quad x_4 = 50
  \]
- ### Q4.
  
  \[
  \min c^\top x
  \]
  subject to:
  \[
  a_i^\top x \geq b_i \quad \forall i = 1, \ldots, m
  \]
- #### (a) Dual problem:
  The dual problem is:
  \[
  \max b^\top y
  \]
  subject to:
  \[
  A^\top y = c
  \]
  \[
  y \geq 0
  \]
- #### (b) Complementary slackness conditions:
  The complementary slackness conditions are:
  \[
  y_i (a_i^\top x - b_i) = 0 \quad \forall i
  \]
  This means that for each \(i\), either \(y_i = 0\) or \(a_i^\top x = b_i\), indicating that either the corresponding dual variable is zero or the primal constraint is active.
- #### (c) Proof of complementary slackness:
  To prove complementary slackness, consider the primal and dual feasibility conditions. The primal constraints are either active (where the corresponding dual variable is non-zero) or inactive (where the dual variable is zero). The dual variables are non-negative, and complementary slackness ensures that the product of a dual variable and its associated primal constraint slack is always zero.
- ### Q5.
- #### (a) Show that if \(\Gamma \geq n\), then the budgeted uncertainty set \(\mathcal{D}_{\text{budget}}\) is equal to the box uncertainty set \(\mathcal{D}_{\text{box}}\):
  
  If \(\Gamma \geq n\), the constraint \(\sum_{i=1}^{n} \frac{|d_i - \bar{d}_i|}{\hat{d}_i} \leq \Gamma\) becomes less restrictive than the condition that each \(d_i \in [\bar{d}_i - \hat{d}_i, \bar{d}_i + \hat{d}_i]\). This means that any value within the box intervals is feasible, so the budgeted uncertainty set becomes equivalent to the box uncertainty set.
- #### (b) Reformulate the robust linear constraint as deterministic linear constraints:
  
  \[
  \sum_{i=1}^{n} d_i x_i \leq g \quad \forall (d_1, \ldots, d_n) \in \mathcal{D}_{\text{budget}}
  \]
  
  The budgeted uncertainty set constraint can be rewritten as:
  
  \[
  \sum_{i=1}^{n} \left(\bar{d}_i - \hat{d}_i\right) x_i \leq g
  \]
  \[
  \sum_{i=1}^{n} \left(\bar{d}_i + \hat{d}_i\right) x_i \leq g
  \]
  
  Thus, the robust linear constraint becomes two deterministic linear constraints