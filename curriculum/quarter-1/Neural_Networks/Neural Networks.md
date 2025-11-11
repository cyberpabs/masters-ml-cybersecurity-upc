# Introduction

A **neural network** is a pool of simple processing units called **neurons** which communicate by sending signals to each other over a large number of weighted connections. They are used to solve problems by analyzing vast amounts of data. 

> Inspired by the structure of the **human brain**.

Originally, neurons were threshold logic units: activation is 0 if below a certain threshold and 1 if it's above.

This networks are linear till the activation function. This function introduces a **non-linear transformation** to the output of the weighted sum of inputs and it gives the network the **power to curve and twist its decision boundaries** to fit the intricate patterns found in real-world data.

![[Simple_Neural_Network_example_1.png | 500]]

## Structure of Neural Networks

- **Input layer**: made-up of input nodes, just a representation of the input, input nodes do not perform any operations.
  
- **Hidden layers**: layers of nodes, often simple processing units.
  
- **Output layer**: made-up of output nodes, a representation of the output.
  
- **Connections**: Relationships between the nodes, often the weights are represented on them.
![[Structure_Neural_Network_2.png]]

A neural network can approximate any continuous function. It is so flexible that it can learn to model **any pattern, no matter how complicated**, given enough data and time.

This is called the **[[Universal Approximation Theorem]] (UAT)**.

## NN Architectures
There are different types of Neural Networks based on their core structure and application.
#### One layer
* [[Perceptron]]
#### Two layers
* [[Multi-layer Perceptron]] (MLP) / Feedforward Network
#### More than two layers (Deep Network)
* [[Convolutional Neural Networks]] (CNN)
    * *Sub-types:* [[ResNet]], [[VGG-Net]], [[YOLO]] 

* [[Recurrent Neural Networks]] (RNN)
    * *Variants:* [[Long Short-Term Memory]] (LSTM), [[Gated Recurrent Unit]] (GRU)

## Wide vs deep networks

- **Width (More Neurons in a Layer):** Adding more neurons to a single layer means the network can learn a greater number of **simple patterns** at the same level of complexity **in parallel** (e.g., detecting 50 different types of edges simultaneously).

- **Depth (More Layers):** Adding more layers means the network can learn patterns in a **hierarchy**. It doesn't just learn more patterns; it learns to **combine** those simple patterns into increasingly complex, abstract ones.

The key takeaway is that **deeper networks can reach more expressivity** and **are more efficient** than wider networks. Functions that would require an **exponential number** of neurons in a shallow (wide) network can be learned with only a **polynomial number** of neurons in a deep network.

> By structuring knowledge hierarchically (in **depth**), the network avoids the massive computational cost of trying to learn every complex pattern in a single, huge, wide layer.

## NNs as functions

This networks are composed by a vector of inputs usually called $\{x_1,...,x_n\}$ they multiply themselves using the [[Vectors and Vector Operations#Hadamard multiplication|Hadamard product]] with the weights, also a vector composed of $\{w_1,...,w_n\}$. Sums it all and adds a bias before sending it to the activation function.
![[nn_as_functions.png]]
> In simple words; Each layer, a function multiplies inputs by weights, adds biases, and applies an activation function.
> 
> Inputs -> prediction -> activation function -> Loss function
	$x,w,b$ -> $z = w^Tx + b$ -> $a=\sigma(z)$ -> $L(a,y)$ 

Here we can see a more detailed version thanks to Andrew Ng:
![[nn_representation_complex.png]]
### How to read layers and nodes?

In a case like this:

![[NN_andrew_ng_example.png]]

We must know that:
![[NN_layer_representation_byhand.png|300]]

For the first layer and **first** node: 
$$
\begin{align}
z^{[1]}_1=W^{[1]T}_1x+b^{[1]}_1 \\
a^{[1]}_{1}=\sigma(Z^{[1]}_1)
\end{align}
$$
For the first layer, **second** node: 
$$
\begin{align}
z^{[1]}_2=W^{[1]T}_2x+b^{[1]}_2 \\
a^{[1]}_{2}=\sigma(Z^{[1]}_2)
\end{align}
$$
So we end up with the following:
![[NN_andrew_ng_2.png]]

Doing this in a For Loop is ineficient, we can it like this:

We make a matrix stacking all W's

$$Z^{[i]} =
\begin{bmatrix}
- & w_1^{[1]T} & - \\
- & w_2^{[1]T} & - \\
- & w_3^{[1]T} & - \\
- & w_4^{[1]T} & - 
\end{bmatrix} 

\cdot 

\begin{bmatrix}
x_1 \\
x_2 \\
x_3
\end{bmatrix}

+

\begin{bmatrix}
b_1^{[1]} \\
b_2^{[1]} \\
b_3^{[1]} \\
b_4^{[1]}
\end{bmatrix}

=

\begin{bmatrix}
w_1^{[1]T}x + b_1^{[1]} \\
w_2^{[1]T}x + b_2^{[1]} \\
w_3^{[1]T}x + b_3^{[1]} \\
w_4^{[1]T}x + b_4^{[1]}
\end{bmatrix}

$$
- $W^{[1]} = (4,3)$
- $b^{[1]} = (4,1)$

$$
Z^{[1]}=
\begin{bmatrix}
z_1^{[1]} \\
z_2^{[1]} \\
z_3^{[1]} \\
z_4^{[1]} \\
\end{bmatrix}
$$

The to compute the $a$ we perform the sigmoid function to the $Z$ like this:
$$
a^{[1]}=\begin{bmatrix}
a_1^{[1]} \\
a_2^{[1]} \\
a_3^{[1]} \\
a_4^{[1]} \\
\end{bmatrix} = \sigma(Z^{[1]})
$$

The complete logic with 2 neurons is the following:
![[NN_secuence_1.png|200]]

### Non-vectorized approach:

![[NN_non_vectorized_approach.png|200]]
Notation:
$$
a^{[2](i)}
$$
This means 2 layer, $i^{th}$ example.

### [[Vectorization]] approach:
First we transform the $x^{(i)}$ to a row vector like this:
$$
X = [x^{1}, x^{2}, x^{3}, ..., x^{m}]
$$
And the entire code looks like this:
$$
\begin{align}
	Z^{[1]} &= W^{[1]}X + b^{[1]} \\
	A^{[1]} &= \sigma(Z^{[1]}) \\
	Z^{[2]} &= W^{[2]}A^{[1]}+b^{[2]} \\
	A^{[2]} &= \sigma(Z^{[2]})
\end{align}
$$
![[row_vector_z_explanation.png]]
(\**) Same with $A$ variable - REVISIT, NOT CLEAR*

When you build your neural network, one of the choices you get to make is what [[Activation function]] to use in the hidden layers as well as at the output units of your neural network.

## How NNs learn
The primary goal in training a neural network is to find **weights** and **biases** which minimize the **cost function** (or [[Loss function]]). We commonly use the Mean Squared Error ([[MSE]]) as an example of a cost function.

To find these optimal parameters, we use an optimization technique called [[Gradient Descent#Gradient Descent for Neural Networks|Gradient descent for neural networks]].
![[NN_optimization_valley_1.png]]
In short, to find the minimum of a function $f(x)$:
1. Start with an initial (can be random) guess of the parameters
2. Calculate the gradient (**partial derivatives**) of the **[[Loss function|Cost function]]** with respect to
each parameter.
$$
\frac{\partial f(x)}{\partial x_{j}}
$$
3. Update each parameter in the opposite direction of the gradient, by moving it
a step $\alpha$ in that direction:
$$
x_{j} \rightarrow x_{j}-\alpha \frac{\partial f(x)}{\partial x_{j}}
$$
4. Repeat steps 2 and 3 **until** the parameters **converge to a minimum value**, or
the change in the cost function is smaller than a predefined threshold.

\(\*) *⍺ is called the **step size** or **learning rate***.

> In our case, we want to find the minimize the loss function by altering the weights 
> and we want to calculate the derivative with respect to each weight.

### So what is the loss function for a NN?

By minimizing the [[MSE]], the neural network adjusts its **weights and biases** to make $y_i$​ and $\hat y_i$​ as close as possible.

### Backpropagation

Backpropagation is the algorithm used to compute the gradient with respect
to weights. **This is where NN's learn**.

Since each layer is a function of the previous one, it uses the [[Chain rule]]:
$$
\frac{d}{dx} \big[ f(g(x)) \big]=f’(g(x))g’(x)
$$

> (\*) *Check the [[Others#Resources for Neural Networks|Resources for neural networks]] for more info*

Convergence of the gradient descent algorithm is **not guaranteed**. The choice of
$\alpha$ is key:
![[small_vs_big_learning_rate.png]]
