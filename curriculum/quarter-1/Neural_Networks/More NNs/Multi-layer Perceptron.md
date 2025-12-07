A **stack of [[Perceptron|perceptrons]]** organized into layers, which allows it to overcome the limitations of a single perceptron. It is often referred to interchangeably with a **Feedforward Neural Network (FNN)**.

An MLP always consists of at least **three layers**:

1. **Input Layer:** Takes the raw data features (e.g., the size, color, and price of a house).
   
2. **Hidden Layer(s):** One or more layers in the middle. This is where the **magic happens**. Each neuron in the hidden layer calculates complex features by combining inputs from the previous layer using **non-linear activation functions**. This allows the network to find intricate patterns.

3. **Output Layer:** Produces the final result (e.g., the predicted selling price of the house).

![[MLP_example_1.png]]