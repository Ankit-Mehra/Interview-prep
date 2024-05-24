# Git

### 1. What is Git, and why is it used?

**Answer:** Git is a distributed version control system used for tracking changes in source code during software development. It's designed to handle everything from small to very large projects with speed and efficiency. Git enables multiple developers to work on the same project simultaneously, managing changes from multiple sources effectively.

**Example:** When a developer wants to start working on a new feature for a project, they can create a new branch in Git. This branch allows them to make changes without affecting the main codebase. Once the feature is complete and tested, it can be merged back into the main branch.

```bash
git branch new-feature
git checkout new-feature
# Developer makes changes and commits them
git commit -am "Add new feature"
# Merge the new feature into the main branch
git checkout main
git merge new-feature
```

### 2. Explain the difference between `git pull` and `git fetch`.

**Answer:** Both `git pull` and `git fetch` are used to update the local version of a repository from a remote source. However, `git fetch` only downloads new data from a remote repository without integrating any of this new data into your working files. `git pull`, on the other hand, not only downloads the new data but also integrates it into your current working branch.

**Example:** If you just want to see what others have done but keep your local branch work untouched, you would use `git fetch`.

```bash
git fetch origin
```

If you want to update your current branch with the latest changes from the remote, you would use `git pull`.

```bash
git pull origin main
```

### 3. What is a branch in Git? How do you create a new branch?

**Answer:** A branch in Git is essentially a lightweight movable pointer to one of the commits. It represents an independent line of development in a project, allowing you to work on new features or bug fixes without affecting the main codebase.

**Example:** To create a new branch named `feature-x` and switch to it, you use the following commands:

```bash
git branch feature-x
git checkout feature-x
# Or in a single command
git checkout -b feature-x
```

### 4. Explain what a merge conflict is and how to resolve it.

**Answer:** A merge conflict occurs when Git is unable to automatically resolve differences in code between two commits. This typically happens when two branches have made edits to the same line in a file, or when one branch deletes a file while another branch was modifying it.

**Example:** To resolve a merge conflict, you first need to edit the files to fix the conflicting changes. After editing, you mark the file as merged with `git add`, and then you can complete the merge process with `git commit`.

```bash
# Detect which files have conflicts
git status
# Manually edit the files to resolve conflicts
# Add the file to mark it as resolved
git add <filename>
# Commit the resolved changes
git commit -m "Resolved merge conflict by incorporating both feature changes"
```

### 5. How do you revert a commit that has already been pushed and made public?

**Answer:** One way to revert a public commit is by using `git revert`, which creates a new commit that undoes all changes made in a specified commit. This is a safe way to undo changes without rewriting history.

**Example:**

```bash
# Revert the commit
git revert <commit-hash>
# Push the changes to the remote repository
git push origin main
```

This set of questions and answers provides a solid foundation for understanding Git's core functionalities and common practices.

### 6. What is the difference between `git merge` and `git rebase`?

**Answer:** Both `git merge` and `git rebase` are used to integrate changes from one branch into another, but they do it in different ways. `git merge` combines the histories of the merged branches into one, creating a new commit for the merge if necessary. `git rebase` rewrites the commit history by moving the branch's commits to the tip of the branch being rebased onto, which can create a cleaner project history without merge commits.

**Example:**

- Using `git merge` to combine the feature branch into the main branch:
    
    ```bash
    git checkout main
    git merge feature-branch
    ```
    
- Using `git rebase` to rebase the feature branch onto the main branch:
    
    ```bash
    git checkout feature-branch
    git rebase main
    # Then you can merge feature-branch into main without a merge commit
    git checkout main
    git merge feature-branch
    ```
    

### 7. Explain what `git stash` is and provide a use case.

**Answer:** `git stash` temporarily shelves (or stashes) changes you've made to your working directory so you can work on a different task. Your working directory is then reverted to the last commit state. The stashed changes can be reapplied over the same or a different branch later.

**Example:** Imagine you're working on a new feature when you need to switch branches to fix an urgent bug. You haven't completed the feature work enough to make a commit, so you stash your changes, switch branches to fix the bug, then return to your feature branch and reapply the stash.

```bash
# Stash changes in your working directory
git stash
# Do work on another branch
git checkout main
# After finishing your work in the main, switch back
git checkout feature-branch
# Reapply the stashed changes
git stash pop
```

### 8. How do you find a bug in your project's history using Git?

**Answer:** Git provides the `git bisect` command, which uses a binary search algorithm to find which commit in your project's history introduced a bug. You start by marking a known bad commit and a known good commit. Git will then checkout a commit between those two endpoints, and you test the current project state. You mark this commit as good or bad, and Git will again checkout a commit halfway between the known good and bad commits. This process repeats until Git identifies the commit that introduced the bug.

**Example:**

```bash
# Start bisecting
git bisect start
# Mark the current commit as bad
git bisect bad
# Mark a commit where everything was fine as good
git bisect good <commit-hash>
# Git will now checkout a commit for you to test. After testing, mark it as good or bad:
git bisect good # or git bisect bad
# Repeat until Git identifies the culprit. To finish and return to the original branch:
git bisect reset
```

### 9. What is the purpose of `git cherry-pick`?

**Answer:** `git cherry-pick` is a command that allows you to select a specific commit from one branch and apply it onto another branch. This is useful for applying a few commits from a development branch to a production branch without merging all changes from development.

**Example:**

```bash
# Switch to the branch you want to apply the commit to
git checkout main
# Cherry-pick the commit
git cherry-pick <commit-hash>
```

### 10. Describe how you would clean up unused branches in your local and remote repositories.

**Answer:** To clean up unused branches, you can delete them both locally and remotely. Locally, you use `git branch -d` for branches that have been merged or `git branch -D` to force delete unmerged branches. Remotely, you use `git push <remote> --delete <branch-name>`.

**Example:**

- Delete a local branch:
    
    ```bash
    git branch -d feature-unused
    ```
    
- Force delete an unmerged local branch:
    
    ```bash
    git branch -D feature-unfinished
    ```
    
- Delete a remote branch:
    
    ```bash
    git push origin --delete feature-unused
    ```
    

These questions delve into the more nuanced aspects of Git, showcasing its flexibility and power in handling various version control scenarios.