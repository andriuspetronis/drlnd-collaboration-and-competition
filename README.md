# Project: Collaboration and Competition

The goal of this project project is to bounce a ball over a net for as long as possible with two agents using rackets.

![Alt Text](https://imgur.com/CMW2H1N.png)

### Project Details

**State:** The observation space consists of 8 variables corresponding to the position and velocity of the ball and racket. Also, each agent receives its own, local observation.

**Action:** Two continuous actions are available, corresponding to movement toward (or away from) the net, and jumping.

**Reward:** If an agent hits the ball over the net, it receives a reward of +0.1. If an agent lets a ball hit the ground or hits the ball out of bounds, it receives a reward of -0.01. Thus, the goal of each agent is to keep the ball in play.

**Solution:** The task is episodic, and in order to solve the environment, your agents must get an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents). Specifically,

- After each episode, we add up the rewards that each agent received (without discounting), to get a score for each agent. This yields 2 (potentially different) scores. We then take the maximum of these 2 scores.
- This yields a single **score** for each episode.

The environment is considered solved, when the average (over 100 episodes) of those **scores** is at least +0.5.


### Getting Started
For this project, you could download a pre-built Unity environment from one of the links below. You need only select the environment that matches your operating system:

- Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux.zip)
- Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis.app.zip)
- Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86.zip)
- Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Windows_x86_64.zip)

Then, place the file in the `data/` folder in the DRLND GitHub repository, and unzip (or decompress) the file.

(*For Windows users*) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

(*For AWS*) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P3/Tennis/Tennis_Linux_NoVis.zip) to obtain the "headless" version of the environment. You will not be able to watch the agent without enabling a virtual screen, but you will be able to train the agent. (*To watch the agent, you should follow the instructions to [enable a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the Linux operating system above.*)

**Further setup steps to run code locally:**

1. Create a new environment:
```
conda create --name drlnd python=3.6
source activate drlnd
```
2. Install Jupyter notebook:
```
conda install jupyter notebook
```
3. Place extracted `Tennis_Linux` folder in the `data/` directory:
```
./data/Tennis_Linux/Tennis.x86_64
```


### Instructions
Follow the instructions in Tennis.ipynb to get started with training your own agent!

**Note:** The original notebook has been trained on the Udacity DRLND workspace with CPU. Here is the specific line for training the agent:

```
scores = ddpg()
```

**Reference:** [Udacity Deep Reinforcement Learning Nanodegree Program](https://www.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893)