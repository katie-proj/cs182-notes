# Lecture 20
## Unfairness
AI algorithms are supposedly unbiased, but they are trained on data that may encode bias. 

## Queen Cynthia Dwork 🤩

## Individual Fairness
Randomized classifier M, metric on individuals d, and metric on distributions over outcomes D. M satisfies the **Lipschitz property** if for all individuals 
x,y, ``D(M(x), M(y)) <= d(x,y)``. Two individuals who are similar according to d should also be similar under D.  
We also want to minimize a loss function, leading to an optimization problem:
```
\mu_x(a) = P(x is assigned to a)
min sum over individuals [ sum over assignments [ \mu_x(a) * L(x,a) ] ] such that
for all individuals x,y, D(\mu_x, \mu_y) <= d(x,y)
for all individuals x, \mu_x is a valid distribution
```

### Choices for metric D
1. total variation for distributions: D(P,Q) = 1/2 * sum over assignments a ( |P(a) - Q(a)| )

### Envy-freeness
Each individual x has a utility u_xa for each outcome a. A randomized classifier M is **envy-free** if and only if for all individuals x,y the expected utility 
of outcomes for x over x's distribution is better than the expected utility for of outcomes for x over y's distribution. 
- evny-freeness isn't useful in situatiosn where there is a desirable and an undesirable outcome

## Group Fairness
Assume we are making a binary decision \hat Y and there is a legally protected attribute G.  
**Demographic parity**: P(\hat Y = 1 | G = 0) = P(\hat Y = 1 | G = 1)
- demogrpahic parity is flawed because it is possible that unqualified candidates are accepted 

**Equalized odds**: P(\hat Y = \hat y | G = 0, Y = y) = P(\hat Y = \hat y | G = 1, Y = y)
- equalized odds and demographic parity are incomparable

## Risk Scores
Each person has a feature vector \sigma. p_\sigma = fraction of people with feature vector \sigma and a true positive label. A **risk assignment** is an 
assignment of people to bins, where each bin b is labeled with a score v_b = P(positive label). 
1. **Calibration within groups**: achieved when for each group G and each bin b, the expected number of members of group G in b who belong to the positive class is a v_b fraction of the expected number of members of group G assigned to b
3. **Equalized odds**: requires that the average score assigned to members of group 0 who belong to the negative class would be the same as the average score assigned to members of group 1 who belong to the negative class

### Achieving calibration and equalized odds
Occurs when either:
1. perfect prediction (either p_\sigma = 0,1) -- then create two bins 0,1 with respective risk scores 0,1
2. equal base rates (two gorups have the same fraction of members in the positive class)

**Theorem**: If a risk assignment satisfies calibration and equalized odds, the instance must allow for perfect prediction or have equal base rates.
