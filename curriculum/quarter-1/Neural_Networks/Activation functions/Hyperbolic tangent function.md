A [[Hyperbolic function]] using the "tanh".
Used as an activation function in neural networks, especially in [[Recurrent Neural Networks]]. 

Example:
![[Hyperbolic_tangent_function_example.png|400]](\**) Instead of $y = tanh(x)$ in neural networks context it's more like **$a = tanh(z)$** *

And the formula is:
$$
\begin{align}
a &= tanh(z) \\
&= \frac{e^z-e^{-z}}{e^z+e^{-z}}
\end{align}
$$
And it goes between $[-1, 1]$.
It turns out that for hidden units it almost always works better than the [[Sigmoid function]], because it makes more sense to get a value $0 \leq \hat{y} \leq 1$.

