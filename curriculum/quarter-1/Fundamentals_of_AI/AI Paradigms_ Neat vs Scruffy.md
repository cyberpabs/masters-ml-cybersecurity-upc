# AI Paradigms

The history of AI research is categorized into two main schools of thought: **Neat** and **Scruffy**. (Based on Lecture 2)

* This distinction was popularized by the 'scruffy' researcher **Roger Schank** in the 1970s.
* Both camps operate under the **Functionalist Assumption**: the goal is to produce intelligent behavior.

## The Neat Approach (Symbolic AI)

**Neat AI** focuses on building **thinking first**, where computers perform most of the search and reasoning through formal rules.

* **Core Idea:** Intelligence is achieved through **symbolic manipulation** and **formal reasoning**.
* **Key Concept: [[Physical Symbol System Hypothesis (PSSH)]]**
    * Proposed by Allen Newell and Herbert A. Simon.
    * States that a physical symbol system has the necessary and sufficient means for general intelligent action.
    * A system that can manipulate structured symbol structures (lists, logical sentences).
* **Challenges:**
    * **The [[Symbols Grounding Problem]]**: How do the abstract symbols used by the system relate to the real world (e.g., the **"Chinese Room"** argument)?
    * **The [[Frame Problem]]**: The difficulty of formally stating all the things that *do not* change when an action is performed.

### Planning with STRIPS

**STRIPS** (STanford Research Institute Problem Solver) is a classic example of a neat-based planning language. Actions are defined by:

1.  **Preconditions**: What must be true to execute.
2.  **Add List**: What becomes true after execution.
3.  **Delete List**: What stops being true after execution.

## The Scruffy Approach (Connectionist/Emergent AI)

**Scruffy AI** focuses on building intelligent behavior through the agent's **interaction with its environment**, allowing **behavior to emerge** from the system's low-level components.

* **Core Idea:** Intelligence is too complex to be explicitly programmed; it arises from a complex system's interaction with the world.
* **Key Concepts:**
    * **Emergence**: High-level intelligence appears from the interaction of many simple elements (e.g., neurons in a network).
    * **Reactive Planning**: Plans are pre-written or learned as immediate responses to perceived situations, rather than being derived from first-principles logic.
* **Modern Context:** The rise of **Machine Learning** and **Deep Learning** (the recent AI "Summer") is often considered a victory for the scruffy, or connectionist, approach.

## The Future: Neuro-Symbolic AI

**[[Neuro-Symbolic AI]]** is a hybrid approach aiming to combine the strengths of both paradigms.

* **Neat Strengths**: Planning and deductive reasoning.
* **Scruffy Strengths**: Vision and pattern recognition.
* **Goal**: To create systems where symbolic knowledge can guide and constrain deep learning, or where neural networks learn to extract and apply formal logic.