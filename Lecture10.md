# Lecture 10 - AI Game Playing
## Extensive-form Games
- moves are done sequentially, not simultaneously
- game forms a tree
- nodes are labeled by players
- leaves show payoffs

## Subgame-perfect equilibrium
Each subtree forms a subgame. A set of strategies is a **subgame-perfect equilibrium** if it is a Nash equilibrium in each subgame.
- players may be able to improve their equilibrium payoff by eliminating strategies

### Backwards Induction
1. start by looking at the node directly above leaves
2. replace node with payoff (leaf) we know we will get, if the game reaches that node
3. continue until there is one payoff remaining (the solution under subgame-perfect Nash equilibrium)

However, backwards induction to solve subgame-perfect equilibrium can lead to strange outcomes (where payoffs predicted in isolation is much lower than in reality)  

## Zero-Sum Games
Zero-sum means that the net utility is zero (if one player wins, the other loses). A game position is a node in the game tree. Children of a node are positions 
that are reachable in one move. Each leaf specifies a payoff to the max player.

## Minimax Search
```
function MaxEval (node n)
  if n is a leaf then return Payoff(n)
  v := -inf
  for all children n' of n:
    // children are controlled by min player
    v := max(v, MinEval(n'))
  return v
  
function MinEval (node n)
  if n is a leaf then return Payoff(n)
  v := inf
  for all children n' of n:
    v := min(v, MaxEval(n'))
  return v
```
The recursion will go all the way down to the leaves, and the values of the leaves will be propogated back up to the root.  

### Zermelo's Theorem
(Checkers) In any two-player, zero-game, extensive-form game, either white can force a win, or black can force a win, or both sides can force a draw.
- theorem is proved by Minimax search

## Alpha-beta Pruning
We can prune large parts of the search tree that are irrelevant. For a node ``n``, if there's a better node at the same level ``m`` or at a different 
level ``m'``, then optimal play wouldn't choose ``n``.
```
function MaxEval (node n, numbers alpha, beta)
  // max can guarantee >= alpha
  // min can guarantee <= beta
  if n is a leaf then return Payoff(n)
  v := alpha
  for all children n' of n:
    v := max(v, MinEval(n', v, beta))
    if v >= beta then return v
  return v

function MinEval (node n, numbers alpha, beta)
  if n is a leaf then return Payoff(n)
  v := beta
  for all children n' of n:
    v := min(v, MaxEval(n', alpha, v))
    if v <= alpha then return v
  return v
```
Choosing the optimal pruning of the game tree is essentially the same as solving the game. In the worst-case, if the game tree has height ``h`` and branching 
factor ``b``, then we must check ``b^h`` leaves in Alpha-beta purning. Effectiveness of pruning is highly dependent on the order in which states are examined. 

### Heuristic Alpha-beta Search
To reduce computation we can cut off the search at a **horizion** ``d`` and apply an **evaluation function**. We modify a line in pseudocode:
```
if Cutoff(n, d) then return Eval(n)
```
Evaluation function returns an estimate of the payoff at the given node, and should be easy to compute. However, in some nodes the evaluation function may 
be off because a pending move will make a big impact. So we can introduce **quiescense search**, which will only cut off if you are in a **quiescense state** 
(a relative calm, stable state).
