# Hi, I'm GP 👋

## About Me
- 🌱 I'm currently learning Git and version control
- 💻 I'm interested in your interests e.g. cloud computing, web dev
- 📫 How to reach me: your email or social link

## Projects
- [git-learning-log](https://github.com/Git-Guru-commit/git-learning-log) - My first Git project tracking a learning log

# Command learned today
## Git Commands Reference

### Basic Setup & Initialization

```bash
git init                                    # Initialize a new Git repository
git remote add origin <url>                 # Connect to remote repository
git branch -M main                          # Rename branch to main
```

---

### Staging & Committing

```bash
git add <file>                              # Stage file for commit
git commit -m "<message>"                   # Create a commit with message
```

---

### Viewing History

```bash
git log                                     # View full commit history
git log --oneline                           # View commits in compact format
git log --oneline --graph                   # View commit tree with branches
git reflog                                  # View all HEAD movements (including resets)
```

---

### Branches

```bash
git branch -M <new-name>                    # Rename current branch
git branch <branch-name>                    # Create new branch
git branch <branch-name> <commit-hash>      # Create branch from specific commit
git merge <branch-name>                     # Merge branch into current branch
```

---

### Status & Inspection

```bash
git status                                  # Check status of working directory
```

---

### Undoing Changes

#### Safe Methods (Preserve History)

| Command | Effect |
|---------|--------|
| `git revert HEAD` | Creates new commit that reverses the last commit. Safe for public work. |
| `git reset --soft HEAD~1` | Moves HEAD back 1 commit. Changes stay staged and ready to commit. |

#### Destructive Methods (Use With Caution)

| Command | Effect |
|---------|--------|
| `git reset --hard HEAD~1` | Moves HEAD back 1 commit and discards all changes. Destructive. |
| `git checkout -- <file>` | Replaces file with version from last commit. Unsaved edits lost permanently. |

---

### Recovery (After Destructive Operations)

```bash
git reflog                                  # Find lost commits
git branch <recovery-branch> <commit-hash>  # Recover commit by creating branch
git merge <recovery-branch>                 # Merge recovered content back
```

**Example:**
```bash
git reset --hard HEAD~1              # Lost changes
git reflog                           # Find commit hash (e.g., f2c4cda)
git branch recover-section f2c4cda   # Create recovery branch
git merge recover-section            # Merge back to main
```

---

### Remote Operations

```bash
git push -u origin main                     # Push main branch to remote (sets upstream)
git push origin <branch-name>               # Push specific branch to remote
```

---

### Quick Syntax Notes

- `HEAD` = Current commit
- `HEAD~1` = One commit before current
- `--` = Separates command from filename (prevents Git from confusing filename with branch)