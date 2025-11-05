# DBSCAN

A non-parametric clustering algorithm that groups together data points that are closely packed (high density) while marking points that lie alone in low-density regions as **outliers** or **noise**.

## Key Concepts (To be elaborated)
DBSCAN differs from [[K-Means Clustering]] and [[Hierarchical Clustering (HAC)]] by not requiring the number of clusters to be specified beforehand and by identifying clusters of arbitrary shape.

1.  **Eps ($\epsilon$)**: The maximum radius used to search for neighbors.
2.  **MinPts**: The minimum number of points required to form a dense region (a cluster).

## Point Categories
* **Core Point**: A point that has at least *MinPts* neighbors within distance *Eps*.
* **Border Point**: A point that is within distance *Eps* of a Core Point, but has fewer than *MinPts* neighbors itself.
* **Noise Point**: A point that is neither a Core Point nor a Border Point.

## Advantages (To be elaborated)
* Can find arbitrarily shaped clusters.
* Is robust to outliers.
![[DBSCAN (Density-Based Spatial Clustering)_example.png]]