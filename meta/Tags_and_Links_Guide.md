# 🏷️ Tag & Link Guide

_Master’s in Machine Learning and Cybersecurity for Internet Connected Systems (UPC)_

This guide defines how to tag and link notes consistently across your Obsidian vault.  
Keeping a clean tag system ensures better search results, Dataview queries, and an intuitive graph structure.

---

## 🔖 1. Tag Categories

### 🎓 **Academic Structure**

|Tag|Description|
|---|---|
|`#semester-1`, `#semester-2`, `#semester-3`|Courses or notes tied to a specific semester|
|`#course`|Generic tag for any class-related note|
|`#project`|For lab work, assignments, or thesis tasks|
|`#resources`|Notes summarizing external materials (books, papers, etc.)|

---

### 🤖 **Machine Learning & AI**

|Tag|Description|
|---|---|
|`#ml`|General machine learning topics|
|`#ai`|Artificial intelligence concepts|
|`#dl`|Deep learning (CNNs, RNNs, transformers)|
|`#nn`|Neural networks|
|`#supervised`, `#unsupervised`, `#reinforcement`|Learning paradigms|
|`#nlp`|Natural language processing|
|`#optimization`|Optimization and loss functions|
|`#math`, `#stats`, `#prob`|Core mathematical foundations|

---

### 🔐 **Cybersecurity & Networks**

| Tag                    | Description                              |
| ---------------------- | ---------------------------------------- |
| `#cybersecurity`       | General security topics                  |
| `#cryptography`        | Encryption and key management            |
| `#network-security`    | Network and protocol defense             |
| `#ethical-hacking`     | Pen-testing and vulnerability assessment |
| `#malware`             | Malware analysis                         |
| `#forensics`           | Digital forensics                        |
| `#industrial-security` | ICS/SCADA and industrial systems         |
| `#wireless`            | Wireless and mobile network security     |

---

### 🌐 **IoT & Systems**

|Tag|Description|
|---|---|
|`#software-engineering`|Software Engineering topics (general)|
|`#iot`|Internet of Things systems|
|`#cyberphysical`|Cyber-physical and embedded systems|
|`#sensors`|Sensor networks and hardware|
|`#cloud`|Cloud computing and distributed systems|
|`#database`|Relational / non-relational data systems|
|`#frontend`|Web and interface technologies|
|`#hpc`|High-performance computing|

---

## 🧭 2. Tagging Rules

- Always use **lowercase** tags.
- For multi-word tags, use **hyphens** (`#network-security`), not underscores.
- Add **at least one domain tag** (`#ml`, `#cybersecurity`, etc.) and one **semester tag**.
- Example YAML front-matter:
```yaml
---
    semester: 1
    ects: 3
    type: compulsory
    tags: []
---
```

---

## 🔗 3. Internal Linking Conventions

- Use double brackets for course or concept references:
```
See [[Machine_Learning]] for algorithm fundamentals.
 ```
- Link **concepts → course folders** when possible to show structure.  
    Example: `[[CyberPhysical_Systems/IoT_Architecture]]`
- Create **index notes** with links for overview pages:
```
    - [[Machine_Learning]]
    - [[Neural_Networks]]
    - [[Cryptography]]
```
- Avoid duplicate spellings: if a note is called _Machine_Learning_, always link it exactly that way.

---

## 🧩 4. Dataview Tips

Example queries to list all ML-related courses:
```dataview
TABLE semester, topics
FROM "curriculum"
WHERE contains(topics, "ml")
SORT semester ASC
```

To list all cybersecurity notes:
```dataview
LIST FROM "curriculum"
WHERE contains(topics, "cybersecurity")
```

---

## 🗂️ 5. Maintenance

- Review this file each semester to add new tags or categories.
- Keep tags minimal and meaningful — 5–8 per note is plenty.
- Regularly use the **Graph View → Group by Tags** to ensure your structure stays coherent.