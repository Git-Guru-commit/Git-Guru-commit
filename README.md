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
git checkout -b <branch-name>               # Create and switch to new branch (shortcut)
git merge <branch-name>                     # Merge branch into current branch
git log --oneline <branch-name>             # View commit history of specific branch
```

---

### Status & Inspection

```bash
git status                                  # Check status of working directory
git show HEAD:<file>                        # View file content from a specific commit
git cherry-pick <commit-hash>               # Apply specific commit to current branch
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

### Bisect (Find Bug-Introducing Commit)

```bash
git bisect start                            # Start bisect session
git bisect bad                              # Mark current commit as bad (has bug)
git bisect good <commit-hash>               # Mark a known good commit
git bisect good                             # Continue marking commits as good/bad
git bisect reset                            # Exit bisect session
```

**Workflow:**
```bash
git bisect start
git bisect bad                   # Current commit has the bug
git bisect good 2703ee8         # This old commit was good
# Git checks out midpoint commit — test and mark as good or bad
git bisect good                 # If this one is good
# Continue until Git identifies the bad commit
git bisect reset                # Back to original branch
```

---

### Tags (Release Markers)

```bash
git tag -a <tag-name> -m "<message>"       # Create annotated tag with message
git push origin <tag-name>                  # Push specific tag to remote
git push origin --tags                      # Push all tags to remote
```

**Example:**
```bash
git tag -a v1.0 -m "First release: Git fundamentals complete"
git push origin v1.0
```

### Remote Operations

```bash
git push -u origin main                     # Push main branch to remote (sets upstream)
git push origin <branch-name>               # Push specific branch to remote
git push origin <branch-name> --force-with-lease  # Force push safely (respects remote changes)
git fetch origin                            # Fetch updates from remote without merging
git reset --hard origin/main                # Reset local branch to remote version (destructive)
```

---

### Rebase (Rewrite Commit History)

```bash
git rebase -i HEAD~<n>                      # Interactive rebase: edit last n commits
```

**Interactive Rebase Options:**
- `pick` - Use commit
- `reword` - Change commit message
- `squash` - Combine with previous commit
- `fixup` - Combine and discard message
- `drop` - Remove commit

**Example:**
```bash
git rebase -i HEAD~4                 # Open editor for last 4 commits
# Edit, squash, reorder, or drop commits as needed
```

---

### Stash (Temporary Storage)

```bash
git stash                                   # Save changes temporarily
git stash list                              # View all stashed changes
git stash pop                               # Apply and remove latest stash
git stash apply                             # Apply stash without removing it
git stash drop                              # Delete a stash
```

**Workflow:**
```bash
git stash                  # Save work in progress
git fetch origin           # Pull latest changes
git stash pop              # Apply saved work back
```

---

### Configuration

```bash
git config --global core.editor "nano"      # Set default editor for Git (nano/vim/code)
```

---

### Quick Syntax Notes

- `HEAD` = Current commit
- `HEAD~1` = One commit before current
- `--` = Separates command from filename (prevents Git from confusing filename with branch)