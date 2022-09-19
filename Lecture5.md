# Lecture 5

## Recap
Motion planning problems require discretization of free space

## Planning and Identification
**planning**: sequence of actions  
**identification**: assignments to variables

## Constraint Satisfaction Problems (CSP)
Defined by a set of variables ``X_1, X_2, ..., X_n``, constraints ``C_1, C_2, ..., C_n``, and assignment ``{X_i = v_i, ...}``. State is defined by variables
``X_i`` with values from a domain D. Goal test is the set of constraints specifying allowable combinations of values for subsets of variables.  

Initial state: empty assignment {}, where all variables are unassigned  
Successor function: value can be assigned to any unassigned variable, provided that it does not conflict with previously assigned variables  
Goal test: whether or not the current assignment is complet  
Path cost: a constant cost (1) for every step  

### Types of Constraints
1. continuous domain -- linear programming, quadratic programming
2. unary constraint -- restricts the value of a single variable ``X_1 != value``
3. binary constraint -- relates two variables, ``X_1 != X_2``
4. global constraint -- constraint involving all variables in the problem 

Every finite-domain constraint can be reduced to a set of binary constraints if enough auxiliary variables are introduced.  

## Improving Search Efficiency
 ### Forward Checking
 A type of filtering. Keep track of domains for unassigned variables and cross off bad options.
 1. assign the variable and remove conflicting values from other variable domains using the constraint graph
 2. continue to the next variable, again removing conflicting values from remaining domains
 3. assign next variable and if its domain is left empty, backtrack

### Arc Consistency
Extend the forward checking concept by following constraints all the way through the constraint graph.

### Minimum Remaining Values
Pick the next node for expansion that has the fewest number of legal values left in its domain.

### Local Search
Start with an initial assignment. Then use the heuristic for choosing a new value for a variable by selecting the value that results in the minimum number
of conflicts with other variables.

### Use Subproblems
Decompose the problem into many subproblems.
 
