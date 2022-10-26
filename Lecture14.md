# Lecture 14 -- Hidden Markov Model

## Markov Chains
Infinite process described by random variables ``X_0, X_1, ...``.
- Markov assumption: ``P(X_t | X_0, X_1, ..., X_{t-1}) = P(X_t | X_{t-1})``
- stationary assumption: for all t, t' ``P(X_t | X_{t-1}) = P(X_t' | X_{t-1}')``

## Hidden Markov Model
Sometimes we can't directly observe the state of the world, but rather only observe evidence. A HMM satisfies same assumptions as in Markov chains, with the 
additional **Markov sensor assumption** that current evidence is conditionally independent of everything else given the current state.
- Markov sensor assumption: ``P(E_t | X_0, ..., X_t, E_0, ..., E_t) = P(E_t | X_t)``

## Inference
1. Filtering ``P(X_t | e_1, ..., e_t)``
2. Prediction ``P(X_{t+k} | e_1, ..., e_t)``
3. Smoothing ``P(X_k | e_1, ..., e_t), k < t``
4. Max likelihood ``argmax P(x0, ..., x_t | e_1, ..., e_t)`` (most likely sequence given evidence observed)

### Filtering
We want an iterative algorithm that would computer ``P(X_{t+1} | e_1, ..., e_{t+1})`` given ``e_{t+1}`` and previous calculation of ``P(X_t | e_1, ..., e_t)``. 
Use Bayes' rule, but always condition on ``e_1, ..., e_t``. 

``P(X_{t+1} | e_1, ..., e_{t+1}) \prop P(e_{t+1} | X_{t+1}) * sum over x_t [P(x_t | e_1, ..., e_t) * P(X_{t+1} | x_t)]``

### Prediction
Prediction follows from filtering.

### Maximum Likelihood
We want an interative algorithm to compute the most likely sequence of states given the evidence.

``max P(x_0, ..., x_t, X_{t+1} | e_1, ..., e_{t+1}) \prop P(e_{t+1} | X_{t+1}) * max P(X_{t+1} | x_t) * max Pr(x_0, ..., x_t | e_1, ..., e_t)``
