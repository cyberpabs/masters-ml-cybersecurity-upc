A loss function used in [[NN for classification#Binary classification|binary classification]] problems. It quantifies the difference between the actual class labels (0 or 1) and the predicted probabilities output by the model. The lower the binary cross-entropy value, the better the model’s predictions align with the true labels.

Mathematically, Binary Cross-Entropy (BCE) is defined as:
$$
BCE = -\frac{1}{N}\sum\limits _{i=0}^{N}\bigl[ y_{i}log(p_i)+(1-y_i)log(1-p_i)\bigr]
$$
where:
- $N$ is the number of observations.
- $y_i$​ is the actual binary label (0 or 1) of the $i^{th}$ observation.
- $p_{i}$​ is the predicted probability of the $i^{th}$ observation being in class 1.

Since the model’s output is a probability between 0 and 1, minimizing binary cross-entropy during training **helps improve predictive accuracy**, ensuring the model **effectively distinguishes between two classes**.