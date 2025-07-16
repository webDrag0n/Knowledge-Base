- #Homework
- Course Code: DDA5002
  Name: Lin Zexin
  Student ID: 120010061
- ## Question 1
- ### (a) 
  
  Let $x_1, x_2 \in S$ and $\lambda \in [0,1]$. Then:
  
  $Ax_1 + b \in Y$ and $Ax_2 + b \in Y$
  
  For $\lambda x_1 + (1-\lambda)x_2$:
  
  $A(\lambda x_1 + (1-\lambda)x_2) + b = \lambda(Ax_1 + b) + (1-\lambda)(Ax_2 + b) - \lambda b - (1-\lambda)b + b$
  
  $= \lambda(Ax_1 + b) + (1-\lambda)(Ax_2 + b)$
  
  Since $Y$ is convex and $Ax_1 + b, Ax_2 + b \in Y$, we have $\lambda(Ax_1 + b) + (1-\lambda)(Ax_2 + b) \in Y$
  
  Therefore, $\lambda x_1 + (1-\lambda)x_2 \in S$, which proves $S$ is convex.
- ### (b)
  
  The quadratic-over-linear function $f(x,y) = \frac{x^2}{y}$ is convex when $y > 0$.
- ### (c)
  
  (i) $\exp g(x)$ is convex if $g(x)$ is convex.
  
  (ii) $\frac{1}{g(x)}$ is not convex in general, even if $g(x)$ is convex.
  
  (iii) $\sum_{i=1}^{m} \exp g_{i}(x)$ is convex if each $g_i(x)$ is convex.
  
  For the set $X=\{x \in \mathbb{R}: \alpha \leq \sqrt{x} \leq \beta\}$:
  
  This can be rewritten as $X = \{x \in \mathbb{R}: \alpha^2 \leq x \leq \beta^2, x \geq 0\}$
  
  This is an interval $[\alpha^2, \beta^2]$ (assuming $\alpha \geq 0$), which is convex.
- ### (d)
  
  The function $f(x) = x_{[2]}$ (second largest component of $x$) is convex.
- ## Question 2
- ### (a) 
  
  False. A convex optimization problem can have multiple global optimal solutions.
  
  Counterexample: $\min_{x \in \mathbb{R}} 0$ has infinitely many optimal solutions.
- ### (b) 
  
  False. A convex optimization problem may not have an optimal solution if the feasible region is unbounded.
  
  Counterexample: $\min_{x \in \mathbb{R}} x$ has no optimal solution.
- ### (c) 
  
  True. If a convex optimization problem has an optimal solution, then the set of optimal solutions is convex. If this set contains more than one point, it contains infinitely many points (all convex combinations of any two distinct optimal solutions).
- ### (d) 
  
  False. Consider $f(x) = -x^2$ on $[-1,1]$. The feasible region is non-empty, closed, and convex. Every local optimal solution is globally optimal (at $x = -1$ and $x = 1$), but $f$ is not convex.
- ## Question 3
- ### (a)
  
  $\nabla f(x) = \begin{pmatrix} 
  
  2x_1 + \frac{3}{2}x_1^2 - 2 - x_2^2 \\
  
  -2x_1 \cdot 2x_2 + \frac{1}{2}x_2^3
  
  \end{pmatrix} = \begin{pmatrix} 
  
  2x_1 + \frac{3}{2}x_1^2 - 2 - x_2^2 \\
  
  -4x_1x_2 + \frac{1}{2}x_2^3
  
  \end{pmatrix}$
  
  $H(x) = \begin{pmatrix} 
  
  2 + 3x_1 & -4x_2 \\
  
  -4x_2 & -4x_1 + \frac{3}{2}x_2^2
  
  \end{pmatrix}$
  
  Critical points: $\nabla f(x) = 0$
  
  From second equation: $x_2(-4x_1 + \frac{1}{2}x_2^2) = 0$
  
  So either $x_2 = 0$ or $x_1 = \frac{x_2^2}{8}$
  
  Case 1: $x_2 = 0$
  
  Substituting into first equation: $2x_1 + \frac{3}{2}x_1^2 - 2 = 0$
  
  Solving: $x_1 = \frac{-2 \pm \sqrt{4 + 12}}{3} = \frac{-2 \pm 2\sqrt{4}}{3} = \frac{-2 \pm 4}{3}$
  
  So $x_1 = \frac{2}{3}$ or $x_1 = -2$
  
  Case 2: $x_1 = \frac{x_2^2}{8}$
  
  Substituting into first equation: $2(\frac{x_2^2}{8}) + \frac{3}{2}(\frac{x_2^2}{8})^2 - 2 - x_2^2 = 0$
  
  Simplified: $\frac{x_2^2}{4} + \frac{3}{2}(\frac{x_2^4}{64}) - 2 - x_2^2 = 0$
  
  $\frac{x_2^2}{4} + \frac{3x_2^4}{128} - 2 - x_2^2 = 0$
  
  $-\frac{3x_2^2}{4} + \frac{3x_2^4}{128} - 2 = 0$
  
  Solving this equation yields $x_2 = \pm 2\sqrt{2}$
  
  For $x_2 = 2\sqrt{2}$: $x_1 = \frac{(2\sqrt{2})^2}{8} = 1$
  
  For $x_2 = -2\sqrt{2}$: $x_1 = \frac{(2\sqrt{2})^2}{8} = 1$
  
  Critical points: $(2/3, 0)$, $(-2, 0)$, $(1, 2\sqrt{2})$, $(1, -2\sqrt{2})$
- ### (b)
  
  For $(2/3, 0)$:
  
  $H(2/3, 0) = \begin{pmatrix} 2 + 3(2/3) & 0 \\ 0 & -4(2/3) \end{pmatrix} = \begin{pmatrix} 4 & 0 \\ 0 & -8/3 \end{pmatrix}$
  
  Has positive and negative eigenvalues, so it's a saddle point.
  
  For $(-2, 0)$:
  
  $H(-2, 0) = \begin{pmatrix} 2 + 3(-2) & 0 \\ 0 & -4(-2) \end{pmatrix} = \begin{pmatrix} -4 & 0 \\ 0 & 8 \end{pmatrix}$
  
  Has positive and negative eigenvalues, so it's a saddle point.
  
  For $(1, 2\sqrt{2})$:
  
  $H(1, 2\sqrt{2}) = \begin{pmatrix} 5 & -8\sqrt{2} \\ -8\sqrt{2} & -4 + 6 \end{pmatrix} = \begin{pmatrix} 5 & -8\sqrt{2} \\ -8\sqrt{2} & 2 \end{pmatrix}$
  
  Determinant = $5 \cdot 2 - (-8\sqrt{2})^2 = 10 - 128 < 0$
  
  So it's a saddle point.
  
  For $(1, -2\sqrt{2})$:
  
  $H(1, -2\sqrt{2}) = \begin{pmatrix} 5 & 8\sqrt{2} \\ 8\sqrt{2} & 2 \end{pmatrix}$
  
  Determinant = $5 \cdot 2 - (8\sqrt{2})^2 = 10 - 128 < 0$
  
  So it's a saddle point.
- ### (c)
  
  All critical points are saddle points, so $f$ has no local minimizer. As $x_1, x_2 \to -\infty$, $f(x) \to -\infty$, so there's no global minimizer.
- ## Question 4
- ### (a)
  
  $\nabla f_\alpha(x) = \begin{pmatrix} 2\alpha x_1 - 2x_2 \\ 2x_2 - 2x_1 - 2 \end{pmatrix}$
  
  For stationary points: $\nabla f_\alpha(x) = 0$
  
  $2\alpha x_1 - 2x_2 = 0$
  
  $2x_2 - 2x_1 - 2 = 0$
  
  From first equation: $x_2 = \alpha x_1$
  
  Substituting into second: $2\alpha x_1 - 2x_1 - 2 = 0$
  
  $(2\alpha - 2)x_1 = 2$
  
  $x_1 = \frac{1}{\alpha - 1}$ for $\alpha \neq 1$
  
  If $\alpha = 1$, then:
  
  $2x_1 - 2x_2 = 0 \implies x_1 = x_2$
  
  $2x_2 - 2x_1 - 2 = 0 \implies x_2 = x_1 + 1$
  
  These are inconsistent, so no stationary points when $\alpha = 1$.
  
  For $\alpha \neq 1$: $x_1 = \frac{1}{\alpha - 1}$ and $x_2 = \frac{\alpha}{\alpha - 1}$
- ### (b)
  
  The Hessian: $H_\alpha = \begin{pmatrix} 2\alpha & -2 \\ -2 & 2 \end{pmatrix}$
  
  Determinant: $\det(H_\alpha) = 4\alpha - 4 = 4(\alpha - 1)$
  
  For $\alpha > 1$:
  
  $\det(H_\alpha) > 0$ and $2\alpha > 0$, so $H_\alpha$ is positive definite.
  
  Therefore, the stationary point is a local minimizer.
  
  For $\alpha < 1$:
  
  $\det(H_\alpha) < 0$, so $H_\alpha$ has both positive and negative eigenvalues.
  
  Therefore, the stationary point is a saddle point.
- ### (c)
  
  For $f_\alpha$ to have a global minimizer, it needs to be bounded below.
  
  For $\alpha > 1$, the function is strictly convex (positive definite Hessian), so the stationary point is the global minimizer.
  
  For $\alpha = 1$:
  
  $f_1(x) = x_1^2 + x_2^2 - 2x_1x_2 - 2x_2 = (x_1 - x_2)^2 - 2x_2$
  
  As $x_2 \to \infty$, $f_1(x) \to -\infty$, so no global minimizer.
  
  For $\alpha < 1$:
  
  Consider the direction $v = (t, \alpha t)$ for large $t$:
  
  $f_\alpha(v) = \alpha(\alpha t)^2 + (\alpha t)^2 - 2(\alpha t)(\alpha t) - 2(\alpha t)$
  
  $= \alpha^3t^2 + \alpha^2t^2 - 2\alpha^2t^2 - 2\alpha t$
  
  $= (\alpha^3 - \alpha^2)t^2 - 2\alpha t$
  
  When $\alpha < 0$, as $t \to \infty$, $f_\alpha(v) \to -\infty$.
  
  When $0 \leq \alpha < 1$, as $t \to -\infty$, $f_\alpha(v) \to -\infty$.
  
  Therefore, $f_\alpha$ has a global minimizer if and only if $\alpha > 1$.
- ## Question 5
  
  Let $x^*$ be a local minimum of the problem.
  
  By the KKT conditions:
  
  1. There exist Lagrange multipliers $y \in \mathbb{R}^m$ such that:
	- $\nabla f(x^*) = \sum_{i=1}^m y_i \nabla g_i(x^*)$, where $g_i(x) = a_i^T x - b_i$
	- $y_i \geq 0$ for all $i$
	- $y_i \cdot (a_i^T x^* - b_i) = 0$ for all $i$ (complementary slackness)
	  
	  2. Since $\nabla g_i(x) = a_i$, we have:
	  
	  $\nabla f(x^*) = \sum_{i=1}^m y_i a_i = A^T y$
	  
	  This proves the required conditions:
- $\nabla f(x^*) = A^T y$
- $y \geq 0$
- $y_i \cdot (a_i^T x^* - b_i) = 0$ for all $i$