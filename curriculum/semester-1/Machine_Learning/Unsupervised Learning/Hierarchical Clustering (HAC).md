# Hierarchical Clustering (HAC)

An algorithm that builds a hierarchy (or tree) of clusters, commonly represented by a **dendrogram**. HAC does not require you to pre-specify the number of clusters.

## Types

1.  **Agglomerative (Bottom-Up)**:
    * Starts with every single data point as its own cluster.
    * In each step, it merges the **two closest clusters**.
    * Continues until only one cluster (the root) remains.

2.  **Divisive (Top-Down)**:
    * Starts with all data points in one single cluster.
    * In each step, it splits the **most dissimilar cluster** into two sub-clusters.
    * Continues until every point is its own cluster.

## Dendrogram
* The tree-like structure used to visualize the hierarchy of clusters.
* Cutting the dendrogram horizontally determines the number of clusters.
![[Hierarchical Clustering (HAC)_example.png]]