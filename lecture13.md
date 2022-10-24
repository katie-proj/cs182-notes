# Lecture 13 -- Bayesian Networks
## Conditional Probability 🎲
``P(A|B) = P(A and B)/P(B)``  
Chain Rule: ``P(A_1 and ... and A_n) = P(A_1) * P(A_2|A_1) * ... * P(A_n|A_1, A_2, ...)``  
Bayes Rule: ``P(A|B) = P(B|A)P(A)/P(B)``  

## Bayesian Networks
Model Cause and Effect:
- direct cause A --> B; ``P(B|A)``
- indirect cause A --> B --> C; ``P(B|A), P(C|B)``
- common cause A --> B,C; ``P(B|A), P(C|A)``
- common effect A, B --> C; ``P(C|A,B)``

In a Bayes net, each random variable is conditionally independent of its predecessors given its parents. ``P(x_i|x1,...,x_i-1) = P(x_i|parents(X_i))``. 
The representation of the Bayes net must satisfy conditional independence, and the node ordering affects how compact (# edges) the representation is. 

## Sampling
Draw samples for each event in the Bayes net. **Rejection sampling** rejects any events that is not consistent with the output we are trying to estimate; keep 
the samples that are consistent with evidence. However, rejection sampling can be very inefficient if we are conditioning on evidence that is unlikely to occur.

## Likelihood Weighting
```
function Weighted-Sample(bn, e):
  w = 1, x = initialized from e
  for each variable X_i in X_1, ..., X_n:
    if X_i is an evidence variable with value x_i in e:
      w := w * P(X_i = x_i | parents(X_i))
    else:
      x_i := random sample conditioned on parents
  return x, w
```

probability of sampling ``z`` * weight of sample = joint probability of ``z,e`` ==> unbiased estimator  

When the evidence variables appear later in the ordering, the probability of actually observing the evidence is low (leading to low weights). So likelihood 
weighting is still problematic if observing such evidence should be weighted heavily.
