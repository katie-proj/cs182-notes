# Lecture 1
AI requires a decision-making agent that takes actions to reach a predefined goal and receives feedback in an environment  
- AI should maximize the expected utility
- environment is not under our control (i.e. noise that is not modeled for the agent)

**agent**: entity that perceives its environment and acts upon that environment
- rational agent selects actions that maximize its expected utility
- the percepts, environemnt, and action space dictate techniques for selecting rational actions

**environment**: the world in which the agent exists and which externally influences the agents' behavior
**actuators**: actions that hte agent can take and control  

Computation and uncertainty are key elements when deciding the solvability of a problem, the type of model and methods to use, and the solution strategy available to us.   

Types of problems:
-	Fully vs partially observable – how much information about the environment is available to the agent
-	Deterministic vs. stochastic – is there randomness involved in the outcome of an agent’s decision, stochasticity in the next state given the current state
-	Episodic vs. sequential – what role does the agent’s history play in decision making 
-	Static vs. dynamic – is the environment changing while the agent makes a decision
-	Discrete vs. continuous – domain of the action space and state space
-	Single-agent vs. multiagent – how many agents are involved  

Types of agents:
- Reflex agent – agent that acts according to a rule whose condition matches the current state
-	Model-based reflex agent – agent keeps track of the part of the world that it can’t see now (uncertainty, future evolution of the state)
-	Utility-based agent – utility function maps a state, or sequence of states, onto a real number (how you reach your goal is also important
-	Learning agents – uses feedback on the problem generation part (formulation of possible actions) to learn which behaviors are desirable
