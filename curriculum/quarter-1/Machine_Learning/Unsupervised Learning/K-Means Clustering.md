# K-Means Clustering

An iterative, **partition-based** clustering algorithm. The number of clusters ($k$) must be specified beforehand.
## Mechanism (The K-Means Loop)

1.  **Initialization**: Choose $k$ and randomly place $k$ **centroids** (the center point of each cluster).
2.  **Assignment Step (E-Step)**: Assign every data point to the cluster of the closest centroid (typically using Euclidean distance).
3.  **Update Step (M-Step)**: Recalculate each centroid as the **mean** of all points assigned to its cluster.
4.  **Repeat**: Steps 2 and 3 are repeated until the centroids no longer change significantly (convergence).

![[K-Means Clustering_iter_steps.png]]

## Strengths & Weaknesses
* Fast and efficient for large datasets.
* Sensitive to the initial choice of $k$ and the starting positions of the centroids.
* Assumes clusters are roughly **spherical** and of equal size.