# Lecture 9
## Normal-Form Game
A game in **normal form** consists of a set of ``N`` players and a strategy set ``S``. For each player ``i``, there is a utility function ``u_i`` that takes in
a strategy pofile and returns the utility: ``u_i(s_1, ..., s_n)`` so the utility may depend on other players' strategies.

### Prisoner's Dilemma
Two men are charged with a crime. If one blames the other, then that person will be freed and the other will be jailed for 9 years. If they both blame the other
person, then they will both be jailed for 6 years. If neither blame each other, they will both be jailed for 1 year.  
- cooperate, cooperate: -1, -1
- cooperate, defect: -9, 0
- defect, cooperate: 0, -9
- defect, defect: -6, -6

No matter what the other player does, you are better off defecting (rational decision). However, the result from both players acting rational is not optimal 
(getting 6 years instead of 1). Here, defection is a **dominant strategy** because there is one strategy that is better, regardless of what the other player does.

### Nash Equilibirum
In a Nash equilibirum, no player wants to unilaterally deviate (each player's strategy is a best response to strategies of others). Formally, Nash equilibrium 
is a vector of strategies ``s = (s_1, ..., s_n)`` such that for al players ``i``, ``u_i(s) >= u_i(s_1, ..., s_{i-1}, s_i', s_{i+1}, ..., s_n)``.
- if one player shifts their strategy but everyone else keeps the same strategy, then that player does not gain any additional utility
- there is no Nash equilibrium in rock-paper-scissors, because there is always a player that is not winning (either losing or tied), so that player will deviate to a winning strategy

### Hotelling Model
Suppose the political spectrum is the real number line. Each voter has a position on the line, and there is a distribution of voters. Players are candidates
who strategically choose positions ``x_1, ..., x_n``. Each candidate attracts the votes of voters who are closest to them (votes split equally in a tie).
- let ``m`` be the median of a distribution
- if ``x_2 < m``, then the best response of candidate 1 is to choose ``x_1 > x_2`` and ``(x_1 + x_2)/2 < m`` to capture the median and more
- symmetrical response if ``x_2 > m``
- if ``x_2 = m``, then the best response of candidate 1 is to choose ``x_1 = m``

## Mixed Strategies
A **mixed strategy** is a probability distribution over (pure) strategies. The mixed strategy of player ``i`` is ``x_i`` where ``x_i(s_i) = P(i plays s_i)``. 
Then the utility of a player is ``u_i(x_1, ..., x_n) = sum of [u_i(s_1, ..., s_n) * product of x_j(s_j)]``, the expected value of utility sums over all strategy profiles and
 for each profile calculates the product of the utility for that profile and the probability of that profile.
 - once we allow mixed strategies, we are guaranteed to have at least on Nash equilibrium in any finite game
