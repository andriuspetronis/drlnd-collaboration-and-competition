# Project: Collaboration and Competition

The goal of this project project is to bounce a ball over a net for as long as possible with two agents using rackets.

![Alt Text](https://imgur.com/CMW2H1N.png)

### Learning Algorithm
Deep Deterministic Policy Gradient (DDPG) algorithm has been used to train the agents. In general, it learns both a Q-function and a policy at the same time. More specifically, the algorithm use off-policy data together with the Bellman equation for finding the Q-values, while the policy uses the Q-function. More detailed description could be found [here](https://spinningup.openai.com/en/latest/algorithms/ddpg.html).

**Quick Facts**
Here are some quick facts abou the DDPG algorithm from OpenAI:
- DDPG is an off-policy algorithm.
- DDPG can only be used for environments with continuous action spaces.
- DDPG can be thought of as being deep Q-learning for continuous action spaces.

**Pseudocode**
Authors in the [Continuous control with deep reinforcement learning](https://arxiv.org/abs/1509.02971) paper summarises DDPG algorithm using the following pseudocode:

![Pseudocode](https://i.imgur.com/HVYe1A7.png)

Some of these steps are not straight-forward and might require additional explanation.

**Replay buffer**
The main idea behind the replay buffer is to generate a finite number of experiences (state, action, reward, next state) and store them into a cache. Later, this buffer is used for sampling mini-batches needed for updating both policy (Actor) and value (Critic) networks. As a result, this helps to decorrelate experiences used for training and should lead to some better convergence properties.

**Actor and Critic network updates**
The updates of the value network are similar to those in the Q-learning algorithm. However, in this situation next state values are calculated based on the value and policy target networks. Later, the goal is to minimaze a mean-squared loss between original and updated Q values.

**Target network updates**
Soft updates are used for target network, meaning that its weights are slowly blending into the weights of the corresponding regular network. So, there is a slight mismatch between both target and regular networks.

**Exploration**
Instead of using epsilon-greedy exploration for selecting actions, DDPG alorithm adds noise to the action itself. This is needed as the algorithm deals with continuous actions, so the same logic could not apply as with distrete action spaces.

**Hyperparameters**

| Parameter | Value | Description |
|---|---|---|
| n_episodes | 10000 | maximum number of training episodes |
| max_t | 1000 | maximum number of timesteps per episode |
| BUFFER_SIZE | 1e5 | replay buffer size |
| BATCH_SIZE | 128 | minibatch size |
| GAMMA | 0.99 | discount factor |
| TAU | 1e-3 | for soft update of target parameters |
| LR_ACTOR | 1e-3 | learning rate of the actor |
| LR_CRITIC | 1e-3 | learning rate of the critic |
| WEIGHT_DECAY | 0 | L2 weight decay |

**Neural network architecture**
The neural network consists of two hidden layers (`first_layer_size = 256` and `second_layer_size = 128`) for both Actor and Critic. Also, it uses a **rectified linear unit (ReLU)** activation function for Actor and **leaky rectified linear unit (Leaky ReLU)** for Critic. More information about the network architecture could be found in the `model.py` file.


### Plot of Rewards
The environment is considered solved after agents get an average score of +0.5 (over 100 consecutive episodes, and over all agents). The current architecture allows the agent to solve it over 597 episodes.

```
Episode 100	Average Score: 0.01
Episode 200	Average Score: 0.01
Episode 300	Average Score: 0.00
Episode 400	Average Score: 0.00
Episode 500	Average Score: 0.05
Episode 600	Average Score: 0.10
Episode 697	Average Score: 0.52
Environment solved in 597 episodes!	Average Score: 0.52
```

A plot of rewards per episode:

![Rewards plot](https://imgur.com/4bEb4S2.png)

### Ideas for Future Work
It would be possible to experiment with alternative algorithms. For instance, it wold be possible to implement algorithms like [PPO](https://arxiv.org/pdf/1707.06347.pdf), [A3C](https://arxiv.org/pdf/1602.01783.pdf), and [D4PG](https://openreview.net/pdf?id=SyZipzbCb) that use multiple (non-interacting, parallel) copies of the same agent to distribute the task of gathering experience. Also, it might be interesting to try other more complicated environments (i.e. [Crawler](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#crawler)).

**Reference:** 
[Udacity Deep Reinforcement Learning Nanodegree Program](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893)
[Deep Deterministic Policy Gradients Explained](https://towardsdatascience.com/deep-deterministic-policy-gradients-explained-2d94655a9b7b)
[OpenAI](https://spinningup.openai.com/en/latest/algorithms/ddpg.html)