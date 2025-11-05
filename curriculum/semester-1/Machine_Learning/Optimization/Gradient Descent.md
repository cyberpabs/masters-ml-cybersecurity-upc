# Gradient Descent (GD)

The most recognized **optimization algorithm** in ML.

## The Idea
The goal is to iteratively adjust the model's parameters (weights and biases) to minimize the **Cost Function**. It does this by moving in the direction of the steepest descent (negative of the gradient).
![[Gradient Descent_example_1.png]]

## Learning Rate ($\alpha$)
The single most important hyperparameter, as it determines the size of the steps taken.
* **Too large**: May overshoot the minimum and fail to converge.
* **Too small**: Training will be excessively slow.

## Types of Gradient Descent

### 1. Batch Gradient Descent
* **Update**: Uses **all** training examples to calculate the gradient for one update.
* **Pro/Con**: Stable, but very slow for large datasets.

### 2. Stochastic Gradient Descent (SGD)
* **Update**: Uses **one** random training example for each update.
* **Pro/Con**: Fastest updates, but noisy and high-variance convergence.

### 3. Mini-Batch Gradient Descent
* **Update**: The preferred method. Uses a small subset (**mini-batch**, e.g., 32 to 128) of training examples for each update.
* **Pro**: Balances stability (like Batch GD) with speed (like SGD).