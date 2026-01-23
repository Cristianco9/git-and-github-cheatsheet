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

---

## Git Commands Cheat Sheet

### `git`

The base command used to execute any Git instruction.

```bash
git <command>
```

---

### `gitk`

Opens a graphical user interface (GUI) for Git that displays detailed information 
about:

- Commits
- Branches
- File history

> ℹ️ Note:
> On some systems, gitk is not installed by default and must be installed 
separately using a package manager.

```bash
gitk
```

---

### `git gui`

Opens a graphical Git interface that allows you to:

- Create commits
- Browse project files
- Perform basic Git actions visually

> ℹ️ Note:
> Like gitk, git gui may require a separate installation on some systems.

```bash
git gui
```
---

### `git clone`

Clones a remote repository into the local directory where the command is executed.

- Creates a full copy of the repository
- Includes all commit history

```bash
git clone https://github.com/username/repository.git
```

---

> ⚠️ Common mistake:
> Trying to run git clone inside an already initialized repository.

### `git init`

Initializes a new Git repository in the current directory.

```bash
git init
```

Used when starting a project from scratch.

---

### `git add`

Adds files from the working directory to the staging area.

Add a specific file

```bash
git add file.txt
```

Add all modified and new files in the current directory

```bash
git add .
```

Add all files in the project (tracked and untracked)

```bash
git add -A
```

> ⚠️ Common mistake:
> Forgetting to run git add before committing changes.

---

### `git mv`

Moves or renames files that are tracked by Git.

Rename or move a file

```bash
git mv old-name.txt new-name.txt
```

Force move or rename

```bash
git mv -f old-name.txt new-name.txt
```

Equivalent long option:

```bash
git mv --force old-name.txt new-name.txt
```

Skip move or rename

```bash
git mv -s old-name.txt new-name.txt
```

---

### `git revert HEAD`

Reverts the changes introduced by the last commit, creating a new commit that 
undoes those changes.

```bash
git revert HEAD
```

> ℹ️ Safe for shared repositories because it does not rewrite history.

---

### `Git Reset` 

> (Advanced – Use with Caution ⚠️)

```bash
git reset --hard
```

Resets:

- HEAD
- Staging Area (INDEX)
- Working Directory (WD)

All changes after the specified commit are permanently deleted.

```bash
git reset 48ba633d9d23b634d6965a06e518e47290046806 --hard
```

> ⚠️ Danger:
> This command cannot be undone.

---

### `git reset --soft`

Moves HEAD to a previous commit while:

- Keeping changes in the staging area
- Keeping changes in the working directory

```bash
git reset ce8d510e4315d40f95f947f6a9cb712b1579fe23 --soft
```

Used when you want to rewrite commits without losing work.

---

### `git reset --mixed`

Moves HEAD to a previous commit while:

- Clearing the staging area
- Keeping changes in the working directory

```bash
git reset 48ba633d9d23b634d6965a06e518e47290046806 --mixed
```

> ℹ️ This is the default behavior of git reset if no flag is provided.

---

### `git rm --cached`

Removes a file **from the staging area only**.

- The file is **not deleted** from the disk
- Commonly used when a file should no longer be tracked

```bash
git rm --cached file.txt
```

> ⚠️ Common mistake:
> Thinking this command deletes the file from the system.

---

### `git rm --force`

Removes a file from:

- Git tracking
- The local file system

Git still keeps historical records, so the file can be recovered.

```bash
git rm --force file.txt
```

> ⚠️ Warning:
> Use with caution. The file is deleted from disk.

---

### `git rm HEAD`

Moves changes from the staging area back to unstaged.

```bash
git rm HEAD file.txt
```

> ℹ️ This is useful when you staged a file by mistake.

---

### `git bisect`

Used to search through commits to identify where a bug was introduced.

Commits are labeled as:

- good / new
- bad / old

---

### `git bisect start`

Starts the bisect process.

```bash
git bisect start
```

---

### `git bisect bad`

Marks the current commit as bad.

```bash
git bisect bad
```

---

### `git bisect good`

Marks a commit as good.

```bash
git bisect good v2.6.13.rc2
```

---

### `git bisect reset`

Clears all bisect labels and returns to the original branch state.

```bash
git bisect reset
```

---

### `git grep`

Searches for regular expressions inside project files.

```bash
git grep "function"
```

Useful for quickly finding code across the repository.

---

### `git reflog`

Displays the complete history of HEAD, including:

- Deleted commits
- Reset operations

```bash
git reflog
```

> ℹ️ Very useful for recovering lost commits.

---

### `git log`

Displays the commit history of a repository or a specific file.

```bash
git log
git log history.txt
```

---

### `git log -p`

Shows commit history including the changes (diffs).

```bash
git log -p
```

---

### `git log --stat`

Displays commit history with detailed statistics of file changes.

```bash
git log --stat
```

---

### `git log --all`

Shows all commits across all branches.

```bash
git log --all
```

---

### `git log --all --graph --decorate --oneline`

Displays a graphical representation of:

- Branches
- Merges
- Commits
- Fetch and merge history

```bash
git log --all --graph --decorate --oneline
```

> ⭐ Highly recommended for understanding branch workflows.

---

### `git log -S "keyword"`

Searches commits by specific keywords in the changes.

```bash
git log -S "header"
git log -S "products"
git log -S "router"
```

---

### `git log --pretty=format:""`

Displays commit history using a custom format.

```bash
git log --pretty=format:"%h - %an, %ar : %s"
```

Common placeholders:

- %h → commit hash
- %an → author name
- %ar → relative date
- %s → commit message

---

### `git show`

Displays detailed information about:

- A specific commit
- File changes
- Branch references

```bash
git show
```

---

### `git show-ref --tags`

Lists all tags and the commits they reference.

```bash
git show-ref --tags
```

---

### `git show --branch`

Displays existing branches in the project and their history.

```bash
git show --branch
```

Useful for understanding how branches relate to commits.

---

### `git status`

Shows the current state of the repository:

- Modified files
- Staged files
- Untracked files
- Current branch

```bash
git status
```

> ⭐ Run this command often.

---

### `git branch`

Lists all local branches in the repository.

```bash
git branch
```

---

### `git branch -r`

Lists all remote branches.

```bash
git branch -r
```

---

### `git branch "new-branch-name"`

##### Create a new branch

Creates a new branch without switching to it.

```bash
git branch DevOps
```

---

### `git branch -m "new-name"`

##### Rename a branch

Renames an existing branch.

```bash
git branch -m hotfix
```

---

### `git branch -d "branch-name"`

##### Delete a branch

Deletes a specific branch.

```bash
git branch -d header
```

Equivalent long option:

```bash
git branch --delete hotfix
```

---

### `git branch -D "branch-name"`

##### Force delete a branch

Deletes a branch even if it has not been merged.

```bash
git branch -D feature-x
```

> ⚠️ Warning:
> Use only when you are sure the branch is no longer needed.

---

### `git branch -v`

Displays the latest commit on each branch.

```bash
git branch -v
```

---

### `git branch --merged`

Lists branches that have been merged into the current branch.

```bash
git branch --merged
```

---

### `git branch --no-merged`

Lists branches that have not been merged into the current branch.

```bash
git branch --no-merged
```

---

### `git switch`

Switches between branches.

```bash
git switch home
```

> ℹ️ Recommended over checkout for branch switching.

---

### `git checkout`

Used to:

- Switch between branches
- Restore previous versions of files

Switch branches

```bash
git checkout header
```

Return to the previous branch

```bash
git checkout -
```

---

### `git checkout -b "new-branch-name"`

##### Create and switch to a new branch

Creates a new branch and switches to it immediately.

```bash
git checkout -b header
```

---

### `git commit -m "message"`

Commits staged files to the repository with a commit message.

```bash
git commit -m "the first commit"
```

> ⚠️ Common mistake:
> Committing with unclear or empty messages.

---

### `git commit -am "message"`

Stages and commits previously tracked files only.

```bash
git commit -am "update styles"
```

> ⚠️ Common mistake:
> Assuming this command includes new (untracked) files.

---

### `git commit --amend -m "message"`

Changes the commit message of the last commit.

```bash
git commit --amend -m "updated commit message"
```

---

### `git commit --amend --no-edit`

Adds changes to the last commit without changing the message.

```bash
git commit --amend --no-edit
```

---

### `git diff`

##### Comparing Changes

Shows differences between:

- Files
- Commits
- Versions

```bash
git diff 48ba633d9d23b634d6965a06e518e47290046806 \
c327a24e4603f8d8ef166f99ea685b3d690a830b
```

---

### `git merge`

###### Merging

Merges changes from a specified branch into the current branch.

```bash
git merge feature-branch
```

> ⚠️ Common mistake:
> Merging without first pulling the latest changes from the remote repository.

---

