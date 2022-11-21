# Lecture 21 -- Value Alignment
## Three Laws of Robotics (Asimov)
1. Don't harm humans
2. Obey orders
3. Protect Yourself

## Ethical Robots
Environment includes a robot, human, and a hole that can be snesed by the robot but not the human
```
if for all robot actions, the human is equally safe:
  output safe actions
else:
  output action(s) for least unsafe human outcome(s)
```
What should the robot do when there are two humans in danger? The robot may become indecisive in choosing who to save.

## Trolley Problem
The ethical dilemma manifests in real life when discussing autonomous vehicles. Social dilemma finds that morality of sacrifice but practice of sacrifice 
of yourself diverge from each other. 

## Decision Making Framework
1. Data collection
2. Learning -- learning what people would prefer even if data for the dilemma is never collected, creating predicted votes
3. Aggregation -- retrieve winning alternative after ranking predicted votes

Voting rule should be robust to noise such that the output ranking from the true profile is the the same as the ranking from the noisy profile.
