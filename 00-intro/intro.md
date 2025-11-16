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


# Reinforcement Learning: Agent, Environment, and Core Concepts

## 1. The Agent–Environment Interaction

At each time step \( t \):

### Agent
The agent is in a state \( S_t \), which is an exhaustive description of the system at that time.  
From this state, it selects an action \( A_t \) that is feasible in that state.

### Environment
Given the state–action pair \( (S_t, A_t) \), the environment:
- Provides a reward \( R_{t+1} \)
- Produces the next state \( S_{t+1} \)

The loop is:
\[
S_t \rightarrow A_t \rightarrow R_{t+1} \rightarrow S_{t+1}
\]

---

## 2. Episodes

An episode consists of a full sequence of interactions:
\[
S_0, A_0, R_1, S_1, A_1, R_2, S_2, A_2, R_3, \dots
\]

Episodes terminate when a terminal state is reached.

---

## 3. Observations and History

At each step, the agent receives an observation \( o_{t+1} \).

### Fully Observable Environments
\[
S_{t+1} = o_{t+1}
\]

### Partially Observable Environments
The agent cannot directly observe the true state.  
It must infer it from the history:
\[
H_t = O_1, R_1, A_1, \dots, A_{t-1}, O_t, R_t
\]
State estimation:
\[
S_t = f(H_t)
\]

---

## 4. Components of an Agent

An RL agent may include the following components:

### 1. Policy (always present)
A policy is the agent’s behaviour function mapping states to actions.

The RL objective is to find the optimal policy that maximizes cumulative reward.

Types of policies:
- **Deterministic:**  
  \[
  a = \pi(s)
  \]
- **Stochastic:**  
  \[
  \pi(a|s) = \mathbb{P}(A_t = a \mid S_t = s)
  \]

---

### 2. Value Function (optional)
A value function provides a quantitative measure of how good each state is.

---

### 3. Q-Value Function (optional)
A q-value function provides a quantitative measure of how good each state–action pair is:
\[
Q(s,a)
\]

---

### 4. Model (optional)
A model is the agent’s internal representation of the environment, used to predict next states and rewards.

---

## Summary
- The agent selects actions; the environment responds with rewards and new states.  
- Learning occurs through repeated episodes.  
- Observability determines whether the agent uses states directly or reconstructs them from history.  
- Core RL components include the policy, value function, q-value function, and model.  
- The ultimate objective is to learn an optimal policy that maximizes cumulative rewards.



