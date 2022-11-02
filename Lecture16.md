# Lecture 16 -- Reinforcement Learning
## Passive RL
Goal: estimate utility of each state ``s`` for fixed policy `pi`  
We observe the reward `R(s)` when visiting state `s`. We estimate the tranisiton probability by observing how many times `s'` is reached when taking action 
`pi(s)` in `s` and normalizing. Compute estimate of utility = `U(s) = R(s) + gamma * sum over s' [P(s'|s, pi(s)) * U(s')]`

## Temporal-Difference Learning
Each time a transition from `s` to `s'` is encountered, update `U(s) = (1-alpha)U(s) + alpha[R(s) + gamma*U(s')]`. The learning rate `alpha` depends on the 
number of times state `s` was visited (`k_s`). If `alpha` decreased appropriately as `k_s` increases, then `U` will converge to the true utility based on 
fixed policy `pi`.

## Monte Carlo Redux
Goal: learn an approximately optimal policy  
Instead of a fixed policy, we take a random action each step. We estimate `U(s) = R(s) + gamma * max over a sum over s' [P(s'|s,a) * U(s')]`

## Q-Learning
If we had an estimate `Q(s,a)` for every state-action pair, then we could choose `pi(s) = argmax over a Q(s,a)`. 

## Exploration vs. Exploitation
- epsilon greedy: w/p epsilon act randomly, w/p 1-epsilon act greedily
- softmax: create probability distribution for taking an action
