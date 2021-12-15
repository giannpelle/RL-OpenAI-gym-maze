# Reinforcement Learning
This project presents a variety of solutions for the third-party environment **gym-maze** (available [here](https://github.com/tuzzer/gym-maze/)) from [OpenAI Gym](https://gym.openai.com).

## Environment: gym-maze
A simple 2D maze environment where an agent (blue dot) should escape from the environment starting from the top left corner (blue square) and reaching the exit location at the bottom right corner (red square) of the maze. 
The objective is to find the shortest path from the start to the goal.

<kbd>![Simple 2D maze environment](http://i.giphy.com/Ar3aKxkAAh3y0.gif)</kbd>

### Action space
The agent may only choose to go up, down, right, or left ("N", "S", "E", "W"). If there's a wall facing the agent, it will stay still.

### Observation space
The observation space is the (x, y) coordinate of the agent. The top left cell is (0, 0).

### Reward
A reward of 1 is given when the agent reaches the goal. For every step in the maze, the agent recieves a reward of -0.1/(total number of cells of the maze).

# Tabular solution methods
The [agents](https://github.com/giannpelle/RL-OpenAI-gym-maze/blob/master/agents) directory contains the most popular algorithms to solve the environment using a table to store the state and action spaces.

## Monte Carlo
It was developed following the pseudocode of the Monte Carlo First-Visit method (available in [Sutton & Barto](https://mitpress.mit.edu/books/reinforcement-learning-second-edition)), with 2 major differences:
1. the exploration strategy of the agent follows a *stretched exponential decay function* to slowly lower the epsilon value of the epsilon greedy policy
2. the returns average is calculated using the *running average* formula for performance reasons
The code implementation is available [here](https://github.com/giannpelle/RL-OpenAI-gym-maze/blob/main/agents/MC_first_visit_agent.py).

## Q-learning
It was developed following the pseudocode of the Q-Learning method (available in [Sutton & Barto](https://mitpress.mit.edu/books/reinforcement-learning-second-edition)) following an UCB (Upper Confidence Bound) exploration policy. The code implementation is available [here](https://github.com/giannpelle/RL-OpenAI-gym-maze/blob/main/agents/Q_learning_agent.py).

## Double Q-learning
It was developed following the pseudocode available [here](https://papers.nips.cc/paper/2010/hash/091d584fced301b442654dd8c23b3fc9-Abstract.html) (Hasselt et al., 2010). The code implementation is available [here](https://github.com/giannpelle/RL-OpenAI-gym-maze/blob/main/agents/Double_Q_learning_agent.py).

## SARSA
It was developed following the pseudocode of the SARSA method (available in [Sutton & Barto](https://mitpress.mit.edu/books/reinforcement-learning-second-edition)) following an UCB (Upper Confidence Bound) exploration policy. The code implementation is available [here](https://github.com/giannpelle/RL-OpenAI-gym-maze/blob/main/agents/SARSA_agent.py).

## Dyna-q plus
It was developed following the pseudocode of the Dyna-Q-plus method (available in [Sutton & Barto](https://mitpress.mit.edu/books/reinforcement-learning-second-edition)) following an UCB (Upper Confidence Bound) exploration policy. The code implementation is available [here](https://github.com/giannpelle/RL-OpenAI-gym-maze/blob/main/agents/Dyna_q_plus_agent.py).

## Installation

```bash
cd RL-OpenAI-gym-maze
conda env create -f environment.yml
conda activate gym-maze
python setup.py install

python maze_player.py --method=montecarlo
python maze_player.py --method=qlearning
python maze_player.py --method=doubleqlearning
python maze_player.py --method=sarsa
python maze_player.py --method=dynaqplus
```
## Example

![Solving 20x20 maze with loops and portals using Q-Learning](http://i.giphy.com/rfazKQngdaja8.gif)

