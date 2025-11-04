# Uninformed and Informed Search

Search is one of the most fundamental concepts in AI and Computer Science. It provides a systematic method for finding solutions or constructing sequences of actions to reach a goal state. (Based on Lecture 3)

* **Problem Solving as Search:** The dominant approach in AI is formulating a problem as **search in a state space**. This involves defining a goal, representing states, defining legal actions, and finding a solution sequence. (See [[Classical Planning and Constraint Satisfaction Problems (CSP)]] for more on formulation).

## Uninformed (Blind) Search

These algorithms are called "blind" because they have no information about the state space other than what is provided in the problem definition (i.e., they don't know if one non-goal state is "better" than another).

### 1. Breadth-First Search (BFS)

* **Strategy:** Explores the search space level by level. It expands all nodes at depth $d$ before expanding any node at depth $d+1$.
* **Implementation:** Uses a **FIFO (First-In, First-Out) Queue** to store the frontier (nodes to be expanded).
* **Completeness:** Yes, it is guaranteed to find a solution if one exists.
* **Optimality:** Yes, it is guaranteed to find the *shortest* path in terms of number of steps (when step cost is uniform).
* **Time/Space Complexity:** Exponential in depth ($O(b^d)$, where $b$ is branching factor and $d$ is depth of the shallowest goal). Space is the main bottleneck.

### 2. Depth-First Search (DFS)

* **Strategy:** Explores one branch of the tree as far as possible before backtracking.
* **Implementation:** Uses a **LIFO (Last-In, First-Out) Stack** to store the frontier.
* **Completeness:** No, it can get stuck in infinite loops in a non-finite or graph-like search space unless a mechanism is used to check for repeated states (like **Depth-Limited Search** or **Iterative Deepening Search (IDS)**).
* **Optimality:** No, it may find a very long path to the goal if a shorter one exists elsewhere.
* **Time/Space Complexity:** Time is exponential ($O(b^m)$, where $m$ is maximum depth). Space is much better ($O(bm)$), making it memory efficient.

## Informed (Heuristic) Search

Informed search uses knowledge of the problem, typically via a **heuristic function**, to guide the search and focus on promising parts of the state space.

* **Heuristic ($h(n)$):** A function that estimates the cost of the cheapest path from state $n$ to the goal state. It acts as a "rule of thumb" to prioritize search.

### Best-First Search

A general term for search algorithms that select the next node based on an **evaluation function** $f(n)$.

1.  **Greedy Best-First Search:**
    * **Evaluation Function:** $f(n) = h(n)$ (estimated cost to the goal).
    * **Goal:** Attempts to expand the node that seems closest to the goal.
    * **Result:** Fast, but not optimal or complete.

2.  **A* Search (A-Star)**
    * **Evaluation Function:** $f(n) = g(n) + h(n)$
        * $g(n)$: The actual cost incurred from the start node to node $n$.
        * $h(n)$: The estimated cost from node $n$ to the goal (the heuristic).
    * **Goal:** Attempts to expand the node that minimizes the *total estimated path cost*.
    * **Completeness & Optimality:** Yes, provided the heuristic $h(n)$ is **admissible** (never overestimates the cost to the goal) and **consistent** (for any node $n$ and successor $n'$, $h(n) \le c(n, n') + h(n')$).

***
(1)
![[8-puzzle-problem.png]]
(2)
![[Manhattan_distances_8-puzzle.png]]
*Comparison of two heuristics for the 8-puzzle problem: (1) Number of misplaced tiles (admissible); (2) Sum of Manhattan distances (more informed/better heuristic).*
***

## Advanced Search Techniques

* **Iterative Deepening A* (IDA*)**: Combines the space efficiency of DFS with the optimality of A* by performing a series of depth-limited DFS searches, gradually increasing the cost cutoff $f(n) \le C$.
* **Simplified Memory-Bound A* (SMA*)**: A modification of A* that works within a limited memory space, discarding least promising nodes when memory is full.