- #Homework
- Course Code: DDA5002
  Name: Lin Zexin
  Student ID: 120010061
- ## Q1.
- #### Decision Variables:
  Let \( x_{it} \) represent the proportion of block \( i \) mined in period \( t \), and let \( y_{it} \) represent the proportion of the mined rock from block \( i \) in period \( t \) that is sent to the processing plant (with the remainder being sent to waste).
- \( x_{it} \in [0, 1] \): Fraction of block \( i \) mined in period \( t \).
- \( y_{it} \in [0, 1] \): Fraction of block \( i \) mined in period \( t \) sent to the processing plant.
- #### Parameters:
- \( r_i \): Tons of rock in block \( i \).
- \( m_i \): Units of mineral in block \( i \).
- \( R_f \): Maximum tons of rock mined in each period.
- \( C_t \): Maximum tons of rock sent to the processing plant in period \( t \).
- \( b_t \): Cost per ton of rock mined in period \( t \).
- \( p_t \): Cost per ton of rock sent to the processing plant in period \( t \).
- \( g_t \): Revenue per unit of mineral extracted in period \( t \).
- \( P \): Set of precedence constraints, where \( (i, j) \in P \) implies that block \( i \) must be mined before block \( j \).
- #### Objective Function:
  \[
  \text{Maximize} \quad Z = \sum_{t=1}^{T} \sum_{i=1}^{N} \left( \frac{2}{5} m_i g_t x_{it} y_{it} \right) - \sum_{t=1}^{T} \sum_{i=1}^{N} \left( \frac{1}{2} r_i b_t x_{it} \right) - \sum_{t=1}^{T} \sum_{i=1}^{N} \left( \frac{2}{5} r_i p_t x_{it} y_{it} \right)
  \]
- #### Constraints:
  
  1. **Mining Capacity per Period:**
   The total amount of rock mined in each period must not exceed the available mining capacity \( R_f \).
   \[
   \sum_{i=1}^{N} r_i x_{it} \leq R_f \quad \forall t \in \{1, 2, \dots, T\}
   \]
  
  2. **Processing Capacity per Period:**
   The total amount of rock processed in each period must not exceed the processing plant capacity \( C_t \).
   \[
   \sum_{i=1}^{N} r_i y_{it} x_{it} \leq C_t \quad \forall t \in \{1, 2, \dots, T\}
   \]
  
  3. **Block Mining Proportion:**
   The fraction of block \( i \) mined in period \( t \) must be between 0 and 1.
   \[
   0 \leq x_{it} \leq 1 \quad \forall i \in \{1, 2, \dots, N\}, \forall t \in \{1, 2, \dots, T\}
   \]
  
  4. **Block Processing Proportion:**
   The fraction of mined rock from block \( i \) sent to the processing plant must be between 0 and 1.
   \[
   0 \leq y_{it} \leq 1 \quad \forall i \in \{1, 2, \dots, N\}, \forall t \in \{1, 2, \dots, T\}
   \]
  
  5. **Precedence Constraints:**
   If block \( i \) is mined in period \( t \), then all of block \( i \) must have been mined in period \( t \) or earlier if it has precedence over block \( j \).
   \[
   x_{it} = 0 \quad \text{if} \quad (i, j) \in P \text{ and } t > t' \quad \forall i, j \in \{1, 2, \dots, N\}, \forall t \in \{1, 2, \dots, T\}
   \]
  
  6. **Non-Negativity:**
   The decision variables must be non-negative.
   \[
   x_{it} \geq 0, \quad y_{it} \geq 0 \quad \forall i \in \{1, 2, \dots, N\}, \forall t \in \{1, 2, \dots, T\}
   \]
- #### Explanation of Constraints:
- **Mining and Processing Capacity Constraints (1 & 2):** Ensure that the total amount of rock mined and processed in any period does not exceed the available mining and processing plant capacities.
- **Block Mining and Processing Proportions (3 & 4):** These constraints ensure that the proportion of each block mined and sent to the processing plant remains within the allowable range (between 0 and 1).
- **Precedence Constraints (5):** Guarantee that mining of a block follows the required precedence order, ensuring that no block \( j \) is mined before block \( i \) if there is a precedence relationship.
- **Non-Negativity (6):** Ensures that the decision variables are non-negative, as proportions cannot be negative.
  
  The objective function captures the total profit from mining, processing, and the associated costs and revenues. The decision variables \( x_{it} \) and \( y_{it} \) are chosen to maximize the profit subject to the constraints.
- ## Q2.
- ### Problem Formulation
  
  We need to formulate a Mixed Integer Linear Program (MILP) to minimize the total cost, which consists of both production and transportation costs. The decision variables include both the production levels at each factory and the transportation quantities from each factory to each warehouse.
- #### Decision Variables:
  1. \( y_i \) = The number of products produced at factory \( i \), where \( i = 1, \dots, m \).
  2. \( x_{ij} \) = The number of products transported from factory \( i \) to warehouse \( j \), where \( i = 1, \dots, m \) and \( j = 1, \dots, n \).
- #### Parameters:
- \( d_j \): The demand for products at warehouse \( j \).
- \( c_{ij} \): The transportation cost per product from factory \( i \) to warehouse \( j \).
- \( f_i(y_i) \): The piecewise linear production cost function for factory \( i \).
  \[
  f_i(y_i) = L_i^k + p_i^k(y_i - s_i^{k-1}), \quad s_i^{k-1} \leq y_i \leq s_i^k \quad k = 1, \dots, K_i
  \]
- \( s_i^{k} \): The end of the \( k \)-th production segment for factory \( i \).
- \( p_i^k \), \( L_i^k \): Parameters of the piecewise linear cost function for factory \( i \).
- \( q_i \): The minimum number of products that factory \( i \) must produce if it is operational.
- \( s_i^{K_i} \): The maximum production capacity of factory \( i \).
- \( b \): The maximum absolute difference in the number of products manufactured by two different factories.
- \( h \): The production threshold for factories, above which the total production across all factories must not exceed \( g \).
- \( g \): The total upper limit on production if any factory exceeds \( h \) products.
- **Objective Function:**
  \[
  \text{Minimize} \quad Z = \sum_{i=1}^{m} f_i(y_i) + \sum_{i=1}^{m} \sum_{j=1}^{n} c_{ij} x_{ij}
  \]
- **Subject to:**
  
  1. **Demand Satisfaction:**
  \[
  \sum_{i=1}^{m} x_{ij} = d_j, \quad \forall j \in \{1, 2, \dots, n\}
  \]
  
  2. **Production-to-Transportation Balance:**
  \[
  \sum_{j=1}^{n} x_{ij} = y_i, \quad \forall i \in \{1, 2, \dots, m\}
  \]
  
  3. **Production Bounds:**
  \[
  q_i \leq y_i \leq s_i^{K_i}, \quad \forall i \in \{1, 2, \dots, m\}
  \]
  
  4. **Max Production Difference Between Factories:**
  \[
  |y_i - y_j| \leq b, \quad \forall i, j \in \{1, 2, \dots, m\}, \, i \neq j
  \]
  
  5. **Production Limit with Threshold \( h \):**
  
  Indicator variable \( z_i \) for whether factory \( i \) produces more than \( h \) products:
  \[
  y_i - h \leq M \cdot z_i, \quad \forall i \in \{1, 2, \dots, m\}
  \]
  where \( M \) is a large constant.
  
  Total production constraint:
  \[
  \sum_{i=1}^{m} y_i \leq g + M \cdot \sum_{i=1}^{m} z_i
  \]
  
  6. **Piecewise Linear Production Cost:**
  **Binary Assignment for Segments:**
  \[
  s_i^{k-1} \cdot w_i^k \leq y_i \leq s_i^k \cdot w_i^k, \quad \forall k = 1, 2, \dots, K_i
  \]
  **Cost Calculation:**
  \[
  t_i^k = L_i^k + p_i^k(y_i - s_i^{k-1}), \quad \forall k = 1, 2, \dots, K_i
  \]
  **Total Cost for Factory \( i \):**
  \[
  f_i(y_i) = \sum_{k=1}^{K_i} w_i^k \cdot t_i^k
  \]
  
  7. **Non-Negativity Constraints:**
  \[
  y_i \geq 0, \quad \forall i \in \{1, 2, \dots, m\}
  \]
  \[
  x_{ij} \geq 0, \quad \forall i \in \{1, 2, \dots, m\}, \quad \forall j \in \{1, 2, \dots, n\}
  \]
- ## Q3.
- ### **(a) Integer Linear Program for Minimizing Total Cost Over \( T \) Periods**
- #### **Decision Variables:**
  1. \( x_{ijt} \): The amount of material transported from supply node \( i \) to demand node \( j \) in period \( t \).
  2. \( u_{at} \): The capacity of arc \( a \in A \) in period \( t \).
  3. \( \Delta u_{at} \): The amount by which the capacity of arc \( a \in A \) is increased in period \( t \).
  4. \( z_{at} \): A binary variable indicating whether arc \( a \in A \) has its capacity increased in period \( t \).
- #### **Objective Function:**
  \[
  \text{Minimize} \quad Z = \sum_{i \in S} \sum_{j \in D} \sum_{t=1}^{T} c_{ijt} x_{ijt} + \sum_{a \in A} \sum_{t=1}^{T} \left( f_{at} z_{at} + q_{at} \Delta u_{at} \right)
  \]
- #### **Constraints:**
  1. **Supply constraints** (the total material supplied at supply point \( i \) should not exceed the available supply):
  
  \[
  \sum_{j \in D} \sum_{t=1}^{T} x_{ijt} \leq b_{it}, \quad \forall i \in S, \, t \in \{1, 2, \dots, T\}
  \]
  
  2. **Demand constraints** (the total material demand at demand point \( j \) should be met):
  
  \[
  \sum_{i \in S} \sum_{t=1}^{T} x_{ijt} \geq d_{jt}, \quad \forall j \in D, \, t \in \{1, 2, \dots, T\}
  \]
  
  3. **Flow conservation** (the material flow must satisfy the network's flow conservation):
  
  \[
  \sum_{i \in N} x_{ijt} - \sum_{k \in N} x_{jik} = 0, \quad \forall j \in N, \, t \in \{1, 2, \dots, T\}
  \]
  
  4. **Arc capacity constraints** (the amount of flow along an arc \( a \) must not exceed its capacity):
  
  \[
  \sum_{i \in N} x_{ijt} \leq u_{at}, \quad \forall a = (i, j) \in A, \, t \in \{1, 2, \dots, T\}
  \]
  
  5. **Capacity increase** (The increase in capacity must be equal to the difference between the current capacity and the initial capacity):
  
  \[
  \Delta u_{at} = u_{at} - u_0, \quad \forall a \in A, \, t \in \{1, 2, \dots, T\}
  \]
  
  6. **Maximum capacity constraint** (the capacity of any arc cannot exceed the maximum allowed):
  
  \[
  u_{at} \leq m_a, \quad \forall a \in A, \, t \in \{1, 2, \dots, T\}
  \]
  
  7. **Link between capacity increase and binary variable** (If the capacity is increased, then the binary variable \( z_{at} \) must be 1):
  
  \[
  u_{at} - u_0 \leq M z_{at}, \quad \forall a \in A, \, t \in \{1, 2, \dots, T\}
  \]
  Where \( M \) is a large constant that ensures the constraint holds when \( z_{at} = 1 \).
- #### **Non-negativity and Binary Constraints:**
  \[
  x_{ijt} \geq 0, \quad \forall i \in S, \, j \in D, \, t \in \{1, 2, \dots, T\}
  \]
  \[
  u_{at} \geq u_0, \quad \forall a \in A, \, t \in \{1, 2, \dots, T\}
  \]
  \[
  z_{at} \in \{0, 1\}, \quad \forall a \in A, \, t \in \{1, 2, \dots, T\}
  \]
  \[
  \Delta u_{at} \geq 0, \quad \forall a \in A, \, t \in \{1, 2, \dots, T\}
  \]
- ### **(b) Integer Linear Program with Maintenance Costs, Decommissioning, and Arc Shutdown**
- #### **Decision Variables:**
  1. \( x_{ijt} \): The amount of material transported from supply node \( i \) to demand node \( j \) in period \( t \).
  2. \( u_{at} \): The capacity of arc \( a \in A \) in period \( t \).
  3. \( z_{at} \): A binary variable indicating whether arc \( a \in A \) has its capacity increased in period \( t \).
  4. \( y_{at} \): A binary variable indicating whether arc \( a \in A \) is open in period \( t \) (1 if open, 0 if closed).
  5. \( q_{at} \): The amount of decommissioning cost incurred when shutting down arc \( a \) in period \( t \).
- #### **Objective Function:**
  We need to minimize the total cost, which now includes:
- **Transportation costs**
- **Overhead and cost of increasing arc capacities**
- **Maintenance cost for each arc**
- **Decommissioning cost for shutting down arcs**
  
  The objective function becomes:
  
  \[
  \text{Minimize} \quad Z = \sum_{i \in S} \sum_{j \in D} \sum_{t=1}^{T} c_{ijt} x_{ijt} + \sum_{a \in A} \sum_{t=1}^{T} \left( f_{at} z_{at} + q_{at} \Delta u_{at} + c_{at} y_{at} \right) + \sum_{a \in A} \sum_{t=1}^{T} w_{at} (1 - y_{at})
  \]
- #### **Constraints:**
  1. **Supply constraints**:
  \[
  \sum_{j \in D} \sum_{t=1}^{T} x_{ijt} \leq b_{it}, \quad \forall i \in S, \, t \in \{1, 2, \dots, T\}
  \]
  
  2. **Demand constraints**:
  \[
  \sum_{i \in S} \sum_{t=1}^{T} x_{ijt} \geq d_{jt}, \quad \forall j \in D, \, t \in \{1, 2, \dots, T\}
  \]
  
  3. **Flow conservation**:
  \[
  \sum_{i \in N} x_{ijt} - \sum_{k \in N} x_{jik} = 0, \quad \forall j \in N, \, t \in \{1, 2, \dots, T\}
  \]
  
  4. **Arc capacity constraints**:
  \[
  \sum_{i \in N} x_{ijt} \leq u_{at}, \quad \forall a = (i, j) \in A, \, t \in \{1, 2, \dots, T\}
  \]
  
  5. **Capacity increase**:
  \[
  \Delta u_{at} = u_{at} - u_0, \quad \forall a \in A, \, t \in \{1, 2, \dots, T\}
  \]
  
  6. **Maximum capacity**:
  \[
  u_{at} \leq m_a, \quad \forall a \in A, \, t \in \{1, 2, \dots, T\}
  \]
  
  7. **Link between capacity increase and binary variable**:
  \[
  u_{at} - u_0 \leq M z_{at}, \quad \forall a \in A, \, t \in \{1, 2, \dots, T\}
  \]
  
  8. **Shutdown and maintenance costs**:
  \[
  y_{at} \in \{0, 1\}, \quad \forall a \in A, \, t \in \{1, 2, \dots, T\}
  \]
  \[
  \sum_{t=1}^{T} y_{at} \geq K \quad \text{(if an arc is shut down in period \( t \), it must remain shut down for at least \( K \) periods)}
  \]
  \[
  \sum_{t=1}^{T} (1 - y_{at}) = 1 \quad \text{(if an arc is shut down, it cannot carry any flow)}
  \]
- #### **Non-negativity and Binary Constraints:**
  \[
  x_{ijt} \geq 0, \quad \forall i \in S, \, j \in D, \, t \in \{1, 2, \dots, T\}
  \]
  \[
  u_{at} \geq u_0, \quad \forall a \in A, \, t \in \{1, 2, \dots, T\}
  \]
  \[
  z_{at} \in \{0, 1\}, \quad \forall a \in A, \, t \in \{1, 2, \dots, T\}
  \]
- ## Q4.
- ### **LP Formulation:**
  
  **Decision Variables:**
  \( x_t \) represent the number of shifts starting at hour \( t \), where \( t \in \{0, 1, 2, \dots, 23\} \).
  
  The variable \( x_t \) represents how many salesclerks are assigned to shifts that start at hour \( t \).
  
  **Objective function:**
  \[
  \text{Minimize} \quad Z = \sum_{t=0}^{23} c_1 \cdot x_t
  \]
  
  **Subject to:**
  \[
  \sum_{t: \, t \leq h \leq t+8, \, t+4 \neq h} x_t \geq r_h, \quad \forall h \in \{0, 1, \dots, 23\}
  \]
  
  \[
  x_t \geq 0, \quad \forall t \in \{0, 1, \dots, 23\}
  \]
  
  \[
  x_t \in \mathbb{Z}^+, \quad \forall t \in \{0, 1, \dots, 23\}
  \]
- ## Q5.
- ### **(a) Formulation of the problem as a Linear Program**
- introduce auxiliary variables:
- Let \( y_1 = 2x_1 + 3x_2 \)
- Let \( y_2 = x_1 - x_2 \)
  
  Thus, the objective becomes:
  
  \[
  \min \left( \max \left( |y_1|, |y_2| \right) \right)
  \]
  
  To handle the absolute values of \( y_1 \) and \( y_2 \), we introduce two new variables:
- \( z_1 \geq y_1 \)
- \( z_2 \geq -y_1 \)
- \( z_3 \geq y_2 \)
- \( z_4 \geq -y_2 \)
  
  Thus, the objective becomes:
  
  \[
  \min \max(z_1, z_3)
  \]
- The constraint is:
  
  \[
  \left| x_1 \right| + 2 \max \left( x_1, x_2 \right) \leq 1
  \]
  
  linearize the absolute values and the maximum function. First, introduce:
- \( w_1 \geq x_1 \)
- \( w_2 \geq -x_1 \)
- \( w_3 \geq x_2 \)
- \( w_4 \geq -x_2 \)
  
  Now, for the maximum function:
  
  \[
  \max(x_1, x_2) \leq w_3
  \]
  
  Thus, the constraint becomes:
  
  \[
  w_1 + w_2 + 2w_3 \leq 1
  \]
- The LP formulation for this problem is:
  
  **Objective:**
  
  \[
  \min z_1 \quad \text{subject to} \quad z_1 \geq z_3
  \]
  
  **Subject to:**
  
  \[
  w_1 + w_2 + 2w_3 \leq 1
  \]
  
  \[
  z_1 \geq y_1 \geq 2x_1 + 3x_2
  \]
  
  \[
  z_1 \geq -y_1 \geq -(2x_1 + 3x_2)
  \]
  
  \[
  z_3 \geq y_2 \geq x_1 - x_2
  \]
  
  \[
  z_3 \geq -y_2 \geq -(x_1 - x_2)
  \]
  
  \[
  w_1 \geq x_1 \geq -w_1
  \]
  
  \[
  w_2 \geq x_2 \geq -w_2
  \]
- ### **(b) Formulation of the problem as a Linear Program**
- For each \( y_i - ax_i - b \), introduce two variables:
- \( z_i \geq y_i - ax_i - b \)
- \( z_i \geq -(y_i - ax_i - b) \)
  
  Now the objective becomes:
  
  \[
  \min \max(z_1, z_2, \dots, z_n)
  \]
- The LP formulation is:
  
  **Objective:**
  \[
  \min z
  \]
  
  **Subject to:**
  \[
  z \geq y_i - ax_i - b \quad \forall i
  \]
  
  \[
  z \geq -(y_i - ax_i - b) \quad \forall i
  \]
  
  \[
  a \geq 0, \, b \geq 0
  \]
- ### **(c) Formulation of the problem as a Linear Program**
- introduce auxiliary variables for each \( \alpha_i t + \beta_i \):
- Let \( z_i \geq \alpha_i t + \beta_i \)
  
  Thus, the function becomes:
  
  \[
  f(t) = \max(z_1, z_2, \dots, z_n)
  \]
- introduce auxiliary variables to handle \( |x| \):
- Let \( w_1 \geq x \)
- Let \( w_2 \geq -x \)
  
  Thus, \( f(|x|) = \max(w_1, w_2) \).
- **Objective:**
  \[
  \min \max(w_1, w_2) + \max(y, 0)
  \]
  
  **Subject to:**
  \[
  x + y \leq 4
  \]
  
  \[
  -10 \leq x \leq 10, \quad -10 \leq y \leq 10
  \]
  
  \[
  w_1 \geq x, \quad w_2 \geq -x
  \]
  
  \[
  w_1 \geq \alpha_i |x| + \beta_i \quad \forall i
  \]
- ### **(d) Modifications for \( \alpha_i \geq 0 \)**
  
  **Objective:**
  
  \[
  \min \max(w_1, w_2) + \max(y, 0)
  \]
  
  **Subject to:**
  
  \[
  x + y \leq 4
  \]
  
  \[
  -10 \leq x \leq 10, \quad -10 \leq y \leq 10
  \]
  
  \[
  w_1 \geq x, \quad w_2 \geq -x
  \]
  
  \[
  w_1 \geq \alpha_i |x| + \beta_i \quad \forall i
  \]
  
  \[
  \alpha_i \geq 0 \quad \forall i
  \]
-