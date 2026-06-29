# Git Cheat Sheet

> A practical reference for everyday Git use — from beginner basics to power user commands.

---

## Table of Contents

1. [Core Concepts](#core-concepts)
2. [Setup](#setup)
3. [Starting a Repository](#starting-a-repository)
4. [Daily Commands](#daily-commands)
5. [Branching](#branching)
6. [Merging & Rebasing](#merging--rebasing)
7. [Remote Repositories](#remote-repositories)
8. [Undoing Things](#undoing-things)
9. [Viewing History & Diffs](#viewing-history--diffs)
10. [Stashing](#stashing)
11. [Tags](#tags)
12. [The .gitignore File](#the-gitignore-file)
13. [Common Workflows](#common-workflows)
14. [Fixing Common Errors](#fixing-common-errors)

---

## Core Concepts

| Term | Plain English |
|---|---|
| **Repository (repo)** | A folder tracked by Git — contains all your files and their history |
| **Commit** | A saved snapshot of your files at a point in time |
| **Branch** | A parallel version of your repo — lets you work without affecting the main copy |
| **Main / Master** | The default primary branch of a repository |
| **Remote** | A version of your repo hosted online (e.g. GitHub, GitLab) |
| **Origin** | The default name for your remote repository |
| **Staging area** | A holding zone where you prepare changes before committing |
| **Push** | Upload your local commits to the remote |
| **Pull** | Download and merge changes from the remote into your local repo |
| **Fetch** | Download changes from remote without merging them |
| **Merge** | Combine two branches together |
| **Clone** | Download a full copy of a remote repo to your machine |
| **HEAD** | A pointer to the current commit you're working from |
| **Index** | Another name for the staging area |

---

## Setup

Run these once when you first install Git on a machine.

```bash
# Set your name and email (appears in every commit)
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

# Set default branch name to main
git config --global init.defaultBranch main

# Set your preferred editor (optional)
git config --global core.editor "code --wait"   # VS Code
git config --global core.editor "nano"           # Nano

# View all your config settings
git config --list
```

---

## Starting a Repository

```bash
# Turn an existing folder into a Git repo
git init

# Clone an existing repo from GitHub
git clone https://github.com/username/repo-name.git

# Clone into a specific folder name
git clone https://github.com/username/repo-name.git my-folder
```

---

## Daily Commands

These are the commands you'll use every single day.

### Check status

```bash
# See what's changed, staged, or untracked
git status

# Short version
git status -s
```

### Stage changes

```bash
# Stage a specific file
git add filename.md

# Stage all changes in current folder
git add .

# Stage all changes in the whole repo
git add -A

# Stage parts of a file interactively
git add -p filename.md
```

### Commit

```bash
# Commit staged changes with a message
git commit -m "your message here"

# Stage all tracked files and commit in one step
git commit -am "your message here"

# Amend the last commit message (before pushing)
git commit --amend -m "corrected message"
```

### The add → commit cycle

```
[ Edit files ] → git add . → git commit -m "message" → [ repeat ]
```

### Good commit message format

```
Short summary under 50 characters

Optional longer description after a blank line.
Explain what changed and why, not how.
```

---

## Branching

```bash
# List all local branches
git branch

# List all branches including remote
git branch -a

# Create a new branch
git branch feature-name

# Switch to a branch
git checkout feature-name

# Create and switch in one step (preferred)
git checkout -b feature-name

# Modern syntax (Git 2.23+)
git switch feature-name
git switch -c feature-name   # create and switch

# Rename current branch
git branch -M new-name

# Delete a branch (safe — won't delete if unmerged)
git branch -d feature-name

# Force delete a branch
git branch -D feature-name
```

---

## Merging & Rebasing

### Merging

```bash
# Merge a branch into your current branch
git merge feature-name

# Merge without fast-forward (preserves branch history)
git merge --no-ff feature-name

# Abort a merge in progress
git merge --abort
```

### Rebasing

```bash
# Rebase current branch onto main
git rebase main

# Interactive rebase — edit, squash, reorder last N commits
git rebase -i HEAD~3

# Abort a rebase in progress
git rebase --abort

# Continue after resolving conflicts
git rebase --continue
```

> **Merge vs. Rebase:** Merge preserves history with a merge commit. Rebase rewrites history for a cleaner linear log. Never rebase branches others are using.

---

## Remote Repositories

```bash
# View remote connections
git remote -v

# Add a remote
git remote add origin https://github.com/username/repo.git

# Change remote URL
git remote set-url origin https://github.com/username/new-repo.git

# Remove a remote
git remote remove origin

# Push to remote (first time)
git push -u origin main

# Push after first time
git push

# Push a specific branch
git push origin feature-name

# Pull (fetch + merge)
git pull

# Pull from a specific branch
git pull origin main

# Fetch without merging
git fetch origin

# Delete a remote branch
git push origin --delete feature-name
```

---

## Undoing Things

### Before committing

```bash
# Discard changes in a file (restore to last commit)
git checkout -- filename.md

# Modern syntax
git restore filename.md

# Unstage a file (keep changes, remove from staging)
git reset HEAD filename.md

# Modern syntax
git restore --staged filename.md

# Discard ALL uncommitted changes (dangerous — can't undo)
git restore .
```

### After committing

```bash
# Undo last commit but keep changes staged
git reset --soft HEAD~1

# Undo last commit and unstage changes (files unchanged)
git reset HEAD~1

# Undo last commit and DISCARD all changes (dangerous)
git reset --hard HEAD~1

# Safely undo a commit by creating a new reverse commit
git revert HEAD

# Revert a specific commit
git revert abc1234
```

### Fix last commit (before pushing)

```bash
# Add forgotten file to last commit
git add forgotten-file.md
git commit --amend --no-edit

# Change last commit message
git commit --amend -m "new message"
```

> **Rule of thumb:** Use `reset` for local commits you haven't pushed. Use `revert` for commits already pushed to a shared remote.

---

## Viewing History & Diffs

```bash
# View commit history
git log

# Compact one-line log
git log --oneline

# Log with graph (great for branches)
git log --oneline --graph --all

# Show changes in a specific commit
git show abc1234

# Show what changed between working directory and last commit
git diff

# Show what's staged and ready to commit
git diff --staged

# Compare two branches
git diff main..feature-name

# Compare two commits
git diff abc1234..def5678

# See who changed each line of a file
git blame filename.md
```

---

## Stashing

Stashing lets you save work-in-progress without committing it — useful when you need to switch branches quickly.

```bash
# Stash current changes
git stash

# Stash with a description
git stash push -m "work in progress on feature X"

# List all stashes
git stash list

# Apply the most recent stash (keeps it in stash list)
git stash apply

# Apply and remove from stash list
git stash pop

# Apply a specific stash
git stash apply stash@{2}

# Delete a specific stash
git stash drop stash@{0}

# Delete all stashes
git stash clear
```

---

## Tags

Tags mark specific points in history — typically used for releases.

```bash
# List all tags
git tag

# Create a lightweight tag
git tag v1.0.0

# Create an annotated tag (recommended)
git tag -a v1.0.0 -m "Release version 1.0.0"

# Tag a specific past commit
git tag -a v1.0.0 abc1234

# Push a tag to remote
git push origin v1.0.0

# Push all tags
git push origin --tags

# Delete a local tag
git tag -d v1.0.0

# Delete a remote tag
git push origin --delete v1.0.0
```

---

## The .gitignore File

A `.gitignore` file tells Git which files to never track. Place it in the root of your repo.

```bash
# Create a .gitignore
touch .gitignore
```

### Common .gitignore patterns

```gitignore
# Ignore a specific file
secret.txt

# Ignore a file type
*.log
*.env

# Ignore a folder
node_modules/
.obsidian/workspace.json

# Ignore everything in a folder but keep the folder
logs/*
!logs/.gitkeep

# Ignore OS files
.DS_Store         # Mac
Thumbs.db         # Windows

# Ignore editor files
.vscode/
.idea/
```

> If a file is already tracked, adding it to `.gitignore` won't stop tracking it. Run `git rm --cached filename` first.

---

## Common Workflows

### Standard solo workflow

```bash
# 1. Pull latest changes before starting
git pull

# 2. Make your changes...

# 3. Stage and commit
git add .
git commit -m "describe what you did"

# 4. Push to remote
git push
```

### Feature branch workflow (teams)

```bash
# 1. Create a new branch for your work
git checkout -b feature/my-feature

# 2. Make changes and commit regularly
git add .
git commit -m "add new feature"

# 3. Push branch to remote
git push -u origin feature/my-feature

# 4. Open a Pull Request on GitHub

# 5. After PR is merged, clean up
git checkout main
git pull
git branch -d feature/my-feature
```

### Sync a forked repo

```bash
# Add the original repo as upstream (once)
git remote add upstream https://github.com/original/repo.git

# Fetch and merge upstream changes
git fetch upstream
git merge upstream/main
```

---

## Fixing Common Errors

### "src refspec main does not match any"
You have no commits yet. Run:
```bash
git add .
git commit -m "first commit"
git push -u origin main
```

### "You are on branch master, not main"
Rename your branch:
```bash
git branch -M main
git push -u origin main
```

### "Please tell me who you are"
Set your identity:
```bash
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```

### "Merge conflict"
Open the conflicted file — Git marks conflicts like this:
```
<<<<<<< HEAD
Your local version
=======
The incoming version
>>>>>>> origin/main
```
Delete the markers, keep what you want, then:
```bash
git add .
git commit -m "resolve merge conflict"
```

### "Authentication failed" on push
GitHub no longer accepts passwords. Use a Personal Access Token:
1. GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Generate a token with `repo` scope
3. Use it as your password when Git prompts you

### Accidentally committed to main
```bash
# Move your commit to a new branch instead
git branch feature/my-work     # save commit to new branch
git reset --hard HEAD~1        # remove it from main
git checkout feature/my-work   # switch to the new branch
```

### Need to undo a push to remote
```bash
# Revert the commit (safe for shared repos)
git revert HEAD
git push
```

---

## Quick Reference Card

| Task | Command |
|---|---|
| Initialize repo | `git init` |
| Clone repo | `git clone <url>` |
| Check status | `git status` |
| Stage all | `git add .` |
| Commit | `git commit -m "message"` |
| Push | `git push` |
| Pull | `git pull` |
| New branch | `git checkout -b name` |
| Switch branch | `git checkout name` |
| Merge branch | `git merge name` |
| View log | `git log --oneline` |
| Discard changes | `git restore filename` |
| Unstage file | `git restore --staged filename` |
| Undo last commit | `git reset HEAD~1` |
| Stash changes | `git stash` |
| Apply stash | `git stash pop` |
| View remotes | `git remote -v` |
| Rename branch | `git branch -M new-name` |

---

*Generated with Claude — git-cheat-sheet.md*
