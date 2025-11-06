# Propositional and First-Order Logic (FOL)

Logic forms the foundation of the **[[AI Paradigms_ Neat vs Scruffy|Neat]]** approach to AI, providing a formal, systematic way of representing knowledge and performing deductive reasoning. (Based on Lecture 6 and FOL PPT)

## Propositional Logic (PL)

PL is a simple logic used for reasoning about facts.

* **Syntax (The Language):**
    * **Propositional Variables:** Simple statements that are either $\text{True (T)}$ or $\text{False (F)}$ (e.g., $P$, $Q$).
    * **Connectives:**
        * Negation ($\neg p$)
        * Conjunction ($p \land q$)
        * Disjunction ($p \lor q$)
        * Implication ($p \to q$)
        * Biconditional ($p \leftrightarrow q$)
* **Semantics (The Meaning):** Defines the truth of sentences based on the truth of their parts using **truth tables**.
* **Inference:** The process of deriving new, valid conclusions (sentences) from an existing Knowledge Base (KB). **Modus Ponens** ($((P \to Q) \land P) \implies Q$) is a key rule of inference.
* **Limitation:** PL only deals with true/false *facts*. It cannot express properties of objects or relationships between them.

## First-Order Logic (FOL) / Predicate Logic

FOL is a much more expressive logic that models the world in terms of objects, properties, relations, and functions.

### Components of FOL

| Component | Description | Example |
| :--- | :--- | :--- |
| **Objects** | Things with individual identities. | $\text{Student}$, $\text{Lecture}$, $\text{Latveria}$ |
| **Properties (Predicates)** | Attributes of objects. | $\text{Blue}(\text{car})$, $\text{Hostile}(\text{Latveria})$ |
| **Relations (Predicates)** | Relationships between objects. | $\text{BrotherOf}(\text{John}, \text{Sue})$ |
| **Functions** | A relation with only one 'value' for a given 'input'. | $\text{FatherOf}(\text{John})$ |
| **Constants** | Names for specific objects. | $\text{T'Chapa}$, $\text{Wakanda}$ |

### Quantifiers

FOL introduces quantifiers to express properties over collections of objects:

1.  **Universal Quantifier ($\forall$)**: "For all" or "Every"
    * $\forall x \text{ Missiles}(x) \to \text{Weapon}(x)$
2.  **Existential Quantifier ($\exists$)**: "There exists" or "Some"
    * $\exists x \text{ Owns}(\text{Latveria}, x) \land \text{Missiles}(x)$

### Inference with FOL

Inference in FOL is more complex than in PL. The goal is to prove a sentence is true given the KB, which involves manipulating expressions with quantifiers.

* **KB Example (Missiles Problem):**
    1.  $\text{Missiles}(x) \to \text{Weapon}(x)$
    2.  $\text{EnemyOf}(x, \text{Wakanda}) \to \text{Hostile}(x)$
    3.  $\text{Wakandian}(\text{T'Chapa})$
    4.  $\text{EnemyOf}(\text{Latveria}, \text{Wakanda})$
    5.  $\exists x \cdot \text{Owns}(\text{Latveria}, x) \land \text{Missiles}(x)$
    6.  $\forall x \cdot \text{Missile}(x) \land \text{Owns}(\text{Latveria}, x) \to \text{Sells}(\text{T'Chapa}, x, \text{Latveria})$
    7.  $\text{Wakandian}(x) \land \text{Weapon}(y) \land \text{Sells}(x, y, z) \land \text{Hostile}(z) \to \text{Criminal}(x)$

* By applying rules like **Universal Elimination** (instantiating $x$ with a constant) and **Modus Ponens**, one can infer:
    * From (2) and (4): $\text{Hostile}(\text{Latveria})$
    * From (1) and (5): $\exists x \cdot \text{Owns}(\text{Latveria}, x) \land \text{Weapon}(x)$
    * ... and eventually deduce $\text{Criminal}(\text{T'Chapa})$.