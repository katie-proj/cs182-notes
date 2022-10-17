# Lecture 12
## Social Choice
We will focus on expressing choice via rankings.
### Plurality 🥇
Each person votes for a single alternative alternative, and the alternative with the most points wins. 
- winner is the person who gets the most first-place votes wins

### Borda Count
Each voter awards ``m-k`` points to the alternative placed in the ``k``th position, where ``m`` is the # of alternatives.
- sum the number of points based on the rankings made across all voters

### Single Transferble Vote (STV)
Votes are tabulated in rounds, where in each round the alternative with the lowest plurality scores is eliminated. The last alternative left standing is the winner.
- once an alternative has been eliminated, then the next desirable alternative takes its place (e.g. if someone ranks B first and C second, but B gets eliminated, then C becomes first-rank)

## Condorcet Paradox 🍳 🥚
- voter 1 ranks: A, B, C
- voter 2 ranks: C, A, B
- voter 3 ranks: B, C, A  

Even though individual preferences are acyclic, the preferences of the majority is cyclical. A beats B, C beats A, B beats C.

### Condorcet Consistency
A **Condorcet winner** is an alternative that defeats every other alternative in a head-to-head majority comparison. A rule is **Condorcet consistent** if it 
always selects a Condorcet winner whenever it is presented with a profile that contains one.
- to put A and B in a head-to-head majority comparison, check the # of people who rank A above B and the # of people who rank B above A
- neither plurality, Borda Count, nor STV is Condorcet consistent

## Llull's Rule 🙏 ⛪
Each alternative receives one point for each head-to-head comparison it wins (as well as for tied comparisons). This is Condorcet consistent.
- the Condorcet winner will receive ``m-1`` points when there are ``m`` candidates because, by definition, it beats all other alternatives

## Dodgson's Rule 🖋️ 🎩
The **Dodgson score** of an alternative X is the minimum # of swaps between adjacent alternatives needed to make X a Condorcet winner; select an alternative with minimum score
- the lower the score, the closer the alternative is to the Condorcet winner
- Condorcet consistent because it defines for each alternative the distance from Condorcet winner (e.g. Condorcet winner has score 0, ...)
- NP-hard to compute 😲

### Independence of Clones
A subset of alternatives ``K`` is a set of **clones** if no voter ranks any alternative outside of ``K`` between two alternatives of ``K``.
- clones are adjacent to each other in every voter's ranking
- under plurality, cloning a candidate may prevent them from winning (spoiler candidate)  

A voting rule is **independent of clones** if and only if it satisfies the following conditions:
1. an alternative that is a member of a set of clones wins if and only if some member of that set of clones wins after a member of the set is eliminated
2. an alternative that is not a member of a set of clones wins if and only if that same alternative wins after any clone is eliminated

STV is independent of clones because you can think of clones being eliminated and their ranking being transferred to the remaining clones.
