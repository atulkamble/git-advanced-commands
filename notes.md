Here are focused study notes based on the questions that were missed.

# Git Advanced Study Notes

## 1. Git Merge

### Purpose

`git merge` combines changes from one branch into another branch.

### Example

```bash
git switch main
git merge feature
```

This merges the `feature` branch into `main`.

### Important Point

Merge normally preserves the original branch history.

### Common Merge Types

#### Fast-Forward Merge

A fast-forward merge happens when the current branch has no new commits after the feature branch was created.

```bash
git merge feature
```

Git simply moves the branch pointer forward.

#### No Fast-Forward Merge

```bash
git merge --no-ff feature
```

This command always creates a merge commit, even when a fast-forward merge is possible.

### Remember

```text
Merge = Combine branches while preserving history
```

---

## 2. Git Rebase

### Purpose

`git rebase` moves or reapplies commits onto another base commit.

### Example

```bash
git switch feature
git rebase main
```

This places the feature branch commits on top of the latest `main` branch.

### Advantage

It creates a clean and linear commit history.

### Risk

Rebase rewrites commit history and generates new commit hashes.

### Important Rule

Avoid rebasing commits that have already been shared with other developers unless the team agrees.

### Remember

```text
Rebase = Rewrite history for a clean linear timeline
```

---

## 3. Merge vs Rebase

| Feature                    | Merge      | Rebase        |
| -------------------------- | ---------- | ------------- |
| Preserves original history | Yes        | No            |
| Rewrites commit history    | No         | Yes           |
| Creates merge commit       | Sometimes  | No            |
| Best for shared branches   | Yes        | Use carefully |
| Creates linear history     | Not always | Yes           |

### Quick Memory Tip

```text
Merge preserves history.
Rebase rewrites history.
```

---

## 4. Git Cherry-Pick

### Purpose

`git cherry-pick` applies one specific commit from another branch to the current branch.

### Example

```bash
git cherry-pick a1b2c3d
```

This copies the changes from commit `a1b2c3d` onto the current branch.

### Use Case

A bug fix exists on another branch, but you do not want to merge the complete branch.

### Remember

```text
Cherry-pick = Copy one selected commit
```

---

## 5. Git Revert

### Purpose

`git revert` safely undoes a commit by creating a new commit that reverses the previous changes.

### Example

```bash
git revert a1b2c3d
```

### Best Use Case

Use `git revert` when the commit has already been pushed to a shared remote repository.

### Why It Is Safe

It does not delete or rewrite existing history.

### Remember

```text
Revert = Safely undo a shared or pushed commit
```

---

## 6. Git Reset

### Purpose

`git reset` moves the HEAD pointer to another commit.

There are three important reset modes.

### Soft Reset

```bash
git reset --soft HEAD~1
```

Effect:

* Removes the commit
* Keeps changes staged
* Does not remove file changes

### Mixed Reset

```bash
git reset --mixed HEAD~1
```

or:

```bash
git reset HEAD~1
```

Effect:

* Removes the commit
* Unstages changes
* Keeps changes in the working directory

### Hard Reset

```bash
git reset --hard HEAD~1
```

Effect:

* Removes the commit
* Clears the staging area
* Deletes working-directory changes

### Comparison

| Reset Type | Commit Removed | Changes Staged | Changes Kept |
| ---------- | -------------: | -------------: | -----------: |
| `--soft`   |            Yes |            Yes |          Yes |
| `--mixed`  |            Yes |             No |          Yes |
| `--hard`   |            Yes |             No |           No |

### Warning

`git reset --hard` can permanently remove uncommitted changes.

### Remember

```text
Soft = Keep staged
Mixed = Keep unstaged
Hard = Delete changes
```

---

## 7. Git Stash

### Purpose

`git stash` temporarily saves unfinished work without creating a normal commit.

### Save Changes

```bash
git stash
```

### Save with a Message

```bash
git stash push -m "Incomplete login feature"
```

### View Stashes

```bash
git stash list
```

### Restore Latest Stash

```bash
git stash apply
```

This restores the changes but keeps the stash entry.

### Restore and Remove Stash

```bash
git stash pop
```

### Delete a Stash

```bash
git stash drop stash@{0}
```

### Important Note

By default, untracked files are not included.

To include untracked files:

```bash
git stash -u
```

### Remember

```text
Stash = Temporarily save unfinished work
```

---

## 8. Git Reflog

### Purpose

`git reflog` records local movements of HEAD and other references.

### Command

```bash
git reflog
```

### Use Cases

* Recover a deleted branch
* Recover a commit after reset
* Recover commits after a failed rebase
* Find an earlier HEAD position

### Recovery Example

```bash
git reflog
git reset --hard HEAD@{2}
```

### Remember

```text
Reflog = Recovery history of HEAD movements
```

---

## 9. Merge Conflicts

### Cause

A merge conflict usually occurs when two branches modify the same lines differently.

### Example Scenario

Branch A changes:

```text
Port: 8080
```

Branch B changes:

```text
Port: 5000
```

Git cannot automatically decide which value to keep.

### Conflict Markers

```text
<<<<<<< HEAD
Current branch changes
=======
Incoming branch changes
>>>>>>> feature
```

### Resolution Steps

```bash
git status
```

Open the conflicting file and keep the required changes.

Then run:

```bash
git add filename
git commit
```

During rebase:

```bash
git add filename
git rebase --continue
```

To cancel the merge:

```bash
git merge --abort
```

To cancel the rebase:

```bash
git rebase --abort
```

### Remember

```text
Conflict = Same section changed differently
```

---

## 10. Git Add

### Stage All Changes in the Current Directory

```bash
git add .
```

This stages:

* New files
* Modified files
* Deleted files

### Stage All Repository Changes

```bash
git add -A
```

### Stage One File

```bash
git add app.py
```

### Why `git add *` Is Different

```bash
git add *
```

The shell expands `*`, and hidden files may not be included.

### Recommended Command

```bash
git add .
```

or:

```bash
git add -A
```

### Remember

```text
git add . = Stage changes under the current directory
```

---

## 11. Git Log

### Full Commit History

```bash
git log
```

### Compact Commit History

```bash
git log --oneline
```

Example:

```text
a1b2c3d Fix login issue
e4f5g6h Add user registration
```

### Graph View

```bash
git log --oneline --graph --all --decorate
```

### Last Five Commits

```bash
git log -5 --oneline
```

### Remember

```text
git log --oneline = One commit per line
```

---

## 12. Git HEAD

### Meaning

HEAD represents the currently checked-out branch or commit.

Normally:

```text
HEAD → Current branch → Latest commit
```

### Example

```bash
git branch
```

Output:

```text
* main
  feature
```

HEAD currently points to `main`.

### Detached HEAD

A detached HEAD occurs when you check out a specific commit directly.

```bash
git checkout a1b2c3d
```

In this state, HEAD points directly to the commit instead of a branch.

### Remember

```text
HEAD = Current branch or current commit
```

---

## 13. Git Fetch

### Purpose

`git fetch` downloads updates from a remote repository without merging them into the current branch.

### Command

```bash
git fetch origin
```

### View Remote Changes

```bash
git log main..origin/main
```

### Merge Later

```bash
git merge origin/main
```

### Remember

```text
Fetch = Download only
```

---

## 14. Git Pull

### Purpose

`git pull` downloads and integrates remote changes.

It is approximately equivalent to:

```bash
git fetch
git merge
```

### Command

```bash
git pull origin main
```

### Fetch vs Pull

| Command     | Downloads Changes | Merges Automatically |
| ----------- | ----------------: | -------------------: |
| `git fetch` |               Yes |                   No |
| `git pull`  |               Yes |                  Yes |

### Remember

```text
Fetch = Download only
Pull = Download and integrate
```

---

## 15. Git Tag

### Purpose

Tags mark important commits, commonly software releases.

### Lightweight Tag

```bash
git tag v1.0.0
```

### Annotated Tag

```bash
git tag -a v1.0.0 -m "Version 1.0.0 release"
```

### List Tags

```bash
git tag
```

### Push One Tag

```bash
git push origin v1.0.0
```

### Push All Tags

```bash
git push origin --tags
```

### Remember

```text
Tag = Release marker
```

---

## 16. Interactive Rebase

### Purpose

Interactive rebase allows you to modify recent commit history.

### Command

```bash
git rebase -i HEAD~3
```

### Common Actions

| Action   | Meaning                      |
| -------- | ---------------------------- |
| `pick`   | Keep the commit              |
| `reword` | Change commit message        |
| `edit`   | Modify the commit            |
| `squash` | Combine with previous commit |
| `fixup`  | Combine and discard message  |
| `drop`   | Remove the commit            |

### Example

```text
pick a1b2c3 Add login page
squash d4e5f6 Fix login typo
pick g7h8i9 Add logout
```

The first two commits will be combined.

### Important Rule

Do not rewrite public shared history unnecessarily.

### Remember

```text
Interactive rebase = Squash, reorder, edit or remove commits
```

---

## 17. Git Blame

### Purpose

`git blame` shows who last modified each line of a file.

### Command

```bash
git blame app.py
```

### Output Includes

* Commit hash
* Author
* Date
* Line number
* Source line

### Specific Line Range

```bash
git blame -L 10,20 app.py
```

### Use Case

Find the commit and developer associated with a line that introduced an issue.

### Remember

```text
Blame = Who changed each line?
```

---

## 18. Git Bisect

### Purpose

`git bisect` finds the commit that introduced a bug using binary search.

### Start Bisect

```bash
git bisect start
```

### Mark Current Commit as Bad

```bash
git bisect bad
```

### Mark a Known Working Commit as Good

```bash
git bisect good a1b2c3d
```

Git checks out a middle commit.

Test the application and mark it:

```bash
git bisect good
```

or:

```bash
git bisect bad
```

Continue until Git identifies the first bad commit.

### Finish

```bash
git bisect reset
```

### Remember

```text
Bisect = Which commit introduced the bug?
```

---

## 19. Git Blame vs Git Bisect

| Command      | Purpose                             |
| ------------ | ----------------------------------- |
| `git blame`  | Finds who changed each line         |
| `git bisect` | Finds which commit introduced a bug |

### Quick Memory Tip

```text
Blame = Who?
Bisect = Which commit?
```

---

## 20. Safe Force Push

### Unsafe Command

```bash
git push --force
```

This may overwrite changes pushed by another developer.

### Safer Command

```bash
git push --force-with-lease
```

This checks whether the remote branch still matches the expected state before overwriting it.

### Use Case

After rebasing your own remote feature branch:

```bash
git rebase main
git push --force-with-lease
```

### Remember

```text
Use --force-with-lease instead of --force
```

---

## 21. Trunk-Based Development

### Meaning

Developers frequently merge small changes into one main branch, usually called:

```text
main
```

or:

```text
trunk
```

### Characteristics

* Short-lived feature branches
* Frequent integration
* Small commits
* Automated testing
* Continuous integration
* Frequent deployment

### Best Suited For

* CI/CD
* DevOps teams
* Fast release cycles
* Automated testing environments

### Remember

```text
Trunk-Based Development = Frequent integration into main
```

---

## 22. Git Flow

### Main Branches

```text
main
develop
feature/*
release/*
hotfix/*
```

### Advantages

* Clear release structure
* Suitable for versioned releases
* Useful for larger release cycles

### Limitations

* More complex
* Uses multiple long-lived branches
* Slower than trunk-based development for frequent deployment

### Git Flow vs Trunk-Based Development

| Feature            | Git Flow     | Trunk-Based |
| ------------------ | ------------ | ----------- |
| Main branches      | Multiple     | Usually one |
| Feature branches   | Longer-lived | Short-lived |
| Release management | Structured   | Continuous  |
| CI/CD speed        | Moderate     | High        |
| Complexity         | Higher       | Lower       |

---

# Essential Commands Revision Table

| Task                                    | Command                         |
| --------------------------------------- | ------------------------------- |
| Combine branches                        | `git merge branch-name`         |
| Force merge commit                      | `git merge --no-ff branch-name` |
| Rewrite branch history                  | `git rebase branch-name`        |
| Copy one commit                         | `git cherry-pick commit-hash`   |
| Safely undo pushed commit               | `git revert commit-hash`        |
| Remove commit and keep staged changes   | `git reset --soft HEAD~1`       |
| Remove commit and keep unstaged changes | `git reset --mixed HEAD~1`      |
| Remove commit and delete changes        | `git reset --hard HEAD~1`       |
| Temporarily save work                   | `git stash`                     |
| Restore stashed work                    | `git stash pop`                 |
| View HEAD movements                     | `git reflog`                    |
| Stage current directory changes         | `git add .`                     |
| Compact commit history                  | `git log --oneline`             |
| Download remote changes only            | `git fetch`                     |
| Download and integrate changes          | `git pull`                      |
| Create release marker                   | `git tag v1.0.0`                |
| Modify recent commit history            | `git rebase -i HEAD~3`          |
| Find who changed a line                 | `git blame filename`            |
| Find bug-introducing commit             | `git bisect`                    |
| Safer force push                        | `git push --force-with-lease`   |

---

# Quick Revision Points

1. Merge combines branches and preserves history.
2. Rebase rewrites commits onto a new base.
3. Cherry-pick applies one selected commit.
4. Revert safely undoes a pushed commit.
5. Reset changes local history.
6. Hard reset deletes working changes.
7. Stash temporarily saves unfinished work.
8. Reflog helps recover lost commits.
9. Merge conflicts usually happen on overlapping lines.
10. `git add .` stages current-directory changes.
11. `git log --oneline` shows compact history.
12. HEAD represents the current branch or commit.
13. Fetch downloads without merging.
14. Pull downloads and integrates.
15. Tags identify releases.
16. Interactive rebase can squash commits.
17. Blame finds who changed a line.
18. Bisect finds the commit that introduced a bug.
19. `--force-with-lease` is safer than `--force`.
20. Trunk-based development supports frequent CI/CD integration.

---

# Final Memory Formula

```text
Merge = Combine
Rebase = Rewrite
Cherry-pick = Copy
Revert = Reverse safely
Reset = Move HEAD
Stash = Save temporarily
Reflog = Recover
Blame = Who
Bisect = Which commit
Fetch = Download
Pull = Download + integrate
Tag = Release
```

I can also convert these notes into a one-page revision sheet or practical Git lab guide.
