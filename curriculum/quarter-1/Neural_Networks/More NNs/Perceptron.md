Is the **simplest and oldest type** of artificial neural network. It's essentially the basic building block or the "grandparent" of modern neural networks.

In simple terms, you can think of a perceptron as a **single, simple decision-maker**.
## The Basic Decision Process

1. **Inputs:** It takes several inputs, which are pieces of data (e.g., features, measurements, or previous decisions).

2. **Weights:** Each input is assigned a **weight**, which determines its importance to the final decision.
   
3. **Summation:** It multiplies each input by its corresponding weight and then adds all these results together.

4. **Decision (Activation Function):** This sum is then passed through a simple function (the **step function**) that makes the final "yes" or "no" decision.    
    - If the weighted sum is **above a certain threshold** (the bias), the output is **1** (or "Yes").
    - If the weighted sum is **below the threshold**, the output is **0** (or "No").

It's major limitation is that it can only solve problems that are **linearly separable**. This means it can only separate data into two groups if you can draw a single, straight line (or plane) to divide them.