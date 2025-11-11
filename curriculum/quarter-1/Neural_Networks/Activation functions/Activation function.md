Activation functions decide whether a neuron should **be activated or not** based on its input. They essentially **act as a gate**, determining the strength of the signal passed on to the next layer.

In previous notes I talked about the [[Sigmoid function]] when I said that $a^{[1]} = \sigma(z^{[1]})$.
So now I'll change that to an placeholder $g(z^{[i]})$ for any other activation function that may not be a linear one like the Sigmoid.
$$
\begin{align}
z^{[1]}&=W^{[1]}x+b^{[1]} \\
a^{[1]}&=g(z^{[1]}) \\
z^{[2]}&=W^{[2]}a^{[1]}+b^{[2]} \\
a^{[2]}&=g(z^{[2]}) \\
\end{align}
$$
An activation function that almost always works better than the sigmoid function is the tangent function or the [[Hyperbolic tangent function]].

So if $z$ is very large or very small, the slope of the function either ends up being close to zero and so this can slow down [[Gradient Descent]]. So one other choice that is very popular in machine learning is what's called the [[Rectified linear unit (ReLU)]].

Some rules of thumb for choosing activation functions. If your output is zero or one, if you're using binary classification, then the sigmoid function is a very natural choice for the output layer. 

And then for all other units ReLU or the rectified linear unit is increasingly the default choice of activation function. So if you're not sure what to use for your hidden layer, I would just use the ReLU activation function, is what you see most people using these days. 

Although sometimes people also use the $tan h$ activation function. One disadvantage of the ReLU is that the derivative is equal to 0 when z is negative. In practice this works just fine. But there is another version of the ReLU called the Leaky ReLU.