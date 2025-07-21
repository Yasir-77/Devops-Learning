# Git Cheat Sheet 🚀

## 🔄 Basic Workflow
```
git init                        # Initialize new repo
git clone <url>                 # Clone existing repo
git add <file>                 # Stage file
git add .                       # Stage all changes
git commit -m "message"        # Commit staged changes
git status                      # Show working tree status
git log                         # Show commit history
```

## 🌿 Branching & Merging
```
git branch                      # List branches
git branch <name>              # Create new branch
git checkout <branch>          # Switch branch
git checkout -b <new-branch>   # Create & switch
git merge <branch>             # Merge into current branch
git rebase <branch>            # Rebase current branch
git branch -d <branch>         # Delete branch
```

## 🔄 Remote Operations
```
git remote -v                   # List remotes
git push origin <branch>       # Push to remote
git pull origin <branch>       # Pull from remote
git fetch                      # Download objects/refs
```

## ⏪ Undoing Things
```
git reset --soft HEAD~1        # Undo commit, keep changes
git reset --hard HEAD~1        # Completely undo commit
git revert <commit>            # Create undo commit
git commit --amend             # Fix last commit
git stash                      # Temporarily stash changes
git stash pop                  # Restore stashed changes
```

## 🔍 Inspecting Changes
```
git diff                       # Unstaged changes
git diff --staged             # Staged changes
git show <commit>             # Show commit changes
git blame <file>              # Who changed what
```

## 🧹 Cleanup & Maintenance
```
git clean -n                   # Show what would be removed
git clean -f                   # Remove untracked files
git gc                         # Garbage collection
```

## 🎯 Advanced Techniques
```
git cherry-pick <commit>      # Apply specific commit
git rebase -i HEAD~3          # Interactive rebase
git bisect start              # Binary search for bugs
git reflog                    # Show reference logs
```

## 📌 Gitignore Patterns
```
*.log         # Ignore all .log files
/temp/        # Ignore temp directory
.DS_Store     # Mac metadata file
.env          # Environment variables
```
