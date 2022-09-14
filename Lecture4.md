# Lecture 4: Motion Planning
## Recap
Informed search occurs when you search a state space efficiently and optimally. Methods: Greedy BFS, A*, optimality of A*

## Motion Planning
**Discretize the environment**

### Motion Planning Problem
What series of motions will get the robot to the goal? We want to find a series of valid configurations that move the object from source to destination.
- agent has a configuration space ``C``
- set of obstacles ``C_obs``
- initial configuration ``q_init`` and goal configuration ``q_goal``

Searching through state-space is very similar to finding a path from intial state (root of tree) to goal state (leaf of tree). We are interested in an 
algorithm that is complete (terminates in finite time, returns a solution when one exists).

### Discretizing the Space
**Cell decomposition** goes from free space to graph search. Must satisfy the following properties:
1. Accessibility -- computing a path from one point to another inside a cell must be trivially easy
2. Representation -- adjacency information for the cells can be easily extracted to build the roadmap (the edges between nodes on graph)
3. Querying -- for any two points, it should be efficient to determine which cells contain them

#### Vertical Cell Decomposition
Draw vertical lines from vertices on configuration
- 1-cell acts as a buffer cell
- 2-cell typically has a triangular or trapezoidal shape

#### Veisiblity Graph
A visibility graph results in the optimal shortest path roadmap. Two edge types:
1. Reflex vertex -- A polygonal vertex for which the interior angle (in ``C_free``) is > pi
2. Bitangent edges -- mutually visible vertices are connected

Construction complexity is ``O(n log(n) + m)`` where ``n`` = # vertices and ``m`` = # edges. 

### Sampling-based Methods
#### Probabilistic RoadMap (PRM Algorithm)
1. sample N points unfiormly at random from ``C``
2. connect each pair with a straight trajectory
3. delete all vertices and edges that lie in the obstacle set ``C_obs``
4. return the reamining roadmap ``G=(V,E)``

Probabilistically complete: probability of returning a soluiton approaches 1 as the number of samples increases. 

#### Rapidly-exploring Random Tree (RRT Algorithm)
Exploring new areas of the environment by growing branches in a random fashion from already sampled locations. It is complete but not optimal.

#### RRT* Algorithm
1. sample
2. select best parent node (minimize cost from the root)
3. find new lower cost paths
4. rewire tree

Complete and optimal.
