A specific, powerful phase of [[NN for classification#Transfer Learning|transfer learning]] where you take a neural network that has **already been trained** on a massive, general dataset and **adapt it** to a new, specific task using a smaller, task-relevant dataset.

It is often the most effective method for achieving **high performance** in classification (and other) tasks when you have limited data for your specific problem.

### The Mechanism

When fine-tuning, the following steps and techniques are applied:

- **Replacing the Output Layer:** The original output layer is removed and replaced with a new layer tailored to your task (e.g., a **[[Softmax activation function|softmax]]** layer with 3 neurons for "Positive, Negative, Neutral" sentiment classification).

- **Freezing/Unfreezing Layers:** You typically **freeze** the weights of the early layers of the model, which contain the valuable, general features, and **unfreeze** the later layers. This ensures that the model preserves its fundamental knowledge while adjusting the high-level features for the new task.
  
- **Low Learning Rate:** The training process uses a **much smaller learning rate** (often 1/10th of the rate used for pre-training). This prevents the large, beneficial pre-trained weights from being drastically changed or "forgotten" (a phenomenon called _catastrophic forgetting_).