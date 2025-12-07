Supervised learning tasks where the goal is to assign input data into predefined categories or classes. This data can be images, text, audio, or **structured data**.

- [[Image classification]]
- [[Sentiment Analysis]]

> We need to find a **decision boundary** that separated the data into distinct categories, specially when the data is **non-linear** and **complex**.

Clarification: The output of a NN is numerical and usually a probability for each class.

## Why NNs for classification?

Neural Networks are extremely good at **extracting relevant features** from raw data, reducing the need for feature engineering. As we also know, they **perform well on extremely larga datasets** and **can handle a variety of input types**.

Examples of NN classification tasks in the real world:
- Character recognition
- Email spam classifier
- Classification of online product reviews

## Types of classification

### Binary classification
Binary classification is a choice **between two labels**. The output layer typically consists of a single neuron that outputs a value between **0 and 1**, representing the **probability** of the input belonging to one of the two classes.

### Multi-class classification

An instance belongs to **exactly one** class out of three or more possible categories. Generally, the **output layer** contains **one neuron per class**. Ideally, the sum of the values of the output neurons **sums to 1**, to be interpreted as probabilities.
#### Types of multi-class classification

In multi-class classification, the way the model handles the prediction for multiple categories is critical. The two main approaches for structuring the output layer are **One-vs-All** and **One-vs-One**.
##### One-vs-All (OvA)
Is a method that breaks down a classification problem with $N$ possible solutions into **$N$ separate binary classifiers**.

- **Structure:** It consists of one binary classifier for each possible outcome/class.
  
- **Activation Function:** This approach typically uses the **[[Sigmoid function|Sigmoid activation function]]** in the output layer.
  
- **Prediction:** The probability for each class is determined **independently** of all the other classes. For example, in classifying an image as an apple, orange, pear, or grape, the model determines: 
	- "Is it an apple? yes/no," 
	- "Is it an orange? yes/no," and so on, using independent binary classifiers
	  
- **Inefficiency:** This method can become **very inefficient** if there are a large number of labels (classes).

##### One-vs-One (OvO)
When implemented with the standard multi-class approach in neural networks, predicts the probabilities of each label relative to each other. This is achieved by using a specific output layer activation.

- **Structure:** Generally, the output layer contains **one neuron per class**.
  
- **Key Change:** The critical difference from the OvA/Sigmoid approach is the use of the **[[Softmax activation function]]** for the output layer.
  
- **Prediction:** The Softmax function is essential because it **normalizes** the output values, so the sum of the values of the output neurons **sums to 1**, allowing the outputs to be correctly interpreted as probabilities for all classes.
  
- **Assumption:** The Softmax approach **assumes that each example is a member of exactly one class**.

### Multi-label Classification

For tasks where an input can simultaneously be a member of **zero, one, or multiple** classes simultaneously. You **cannot use softmax** and must instead rely on a **one-vs-all approach**.

Think of the "Label" terms as defining the **problem** you are solving, and the "vs." terms as defining the **technique** the neural network uses to solve it.

### Hierarchical Classification
_(Not in lesson)_

It involves classifying images at **multiple levels of hierarchy**. For example, an image of an animal can first be classified as a "mammal" and then further classified as "cat" or "dog".

### **_Summary_**

| **Problem Type (Label)**     | **Classification Technique (vs.)** | **Output Activation** |
| ---------------------------- | ---------------------------------- | --------------------- |
| **One-Label** (Multi-class)  | **One-vs-One** (Implicitly)        | **Softmax**           |
| **Many-Label** (Multi-Label) | **One-vs-All** (Explicitly)        | **Sigmoid**           |

--- 
## Advanced Training Strategies 
### Transfer Learning 

**[[Transfer Learning]]** is a powerful training methodology where a model developed for a massive task is **reused** as the starting point for a related, often smaller, task. 

## Architectures for classification

### Core Architectures by Data Type
| **Architecture**                                             | **Primary Use Case**                | **Key Function/Characteristic**                                                                                                                                           |
| ------------------------------------------------------------ | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[[Multi-layer Perceptron\|Feed Forward Neural Networks]]** | Numerical or Discrete Inputs        | The foundational structure of a neural network.                                                                                                                           |
| **[[Convolutional Neural Networks]] (CNNs)**                 | Images and Spatial Data             | Designed to extract **spatial features** using layers like `Conv2D` and compress them using `Pooling` layers, with a fully connected layer at the end for classification. |
| **[[Recurrent Neural Networks]] (RNNs)**                     | Sequential Data (Text, Time Series) | Designed to handle sequential data by maintaining a form of **"memory"** of previous inputs. Variations include **LSTMs** and **GRUs**.                                   |

### Advanced and Specialized Architectures

These often build upon the core concepts above:

- **1D CNNs (`Conv1D`)**: A variation of the CNN designed specifically to work on sequential data, commonly used for tasks like **text** and **time series analysis**.

- **[[Transformers]]**: Although originally developed for text, these architectures are increasingly used for sequential data and sometimes incorporate character sequences directly for robustness.

- **[[Vision Transformers]] (ViTs)**: These adapt the Transformer model to image tasks, offering a strong, more recent alternative to traditional CNNs.

- **Hybrid Architectures**: These combine elements of both CNNs and Transformers to leverage the strengths of each model type.




## Benchmarks

A benchmark is a **standard or point of reference** against which various things may be compared. 

> When developing a new method or dataset, benchmarks are used to compare it to existing solutions to determine if the new approach is "better".

### Types of benchmarks

| Benchmark Type                 | Evaluation Focus                                                           |
| ------------------------------ | -------------------------------------------------------------------------- |
| **Model/Algorithm Benchmarks** | Performance of state-of-the-art algorithms on specific datasets and tasks. |
| **Hardware Benchmarks**        | The performance of CPUs, GPUs, TPUs, and other accelerators in AI tasks.   |
| **Dataset Benchmarks**         | Standardized datasets against which comparisons are made.                  |

Several widely recognized datasets used as benchmarks:
- [[ImageNet]]
- MNIST
- SQuAD

## Activation functions for classification

In classification, the output of a NN is numerical, and classification is achieved by interpreting these outputs as a **class distribution or probabilities for each class**. The choice of activation function in the output layer depends entirely on the nature of the classification task.
![[relu_vs_tanh.png]]
(\*) https://ml-course.github.io/master/08%20-%20Neural%20Networks.slides.html#/19

#### Common functions

- [[Sigmoid function]]: Used for **binary classification**, which is a choice between two labels. The output layer typically consists of a single neuron that outputs a value between 0 and 1, representing the probability of the input belonging to one of the two classes. Used in conjunction with [[Binary Cross-Entropy (Log loss)]].

- [[Softmax activation function]]: Used for **multiclass classification**, which is a choice between three or more categories. The output layer generally contains one neuron per class. Softmax ensures that the sum of the values of the output neurons sums to 1, so they can be interpreted as probabilities. It assumes that each example is a member of exactly one class. Softmax calculates the exponential of the input for each class ($z_i$) and divides it by the sum of the exponentials of all the raw class scores in the output layer. Used in conjunction with **[[Categorical Cross-Entropy]]** (also called Softmax Loss).

## Loss functions

- [[Binary Cross-Entropy (Log loss)]]: To get a **measure of dissimilarity** between the target and the predicted label. It penalizes incorrect predictions, with larger penalties for predictions that are farther away from the true label (due to the log)
  
- [[Categorical Cross-Entropy]]: Compares the predicted probability distribution over all classes with the one-hot encoded true labels.
