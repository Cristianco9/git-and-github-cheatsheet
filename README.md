# Version Control with Git & GitHub

---

### Codecamp academy
#### Advanced Fullstack Software Development Program
**Instructor:** Cristian Camilo Cortes Ortiz

---

## Git and GitHub

### What is Git?
Git is a **distributed version control system** created by **Linus Torvalds** to 
allow multiple engineers and developers to work **in parallel** on the Linux kernel.

Git is mainly written in **C**, **Bourne Shell**, and **Perl**.  
It allows you to track changes, collaborate safely, and manage different versions 
of a project.

---

### What is GitHub?
GitHub is a **collaborative development platform** that hosts projects using Git.

- Released in **2008**
- Acquired by **Microsoft in 2018**
- Provides tools for collaboration, code review, deployment, and automation

> ⚠️ **Common mistake:**  
> Git ≠ GitHub  
> Git is the tool. GitHub is a platform that uses Git.

---

## Core Git Concepts

### Staging Area
The **staging area** is a temporary space in memory where Git stores the list of 
**tracked files** after running:

```bash
git add
```

Only files in the staging area will be included in the next commit.

> ⚠️ **Common mistake:**  
> Editing files and running `git commit` without running `git add` first.

---

## Branches

Branches are **independent versions of the same project**.  
They allow developers to work on features or fixes **without affecting the main 
codebase**.

---

### Main (Master)

The **main branch** is the **primary and permanent branch** of the project.

- Exists locally and on GitHub  
- Represents the **stable version** of the project  

> ℹ️ **Note:**  
> `master` is deprecated in most projects. `main` is now the standard.

---

### Development Branch

The **development branch** contains **experimental or in-progress features**.

- Changes are tested here  
- Later merged into `main`

---

### Hotfix Branch

A **hotfix branch** is used for **urgent production fixes**.

- Created from `main`  
- Merged back into `main` after the fix  

> ⚠️ **Common mistake:**  
> Applying urgent fixes directly on `main` without a hotfix branch.

---

## Environments

### Production Server

The **production server** hosts the **final version** of the project that users 
interact with.

---

### Development / Staging Server

The **development (staging) server** hosts **testing versions** of the project 
before going live.

---

## Collaboration on GitHub

### Pull Request

A **Pull Request (PR)** is a GitHub feature that pauses the merge process so changes 
can be **reviewed before merging** into the main branch.

**Equivalent names:**

- GitHub: Pull Request  
- GitLab: Merge Request  
- Bitbucket: Push Request  

> ⚠️ **Common mistake:**  
> Merging code without reviewing the changes.

---

### Fork

A **fork** is a complete copy of a repository into your own GitHub account.

- Used to contribute to external projects  
- Allows independent experimentation

---

### Upstream

**Upstream** refers to the **original remote repository** from which a project 
was forked.

Used to keep your fork updated with the original project.

---

## GitHub Pages

GitHub Pages allows you to:

- Host a website directly from a repository  
- Use **free hosting**  
- Access the site via a generated URL  

Commonly used for portfolios, documentation, and demos.