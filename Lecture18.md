# Lecture 18
## Linear Classification
A hypothesis is defined by ``h_w(x) = Threshold(w x)``, where Threshold(z) = +1 if z>=0 and Threshold(z) = -1 if z < 0. A **linear separator** can be found 
via a linear feability program:
```
find w such that
for all i in D+, w x^(i) >= 0
for all i in D-, w x^(i) <= -\epsilon
```

## Perceptron
Learning rule: for each example (x,y), classify \hat y = Threshold(w x) and if \hat y \neq y, update w = w + y x. 

### Support Vector Machines
A separator with farther margins from data points will generalize better. SVM finds a maximum margin separator, where the margin is defined by support vectors. 
It suffices to solve the quadratic program:
```
max alpha of [sum over j of alpha_j - 0.5*sum over j,k of alpha_j alpha_k y^(j) y^(k) (x^(j) x^(k)) such that
sum over j of y^(j) alpha_j = 0
for all j, alpha_j >= 0
```

## Non-Separable Data
If data is non-separable, the Perceptron algorithm will not converge because it doesn't stop making mistakes (continue updating weights, will not converge). 
Howerver, the algorithm may converge if initial data examples are not separable but later examples are separable (once you get to separable data, you stop 
making mistakes and converge). 

### Higher Dimensions
When data is not linearly separable, we can map data to higher dimensions.

### Soft Margin
Rather than have a separator with no mistakes and small margins, we prefer a separator with few mistakes and large margins.
- possible to enable soft margins by introducing slack variables into the SVM objective and constraints

### Logistic Activation Function
Threshold function is very decisive. Instead, we use a logistic/sigmoid function, which is smoother. We interpret the output of the sigmoid function with 
input w x as the probability that the label of x is 1. 

## Gradient Ascent
Converge to optimal solution by moving weights in direction of the gradient.
