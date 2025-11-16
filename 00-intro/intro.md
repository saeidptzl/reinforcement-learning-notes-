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


Agent, Environment, Observations, and Components
1. Agent–Environment Loop
At each time step 
t
t:
Agent
Observes the state 
S
t
S 
t
​	
 
Chooses an action 
A
t
A 
t
​	
 
Environment
Given 
(
S
t
,
A
t
)
(S 
t
​	
 ,A 
t
​	
 ):
Returns a reward 
R
t
+
1
R 
t+1
​	
 
Produces the next state 
S
t
+
1
S 
t+1
​	
 
This forms the fundamental RL interaction loop.
2. Episodes
An episode is a full sequence of transitions:
S
0
,
A
0
,
R
1
,
S
1
,
A
1
,
R
2
,
S
2
,
…
S 
0
​	
 ,A 
0
​	
 ,R 
1
​	
 ,S 
1
​	
 ,A 
1
​	
 ,R 
2
​	
 ,S 
2
​	
 ,…
Training typically involves many episodes.
3. Observations and History
Fully Observable Environments
S
t
+
1
=
O
t
+
1
S 
t+1
​	
 =O 
t+1
​	
 
The observation equals the underlying state.
Partially Observable Environments
The agent only sees an observation.
It must infer the state from history:
H
t
=
O
1
,
R
1
,
A
1
,
…
,
O
t
,
R
t
H 
t
​	
 =O 
1
​	
 ,R 
1
​	
 ,A 
1
​	
 ,…,O 
t
​	
 ,R 
t
​	
 
State estimation:
S
t
=
f
(
H
t
)
S 
t
​	
 =f(H 
t
​	
 )
This is essential in tasks like card games, robotics with sensor noise, etc.
4. Components of an RL Agent
Policy (always present)
Maps states to actions.
Goal of RL: find the policy that maximizes expected cumulative reward.
Deterministic:
a
=
π
(
s
)
a=π(s)
Stochastic:
π
(
a
∣
s
)
=
P
[
A
t
=
a
∣
S
t
=
s
]
π(a∣s)=P[A 
t
​	
 =a∣S 
t
​	
 =s]
Value Function (optional)
Measures how good a state is under a policy.
Q-Value Function (optional)
Measures how good a state–action pair is.
Q
(
s
,
a
)
=
expected return starting in 
s
 taking action 
a
Q(s,a)=expected return starting in s taking action a
Key concept for Q-learning and deep Q-networks.
Model (optional)
The agent’s predicted model of the environment.
Provides estimates of:
next state
reward
Used in model-based RL.
Summary
The agent chooses actions; the environment provides rewards and next states.
Episodes are sequences of interactions.
Observations may or may not fully reveal the state.
Policies, value functions, Q-values, and models are the core building blocks of RL agents.


