# Conditional Probability and Independent Events

Fundamental concepts in probability theory, crucial for understanding probabilistic classifiers like [[Naive Bayes (NB)|Naive Bayes]].

## Conditional Probability

The probability of event A occurring **given** that event B has already occurred.
* **Notation**: $P(A|B)$
* **Formula**:
$$P(A|B) = \frac{P(A \cap B)}{P(B)}$$
    Where $P(A \cap B)$ is the probability of both A and B occurring simultaneously.
## Independent Events

Two events A and B are **independent** if the occurrence of one does not affect the probability of the other.
* **Condition**: The probability of their intersection is the product of their individual probabilities.
$$P(A \cap B) = P(A) \cdot P(B)$$
* **Equivalently**: $P(A|B) = P(A)$.