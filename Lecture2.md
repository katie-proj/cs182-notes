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

### Uniformed Search Strategies
**uniformed search**: no idea of whether one "non-goal" state is better than another  
Complexity for uniformed search is described in terms of branch factor ``b``, depth ``d``, maximum length of any path in the state space ``m``
