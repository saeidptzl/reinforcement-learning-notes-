# Introduction to Reinforcement Learning

Reinforcement Learning (RL) is a framework for learning how agents should act in an environment in order to maximize long-term reward. RL is different from supervised and unsupervised learning because the agent learns from **interaction**, not from labeled datasets.

## Key Concepts
- **Agent:** The learner or decision maker.
- **Environment:** Everything the agent interacts with.
- **State (S):** A representation of the current situation.
- **Action (A):** A decision taken by the agent.
- **Reward (R):** Feedback signal that indicates how good an action was.
- **Policy (π):** A mapping from states to actions.
- **Return (G):** The total accumulated reward over time.

## Objective
The main objective in RL is to learn a policy π that maximizes the expected return:

$$
G_t = \sum_{k=0}^{\infty} \gamma^k R_{t+k+1}
$$

where \( \gamma \in [0, 1] \) is the discount factor.

## What You Will Learn
This course covers:
- Markov Decision Processes (MDPs)
- Bellman Equations
- Dynamic Programming
- Monte-Carlo Learning
- Temporal-Difference Learning
- Policy Gradient Methods
- Deep Reinforcement Learning

This file contains my notes as I progress through the course.


📂 01-rewards / rewards.md
Rewards in Reinforcement Learning
1. What is a Reward?
A reward 
R
t
R 
t
​	
  is a single numeric value given to the agent at time step t.
It tells the agent how good or bad its last action was.
Positive → desirable behavior
Negative → undesirable behavior
Zero → neutral outcome
Rewards are the only feedback signal the agent receives.
2. Time Steps
RL operates in discrete time steps:
state → action → reward → next state
Continuous-time RL exists, but is not considered in this course.
3. Types of Tasks
Episodic Tasks
Tasks with a clear beginning and end.
Examples: games, maze solving.
Continuous Tasks
Tasks that run indefinitely.
Examples: datacenter cooling, autonomous driving during long operation.
4. Examples of Reward Design
Autonomous Agents (cars, drones, robots)
following the correct trajectory
wasting time
---- crashing
Games
winning
losing
scoring points
HVAC / Energy Optimization
energy consumption
user discomfort
Trading
profit
loss
Recommender Systems
click or engagement
ignored recommendation
Chatbots
user satisfaction
user frustration
Each environment defines its own reward function.
5. Cumulative Reward
The agent’s objective is to maximize cumulative reward, the total sum of rewards across time:
G
=
∑
t
R
t
G= 
t
∑
​	
 R 
t
​	
 
In episodic tasks: cumulative reward is computed per episode
In continuous tasks: reward is accumulated over a defined (possibly rolling) horizon
6. Reward Hypothesis
RL is based on the reward hypothesis:
All goals can be expressed as the maximization of expected cumulative reward.
This principle guides all RL design.
7. Sequential Decision Making
Actions influence not only the immediate reward but also future rewards.
Long-term consequences matter
Rewards may be delayed
Sometimes short-term penalties lead to greater long-term gains
Example: a chess sacrifice that leads to a winning strategy later.
Summary
Rewards define what the agent should achieve.
Cumulative reward defines how the agent judges success.
Sequential decisions link present actions to future outcomes.


