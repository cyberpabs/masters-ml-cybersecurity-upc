# Naive Bayes

A simple but effective **probabilistic classifier** based on **Bayes' Theorem**.
## Core Principle

It uses the formula for **[[Conditional Probability]]** to predict the probability of a given input belonging to each possible class.

$$P(\text{Class}|\text{Features}) = \frac{P(\text{Features}|\text{Class}) \cdot P(\text{Class})}{P(\text{Features})}$$

## The "Naive" Assumption

The classifier assumes **conditional independence** between all features, meaning the presence or absence of one feature does not affect the presence or absence of any other feature, given the class. *This assumption rarely holds true in real-world data, but the model still often performs surprisingly well.*

## Types of Naive Bayes

* **Gaussian Naive Bayes**: Used when numerical features are assumed to follow a **normal (Gaussian) distribution**.
* **Multinomial Naive Bayes**: Typically used for discrete counts, like word frequencies in **text classification**.
* **Bernoulli Naive Bayes**: Deals with **binary features** (presence or absence of a term in a document).

## Pros & Cons
| Pros | Cons |
| :--- | :--- |
| Easy to implement and computationally efficient. | Assumes feature independence (rarely true). |
| Effective with a large number of features. | Can be influenced by irrelevant attributes. |
| Performs well with limited training data. | May assign zero probability to unseen events (needs smoothing). |
