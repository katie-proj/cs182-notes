# Lecture 11
## Stackelberg Games
There is a row player (leader) that commits to playing a row. Column player (follower) observes the commitment of leader. The leader can achieve higher 
utility by playing down.
- randomness helps the leader due to imperfect information

### Stackelberg Equilibrium
For a mixed strategy ``x_1`` of the leader, define the best response set of the follower as ``B_2(x_1) = argmax of s_2 in u_2(x_1, s_2)``. In a **strong 
Stackelberg equilibrium (SSE)**, the leader plays a mixed strategy in ``argmax of x_1 (max of s_2 in u_2(x_1, s_2))``.
- ``s_2`` is best response to ``x_1``
- choose a (mixed strategy for the leader given the (follower responds with ``s_2`` to the (leader's strategy ``x_1`` that maximizes the leader's utility)))
SSE can be computed in polynomial time through a linear program:
```
max sum over s_1 of x(s_1)u_1(s_1, s_2*))
st. for all s_2, sum over s_1 of x(s_1)u_2(s_1, s_2*)) >= sum over s_1 of x(s_1)u_2(s_1, s_2)
sum over s_1 of x(s_1) = 1    <-- x is a mixed strategy, so probabilities must sum to 1
```
``s_2*`` is the pure strategy of the follower and best response. 

## Security Games
- set of targets ``T = {1,...,n}``
- set of ``m`` security resources ``\Omega``
- set of schedules ``\sigma \subseteq 2^T``
- resource ``\omega`` can be assigned to one of the schedules in ``A(\omega) \subseteq \sigma``

Attacker chooses one target to attack after observingt the leader's committment. The mixed defender strategy induces coverage probabilities ``c = (c_1,...,c_n)``. 
