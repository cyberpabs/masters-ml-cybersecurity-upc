# Classical Planning and Constraint Satisfaction Problems (CSP)

This module shifts from generic search to structured problem-solving, focusing on formalizing action sequences (**Planning**) and managing resource allocation via **Constraints**. (Based on Lecture 4 and Lecture 5)

## Classical Planning

**Classical Planning** involves finding a sequence of actions that transforms an initial state into a goal state. It assumes the world is:
1.  **Static:** The world does not change on its own.
2.  **Deterministic:** The effects of actions are known and certain.
3.  **Fully Observable:** The agent knows the complete state of the world.

### Planning with STRIPS

As discussed in [[AI Paradigms_ Neat vs Scruffy]], **STRIPS** is a foundational planning representation where actions are defined by:
* **Preconditions (PRE):** A list of conditions that must be true to execute the action.
* **Add List (ADD):** A list of propositions that become true after the action.
* **Delete List (DEL):** A list of propositions that become false after the action.

## Constraint Satisfaction Problems (CSP)

A CSP is a mathematical model for problems where the solution must satisfy a set of constraints.

A CSP is defined by three components: $\text{CSP} = \langle X, D, C \rangle$

1.  **Variables ($X$):** The set of entities we are trying to assign values to (e.g., $X_1, X_2, ...$).
2.  **Domains ($D$):** A set of possible values for each variable (e.g., $D_i$ for $X_i$).
3.  **Constraints ($C$):** A set of relations that specify the combinations of values that are allowed (or disallowed) for subsets of variables (e.g., $X_1 \ne X_2$).

***
![[coloring_graph.png]]
*A simple constraint graph showing variables as nodes and binary constraints as edges (e.g., map coloring problem).*
***

## Solving CSPs

The general approach to solving CSPs combines search with **constraint propagation**.

### 1. Backtracking Search

* The basic uninformed algorithm for CSPs, essentially a **Depth-First Search**.
* It assigns values to one variable at a time and checks for constraint violation. If a constraint is violated, it backtracks.
* **Heuristics to speed up Backtracking:**
    * **Minimum Remaining Values (MRV):** Choose the variable with the fewest remaining legal values (most constrained).
    * **Degree Heuristic:** Choose the variable that is involved in the largest number of constraints on unassigned variables.
    * **Least-Constraining Value Heuristic:** Choose a value that rules out the smallest number of values in connected, unassigned variables.

### 2. Constraint Propagation

This is a preprocessing or interleaving step that reduces the number of legal values for a variable based on existing constraints, which in turn may reduce the legal values for other variables.

* **Arc Consistency (AC-3)**: A method that enforces consistency between two variables. An arc $(X_i, X_j)$ is consistent if for every value $x$ in $D_i$, there is some value $y$ in $D_j$ that satisfies the constraint on the $\text{arc}(X_i, X_j)$. If not, values are pruned from $D_i$.
    * Arc Consistency is applied iteratively until no further domain reduction is possible.
    * All $n$-ary constraints can be transformed into binary constraints (although not always worthwhile).

### 3. Local Search

Local search methods (like **Min-Conflicts**) can be effective for CSPs, especially for large problems.

* **Min-Conflicts:** Starts with a complete, potentially invalid, assignment. It repeatedly selects a variable that is in conflict (violates a constraint) and reassigns its value to the one that minimizes the number of conflicts.