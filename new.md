## 🔁 **git merge**

### ✅ Points to Remember

* Combines two branches
* Creates a **merge commit**
* Preserves full branch history
* Safe and commonly used in teams

### 🎯 Significance

* Best when you want **clear history of feature branches**
* Ideal for **team collaboration**

### 🧪 Example

```bash
git checkout main
git merge feature-login
```

📌 Result: `main` now includes `feature-login` changes with a merge commit

---

## 🔄 **git rebase**

### ✅ Points to Remember

* Moves commits on top of another branch
* **Rewrites history**
* No extra merge commit
* Avoid on shared/public branches

### 🎯 Significance

* Keeps **clean & linear commit history**
* Useful before raising PRs

### 🧪 Example

```bash
git checkout feature-login
git rebase main
```

📌 Result: feature commits appear as if created after latest `main`

---

## 🍒 **git cherry-pick**

### ✅ Points to Remember

* Picks **specific commit(s)** from another branch
* Does NOT merge entire branch
* Commit hash required

### 🎯 Significance

* Apply **hotfix or selective change** quickly
* Very useful in production fixes

### 🧪 Example

```bash
git cherry-pick a1b2c3d
```

📌 Result: Only that commit is applied to current branch

---

## ⚠️ **git conflict resolution**

### ✅ Points to Remember

* Happens when same file lines are changed
* Git pauses operation (merge/rebase/cherry-pick)
* Manual fix required

### 🎯 Significance

* Essential skill for **real-world team projects**
* Shows collaboration maturity

### 🧪 Example

```text
<<<<<<< HEAD
old code
=======
new code
>>>>>>> feature
```

```bash
# fix manually
git add file.txt
git commit
```

---

## ⏪ **git reset**

### ✅ Points to Remember

* Moves HEAD to previous commit
* Can **remove commits**
* Types: `--soft`, `--mixed`, `--hard`
* Dangerous if misused

### 🎯 Significance

* Used to **undo commits locally**
* Clean mistakes before push

### 🧪 Example

```bash
git reset --hard HEAD~1
```

📌 Result: Last commit + changes deleted

---

## 🔙 **git revert**

### ✅ Points to Remember

* Creates a **new commit that undoes changes**
* Safe for shared branches
* Does not rewrite history

### 🎯 Significance

* Best for **undoing changes in production**
* Audit-friendly

### 🧪 Example

```bash
git revert a1b2c3d
```

📌 Result: New commit that reverses that commit

---

## 🧹 **git restore**

### ✅ Points to Remember

* Restores file from staging or commit
* Does NOT affect commit history
* Newer alternative to checkout

### 🎯 Significance

* Safely discard **local file changes**
* Great for beginners

### 🧪 Example

```bash
git restore file.txt
```

📌 Result: File reset to last committed state

---

## 🧠 **One-Line Memory Hook (Exam/Interview)**

* **merge** → combine branches
* **rebase** → rewrite history, clean commits
* **cherry-pick** → pick one commit
* **conflict** → manual resolution
* **reset** → move HEAD (dangerous)
* **revert** → safe undo via new commit
* **restore** → discard local file changes

---

If you already know Git basics (init, clone, add, commit, push, pull, branch, merge), the next step is to practice Git like it is used in real DevOps teams.

---

# Git Advanced Commands and Practice Guide

## Module 1: Repository Inspection

### Current Status

```bash
git status
```

---

### Commit History

```bash
git log
```

Compact

```bash
git log --oneline
```

Graph View

```bash
git log --graph --oneline --all
```

Author wise

```bash
git log --author="Atul"
```

Last 5 commits

```bash
git log -5
```

---

### Difference

Working directory

```bash
git diff
```

Staged

```bash
git diff --cached
```

Between commits

```bash
git diff commit1 commit2
```

---

## Module 2: Staging Area

Stage one file

```bash
git add file.txt
```

Stage all

```bash
git add .
```

Interactive staging

```bash
git add -p
```

Unstage

```bash
git restore --staged file.txt
```

Discard changes

```bash
git restore file.txt
```

---

# Module 3: Commit Management

Amend last commit

```bash
git commit --amend
```

Without changing message

```bash
git commit --amend --no-edit
```

Empty commit

```bash
git commit --allow-empty -m "Pipeline Trigger"
```

---

# Module 4: Branch Management

Create

```bash
git branch feature/login
```

Switch

```bash
git switch feature/login
```

Create + Switch

```bash
git switch -c feature/login
```

Delete

```bash
git branch -d feature/login
```

Force delete

```bash
git branch -D feature/login
```

Rename

```bash
git branch -m old-name new-name
```

List

```bash
git branch
```

Remote

```bash
git branch -r
```

All

```bash
git branch -a
```

---

# Module 5: Merge

Fast Forward Merge

```bash
git merge feature/login
```

No Fast Forward

```bash
git merge --no-ff feature/login
```

Abort merge

```bash
git merge --abort
```

---

# Module 6: Rebase

Rebase current branch

```bash
git rebase main
```

Interactive Rebase

```bash
git rebase -i HEAD~5
```

Continue

```bash
git rebase --continue
```

Abort

```bash
git rebase --abort
```

Skip commit

```bash
git rebase --skip
```

---

# Module 7: Cherry Pick

Copy one commit

```bash
git cherry-pick commitID
```

Multiple commits

```bash
git cherry-pick commit1 commit2
```

Range

```bash
git cherry-pick commit1^..commit5
```

---

# Module 8: Reset

Soft

```bash
git reset --soft HEAD~1
```

Mixed

```bash
git reset HEAD~1
```

Hard

```bash
git reset --hard HEAD~1
```

---

# Module 9: Revert

Undo safely

```bash
git revert commitID
```

---

# Module 10: Stash

Save work

```bash
git stash
```

Named stash

```bash
git stash push -m "Terraform Work"
```

List

```bash
git stash list
```

Apply

```bash
git stash apply
```

Pop

```bash
git stash pop
```

Delete

```bash
git stash drop
```

Clear

```bash
git stash clear
```

---

# Module 11: Tags

Create

```bash
git tag v1.0
```

Annotated

```bash
git tag -a v1.0 -m "Release"
```

Push

```bash
git push origin v1.0
```

Push all

```bash
git push origin --tags
```

---

# Module 12: Remote

Show remotes

```bash
git remote -v
```

Add

```bash
git remote add origin URL
```

Change URL

```bash
git remote set-url origin URL
```

Fetch

```bash
git fetch
```

Pull

```bash
git pull
```

Push

```bash
git push
```

---

# Module 13: Restore Older Version

Checkout file

```bash
git checkout commitID -- file.txt
```

Restore

```bash
git restore file.txt
```

---

# Module 14: Blame

```bash
git blame app.py
```

---

# Module 15: Bisect

Start

```bash
git bisect start
```

Bad

```bash
git bisect bad
```

Good

```bash
git bisect good commitID
```

Reset

```bash
git bisect reset
```

---

# Module 16: Clean

Preview

```bash
git clean -n
```

Delete

```bash
git clean -fd
```

---

# Module 17: Reflog (Most Important)

Show every movement

```bash
git reflog
```

Recover lost commit

```bash
git checkout HEAD@{2}
```

---

# Module 18: Squash Commits

```bash
git rebase -i HEAD~5
```

Change

```
pick
pick
pick
```

to

```
pick
squash
squash
```

---

# Module 19: Aliases

```bash
git config --global alias.st status
```

```bash
git st
```

Useful aliases

```bash
git config --global alias.lg "log --graph --oneline --all"
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm commit
```

---

# Module 20: Hooks

Example

```
.git/hooks/pre-commit
```

```bash
#!/bin/bash

terraform fmt -check
```

---

# Git Practice Projects

## Project 1 – Git Basics

```
student-management

main
```

Practice

* init
* add
* commit
* push
* clone

---

## Project 2 – Branching

```
main

feature-login

feature-profile

feature-payment
```

Tasks

* create branches
* switch
* merge
* delete

---

## Project 3 – Merge Conflict

```
main

feature-login
```

Edit same line

Merge

Resolve conflict

Commit

---

## Project 4 – Rebase

```
main

feature-login
```

Create

```
5 commits
```

Meanwhile

```
main gets 3 commits
```

Practice

```bash
git rebase main
```

Resolve conflicts

Continue

---

## Project 5 – Cherry Pick

```
feature-payment
```

Copy one commit to

```
release
```

---

## Project 6 – Reset & Revert

Create

```
5 commits
```

Practice

```bash
git reset --soft
git reset
git reset --hard
git revert
```

Observe differences.

---

## Project 7 – Stash

Modify

```
10 files
```

Without committing

```bash
git stash
```

Switch branch

Come back

```bash
git stash pop
```

---

## Project 8 – Tags & Releases

Create

```
v1.0
v1.1
v2.0
```

Push tags.

---

## Project 9 – Bisect

Create

```
20 commits
```

Introduce a bug around commit 11.

Use

```bash
git bisect
```

to find it.

---

## Project 10 – Complete DevOps Workflow

Repository:

```
cloud-devops-platform
```

Structure

```
cloud-devops-platform/
│
├── app/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
│
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   └── outputs.tf
│
├── kubernetes/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── ingress.yaml
│
├── ansible/
│   ├── inventory
│   └── playbook.yml
│
├── jenkins/
│   └── Jenkinsfile
│
├── monitoring/
│   ├── prometheus.yml
│   └── grafana-dashboard.json
│
└── README.md
```

Practice workflow:

1. Create `main`.
2. Create feature branches for each component (`feature/docker`, `feature/terraform`, `feature/kubernetes`, etc.).
3. Make multiple commits on each feature branch.
4. Open pull requests (or simulate them locally).
5. Merge some branches with `--no-ff`.
6. Rebase another feature branch onto the updated `main`.
7. Create and resolve merge conflicts intentionally.
8. Cherry-pick a hotfix into a `release` branch.
9. Tag stable versions (`v1.0`, `v1.1`, `v2.0`).
10. Recover a deleted commit using `git reflog`.
11. Use `git bisect` to identify an intentionally introduced bug.
12. Simulate an emergency rollback with `git revert`.

---

## Commands Every DevOps Engineer Should Master

| Category       | Commands                                                                |
| -------------- | ----------------------------------------------------------------------- |
| History        | `git log --graph --oneline --all`, `git reflog`, `git blame`            |
| Branching      | `git switch`, `git branch`, `git merge`, `git rebase`                   |
| Recovery       | `git reset`, `git restore`, `git revert`, `git reflog`                  |
| Collaboration  | `git fetch`, `git pull`, `git push`, `git remote -v`, `git cherry-pick` |
| Temporary work | `git stash`, `git stash pop`, `git stash list`                          |
| Releases       | `git tag`, `git push --tags`                                            |
| Debugging      | `git bisect`, `git diff`, `git log -p`                                  |

For interviews and real-world DevOps work (Azure DevOps, GitHub, GitLab, Jenkins), the highest-priority topics are:

* Git branching strategies (Git Flow, GitHub Flow, Trunk-Based Development)
* Merge vs. Rebase (when and why to use each)
* Interactive rebase (squash, reword, drop)
* Merge conflict resolution
* Cherry-pick for hotfixes
* Reset vs. Restore vs. Revert
* Reflog for recovering lost work
* Stash for context switching
* Tags and release management
* Pull request best practices and code review workflows

Below are the most commonly asked **Git Advanced Interview Questions** for **DevOps, Cloud, SRE, Platform Engineer, Azure DevOps, AWS DevOps, GitHub, GitLab, and Jenkins** interviews.

---

# Git Advanced Interview Questions (2026)

## Git Basics

### 1. What is Git?

**Answer**

Git is a **distributed version control system (DVCS)** used to track source code changes, collaborate with multiple developers, maintain version history, and manage software releases.

---

### 2. Why is Git distributed?

Because every developer has a complete copy of the repository, including its entire commit history.

Benefits:

* Offline commits
* Faster operations
* Backup of repository
* No dependency on central server

---

### 3. Difference between Git and GitHub?

| Git                    | GitHub                        |
| ---------------------- | ----------------------------- |
| Version Control System | Git hosting platform          |
| Installed locally      | Cloud platform                |
| Tracks source code     | Stores Git repositories       |
| CLI based              | Web Interface + Collaboration |
| Works offline          | Internet required             |

---

### 4. What is a Repository?

A repository is a storage location that contains:

* Source code
* Commit history
* Branches
* Tags
* Configuration files

---

### 5. Difference between Local and Remote Repository?

| Local                       | Remote                               |
| --------------------------- | ------------------------------------ |
| Exists on developer machine | Exists on GitHub/GitLab/Azure DevOps |
| Offline                     | Online                               |
| Faster                      | Shared with team                     |

---

# Branching

---

## 6. Why do we create branches?

To isolate development.

Examples

* feature/login
* feature/payment
* bugfix/api
* release/v1.2
* hotfix/security

---

## 7. What happens internally when a branch is created?

Git creates a new pointer to the current commit.

It does **not** duplicate files.

---

## 8. Difference between Branch and Tag?

| Branch               | Tag                    |
| -------------------- | ---------------------- |
| Movable pointer      | Fixed pointer          |
| Used for development | Used for releases      |
| Can receive commits  | Cannot receive commits |

---

## 9. Difference between Checkout and Switch?

Older

```bash
git checkout feature
```

Modern

```bash
git switch feature
```

`git switch` is safer because it only switches branches.

---

# Merge

---

## 10. What is Merge?

Combines two branches together.

Example

```text
main

A---B---C

feature

     D---E
```

After merge

```text
A---B---C-------M
      \        /
       D------E
```

---

## 11. Types of Merge?

* Fast Forward
* Three-way Merge
* No Fast Forward Merge
* Squash Merge
* Octopus Merge (multiple branches)

---

## 12. What is Fast Forward Merge?

No additional merge commit.

History remains linear.

---

## 13. What is Three-way Merge?

Creates a merge commit because both branches have diverged.

---

## 14. What is `--no-ff` merge?

Always creates a merge commit.

Useful for maintaining feature history.

---

# Merge Conflicts

---

## 15. Why do merge conflicts occur?

When the same lines are modified in multiple branches.

---

## 16. How do you resolve conflicts?

1. Open conflicting files.
2. Edit the desired content.
3. Remove conflict markers.
4. Stage the file.
5. Commit or continue the merge/rebase.

---

# Rebase

---

## 17. What is Rebase?

Moves commits from one branch onto another to create a linear history.

---

## 18. Merge vs Rebase?

| Merge                     | Rebase                            |
| ------------------------- | --------------------------------- |
| Preserves history         | Rewrites history                  |
| Creates merge commit      | No merge commit                   |
| Easier                    | Cleaner history                   |
| Safer for shared branches | Better for local feature branches |

---

## 19. When should you use Rebase?

* Before creating a Pull Request
* Updating a feature branch from `main`
* Cleaning commit history

Avoid rebasing shared/public branches.

---

## 20. What is Interactive Rebase?

Allows you to:

* Squash commits
* Edit commit messages
* Reorder commits
* Drop commits
* Split commits

---

# Cherry Pick

---

## 21. What is Cherry Pick?

Copies a specific commit from one branch to another.

Example:

```bash
git cherry-pick <commit-id>
```

---

## 22. When do you use Cherry Pick?

* Hotfixes
* Production fixes
* Copying a single feature
* Avoiding unnecessary merges

---

# Reset / Restore / Revert

---

## 23. Difference between Reset and Revert?

| Reset                        | Revert                  |
| ---------------------------- | ----------------------- |
| Moves HEAD                   | Creates new commit      |
| Changes history              | Preserves history       |
| Dangerous on shared branches | Safe on shared branches |

---

## 24. Types of Reset?

### Soft

Keeps staging area.

### Mixed (default)

Removes staging.

### Hard

Deletes all changes.

---

## 25. Difference between Restore and Checkout?

Restore

```bash
git restore file.txt
```

Checkout

```bash
git checkout file.txt
```

`restore` is newer and more focused on restoring files.

---

# Stash

---

## 26. What is Git Stash?

Temporarily saves uncommitted changes without creating a commit.

---

## 27. Difference between Stash Apply and Pop?

| Apply       | Pop           |
| ----------- | ------------- |
| Keeps stash | Removes stash |

---

# Tags

---

## 28. Why use Tags?

Release management.

Example:

* v1.0
* v2.0
* v3.1

---

## 29. Lightweight vs Annotated Tag?

| Lightweight       | Annotated             |
| ----------------- | --------------------- |
| Simple pointer    | Includes metadata     |
| No author/message | Author, date, message |

---

# Remote

---

## 30. Difference between Fetch and Pull?

| Fetch             | Pull                       |
| ----------------- | -------------------------- |
| Downloads changes | Downloads + merges/rebases |
| Safe              | Updates local branch       |

---

## 31. Why use Fetch before Pull?

To inspect incoming changes before integrating them.

---

# Reflog

---

## 32. What is Reflog?

Tracks where `HEAD` has pointed.

Useful for recovering:

* Lost commits
* Deleted branches
* Accidental resets

---

## 33. Can Git recover deleted commits?

Yes, using:

```bash
git reflog
```

---

# Bisect

---

## 34. What is Git Bisect?

A binary search through commit history to identify the commit that introduced a bug.

---

## 35. Why is Git Bisect useful?

Instead of checking 1,000 commits manually, it narrows the search in approximately **log₂(n)** steps.

---

# Hooks

---

## 36. What are Git Hooks?

Scripts that run automatically before or after Git events.

Examples:

* pre-commit
* commit-msg
* pre-push
* post-merge

---

## 37. Example of pre-commit hook?

* Run tests
* Run Terraform format checks
* Run linting
* Validate commit messages

---

# Git Internals

---

## 38. What is HEAD?

HEAD points to the current branch or commit you are working on.

---

## 39. What is Detached HEAD?

HEAD points directly to a commit instead of a branch.

Changes can be lost unless saved to a branch.

---

## 40. What are Git Objects?

Git stores data as:

* Blob (file contents)
* Tree (directory structure)
* Commit (snapshot + metadata)
* Tag (release reference)

---

# Collaboration

---

## 41. Explain Pull Request (PR).

A Pull Request proposes changes from one branch into another for review before merging.

Typical workflow:

1. Create feature branch.
2. Commit changes.
3. Push branch.
4. Open PR.
5. Review.
6. Merge.
7. Delete feature branch.

---

## 42. Difference between Fork and Clone?

| Fork                               | Clone                |
| ---------------------------------- | -------------------- |
| Server-side copy                   | Local copy           |
| Used for open-source contributions | Used for development |

---

## 43. Git Flow vs GitHub Flow vs Trunk-Based Development

| Strategy                | Best For                                           |
| ----------------------- | -------------------------------------------------- |
| Git Flow                | Enterprise releases with multiple release versions |
| GitHub Flow             | Continuous deployment and web applications         |
| Trunk-Based Development | High-frequency CI/CD and DevOps teams              |

---

# Scenario-Based Questions

### 44. You accidentally ran `git reset --hard`. How would you recover your work?

* Check `git reflog` to find the previous `HEAD`.
* Reset or create a branch from the recovered commit.

---

### 45. You committed directly to `main`. What should you do?

* If not pushed: move the commit to a feature branch using `git branch` and reset `main`.
* If pushed: use `git revert` to safely undo it and follow your team's workflow.

---

### 46. A teammate force-pushed and your local branch diverged. How would you handle it?

* Run `git fetch`.
* Compare histories (`git log --graph`).
* Coordinate with the teammate.
* Rebase or reset only after confirming the correct history.

---

### 47. A production bug must be fixed immediately, but the feature branch isn't ready. What would you do?

* Create a `hotfix` branch from the production/release branch.
* Implement and test the fix.
* Merge it into both the release branch and `main`.
* Cherry-pick or merge it into any active feature branches if needed.

---

### 48. How do you keep a feature branch up to date with `main`?

* Regularly `git fetch`.
* Rebase your local feature branch onto the latest `main` (before opening a PR if allowed by team policy), or merge `main` if your team prefers merge-based history.

---

### 49. When should you avoid using `git push --force`?

Avoid it on shared branches (`main`, `develop`, release branches) because it rewrites remote history and can disrupt teammates' work. If absolutely necessary on your own feature branch, prefer `git push --force-with-lease`.

---

### 50. What is `git push --force-with-lease` and why is it safer?

It force-pushes only if the remote branch hasn't changed since your last fetch, helping prevent overwriting someone else's work.

---

# Common Interview Commands

| Purpose         | Command                             |
| --------------- | ----------------------------------- |
| View history    | `git log --graph --oneline --all`   |
| Find changes    | `git diff`                          |
| Recover commits | `git reflog`                        |
| Temporary save  | `git stash`                         |
| Copy commit     | `git cherry-pick`                   |
| Linear history  | `git rebase`                        |
| Safe undo       | `git revert`                        |
| Local undo      | `git reset`                         |
| Debug bug       | `git bisect`                        |
| Release version | `git tag`                           |
| Remote sync     | `git fetch`, `git pull`, `git push` |
| File ownership  | `git blame`                         |

## Interview Tips

Interviewers often focus less on memorizing commands and more on your decision-making. Be prepared to explain:

* **Why** you would choose `merge` vs. `rebase`.
* **When** to use `revert` instead of `reset`.
* How you recover from mistakes using `reflog`.
* How your team handles feature branches, pull requests, and releases.
* How Git integrates into CI/CD pipelines with tools like GitHub Actions, Azure DevOps Pipelines, GitLab CI, or Jenkins.

Being able to reason through these scenarios is often more valuable than simply recalling command syntax.
