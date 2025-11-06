# K-Nearest Neighbors (k-NN)

An instance-based, **non-parametric**, and **lazy learning** algorithm. It makes predictions based on the similarity to training examples.
## Mechanism
1.  **Choose k**: Select the number of nearest neighbors.
2.  **Calculate Distance**: Find the distance (e.g., Euclidean) between the query point and all training instances.
3.  **Find k Neighbors**: Identify the *k* closest instances to the query point.
4.  **Predict**:
    * **Classification**: The class is determined by a **majority vote** among the *k* neighbors.
    * **Regression**: The output is the **average** (or weighted average) of the values of the *k* neighbors.
## Choosing k

* **Small k**: Captures noise and may lead to **overfitting**.
* **Large k**: Results in a smoother decision boundary, potentially leading to **underfitting**.

![[K-Nearest Neighbors (k-NN)_example.png]]