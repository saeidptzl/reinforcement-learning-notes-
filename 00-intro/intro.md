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



# Multi-Armed Bandits and RL Elements

## 1. RL Elements

A reinforcement learning problem contains:
- **Agent**: the entity that selects actions.
- **States** \( S_t \): complete descriptions of the system.
- **Actions** \( A_t \): possible decisions the agent can take.
- **Environment**: provides rewards and transitions the agent to the next state.
- **Goal**: maximize cumulative reward over time.

The interaction loop:
\[
S_t \rightarrow A_t \rightarrow R_{t+1} \rightarrow S_{t+1}
\]

---

## 2. One-State Simplification

In some simplified RL settings:
- There is only one state, or the environment always returns the agent to the same state:
\[
S_t = S_{t+1}
\]

This reduces the problem to repeated action–reward interactions.

---

## 3. RL vs Multi-Armed Bandits

### Full RL Episode:
\[
S_0, A_0, R_1, S_1, A_1, R_2, S_2, A_2, \dots
\]

### Bandit Episode:
\[
(S_0)\ A_t R_t
\]

Bandits have:
- One state
- Multiple actions
- One reward per episode

---

## 4. Purpose of Multi-Armed Bandits

Multi-armed bandits allow us to study:
- Reward structures
- Decision making under uncertainty
- The exploration–exploitation dilemma

They simplify RL to its core components.

---

## 5. One-Armed Bandit (Slot Machine)

A single-lever machine produces a reward each time it is pulled.  
In RL, the setting assumes many trials to understand the reward pattern.

---

## 6. Multi-Armed Bandits (k-Armed)

The agent has:
- \( k \) different actions (arms)
- One state
- Each action provides rewards following a probability distribution

Goal:
\[
\text{maximize cumulative reward over episodes}
\]

---

## 7. Applications of Bandits

- Online advertising and content selection  
- Medical treatment allocation  
- Server/job scheduling  
- A/B testing

---

## 8. Clinical Trial Example

Each patient corresponds to an episode:
- Treatment choice = action  
- Patient outcome = reward  

Illustrates the exploration–exploitation dilemma.

---

## 9. Action Values in Bandits

Define the true value of an action:
\[
q_*(a) = \mathbb{E}[R_t \mid A_t = a]
\]

This is the expected reward of action \( a \).  
The agent must estimate these values over time.


# Action-Value Estimation and Exploration Strategies in k-Armed Bandits

## 1. Sample-Average Action-Value Estimation

The true value of an action \( q_*(a) \) is unknown.  
It can be estimated using the sample-average method:

\[
Q_t(a) = \frac{\sum_{i=1}^{t-1} R_i \mathbf{1}_{A_i = a}}{\sum_{i=1}^{t-1} \mathbf{1}_{A_i = a}}
\]

This is the average reward obtained from action \( a \) up to time \( t \).  
The estimate is updated every time a new reward is collected.

---

## 2. Clinical Trial Example

- Reward = 1 if treatment is effective, 0 otherwise  
- Initial estimates start at 0  
- A random policy is used  
- Over many episodes, the estimated value of each treatment converges to its true mean reward

Example after 12 trials:
- Pink: \( Q = 0.25 \)  
- Yellow: \( Q = 0.75 \)  
- Blue: \( Q = 0.50 \)

---

## 3. Greedy Policy

The greedy policy selects:

\[
A_t = \arg\max_a Q_t(a)
\]

This policy exploits current knowledge but does not explore other actions.  
It may get stuck with suboptimal actions.

---

## 4. Exploration vs Exploitation

- **Exploration** improves long-term knowledge  
- **Exploitation** uses current best estimates for short-term reward  
- A balance is required to achieve optimal long-term performance

---

## 5. Strategies to Address the Trade-Off

1. ε-greedy  
2. Greedy with optimistic initialization  
3. Upper Confidence Bound (UCB)  
4. Gradient Bandit  

---

## 6. ε-Greedy Policy

\[
A_t = 
\begin{cases}
\text{greedy action} & \text{with probability } 1 - \varepsilon \\
\text{non-greedy action} & \text{with probability } \varepsilon
\end{cases}
\]

- \( \varepsilon \in (0,1) \)  
- Non-greedy actions chosen uniformly  

This ensures continual exploration while still favoring the best-known action.

---

## 7. Example: 10-Armed Bandit

Setup:
- 2000 randomly generated bandit problems  
- Each action’s true value is drawn from \( \mathcal{N}(\mu_k, 1) \)  
- Each \( \mu_k \) is drawn from \( \mathcal{N}(0,1) \)  
- Performance is averaged over all 2000 problems  

---

## 8. Results

- ε = 0 (greedy): worst performance  
- ε = 0.01: good long-term performance  
- ε = 0.1: best initial performance  

The optimal ε depends on the reward variance and problem structure.

---

## 9. Long-Run Behavior

After extended training (e.g., 4000 steps):

- ε = 0.1 continues to perform well  
- ε = 0.01 eventually surpasses it in average reward  
- ε = 0 remains suboptimal  

Exploration is essential for avoiding premature convergence to suboptimal actions.



