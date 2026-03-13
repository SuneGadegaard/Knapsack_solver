# Knapsack_solver
Dynamic programming (DP) based solver for 0-1 knapsack problems and the standard "sorting based" algorithm for fractional "between 0-1" knapsack problems.
The DP algorithm is not fancy as it implements the standard dynamic programming algorithm running in $O(nW)$ time, where $n$ is the number of items, and $W$ is the knapscak capacity.
The only performance improvements are a simple check that removes items with negative profits and then vectorization using `numpy`.

## The 0-1 knapsack problem
Given is $n$ items. We denote by $[n]$ the set of the first $n$ integers. Each item $i$ has a profit $p_i$ and a weight $w_i$ and the knapsack has a capacity $W$. The task is to select a subset $S\subseteq [ n ]$ of the items, such that $\sum_{i\in S}w_i\leq W$ and such that $\sum_{i\in S}p_i\geq \sum_{i\in P}p_i$ for all $P\subseteq [n]$. This  is solved using dynamic programming in the `solve_knapsack`-function.

## The fractional 0-1 knapsack problem
Here we are again given $n$ items but we can now add fractions of items to the items. The problem can be solved by first sorting the items such that $\frac{p_1}{w_1} \geq \frac{p_2}{w_2}\geq ... \geq \frac{p_n}{w_n}$. Then we find the break item $s$ such that $\sum_{i=1}^{s-1}w_i\leq W$ and $\sum_{i=1}^sw_i>W$. The solution is then given by adding items $i=1,...,s-1 $ fully to the knapsack and only $\frac{W-\sum_{i=1}^{s-1}w_i}{w_s}$ of the $s$'th item.

## Example
To solve a 0-1 knapsack problem, one simply
``
import time  # For timing the algorithms
import KPdp as Knapsack  # Provides the algorithms

kpsolver = KPsolver()  # Create a KPsolver-object

# Data for the instance
p = [27, 18, 43, 40, 55, 15, 10, 91, 90, 95]  # Profits
w = [20, 2, 16, 30, 19, 42, 2, 21, 13, 2]  # Weights
cap = 80  # Capacity

# Set the data in the object
psolver.setData(len(p), p, w, cap)

start = time.time()
opt_value, opt_solution = kpsolver.solve_knapsack()  # Solve the knapsack problem
print(f'Total time for DP-algorithm is {time.time() - start} seconds')
print (f'Optimal solution value is {opt_value}')  # Print the optimal objective function value
print(f'Optimal consists of items: {opt_solution}')  # Print indices of included items
``
