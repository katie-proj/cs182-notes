# Lecture 2
## Classical Planning Assumptions
- finite state environemtn -- set of states and actions is finite, changes occur only in response to actions by the actor itself
- determinism -- no uncertainity, we can predict with certainty what state will be produced if action is performed

## Problem Formulation
What are the states (start state, goal state), actions, successor funciton that leads from one state to another based on the action taken?  

Problem comprises of: 
- initial state
- actions -- <action, successor>
- goal test -- question to determine if goal has been achieved
- path cost  

State Space Graphs
- each state can only occur once
- there is not necessarily only one path to get to each state  

## Search
**search strategy**: choice of which state to expand (depends on choice of successor function)  
Measures of search performance: completeness (finding a solution when there is one), optimality (finding the optimal solution), time complexity, space complexity  

Search steps:
1. choose state
2. goal test
3. expand state
4. termination conditions -- soltuion found or no more states left to expand

Search tree:
- nodes correspond to "plans" not states
- leaves are the goal states  

```
function Tree-Search(problem, strategy)
set of frontier nodes contains the start state of problem

loop
  if there are no frontier nodes:
    return failure
  choose a frontier node for expansion using strategy
  if the node contains a goal:
    return the corresponding solution
  else:
    expand the node and add the resulting nodes to the set of frontier nodes
```

### Uniformed Search Strategies
**uniformed search**: no idea of whether one "non-goal" state is better than another  
Complexity for uniformed search is described in terms of branch factor ``b``, depth ``d``, maximum length of any path in the state space ``m``

#### Breadth-first Search
**BFS**: all nodes are expanded at a given depth in the search tree before any nodes at the next level are expanded, use a FIFO queue to keep track
of which node to visit next
- BFS is complete and optimal if measured in # of steps taken (under certain conditions)
- space complexity: ``O(b^d)``
- time complexity: ``O(b^d)``
- exponential complexity search problems cannot be solved by uniformed methods for any but the smallest problem instances

#### Depth-first Search
**DFS**: explore tree down to the root using a rule (such as leftmost branch first) before backing up, using a LIFO queue to keep track of which node to visit next
- DFS is not complete and not optimal
- stores only a single path from the root to a lead node, along with unexpanded sibling nodes for each node on the path --> space complexity: ``O(bm)``
- time complexity: ``O(b^m)``

#### Variations on BFS and DFS
1. Depth-limited search -- set a limitation on depth exploration before moving onto sibling nodes
2. Iterative deepening -- iteratively deepen the depth limit (rather than keeping it constant); complete, not optimal, ``O(bd)`` space copmlexity, ``O(b^d)`` time complexity

### Problem of Repeated States
The desirable properties of BFS and DFS depend on finite branching factor and search tree depth. Repeated states and cycles can lead to an infinite state space.  

We want to detect repeated states before expanding by keeping visited states in memory. 

#### Graph Search
```
function Graph-Search(problem, strategy)
set of frontier nodes contains the start state of problem

loop
  if there are no frontier nodes: 
    return failure
  choose a frontier node for expansion using strategy, and add its state to the explored set
  if the node contains a goal:
    return the corresponding solution
  else:
    expand the node and add the resulting nodes to the set of frontier nodes, only if not in the explored set of visited states
```
