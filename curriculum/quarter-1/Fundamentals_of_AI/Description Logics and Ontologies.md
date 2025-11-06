# Description Logics and Ontologies

While FOL is highly expressive, it is **undecidable** (there is no algorithm guaranteed to terminate in all cases). **Description Logics (DL)** were developed as a decidable subset of FOL focused on efficient Knowledge Representation (KR) and reasoning, particularly with semantic data. (Based on Lecture 7)

## Ontologies

* **Etymology:** From the Greek for 'being' ($\text{öv}$) and 'logical discourse' ($\text{λογία}$). In metaphysics, it is the study of existence.
* **AI Definition:** A formal specification of a shared conceptualization. It defines a set of representational primitives (concepts, roles, and individuals) with which to model a domain of knowledge.
* **Key Idea:** Ontologies provide a **schema** or a vocabulary for a domain, enabling knowledge sharing and reuse.

## Description Logics (DL)

DL is a family of formal knowledge representation languages that serve as the foundation for modern ontologies.

### Components of DL Knowledge Bases

A DL Knowledge Base (KB) is split into two parts:

1.  **TBox (Terminological Box / Schema):**
    * Contains the **schema** or **ontology** (the *shared conceptualization*).
    * It defines **Concepts** (Classes) and **Roles** (Relationships) and their logical relationships.
    * *Example:* $\text{Man} \sqsubseteq \text{Person} \sqcap \exists \text{hasGender}.\text{Male}$ (A Man is a Person AND they existentially have the role $\text{hasGender}$ with value $\text{Male}$).
2.  **ABox (Assertional Box / Data):**
    * Contains **factual data** about specific individuals (the *data*).
    * It asserts that individuals belong to specific concepts or are related by roles.
    * *Example:* $\text{John} : \text{Man}$ (John is a Man), $(\text{John}, \text{Mary}) : \text{hasSpouse}$ (John is related to Mary by $\text{hasSpouse}$).

## Web Ontology Language (OWL)

**OWL** is the W3C standard for describing ontologies on the Semantic Web. OWL is based on Description Logics and comes in different flavors of complexity and expressivity (e.g., $\text{OWL 2}$ is based on the $\text{SROIQ}$ DL).

## Reasoning Tasks in DL

DL reasoners can perform crucial tasks efficiently:

* **Subsumption:** Is Concept A more general than Concept B? (e.g., Is $\text{Man}$ subsumed by $\text{Person}$?)
* **Classification:** Computing the full concept hierarchy (TBox consistency).
* **Instance Checking (Retrieval):** Does a specific individual belong to a concept? (e.g., Is $\text{John}$ an instance of $\text{Criminal}$?)
* **Knowledge Base Consistency:** Is the combination of TBox and ABox logically possible?