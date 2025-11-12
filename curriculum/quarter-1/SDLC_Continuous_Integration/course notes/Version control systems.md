# Forge

Is the consolidated platform, the digital workspace, where the entire project development and delivery lifecycle is managed and orchestrated. It is the central hub for **DevOps** and **CI/CD** workflows.

|Forge Function|Description based on Notes|
|---|---|
|**Version Control System** (VCS)|Hosts the project's source code and full history (e.g., **Git**).|
|**Code Review & History**|Provides the interface for developers to discuss changes (e.g., **Merge Requests**) and trace every modification.|
|**Continuous Integration** (CI)|Manages and automates the process of building and testing code upon every change.|
|**Bug Tracking System**|Links discovered issues directly to the code changes intended to fix them.|
|**Project & Task Management**|Organizes the development work, connecting tasks and sprints to code commits.|
|**Release Management**|Controls the process of packaging, deploying, and releasing software versions.|

**Examples:** **GitHub**, **GitLab**, and **OpenProject**.

## GitOps

A key concept often implemented through the Forge is **GitOps**. This is a **Continuous Delivery (CD)** methodology that dictates:

> **Git is the single source of truth** for both the application and the infrastructure.

It leverages **DevOps** principles and Git-based workflows, typically using containerization technologies, to automate deployments.

# Version Control Systems (VCS)
A Version Control System is a software tool that tracks and manages changes to a codebase over time. Its primary function is to **allow developers to work concurrently and to revert to previous states** if a bug is introduced.

### The Problem: Integration

The core challenge in collaborative development is integrating changes from multiple developers without creating conflicts or breaking the mainline code. Git solves this through two primary branch integration strategies: **Merge** and **Rebase**.

## Centralized vs. Distributed

There are two primary architectures for Version Control Systems (VCS), distinguished by where the official repository and the historical data reside:

### A. Centralized Version Control Systems (CVCS)

CVCS follows a strict **client-server model**. All changes, history, and the codebase reside on a single, central server.

|**Feature**|**Description**|
|---|---|
|**Repository Structure**|**Single Point of Truth (S.P.O.T.)**. Developers must **check out** files, work locally, and then **commit** changes back to the server.|
|**Offline Work**|**Not possible** for most operations (committing, viewing full history). A network connection to the central server is mandatory.|
|**Backup and Redundancy**|The central server is a **Single Point of Failure**. If the server crashes and no external backups exist, the entire project history is lost.|
|**Branching & Merging**|Typically **cumbersome** and slow, as branching requires server communication and can be complex to manage.|
|**Example**|**Subversion (SVN)**, CVS.|

### B. Distributed Version Control Systems (DVCS) 🌐

DVCS (like **Git**) eliminates the reliance on a single server. In this model, every developer has a **full clone** of the entire repository, including the complete history, on their local machine.

| **Feature**               | **Description**                                                                                                                                                                                           |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Repository Structure**  | Every clone is a **full-fledged repository**. Developers **commit** locally, creating history on their machine, and later **push/pull** changes to synchronize with others (e.g., the remote `origin`).   |
| **Offline Work**          | **Full offline capability**. All major operations (committing, branching, viewing history, rolling back) are performed locally without a network connection.                                              |
| **Backup and Redundancy** | **Built-in redundancy**. Every developer’s clone acts as a **full project backup**. If the central server (like GitHub or GitLab) fails, the history can be recovered from any developer's local machine. |
| **Branching & Merging**   | **Fast and lightweight**, as branches are simply pointers managed locally. This is what enables complex workflows and frequent, small feature development.                                                |
| **Example**               | **Git**, Mercurial (Hg), Bazaar.                                                                                                                                                                          |
# Git

Git is the prime example of a DVCS. Even though teams often use a **Forge** (like GitHub or GitLab) to designate one remote repository as the "official" source, the system is still fundamentally distributed. This setup provides the best of both worlds:

1. **Central Coordination:** The Forge acts as the coordination point for CI/CD and pull requests.
   
2. **Decentralized Resilience:** Developers retain the full benefits of local, fast, and resilient operations.

> A **Commit** is the fundamental unit of history in Git. It is a snapshot of the entire repository at a specific moment in time.

| **Component**      | **Description**                                                                                                                                                                                                                                  |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Snapshot**       | Captures the state of all files in the **working directory** and stores a reference to them in the Git database.                                                                                                                                 |
| **Metadata**       | Includes essential information about the change: the commit **Author**, the commit **Committer**, a timestamp, and a **Commit Message** explaining the change.                                                                                   |
| **Parent Pointer** | Every commit (except the first one, the _root_ commit) contains a pointer referencing the SHA of the **previous commit**. This chain of pointers is what defines the linear history of a branch.                                                 |
| **SHA Hash**       | Each commit is cryptographically hashed, resulting in a unique 40-character SHA-1 identifier. If any data (file content or metadata) in the commit changes, the SHA **must change** (this is why **rebase** is destructive—it creates new SHAs). |

> In Git, a **Branch** is not a copy of the code; it is a lightweight, **movable pointer** or label to a specific commit.

- **Creation**: When you create a new branch, Git simply creates a new pointer that points to the exact same commit your current branch is pointing to.

- **Movement**: When you make a new commit, Git automatically moves the branch pointer forward to point at this new commit, extending the history.

- **The** `HEAD`: This is a special pointer that indicates which branch you are currently working on and where the next commit will be added.
#### Quick commands:

```bash
git branch <branch> # Create branch
git branch -d <branch> # Remove a branch
git checkout <branch> # Switch branch (change HEAD)
# if there are no conflicts in doing so

git checkout -b <branch> # Create and switch
# There is also a checkout equivalent: 
git switch <branch> # and
git switch -c <branch>
```

### The Three Stages of Git (The Workflow):

The Git workflow defines three main states for the files in your repository, which dictate how files are tracked and recorded in a commit.

- **Working Directory (Modified):** The files you are currently editing. Changes are unstaged and not yet tracked for the next commit.

- **Staging Area / Index (Staged):** A temporary area where you place the specific changes you want to include in your _next_ commit. This allows you to selectively group related changes, even if you’ve modified many files.

- **Local Repository (Committed):** The hidden `.git` folder that stores the committed snapshots and the full history of the project. Once committed, the changes are safe and part of the permanent history.

![[git_workflow_example.png|500]]


### Branching vocabulary

> **Diverging** refers to a state where two branches (or a local branch and its remote counterpart) have developed independently since their last common commit, meaning **each branch has unique commits that the other does not have**.

#### A. Git Merge or Merging

- **Process:** **Non-destructive** operation. It combines the history of two branches by identifying the common ancestor and the two current tips.

- **Result:** Creates a new commit, the **Merge Commit**, which has two parents.

- **History:** **Preserves all history**, including the exact moment and context where the branches diverged and then joined. The commit graph is **non-linear** (a DAG).

- **Use Case:** Recommended for integrating changes into shared, public branches (like `main`), as it provides a permanent, auditable record of the integration event.

##### Types of merge

- **Merging fast-forward**: simplified, linear merge that is only possible when the target branch has not changed since the source branch was created (i.e., the target branch is a direct ancestor of the source branch).
	- Git simply moves the target branch's pointer forward to the last commit of the source branch. As a result, no new merge commit is created. The history remains perfectly linear.
  
- **Three-way merging**: standard, non-destructive merge used when branches have diverged (meaning they have unique commits since their last common point).
	- Git identifies the three key points: the two branch tips (yours and the other) and the last common ancestor commit. As a result, a new commit (the Merge Commit) is created, which combines the changes from both branches.

#### B. Git Rebase or Rebasing

- **Process:** **Destructive** operation. It takes the commits from one branch (e.g., your feature branch) and re-applies or "replays" them on top of the latest commit of another branch (e.g., `main`).

- **Result:** New commits are created for the replayed changes, giving them **new SHA hashes**. **Merge commits are eliminated.**

- **History:** Creates a **perfectly linear** commit history, making the project log cleaner and easier to read (as if the feature work started from the latest point).

- **Use Case:** Ideal for **cleaning up your local, private feature branch** before submitting a merge request, allowing you to **squash** multiple small commits into one logical change.

- **Golden Rule:** **Never rebase public/shared branches.** Rewriting shared history causes conflicts for all other collaborators.

### Commit Roles in Pull Requests

When integrating a feature branch via a Merge Request (or Pull Request), Git differentiates between the **Author** and the **Committer**:

| Integration Strategy   | Commits Involved                                                                         | Author Role                                          | Committer Role                                       |
| ---------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| **Merge Pull Request** | **Topic Commit:** The developer's work. <br><br>**Merge Commit:** The integration event. | Developer (for Topic) <br><br>Maintainer (for Merge) | Developer (for Topic) <br><br>Maintainer (for Merge) |
| **Fast-forward Merge** | Only one commit, as the history is linear.                                               | Developer (who wrote the change)                     | Maintainer (who accepted the merge)                  |
