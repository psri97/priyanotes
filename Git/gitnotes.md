# 📘 Git Handbook (Interview + Practical Guide)

---

# 🔹 Basic Git Commands

## git init
Creates a new Git repository in your folder.  
Used when starting a new project.

## git status
Shows file status (modified, staged, untracked).  
Helps understand current working state.

## git clone (repository url)
Downloads remote repository to local system.  
Used to start working on existing code.

## git add (file name)
Moves changes to staging area.  
Prepares files for commit.

## git commit -m "message"
Saves staged changes with a message.  
Acts as a checkpoint in history.

## git push origin main
Uploads local commits to remote repo.  
Used to share changes.

## git pull origin main
Fetches + merges latest remote changes.  
Keeps local repo updated.

## git log --oneline
Shows compact commit history.  
Useful for quick tracking.

## git checkout -b (branch name)
Creates and switches to new branch.  
Used for new feature work.

## git checkout (branch name)
Switches to existing branch.  
Helps navigate between work.

## git merge
Combines one branch into another.  
Used to integrate changes.

## git rebase
Reapplies commits on another branch.  
Keeps history clean.

## git reset
Moves HEAD to previous commit.  
Used to undo commits (risky).

## git revert
Creates new commit to undo changes.  
Safe for shared repos.

## git cherry-pick
Applies a specific commit from another branch.  
Useful for selective changes.

---

# 🌿 Branching Strategy

Branching strategy defines how teams manage branches.

## Common Flow
- main → production
- develop → testing
- feature/* → new features
- hotfix/* → urgent fixes

## Why Use
- Avoid breaking production  
- Enable parallel work  
- Improve collaboration  

## Interview Line
"Branching strategy enables safe development using isolated feature branches and stable main branch."

---

# 🔀 Merging Concept

Merging combines code from different branches.

## Types
- Fast-forward → simple linear merge  
- 3-way merge → creates merge commit  

## Example
Merge feature into main after testing.

## Interview Line
"Merging integrates completed features into main branch while preserving history."

---

# ⚠️ Merge Conflict Resolution

## What is Conflict
Occurs when same file/line is modified in multiple branches.

## Identify
Markers appear:
<<<<<<< HEAD  
=======  
>>>>>>> branch  

## Steps to Fix
1. Open file  
2. Edit correct code  
3. Remove markers  
4. git add + git commit  

## Interview Line
"I manually resolve conflicts, remove markers, and commit correct version."

---

# 🔁 Rebase vs Merge

## git merge
- Keeps history  
- One-time conflict resolution  
- Safe for teams  

## git rebase
- Linear history  
- Conflicts may repeat  
- Rewrites history  

## Rule
Never rebase shared branches.

## Interview Line
"Merge is safe and preserves history, rebase creates clean history but must be used carefully."

---

# ❌ Handling Wrong Commits

## LOCAL Repo

### Keep changes
git reset --soft HEAD~1  

### Delete completely
git reset --hard HEAD~1  

---

## REMOTE Repo

### Safe way
git revert <commit-id>  
git push  

### Risky way
git reset --hard HEAD~1  
git push --force  

---

## Key Difference
reset → rewrites history  
revert → safe undo  

---

# 🎯 Scenario-Based Questions

## Wrong branch commit
git branch feature  
git reset --hard HEAD~1  

## Forgot file in commit
git add file.txt  
git commit --amend  

## Push rejected
git pull  
resolve conflicts  
git push  

## Temporary save work
git stash  
git stash pop  

## Recover deleted branch
git reflog  
git checkout -b branch <id>  

## Remove file but keep locally
git rm --cached file.txt  

## Squash commits
git rebase -i HEAD~3  

## Rebase conflict
fix → git add → git rebase --continue  

## Rollback to commit
git reset --hard <commit-id>  

---

# 📚 Git Interview Q&A

## What is Git?
Version control system to track changes and collaborate.

## Git vs GitHub
Git → tool  
GitHub → platform  

## What is staging?
Area before commit using git add.

## add vs commit
add → stage  
commit → save  

## What is branch?
Independent line of development.

## What is HEAD?
Pointer to current commit.

## What is stash?
Temporary storage of changes.

## fetch vs pull
fetch → download only  
pull → download + merge  

## What is tag?
Marks a release version.

## .gitignore
Ignores unnecessary files.


