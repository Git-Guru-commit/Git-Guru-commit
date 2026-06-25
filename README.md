# Hi, I'm GP 👋

## About Me
- 🌱 I'm currently learning Git and version control
- 💻 I'm interested in your interests e.g. cloud computing, web dev
- 📫 How to reach me: your email or social link

## Projects
- [git-learning-log](https://github.com/Git-Guru-commit/git-learning-log) - My first Git project tracking a learning log

## Command learned today
git init
git add learning-log.md
git commit -m "Add initial learning log"

git add learning-log.md
git commit -m "Add What I Learned section"

git log
git status
git log --oneline

git add learning-log.md
git commit -m "Expand learning notes on branches"

git add learning-log.md
git commit -m "Merge add-resources branch and resolve conflict"

git log --oneline --graph

git remote add origin https://github.com/Git-Guru-commit/git-learning-log.git
git branch -M main
git push -u origin main
git push origin add-resources

git reset --soft HEAD~1
    - moves HEAD back by one commit. The soft flag means your file changes stay staged, ready to be re-committed or modified.
    - HEAD 1 means "one commit before the current HEAD." The commit is gone from history, but your work is preserved.

git checkout -- undo-practice.md
    - replaces the file in your working directory with the version from the last commit. Any unsaved edits to that file are permanently discarded.
    - The -- separates the command from the filename. Without it, Git might confuse a filename for a branch name.

git revert HEAD
    - creates a brand new commit that does the exact opposite of whatever HEAD (the most recent commit) did. If the last commit added a line, the revert commit removes it.
    - The original bad commit stays in history (because it was already pushed), but the new revert commit cancels out its effect. This is the safe way to undo public work.

git reset --hard HEAD~1
    - This is the most destructive form of reset. It moves HEAD back one commit, updates the staging area, AND overwrites your working directory. The Bisect section you just added is now gone from the file on disk.

git reflog
    - The commit is gone from git log, but it is not gone from Git. The reflog tracks every time HEAD moves, including resets. Your "lost" commit still exists in Git's object database.

git branch recover-bisect-section f2c4cda
    - This creates a new branch called recover-bisect-section that points directly at the commit you thought was lost. The commit's content (your Bisect section) is now reachable again through this branch.

git merge recover-bisect-section - Merge the recovery branch into main by running