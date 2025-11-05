# Support Vector Machines (SVM)

A powerful supervised learning algorithm used for both **classification** and **regression** (Support Vector Regression - SVR).

## Goal
To find the optimal **Hyperplane** (the decision boundary) that maximizes the **Margin** between the closest data points of different classes.

## Key Concepts
* **Hyperplane**: The decision boundary that separates classes.
* **Support Vectors**: The data points that lie closest to the hyperplane. They are the most crucial points, as they define the orientation and position of the hyperplane and the margin.
* **Margin**: The distance between the hyperplane and the nearest support vector from each class. SVM aims to maximize this distance for better generalization.

![[Support Vector Machines (SVM)_example1.png]]
## Handling Non-Linear Data: The Kernel Trick

* **Problem**: In the original feature space, data might not be linearly separable.
* **Solution**: The **Kernel Trick** uses a **Kernel Function** (e.g., Radial Basis Function - RBF, or Polynomial) to implicitly map the data into a much **higher-dimensional feature space** where a linear separation (a hyperplane) can be found.
## Margin Types

* **Hard Margin**: Strictly separates all data points (sensitive to outliers).
* **Soft Margin**: Allows for some misclassification (outliers) to achieve a wider, more robust margin, leading to better **Outlier Resilience** and generalization.