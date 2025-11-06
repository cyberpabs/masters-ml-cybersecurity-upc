# Historical Background and Core Concepts

This module lays the groundwork for understanding Artificial Intelligence, exploring its history, the concept of an intelligent agent, and the environments in which they operate. (Based on Lecture 1)

## A Quick History of AI

The field of AI has roots in the **early 20th century** with Alan Turing inventing Computer Science to solve problems of intelligence and proposing the **Imitation Game** (Turing Test).

* The term **Artificial Intelligence** was officially proposed for the first time at the **Dartmouth Conference in 1956**.
* The history is marked by alternating periods of great progress and funding (**AI Summers**) and reduced interest (**AI Winters**).

## Agents, Not AI

In modern AI theory, the focus is often placed on **intelligent agents**, rather than abstract intelligence.

An **Agent** is anything that can be viewed as perceiving its **environment** through **sensors** and acting upon that environment through **actuators**.

![[agent_functionality.png]]
*Diagram illustrating the agent-environment interaction. A central 'Agent' box connected via 'Sensors' (input) to an 'Environment' box, and via 'Actuators' (output) back to the 'Environment' box.*
***

A **rational agent** is one that acts to achieve the best outcome or, when there is uncertainty, the best *expected* outcome. The agent's success is measured by a **performance measure**.

## Environment and Its Properties

The characteristics of the environment heavily influence the design of the optimal agent. Key properties include:

| Property          | Description                                                            | Example                                                       |
| :---------------- | :--------------------------------------------------------------------- | :------------------------------------------------------------ |
| **Observable**    | Can the agent's sensors access the complete state?                     | Chess (Fully Observable) vs. Driving (Partially Observable)   |
| **Deterministic** | Is the next state entirely determined by the current state and action? | Chess (Deterministic) vs. Driving (Stochastic)                |
| **Episodic**      | Is the agent's experience divided into atomic, independent episodes?   | Assembly line inspection (Episodic) vs. Driving (Sequential)  |
| **Static**        | Can the environment change while the agent is deliberating?            | Crossword puzzle (Static) vs. Driving (Dynamic)               |
| **Discrete**      | Is the set of states and actions finite/countable?                     | Chess (Discrete) vs. Driving (Continuous)                     |
| **Known**         | Does the agent know the rules (transition function and rewards)?       | Defined board game (Known) vs. Exploring a new city (Unknown) |

## Types of Agents

1.  **[[Simple Reflex Agents]]**: Act based only on the current percept. Only work in fully observable, deterministic environments.
2.  **[[Model-Based Reflex Agents]]**: Maintain an **internal state** (a 'model' of the world) to track unobservable aspects of the environment.
3.  **[[Goal-Based Agents]]**: Use their model to reason about a sequence of actions that will lead to a desired goal state. This involves searching and planning (see [[Uninformed and Informed Search]]).
4.  **[[Utility-Based Agents]]**: Use a **utility function** to choose the action that maximizes the expected happiness when multiple action sequences can achieve a goal, or in environments with uncertainty.
5.  **[[Learning Agents]]**: Include a **learning element** to improve the agent’s components based on feedback from a **critic**.