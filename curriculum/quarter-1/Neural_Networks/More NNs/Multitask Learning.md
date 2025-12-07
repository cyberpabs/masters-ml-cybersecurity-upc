A learning paradigm where a single model is **trained to solve multiple related tasks simultaneously**, using a shared set of parameters or layers.

Instead of training one model for **Task A** and a completely separate model for **Task B**, Multitask Learning or MTL trains a single neural network to output the predictions for _both_ tasks.

The network architecture typically consists of:

1. **A Shared Backbone (or Encoder):** The initial layers of the network are shared across all tasks. This part learns the fundamental features common to all problems (e.g., edges and shapes in computer vision, or word meanings in natural language processing).

2. **Task-Specific Heads (or Decoders):** The final layers of the network branch off, with each branch having its own output layer and loss function tailored to a specific task.    

**Example:** Imagine you are building an AI for a self-driving car. Instead of training separate models for each task, you can use MTL:

- **Task A (Main):** Detect pedestrians (a classification/detection task).

- **Task B (Auxiliary):** Estimate the depth of the scene (a regression task).    

The initial layers of the network learn shared visual features, benefiting both tasks, as a pedestrian is defined by the same pixels used for depth estimation.

![[mtl_example.png]]
