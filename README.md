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
git grep <function>
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

### `git branch <new-branch-name>`

##### Create a new branch

Creates a new branch without switching to it.

```bash
git branch DevOps
```

---

### `git branch -m <new-name>`

##### Rename a branch

Renames an existing branch.

```bash
git branch -m hotfix
```

---

### `git branch -d <branch-name>`

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

### `git branch -D <branch-name>`

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

### `git checkout -b <new-branch-name>`

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

### `git merge --abort`

Cancels an ongoing merge and **returns the repository to the state before the merge**.

```bash
git merge --abort
```

> ⚠️ Useful when a merge causes conflicts and you want to stop the process.

---

### `git rebase`

##### Rebase

Applies the entire history of one branch on top of another branch, rewriting the 
commit history.

```bash
git rebase main
```

> ⚠️ Important rule:
> Use `rebase` only on local branches.
> Never rebase commits that have already been pushed to a shared remote repository.

---

### `git tag`

##### Tags (Versioning)

Lists all version tags in the project.

```bash
git tag
```

---

### `git tag -a -m`

Creates an annotated tag for a specific commit.

- -a → add tag
- -m → message

Common convention: v0.1, v1.0, etc.

```bash
git tag -a v0.1 -m "Result of the first 23 classes of the course." d724093
```

---

### `git tag -d`

Deletes a specific tag locally.

```bash
git tag -d v0.4
```

---

### `git fetch`

##### Remote Repository Synchronization

Downloads the latest changes from the remote repository without merging them.

```bash
git fetch
```

> ⭐ Safe way to see changes before applying them.

---

### `git pull`

Fetches and merges changes from the remote repository into the local branch.

```bash
git pull
```

Keeps the local repository up to date with remote changes.

---

### `git pull origin <branch-name>`

Pulls changes from a specific remote and branch.

```bash
git pull origin main
```

---

### `git pull origin --allow-unrelated-histories`

Merges a remote branch with a local branch even if their histories are unrelated.

```bash
git pull origin main --allow-unrelated-histories
```

> ⚠️ Use this only when combining projects that started independently.

---

### `git push`

##### Pushing Changes

Pushes the latest local commits to the remote repository.

```bash
git push
```

---

### `git push origin <branch>`

Pushes commits to a specific remote branch.

```bash
git push origin main
```

---

### `git push origin --delete <branch-name>`

Deletes a remote branch or tag.

``` bash
git push origin --delete header
git push origin --delete v0.3
```

> ⚠️ Be careful: this affects the remote repository.

---

### `git push origin --tags`

Pushes all local tags to the remote repository.

```bash
git push origin --tags
```

---

### `git push origin :refs/tags/<tag-name>`

Deletes a specific tag from the remote repository.

```bash
git push origin :refs/tags/v0.4
```

---

### `git config`

##### Git Configuration

Accesses Git configuration settings.

```bash
git config
```

---

### `git config --global user.email`

Updates the global user email for Git commits.

```bash
git config --global user.email "mynew-email@theserver.com"
```

> ℹ️ This email should match the one used in your GitHub account.

---

### `git config --global alias.<name>`

##### Git Aliases

Creates a **permanent alias** for a Git command.

Aliases help reduce typing and improve productivity.

```bash
git config --global alias.tree "log --all --graph --decorate --oneline"
```

Now you can run:

```bash
git tree
```

> ⭐ Recommended for frequently used commands.

--- 

### `git remote`

##### Remote Repositories

Lists the names of remote repositories linked to the project.

```bash
git remote
```

---

### `git remote -v`

Shows the remote repository URLs used for:

- Fetch
- Push

```bash
git remote -v
```

---

### `git remote add origin`

Adds a remote repository to the project.

```bash
git remote add origin https://github.com/username/repository.git
```

> ⚠️ Common mistake:
> Trying to push before adding a remote origin.

---

### `git stash`

##### Stashing Changes

Saves current changes in a temporary memory area without committing them.

```bash
git stash
```

Useful when switching branches with uncommitted work.

---

### `git stash list`

Displays all saved stashes.

```bash
git stash list
```

---

### `git stash pop`

Applies the most recent stash and removes it from memory.

```bash
git stash pop
```

---

### `git stash branch`

Creates a new branch and applies the stashed changes to it.

```bash
git stash branch hotfix
```

---

### `git stash drop`

Deletes the most recent stash.

```bash
git stash drop
```

---

### `git stash drop stash@{id}`

Deletes a specific stash.

```bash
git stash drop stash@{ec43825}
```

---

### `git stash save "message"`

Saves changes with a descriptive message.

```bash
git stash save "temporary change in the homepage"
```

> ℹ️ stash save is deprecated but still commonly used in legacy workflows.

---

### `git stash -u`

Stashes all files, including untracked files.

```bash
git stash -u
```

---

### `git stash clear`

Deletes all saved stashes.

```bash
git stash clear
```

> ⚠️ This action cannot be undone.

---

### `git stash apply`

Applies the most recent stash without removing it from memory.

```bash
git stash apply
```

---

### `git stash apply stash@{id}`

Applies a specific stash.

```bash
git stash apply stash@{ec43825}
```

---

### `git stash branch <branch> stash@{id}`

Creates a new branch and applies a specific stash to it.

```bash
git stash branch hotfix stash@{ec43825}
```

---

### `git clean --dry-run`

##### Cleaning Untracked Files

Shows which untracked files would be removed.

```bash
git clean --dry-run
```

> ⭐ Always run this before deleting files.

---

### `git clean -f`

Deletes untracked files (does not delete directories).

```bash
git clean -f
```

---

### `git clean -df`

Deletes untracked files and directories.

```bash
git clean -df
```

> ⚠️ Danger:
> These files cannot be recovered once deleted.

---

### `git clean -xf`

Deletes:

- Untracked files
- Ignored files

```bash
git clean -xf
```

> ⚠️ Danger:
> This removes ignored files (like those in .gitignore).
> Use only if you are absolutely sure.

---

### `git clean -e <file>`

Deletes untracked files except the specified file.

```bash
git clean -e UserData.sql
```

---

### `git clean --exclude <file>`

Same behavior as -e, using the long option format.

```bash
git clean --exclude UserData.sql
```

---

### `git cherry-pick`

##### Applying Specific Commits

Applies a specific commit to the current branch using its hash.

```bash
git cherry-pick f449d87
```

> ⭐ Useful when you need one fix from another branch without merging everything.

> ⚠️ Common mistake:
> Cherry-picking large or dependent commits, which may cause conflicts.

---

### `git shortlog`

##### Contribution History

Displays a summary of commit history and contributors.

```bash
git shortlog
```

---

### `git shortlog -sn`

Shows how many commits each contributor has made.

```bash
git shortlog -sn
```

---

### `git shortlog -sn --all`

Includes commits that were later removed or rewritten.

```bash
git shortlog -sn --all
```

---

### `git shortlog -sn --all --no-merges`

Counts commits per contributor excluding merge commits.

```bash
git shortlog -sn --all --no-merges
```

---

### `git blame`

##### Line-by-Line History

Shows who last modified each line of a file.

```bash
git blame blogpost.html
```

> ℹ️ Useful for understanding why a change was made.

---

### `git blame -L <start>,<end>`

Displays blame information for a specific line range.

```bash
git blame blogpost.html -L 35,54
```

---

### `git blame -L <start>,<end> -c`

Displays blame information with cleaner, more readable formatting.

```bash
git blame blogpost.html -L 35,54 -c
```

---

