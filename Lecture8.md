# Lecture 8 - Integer Programming

## Integer programming
The feasibility problem is to find values for variables ``x_1, ..., x_l`` such that the ``sum from j=1 to l of a_ij * x_j <= b_i``. Integer programming is the 
same as linear programming, but the variables must have integer values (which ruins convexity of linear programming problem).  
Examples of feasibility problems:
- sudoku
- fair division (n players and m items, each player assigns a certain value to each item, goal is to partition items into bundles such that no player would want to switch bundles because they value their bundle the highest

Integer programming optimization will optimize a linear objective function while subject to the constraints of feasibility problems

### Maximimin Share (Fair Division)
The Maximin share (MMS) guarantee of player aims to maximize the minimum value of a bundle. Suppose the minimum value is ``D``, then we want to maximize ``D``
but add an upper bound on ``D`` as part of the linear constraint.  
- ``MMS(i)`` is the maximum minimum value for each player ``i``
- MMS allocation checks if the value player i has for its bundle >= ``MMS(i)`` <--- feasibility problem
- this leads to n+1 linear programs solved, n as a result of finding ``MMS(i)`` for all players and 1 to solve feasibility problem

### Kidney Exchange
Cycle-clover: Given a directed graph ``G``, find a collection of disjoint cycles of length <= ``L`` in ``G`` that maximizes the number of covered vertices

## Comparing Integer Programming and Linear Programming
Optimal under IP <= LP because any solution to IP will be solution to LP. 

### Branch and Bound
The linear program relaxation gives an "admissible" heurisitc, and linear programs can be solved in polynomial time. The branch and bound algorithm:
1. use a search tree to assign the variables one by one
2. at each node, solve the LP relaxation
3. backtrack if there is no solution, or if the solution is worse than the best known, or if the solution is integral
