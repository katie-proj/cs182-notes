# Lecture 3: Informed Serach and Local Search
## Recap
Problems are represented by states, actions, and sucessor functions. Types of uninformed search methods include DFS, BFS, and variants like IDS.

## Uniform-cost Search
Similar to BFS, but change the order of node expansion. **Uniform-cost search** expands the node ``n`` with the lowest path cosst ``g(n)``.
- optimal because it is like BFS, which is optimal
- not complete because the search could get stuck in a self-loop (zero cost), but it is complete if each action has a cost ``epsilon > 0``
- time and space complexity depends on the optial solution cost ``C*``
- time: ``O(b^(c* / epsilon))``
- space: FILL IN LATER

## Uninformed vs. Informed Serach
**uninformed search**: Only generate successors and distinguish goal from non-goal states  
**informed search**: Use strategies that know whether one non-goal states is more promising than another  

## Informed Search
- evaluation function ``f(n)``: implemented as a priority queue that maintains the fringe in ascending order of f-values
- heuristic function ``h(n)``: estimated cost of cheapest path from node ``n`` to a goal node

### Heuristic Function
Characteristics of ``h(n)``:
1. most common form in which additional knowledge of the problem is imparted to the search algorithm
2. should underestimate the cost to the goal (if heuristic is too costly, then the search should ignore that path)
3. if ``n`` is the goal node, then ``h(n)=0``

## Greedy Best-First Search
Strategy: expand the node closest to the goal, using ``f(n)=h(n)``.
- not optimal
- incomplete (like DFS, it can start down an infinite path and never return to try others)
- worse case time and space complexity is ``O(b^m)`` where ``m`` is maximum depth of search space
- using heuristics improves complexity

## A* Search
Uses an evaluation function ``f(n) = g(n) + h(n)``, where ``g(n)`` is the path cost from start node to ``n`` and ``h(n)`` is the estimated cost of the
cheapest path from ``n`` to the goal. So ``f(n)`` is an estimated cost of the cheapest solution through ``n``.
- optimal and complete, provided ``h(n)`` is admissible, branching factor is finite, and actions costs > 0

### Admissibility of Heuristic
Admissible heuristic -- ``h(n)`` never overestimates the cost to reach the goal because ``g(n)`` is the exact cost to reach ``n`` and ``h(n)`` will not overestimate  
Theorem: A* tree search with an admissible heuristic returns an optimal solution

#### 8 Puzzle Example
state: any configuration of tiles  
cost: # of moves to get from current state to goal state  
Possible heuristics:
1. h1 = # of misplaced tiles
2. h2 = sum of the distances of tiles from their goal positions (Manhattan distance)

### A* using Graph Search
Expand nodes in order of lowest ``f(n)`` cost, do not expand the same node twice (use a "closed set").
- not optimal, even if heuristic is admissible
- optimal, if heuristic is consistent
- graph-search algorithm always discards the newly discovered path, even if it is shorter than the original path

Potential solutions:
1. extned graph search to discard the more expensive of any two paths found to the same node --> more bookeeping required
2. ensure that the optimal path to any repeated state is always the first one followed

#### Consistent Heuristics
A heuristic ``h(n)`` is consistent if for every node ``n`` and every successor ``n'`` of ``n`` generated by action ``a``, the estimated cost of reaching
the goal from ``n`` is no greater than the step cost of getting to ``n'`` plus the estimated cost of reaching the goal from ``n``.  
``h(n) <= c(n, a, n') + h(n')``  
The first goal node selected for expansion must be an optimal solution since all later nodes will be at least as expensive. We can arrive at the goal node via
a suboptimal path, but this path won't be expanded.  
**Consistency implies admissibility**  

## Local Search
Uses a single current state (rather than keeping track of multiple paths) and generally move only to neighbors of that state.
- use very little memory (often a constant amount)
- can often find reasonable solutions in a large or infinite state space for which previous systematic solutions are unsuitable

### Hill Climbing
Pick the next state such that it improves the objective function.
- will only achieve local maxima, may not even find a solution
- objective function can be hard to define, and a non-smooth function may lead to a shoulder solution
Stochastic variants can escape local maxima but still does not guarantee a global maximum.
