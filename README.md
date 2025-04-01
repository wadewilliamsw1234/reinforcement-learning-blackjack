# Math 76.03/146: Game Theory and Artificial Intelligence

## Course Description
This course focuses on the emerging interdisciplinary field of game theory and artificial intelligence, providing students with a comprehensive understanding of strategic decision-making, learning dynamics, and cooperative behaviors in AI systems. Through a combination of lectures, discussions, and hands-on projects, the class introduces the fundamental concepts and applications of evolutionary games, repeated games, stochastic games, and multiagent learning systems. The course also covers the ethical implications and alignment mechanisms required to ensure AI systems serve humanity. Throughout the course, students will have gained the necessary knowledge and skills to design AI systems with a strong foundation in game-theoretical principles and an emphasis on cooperation and alignment.

# Learning to Win: An AI-Driven Approach to Beating Blackjack

This repository contains the code and documentation for a project investigating the application of artificial intelligence (AI) and reinforcement learning (RL) to the game of Blackjack. The project was completed as part of the Math 76.03 course on *Game Theory and AI* at Dartmouth College in November 2023 by Kristian Feed and Wade Williams.

## Introduction

Blackjack, also known as 21, is a widely played casino card game that blends luck and strategy. Players aim to achieve a hand value as close to 21 as possible without exceeding it, making decisions such as "hit," "stand," "double down," or "split" based on their hand and the dealer's visible card. This project explores how AI techniques, including traditional strategies and advanced RL algorithms, can learn to play Blackjack effectively, with the goal of approaching or surpassing the established win probability of 42.22% achieved by the basic strategy.

## Objectives

The project aims to:

- Develop and evaluate multiple strategies for playing Blackjack, ranging from random actions to advanced RL methods.
- Compare the performance of these strategies against the benchmark win rate of 42.22% (basic strategy under standard rules).
- Investigate the potential of AI to learn complex strategic decisions in a game with both deterministic rules and probabilistic outcomes.

## Methods

We implemented a Blackjack game simulation to test the following strategies:

- **Random Strategy**: Makes decisions arbitrarily (hit or stand), serving as a baseline.
- **Simple Strategy**: Hits if the player's total is less than 17, otherwise stands, mirroring the dealer's threshold.
- **Basic Strategy**: An optimized rule-based approach derived from mathematical analysis, adjusting actions based on the player's hand (hard or soft totals) and the dealer's up card.
- **Machine Learning (ML) Algorithm**: A feedforward neural network with five layers (16, 128, 32, 8, 1 neurons), using a sigmoid activation for binary classification (hit or stand), trained with binary crossentropy loss and stochastic gradient descent (SGD).
- **Q-Learning (QN)**: A model-free RL method using a Q-table updated via temporal difference learning, with an epsilon-greedy policy for action selection.
- **Deep Q-Learning (DQN)**: An extension of Q-Learning using a neural network with ReLU activations and batch normalization, optimized with mean squared error (MSE) loss and SGD with momentum.

Each strategy was tested over 10 trials of 100,000 simulations, with performance measured by win percentage.

## Results

The table below summarizes the average win rates for each strategy, based on 10 trials of 100,000 simulations each:

| Algorithm       | Structure        | Activation | Loss Function       | Optimizer       | Win Rate |
|-----------------|------------------|------------|---------------------|-----------------|----------|
| Random          | N/A              | N/A        | N/A                 | N/A             | 31.9%    |
| Simple          | N/A              | N/A        | N/A                 | N/A             | 41.6%    |
| Basic           | N/A              | N/A        | N/A                 | N/A             | 43.3%    |
| Machine Learning| Feedforward NN   | Sigmoid    | Binary Crossentropy | SGD             | 41.5%    |
| Q-Learning      | Q-Table          | N/A        | Temporal Difference | N/A             | 32.52%   |
| DQN             | Neural Net       | ReLU       | MSE                 | SGD w/ momentum | 36.82%   |

### Key Findings

- **Basic Strategy** achieved the highest win rate at 43.3%, slightly above the theoretical 42.22% due to the simulation excluding the "surrender" option.
- **Simple Strategy** and **Machine Learning** performed closely, with win rates of 41.6% and 41.5%, respectively, suggesting the ML model approximates simpler rule-based approaches with potential for improvement.
- **Q-Learning** and **DQN** underperformed at 32.52% and 36.82%, respectively, indicating challenges in converging to an optimal policy without further tuning.
- Heat maps comparing win percentages across player hands and dealer cards (available in `results/`) reveal smoother transitions in the basic strategy compared to the ML algorithm, suggesting the latter requires more training to stabilize.
