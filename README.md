# EXP-05---Prescriptive-Analytics---Solving-a-Linear-Programming-Problem-Using-PuLP

## Aim :
To solve a simple linear programming problem using Python’s PuLP library, interpret the optimization results, and provide insights for decision-making.

## Tools Required :
1. Python Programming Language: The main language used for solving the linear programming problem.
2. PuLP Library: A Python library used to model and solve linear programming problems.
3. Solver: A solver (such as CBC, GLPK, or CPLEX) that PuLP uses to find the optimal solution.

## Procedure :

### Step 1: Install Required Libraries:
- Install the PuLP library using the following command:

### Step 2: Import Libraries:
- Import necessary libraries, including LpProblem for creating the linear programming problem, LpVariable for defining decision variables, and LpMaximize for setting the objective function to maximization.
  
### Step 3: Define the Linear Programming Problem:
- Create a linear programming problem instance using LpProblem(). Set the objective to maximize the profit.
  
### Step 4: Define Decision Variables:
- Define the decision variables (e.g., x for the number of units of Product A and y for Product B) using the LpVariable() function, and set their lower bounds to 0 (non-negative).
- Set the Objective Function and Constraints:

### Step 5: Define the objective function 
- Using the += operator, and add the constraints for labor and machine time using the same operator.
- Solve the Problem and Display Results:

### Step 6: Use the solve() method 
- To find the optimal solution. 
- Print the status, values of the decision variables, and the total profit from the optimal solution.

## Program :

```
# Import PuLP library
from pulp import LpMaximize, LpProblem, LpVariable, lpSum, LpStatus

# Create the linear programming problem (maximize profit)
problem = LpProblem("Maximize_Profit", LpMaximize)

# Decision variables: number of units to produce of Product A and Product B
x = LpVariable("x", lowBound=0, cat='Continuous')  # Product A
y = LpVariable("y", lowBound=0, cat='Continuous')  # Product B

# Objective function: Maximize profit
problem += 50 * x + 40 * y, "Total Profit"

# Constraints: labor and machine time
problem += 3 * x + 2 * y <= 100, "Labor constraint"
problem += 2 * x + 4 * y <= 80, "Machine time constraint"

# Solve the problem
problem.solve()

# Output the results
print(f"Status: {problem.status}, {LpStatus[problem.status]}")
print(f"Units of Product A to produce: {x.varValue}")
print(f"Units of Product B to produce: {y.varValue}")
print(f"Total Profit: ${problem.objective.value()}")

```
## Outputs :

![image](https://github.com/user-attachments/assets/fefb26cb-b51b-4927-870b-8e4a0b5931ae)


## Result :
The linear programming model successfully identifies the optimal production plan, suggesting the company should produce 20 units of Product A and 10 units of Product B, resulting in a maximum profit of $1300.
