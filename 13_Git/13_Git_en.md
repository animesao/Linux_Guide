# Git

## Setup

```bash
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
git config --global core.editor "vim"
```

## Basic Commands

| Command | Description |
|---------|-------------|
| `git init` | Initialize repository |
| `git clone url` | Clone repository |
| `git add file` | Add file to staging |
| `git add .` | Add all files |
| `git commit -m "message"` | Commit |
| `git push` | Push to remote |
| `git pull` | Pull from remote |
| `git status` | Status |
| `git log` | Commit history |
| `git log --oneline` | Compact history |
| `git diff` | Differences |

## Branches

| Command | Description |
|---------|-------------|
| `git branch` | List branches |
| `git branch name` | Create branch |
| `git checkout name` | Switch branch |
| `git checkout -b name` | Create and switch |
| `git switch name` | Switch (new way) |
| `git switch -c name` | Create and switch |
| `git branch -d name` | Delete branch |
| `git branch -D name` | Force delete |
| `git merge name` | Merge branch |
| `git rebase name` | Rebase |

## Remote Repositories

| Command | Description |
|---------|-------------|
| `git remote add origin url` | Add remote |
| `git remote -v` | List remotes |
| `git push -u origin main` | First push |
| `git fetch` | Fetch without merge |
| `git pull --rebase` | Pull with rebase |

## Undo Changes

```bash
# Undo staging
git reset HEAD file

# Undo commit (keep changes)
git reset --soft HEAD~1

# Undo commit (delete changes)
git reset --hard HEAD~1

# Undo specific commit
git revert commit_hash

# Undo changes in file
git checkout -- file
```

## Stash

```bash
# Save changes
git stash

# Save with name
git stash push -m "description"

# View stash
git stash list

# Apply stash
git stash apply

# Apply and remove
git stash pop

# Delete stash
git stash drop
```

## Tags

```bash
# Create tag
git tag v1.0.0

# Create tag with description
git tag -a v1.0.0 -m "Release 1.0.0"

# Push tags
git push --tags

# List tags
git tag
```

## Useful Aliases

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.lg "log --oneline --graph --all"
```

## Quick Reference

```bash
# Quick commit
git add . && git commit -m "update"

# View history
git log --oneline --graph

# Create and switch branch
git checkout -b feature

# Merge branch
git merge feature

# Push
git push origin main
```
