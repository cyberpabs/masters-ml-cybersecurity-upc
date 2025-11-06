# Association Rule Mining

The process of finding frequent patterns, associations, or correlations among sets of items in a database (often referred to as Market Basket Analysis).

## Goal
To find rules of the form **$X \rightarrow Y$** (e.g., "People who buy $X$ tend to also buy $Y$").

## Key Evaluation Metrics
These metrics are used to measure the strength and interestingness of a rule $X \rightarrow Y$:

* **Support**: How often the itemset $\{X, Y\}$ appears in the dataset.
    * *Formula*: $P(X \cap Y)$
* **Confidence**: The conditional probability of $Y$ being bought, *given* $X$ was bought. It measures the reliability of the rule.
    * *Formula*: $P(Y | X) = \frac{P(X \cap Y)}{P(X)}$
* **Lift**: Measures how much more likely $Y$ is bought when $X$ is bought, compared to $Y$ being bought independently.
    * *Lift > 1*: $X$ and $Y$ are positively correlated.
    * *Lift < 1*: $X$ and $Y$ are negatively correlated.
    * *Lift = 1*: $X$ and $Y$ are independent.
    * *Formula*: $\frac{\text{Confidence}(X \rightarrow Y)}{P(Y)}$

## Algorithms
* [[Apriori Algorithm]]
* [[Eclat Algorithm]]