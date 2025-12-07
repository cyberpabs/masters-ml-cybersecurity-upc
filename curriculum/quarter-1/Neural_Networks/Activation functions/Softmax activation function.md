Sometimes called the **normalized exponential function** or **softargmax**, takes a vector of arbitrary real-valued numbers and transforms it into a vector of probabilities, where every element is between 0 and 1, and the entire vector sums to 1.

![[softmax_activation_function.png|500]]

### The Formula

For an input vector of raw scores $z=[z_1​,z_2​,…,z_K​]$ for $K$ classes, the Softmax probability for the $i$-th class, $Softmax(z_{i})$, is calculated as:
$$
Softmax(z_{i})= \frac{e^{z_{i}}}{\sum\limits_{j=1}^{K}e^{z_{j}}}
$$
- $e^{z_{i}}$​: The exponential of the raw score for class i. This term ensures the output is positive and **amplifies the differences** between the scores (a slightly higher input score results in a significantly higher probability).

- ​$\sum\limits_{j=1}^{K}e^{z_{j}}$: The **sum of the exponentials** of all $K$ class scores. This acts as a normalization constant (the denominator) for the entire distribution.