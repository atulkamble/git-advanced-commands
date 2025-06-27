**structured, detailed code guide with explanations, step-by-step commands, and a simulated practice scenario**. You’ll be able to follow this on your system like a mini-lab.

---

# 📑 Git Advanced Commands — Complete Practice Guide

---

## 📦 Setup: Create a Practice Repository

```bash
# Create a practice directory and initialize Git
mkdir git-advanced-practice
cd git-advanced-practice
git init

# Create initial file
echo "Line 1" > file.txt

# Stage and commit
git add file.txt
git commit -m "Initial commit"
```

---

## 📌 1️⃣ Git Stash — Temporarily Save Uncommitted Changes

```bash
# Modify file without committing
echo "Temporary work" >> file.txt

# Save changes in a stash
git stash

# List stashes
git stash list

# Apply the most recent stash and remove it from the stack
git stash pop

# Or apply without removing
git stash apply

# Drop the stash if no longer needed
git stash drop
```

---

## 📌 2️⃣ Git Rebase — Reapply Commits on Top of Another Base

```bash
# Create a new branch and make a commit
git checkout -b feature
echo "Feature line" >> file.txt
git add file.txt
git commit -m "Feature commit"

# Switch to main branch and make another commit
git checkout main
echo "Main line" >> file.txt
git add file.txt
git commit -m "Main commit"

# Rebase feature branch on top of main
git checkout feature
git rebase main
```

🔍 **Check history**

```bash
git log --oneline --graph --all
```

---

## 📌 3️⃣ Git Cherry-Pick — Apply Specific Commit to Current Branch

```bash
# Find the commit hash you want to cherry-pick
git log --oneline

# Apply a specific commit
git cherry-pick <commit-hash>
```

---

## 📌 4️⃣ Git Reset and Reflog — Rollback Changes

```bash
# Make a test commit
echo "Test line" >> file.txt
git add file.txt
git commit -m "Test commit"

# View log
git log --oneline

# Reset to previous commit (destructive)
git reset --hard HEAD~1

# View reflog to recover lost commits
git reflog

# Checkout a lost commit
git checkout <commit-hash-from-reflog>
```

---

## 📌 5️⃣ Git Tag — Create and Manage Release Tags

```bash
# Create a lightweight tag
git tag v1.0

# Create an annotated tag
git tag -a v1.0 -m "Version 1.0 Release"

# List tags
git tag

# Push tags to remote
git push origin --tags
```

---

## 📌 6️⃣ Git Clean — Remove Untracked Files

```bash
# Create an untracked file
touch temp.log

# See what would be removed
git clean -nd

# Remove untracked files
git clean -fd
```

---

## 📌 7️⃣ Git Blame — Find Who Modified Each Line

```bash
git blame file.txt
```

---

## 📌 8️⃣ Git Diff Between Branches

```bash
# View differences between main and feature branch
git diff main..feature
```

---

## 📌 9️⃣ Git Bisect — Locate the Commit That Introduced a Bug

```bash
# Start bisect
git bisect start

# Mark current commit as bad
git bisect bad

# Mark a known good commit
git bisect good <commit-hash>

# Git will automatically checkout midpoint commits; test each one and mark as good or bad
# Continue with:
git bisect good
# or
git bisect bad

# When done, reset bisect
git bisect reset
```

---

## 📌 🔟 Git Merge — Squash Commits

```bash
# Merge all feature branch commits into one when merging to main
git checkout main
git merge --squash feature
git commit -m "Merged feature branch as one commit"
```

---

## 📌 📊 View History Graphically

```bash
git log --oneline --graph --all
```

---

## 📁 Directory Structure after Full Practice

```
git-advanced-practice/
├── file.txt
└── (Git repo initialized)
```

---

## 📑 Bonus: Save Practice as a Script

### `git-practice.sh`

```bash
#!/bin/bash

mkdir git-advanced-practice
cd git-advanced-practice
git init

echo "Line 1" > file.txt
git add file.txt
git commit -m "Initial commit"

echo "Temporary work" >> file.txt
git stash

git stash pop

git checkout -b feature
echo "Feature line" >> file.txt
git add file.txt
git commit -m "Feature commit"

git checkout main
echo "Main line" >> file.txt
git add file.txt
git commit -m "Main commit"

git checkout feature
git rebase main

git log --oneline --graph --all
```

---
