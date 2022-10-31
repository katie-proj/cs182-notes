# Lecture 15 -- Markov Decision Processes
## Markov Decision Processes
MDP consists of:
1. set of states ``S`` with initial state ``s_0``
2. set of actions ``A(s)`` for each state
3. transition model ``P(s'|s,a)`` and transitions are Markovian
4. reward function ``R(s)`` that specifies the reward of each state

A policy specifies an action given the current state. With a fixed policy, and MDP induces a Markov chain.

## Discounted Utilities
We assume an **infinite horizon** and a **discount factor**. We can bound utility using infinite geometric sum formula.

## Bellman Equations
Stat/CS 184 Type Vibez 😎

## Policy Iteration
1. Policy evaluation -- given policy, calculate its utility
2. Policy improvement -- calculate a new policy based on the utility

I was not paying attention :D
