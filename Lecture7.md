# Lecture 7 - Convex Optimization

## Minimum Optimization 
Interested in problems of the form ``min x: f(x)`` such that ``x is in F``. Here
- ``x`` is the optimization variable
- ``F`` is the feasible set
- ``x*`` is an optimal solution if ``f(x*) <= f(x)`` for all ``x``

Examples:
1. least-squares regression
2. weber point 

## Convex Optimization
Specialization of a general optimization problem such that ``f`` is a convex function and the feasible region ``F`` is a convex set.  

### Convex Set
``F`` is a convex set if for all ``x, y in F`` and ``theta in [0,1]``, ``theta*x + (1-theta)*y in F`` <-- for every two points, the line connecting them is contained in the set
- intersection of convex sets is also a convex set
- linear inequalities form a convex set

### Convex Function
``f`` is a convex function iff for any ``x,y in R^n`` and ``theta in [0,1]``, ``f(theta*x + (1-theta)*y) <= theta*f(x) + (1-theta)*f(y)``
- graph of the function ``f`` between two points on the function lies below the straight line created by connecting those two points
- for univariate functions (``R -> R``) that are twice differentiable, then ``f''(x) >= 0`` means ``f`` is convex
- ``f`` is concave iff ``-f`` is concave <-- we only need to know how to solve minimization problems because maximimum optimization is equivalent to minimizing the negative of that problem

## Linear Programming
In the **max flow problem**, we are given a directed graph ``G = (V,E)`` with a source ``s`` and a sink ``t``. For each node, we must have flow in = flow out.

## Global and Local Optimality
- ``x`` is globablly optimal if ``x in F`` and for all ``y in F``, ``f(x) <= f(y)``
- ``x`` is locally optimal if ``x in F`` and for all ``y in F`` such that ``||x - y|| <= R``, ``f(x) <= f(y)``  

**Theorem**: for a convex optimization problem, all locally optimal points are globally optimal. The **gradient descent** algorithm follows the objective
function downwards until it reaches a global minimum. It cannot get stuck at a local minimum due to the theorem.
