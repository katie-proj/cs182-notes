# Lecture 6
## Recap
Constraint Satisfaction Problems search to solve identification (or assignment) problems. Types of constraints are unary, binary, and global. 
Solving CSPs can be made easier with (1) fail fast philosophy (e.g. arc consistency, variable, ordering, minimum values remaining), (2) local search, (3) 
structure (e.g. CSP as a tree)

## Multi-Robot Systems 🤖
We are interested in how the state ``x`` evolves over time according to ``f(x)``
- consensus = two agents reaching same point
- collision avoidance = two agents not colliding

Equilibrium point ``f(x*) = x*``

### Types of Systems
**collective swarm**: agents act independently, minimal need for knowledge about other members of the system  
**intentionally cooperative**: have knowledge of the presence of other robots in the environment; act together based on the state, actions, or capabilities
of their teammates in order to accomplish the same goal 

### Encoding Relationships
Graph ``G = (V,E)`` 

### Communication Architectures
stigmergy: sensing signals in the environment that are left behind by other agents (graph with environment as a separate node, all agent nodes connected to it)  
passive: agents sense each other but do not explicitly communicate information (edges with direction, may only be 1-way)  
explicit: agents do share information (highly connected bidirectional edges)    

### Examples
1. foraging/coverage -- weakly cooperative, stigmergy, decentralized
2. flocking/formations -- passive
3. box pushing and cooperative manipulation -- explicit
4. traffic control and multi-robot path planning -- explicit

## Dynamics
As a robot moves, its neighbors and the environment changes. Dynamics allows us to describe individual behavior. 

### Graph Theory
- adjacency matrix captures the influence of agents' states on one another, telling the underlying graph structure and topology
- raising adjacency matrix ``A`` to the ith power results in a matrix that shows how information propogates after i steps
- Laplacian = degree out of graph - adjacency matrix

### Gradient Based Control
``x(t+1) = x(t) + \alpha u(t)``
