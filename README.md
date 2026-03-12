# Knapsack_solver
Dynamic programming based solver for 0-1 knapsack problems as fractional "between 0-1" knapsack problems.
The algorithm is not fancy as it implements the standard dynamic programming algorithm running in $O(nW)$ time, where $n$ is the number of items, and $W$ is the knapscak capacity.

# The 0-1 knapsack problem
Given is $n$ items. We denote by $[n]$ the set of the first $n$ integers. Each item $i$ has a profit $p_i$ and a weight $w_i$ and the knapsack has a capacity $W$. The task is to select a subset $S\subseteq [ n ]$ of the items, such that $\sum_{i\in S}w_i\leq W$ and such that $\sum_{i\in S}p_i\geq \sum_{i\in P}p_i$ for all $P\subseteq [n]$. This  is solved using dynamic programming in the `solve_knapsack`-function.

# The fractional 0-1 knapsack problem
Here we are again given $n$ items but we can now add fractions of items to the items. The problem can be solved by first sorting the items such that $\frac{p_1}{w_$}\geq \frac{p_2}{w_2}\geq \cdots\geq \frac{p_n}{w_n}$

