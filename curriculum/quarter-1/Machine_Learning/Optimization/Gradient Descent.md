# General idea on Gradient Descent (GD)

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

# Gradient Descent for Neural Networks:
This algorithm finds the minimum of a function by iteratively updating its parameters. This section is to explain how it's applied for training some of the most advanced [[Neural Networks]] models called [[Deep Learning]].

We need to start with some initial guesses. We usually set them both to 0.

$$
(w=0, b=0)
$$

We keep changing $w,b$ to reduce $J(w,b)$ until we settle at or near a minimum. Its possible it has more than one minimum as we can see here:

![[Gradient_Descent_deeplearning.png]]
(\**) This is a neural network cost function plot.

## Algorithm (code):

We first update $w$ to find a local minimum:

$$
w = w-\alpha \frac{\partial}{\partial w}J(w,b)
$$

$\alpha$ is the learning rate and it controls how big of a step we take downhill. If $\alpha$ is very large that corresponds to a very aggressive gradient descent procedure where you're trying to take huge steps downhill, this could make it impossible to reach a local minimum and if $\alpha$ is very small, then we are taking very small steps downhill and it will take a lot of time.

Then we update $b$:

$$
b = b-\alpha \frac{\partial}{\partial b}J(w,b)
$$