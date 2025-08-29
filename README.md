
---

# Snake Reinforcement Learning (DQN)

This project implements the classic Snake game and trains an **AI agent** to play it using **Deep Q-Learning (DQN)** with PyTorch.
The agent learns to navigate the game, eat food, and avoid collisions by optimizing long-term rewards.

---

## Project Structure

```
├── agent.py          # RL Agent implementation and training loop
├── helper.py         # Utility functions (plotting training progress)
├── model.py          # Neural network (Q-Network) and trainer
├── Snake_game.py     # Snake game environment (pygame)
├── requirements.txt  # Dependencies
```

---

## Features

* **Custom Snake Environment** built with `pygame`
* **Deep Q-Network (DQN)** implementation in PyTorch
* **Experience Replay** for stable learning
* **Epsilon-Greedy Strategy** for exploration vs exploitation
* **Training Visualization** (live plotting of scores and averages)

---

## How It Works

1. The agent observes the **state** of the Snake game:

   * Danger straight, right, left
   * Current direction
   * Food location relative to snake head

   → Represented as an **11-dimensional state vector**.

2. It chooses an **action**:

   * `[1,0,0]` → keep moving straight
   * `[0,1,0]` → turn right
   * `[0,0,1]` → turn left

3. The environment (`SnakeGameAI`) returns:

   * **Reward** (+10 for food, -10 for death, small penalty otherwise)
   * **Next state**
   * **Game over flag**

4. The agent updates its **Q-network** using **Q-learning**:

   ```
   Q(s, a) = r + γ * max(Q(s’, a’))
   ```

---

## Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/Manavdarji2/Snake-Game-RL.git
   cd snake-rl
   ```

2. Create a virtual environment and install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

---

## Running the Project

### Train the Agent

```bash
python agent.py
```

* A Pygame window will open showing the Snake game.
* The agent will start learning from scratch.
* Training progress (scores & mean scores) is plotted live.
* The best model is saved in `./Model/model.pth`.

### Play the Snake Game (AI-controlled)

If you want to test the trained model, you can modify `agent.py` to load the saved model instead of training from scratch.

---

## Example Training Plot

The helper function continuously plots:

* **Score per game**
* **Mean score** across games

This helps visualize the learning progress.

---

## Requirements

See [`requirements.txt`](./requirements.txt).
Key libraries:

* `pygame` (Snake game environment)
* `torch` (Deep Q-Learning)
* `matplotlib` (Training visualization)
* `numpy`

---

## Future Improvements

* Use **Double DQN** for more stable training
* Add **Prioritized Experience Replay**
* Implement **Convolutional Neural Networks (CNNs)** for pixel-based input
* Train longer for better performance

---

## Acknowledgments

This implementation is inspired by reinforcement learning tutorials and the Deep Q-Learning algorithm.

---

## Model Path

The trained DQN model is saved automatically during training whenever a new high score is achieved.

Path: Save [Model](./Model/model.pth)

Contents:

>The learned weights and biases of the neural network (Linear_QNet)
>
>These parameters represent the agent’s learned strategy for playing Snake

---# Snake-Game-RL
