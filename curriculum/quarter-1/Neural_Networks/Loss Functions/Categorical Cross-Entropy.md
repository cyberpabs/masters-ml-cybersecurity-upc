Also known as **softmax loss**, is one of the most commonly used loss functions in machine learning, particularly for classification problems. It measures the **difference between the predicted probability distribution and the actual (true) distribution of classes**. The function helps a machine learning model **determine how far its predictions are from the true labels** and guides it in learning to make more accurate predictions.

The categorical cross-entropy formula is expressed as:
$$
L(y,\hat y)=−\sum\limits _{i=1}^{C} y_{i}log⁡(\hat y_{i})
$$
where:

- $L(y,\hat y)$ is the categorical cross-entropy loss.
- $y_{i}$ is the true label (0 or 1 for each class) from the one-hot encoded target vector.
- $\hat y_{i}$​ is the predicted probability for class $i$.
- $C$ is the number of classes.