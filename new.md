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
