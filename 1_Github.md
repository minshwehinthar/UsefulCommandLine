# 🐙 Git & GitHub Quick Reference Guide

A complete cheat sheet for Git and GitHub workflows, including basic setups, everyday operations, branching strategies, remote management, and comprehensive undo/reverse commands.

---

## 📑 Table of Contents
- [Setup & Configuration](#-setup--configuration)
- [Daily Workflow](#-daily-workflow)
- [Branching & Merging](#-branching--merging)
- [Remotes & GitHub Sync](#-remotes--github-sync)
- [Stashing Changes](#-stashing-changes)
- [Undo & Reverse Commands](#-undo--reverse-commands)

---

## 🚀 Setup & Configuration

| Command | Description |
| :--- | :--- |
| `git config --global user.name "Your Name"` | Set global username |
| `git config --global user.email "your.email@example.com"` | Set global email address |
| `git config --global init.defaultBranch main` | Set default branch name to `main` |
| `git init` | Initialize a new local Git repository |
| `git clone <repo_url>` | Clone a remote repository to local machine |

---

## 🔄 Daily Workflow

| Command | Description |
| :--- | :--- |
| `git status` | Check status of working tree and staging area |
| `git add .` | Stage all changes in working directory |
| `git add <file_path>` | Stage specific file |
| `git commit -m "commit message"` | Commit staged changes with message |
| `git commit -am "commit message"` | Stage tracked files and commit in one step |
| `git log --oneline --graph --all` | View commit history log with branch graph |

---

## 🔀 Branching & Merging

| Command | Description |
| :--- | :--- |
| `git branch` | List all local branches |
| `git branch -a` | List local and remote branches |
| `git branch <branch_name>` | Create a new branch |
| `git checkout -b <branch_name>` | Create and switch to a new branch |
| `git switch <branch_name>` | Switch to an existing branch |
| `git merge <branch_name>` | Merge target branch into current branch |
| `git branch -d <branch_name>` | Delete a local branch (safe) |
| `git branch -D <branch_name>` | Force delete a local branch |

---

## 🌐 Remotes & GitHub Sync

| Command | Description |
| :--- | :--- |
| `git remote add origin <url>` | Link local repo to a GitHub repository |
| `git remote -v` | View configured remote repositories |
| `git fetch origin` | Download changes from remote without merging |
| `git pull origin <branch_name>` | Fetch and merge changes from remote branch |
| `git push -u origin <branch_name>` | Push local branch to remote and set tracking |
| `git push origin --delete <branch_name>` | Delete a remote branch |

---

## 📦 Stashing Changes

| Command | Description |
| :--- | :--- |
| `git stash` | Temporarily save uncommitted changes |
| `git stash save "message"` | Save stash with descriptive message |
| `git stash list` | List all stashed changes |
| `git stash pop` | Re-apply latest stash and delete it from list |
| `git stash apply` | Apply latest stash and keep it in stash list |
| `git stash drop` | Discard latest stash |
| `git stash clear` | Clear all stashes |

---

## ⏪ Undo & Reverse Commands

### Discarding Unstaged Local Changes
```bash
# Discard local changes in a specific file
git checkout -- <file_path>
# OR (modern Git)
git restore <file_path>

# Discard ALL local unstaged changes in working directory
git restore .

# Remove untracked files and directories (force clean)
git clean -fd
```

### Unstaging Files (Before Commit)
```bash
# Unstage a specific file (keep changes in working directory)
git reset HEAD <file_path>
# OR (modern Git)
git restore --staged <file_path>

# Unstage ALL files
git restore --staged .
```

### Reverting & Modifying Commits
```bash
# Modify the last commit message or add staged files to it
git commit --amend -m "updated commit message"

# Safely revert a public commit by creating a new inverse commit
git revert <commit_hash>

# Revert a merge commit (specify parent index 1)
git revert -m 1 <commit_hash>
```

### Resetting History (Use with Caution)
```bash
# Undo commit, keep changes staged
git reset --soft HEAD~1

# Undo commit, keep changes unstaged in working directory
git reset --mixed HEAD~1

# Undo commit AND permanently destroy all changes
git reset --hard HEAD~1

# Reset local branch to match remote HEAD exactly
git fetch origin
git reset --hard origin/main
```