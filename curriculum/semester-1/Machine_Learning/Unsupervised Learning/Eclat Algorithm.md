# Eclat Algorithm

An algorithm for **[[Association Rule Mining]]** that is often more efficient than [[Apriori Algorithm]] for sparse and large datasets.

## Core Concept
Eclat stands for **Equivalence Class Clustering and bottom-up Lattice Traversal**.

## Mechanism
It uses a depth-first search approach based on the intersection of **Transaction IDs (TIDs)**:
1.  **Vertical Data Format**: The database is structured vertically, where each item is mapped to a list of the Transaction IDs (TIDs) in which it appears.
    * *Example*: Item 'Milk' $\rightarrow$ {TID 1, TID 2, TID 4, TID 5}
2.  **Intersection**: To find the support for a 2-itemset (e.g., {Milk, Bread}), it calculates the intersection of their TID lists. The length of the resulting list is the itemset's support count.
    * *Example*: $\text{TID}(\text{Milk}, \text{Bread}) = \text{TID}(\text{Milk}) \cap \text{TID}(\text{Bread})$
3.  **Bottom-Up Traversal**: It recursively generates itemsets by intersecting the TID lists of smaller itemsets.

## Efficiency
The use of **TID sets** makes the counting process faster than scanning the entire transaction database repeatedly.