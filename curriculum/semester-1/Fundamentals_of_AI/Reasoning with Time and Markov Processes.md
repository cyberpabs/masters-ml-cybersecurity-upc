# Reasoning with Time and Markov Processes

AI systems must often reason and make decisions in environments where outcomes are uncertain, particularly when dealing with sequences of events over time. This leads us to probabilistic models. (Based on Lecture 9 and FOL PPT on MDPs)

## The Markov Assumption

Most probabilistic models that deal with time rely on the **Markov Assumption**.

* **Definition:** The future state of a system depends only on the **present state**, and is conditionally independent of all past states given the present state.
* **Mathematically:** $P(S_t \mid S_{t-1}, S_{t-2}, \dots, S_0) = P(S_t \mid S_{t-1})$
* **First-Order Markov Process (Chain):** The model only relies on the immediate previous state.

## Markov Decision Processes (MDP)

An **MDP** is a mathematical framework for modeling decision-making in environments where outcomes are partly random and partly under the control of an agent. It is the theoretical foundation of **Reinforcement Learning (RL)**.

An MDP is defined by: $\langle S, A, T, R, \gamma \rangle$
1.  **States ($S$):** A set of states the environment can be in.
2.  **Actions ($A$):** A set of actions the agent can take.
3.  **Transition Model ($T$):** $P(s' \mid s, a)$, the probability of moving to state $s'$ from state $s$ when taking action $a$.
4.  **Reward Function ($R$):** $R(s, a, s')$, the reward received for a transition.
5.  **Discount Factor ($\gamma$):** A factor ($0 \le \gamma \le 1$) that determines the importance of future rewards.

* **Goal:** To find an optimal **Policy** ($\pi^*$) that maximizes the expected cumulative discounted reward.
* **Bellman Optimality Equation:** A set of non-linear equations used to solve for the optimal value function $V^*(s)$, from which the optimal policy can be extracted.
* **Policy/Value Iteration:** Algorithms used to iteratively find the optimal value function and policy.

## Hidden Markov Models (HMM)

An **HMM** is a probabilistic model where the system being modeled is a Markov process with **unobservable (hidden) states**. The agent can only observe a sequence of **emissions** (observations) which depend on the underlying hidden state.

* **HMM is defined by:**
    * **Hidden States ($S$):** The underlying process states (e.g., "Rainy", "Sunny").
    * **Observations ($O$):** The observable evidence (e.g., "Umbrella", "No Umbrella").
    * **Transition Matrix ($A$):** $P(S_t \mid S_{t-1})$, the probability of transitioning between hidden states.
    * **Emission Matrix ($B$):** $P(O_t \mid S_t)$, the probability of an observation given a hidden state.
    * **Initial Probabilities ($\pi$):** $P(S_0)$, the probability of starting in a given state.

***
![[HMM_states_observations.png]]
*Image Placeholder: A graphical model of an HMM showing a chain of hidden states $S_t$ influencing their respective observations $O_t$, with transitions from $S_{t-1}$ to $S_t$.*
***

## The Three Core HMM Problems (Rabiner's Problems)

HMMs are used to solve three canonical problems:

1.  **Likelihood (Evaluation):** Given the model ($\lambda$) and an observation sequence ($O$), what is the probability $P(O \mid \lambda)$? (The **Forward Algorithm** is used for this).
2.  **Decoding:** Given the model and an observation sequence, what is the most likely sequence of *hidden states* ($S$) that generated the observations? (The **Viterbi Algorithm** is used for this).
3.  **Learning (Training):** Given a set of observation sequences, how do we adjust the model parameters ($\lambda = \{A, B, \pi\}$) to best fit the data? (The **Forward-Backward (Baum-Welch) Algorithm** is used for this).