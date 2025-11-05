# Apriori Algorithm

A classic algorithm for **[[Association Rule Mining]]** used to find frequent itemsets and derive association rules.

## The Apriori Principle
**If an itemset is frequent (occurs often), then all of its subsets must also be frequent.** This principle is used to prune the search space.

## Mechanism
It uses a breadth-first search approach:
1.  **Generate 1-itemsets**: Count the frequency of all single items. Eliminate those below the minimum **[[Association Rule Mining#Support]]** threshold.
2.  **Generate k-itemsets**: Use the frequent $(k-1)$-itemsets to generate candidate $k$-itemsets. Prune the candidates that are guaranteed to be infrequent based on the Apriori principle.
3.  **Iterate**: Repeat step 2 until no more frequent itemsets can be found.

## Data Format
This algorithm typically works with a **horizontal data format** (transactions listed by customer ID).