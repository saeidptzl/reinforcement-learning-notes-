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


Policies, value functions, Q-values, and models are the core building blocks of RL agents.


