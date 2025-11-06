# Principal Component Analysis (PCA)

A foundational technique for **Dimensionality Reduction** that linearly transforms the data.
## Goal
To reduce the number of features while retaining most of the important information (**variance**).

## Mechanism
1.  Transforms the data onto a new coordinate system.
2.  The new axes (**Principal Components**) are orthogonal (uncorrelated) and are ordered by the amount of variance they capture.
3.  The first principal component captures the largest possible variance, the second captures the next largest, and so on.

## Key Concept: Variance Maximization
PCA can be conceptualized as:
* **Maximizing variance** (squared distance) in the direction of the new axis.
* **Minimizing residuals** (squared distance/error) in the direction perpendicular to the new axis.

![[Principal Component Analysis (PCA)_example.png]]