# Git & GitHub — Quick Reference

A concise reference for commonly used Git and GitHub commands, their purpose, and typical workflows.

## Table of contents
- [What is Git?](#what-is-git)
- [Initial setup](#initial-setup)
- [Working with repositories](#working-with-repositories)
- [Check status & differences](#check-status--differences)
- [File states](#file-states)
- [Staging & committing changes](#staging--committing-changes)
- [Pushing & pulling](#pushing--pulling)
- [Branch management](#branch-management)
- [Commit history](#commit-history)
- [Push an existing local repo to GitHub](#push-an-existing-local-repo-to-github)
- [Rebase & advanced operations](#rebase--advanced-operations)
- [Push branches & tags](#push-branches--tags)
- [Get help](#get-help)

---

## What is Git?
Git is a distributed version control system that helps developers track changes, collaborate, and manage source code efficiently.

---

## Initial setup
Configure your identity so commits are credited correctly:

```bash
git config --global user.name "Rikin Patel"
git config --global user.email "rikinpatel@gmail.com"

# Verify configuration
git config --list
```

---

## Working with repositories

Clone a remote repository:
```bash
git clone <repository_url>
```

Initialize a new local repository:
```bash
git init
```

---

## Check status & differences

Show the working tree status:
```bash
git status
```

Show changes not yet staged:
```bash
git diff
```

Show staged vs. last commit:
```bash
git diff --staged
```

---

## File states
- Untracked — new files not tracked by Git
- Modified — files that have been changed
- Staged — files added to the index (ready to commit)
- Unmodified — no changes since last commit

---

## Staging & committing changes

Add files to the staging area:
```bash
# Add a specific file
git add <file_name>

# Add all changes (tracked and untracked)
git add .
```

Commit staged changes:
```bash
git commit -m "Your commit message"
```

Create a commit and edit message interactively:
```bash
git commit
```

---

## Pushing & pulling

Push to the remote branch `main`:
```bash
git push origin main
```

Push and set upstream for your local branch:
```bash
git push -u origin <branch_name>
```

Pull latest changes from the current branch's remote:
```bash
git pull
```

If you need help with push options:
```bash
git push --help
```

---

## Branch management

List local branches:
```bash
git branch
```

Create a new branch and switch to it:
```bash
git checkout -b <branch_name>
# or using newer command:
git switch -c <branch_name>
```

Switch to an existing branch:
```bash
git checkout <branch_name>
# or
git switch <branch_name>
```

Rename the current branch to `main`:
```bash
git branch -m main
```

Delete a local branch:
```bash
git branch -d <branch_name>
```

🧹 Delete a Remote Branch:
```bash
git push origin --delete branch-name
```

List remote branches:
```bash
git branch -r
```

Fetch remote branches and updates (without merging):
```bash
git fetch
```

---

## Commit history

View commit logs:
```bash
git log
```

Compact, graph-style view:
```bash
git log --graph --oneline --decorate --all
```

Show a file's history:
```bash
git log -- <path/to/file>
```

---

## Push an existing local repo to GitHub

If you have a local repo and want to add a remote and push:

```bash
git remote add origin <repository_url>
git branch -m main            # rename current branch to main (if needed)
git push -u origin main
```

---

## Rebase & advanced operations

Rebase your current branch onto the latest `main` from origin:
```bash
git pull --rebase origin main
```

Use rebase carefully — it rewrites history for local commits.

To abort an in-progress rebase:
```bash
git rebase --abort
```

---

## Push branches & tags

Push all local branches to the remote:
```bash
git push --all origin
```

Push all tags:
```bash
git push --tags
```

---

## Get help
Open git's built-in help pages:

```bash
git help <command>
# example
git help commit
```

Or use the `--help` flag:
```bash
git commit --help
```

---

## Using a .gitignore file (If folder should stay empty)

Useful when you want the folder but don’t want its contents tracked.

---

```bash
mkdir uploads
touch uploads/.gitignore

git add uploads/.gitignore
git commit -m "Add empty uploads directory"
git push origin main
```

---

## Using a .gitkeep file

.gitkeep is a convention (not a Git command) used to keep empty directories.

---

```bash
mkdir logs
touch logs/.gitkeep

git add logs/.gitkeep
git commit -m "Add empty logs directory"
git push origin main
```

---

## Interactive Add (Useful)

Allows you to choose specific files or even parts of files. Select individual files.

---

```bash
git add -i
OR
git add -p

git commit -m "Commit selected changes"
git push origin main
```

---

## Ignore Files You Don’t Want to Push (.gitignore)

---

## Create/Edit .gitignore
```bash
node_modules/
.env
*.log
dist/

git add .gitignore
git commit -m "Add gitignore"
```

---

## Stashing (Interruptions Happen)  

---

## Save your unfinished work safely.
```bash
git stash
```

---

## with message
```bash
git stash push -m "WIP: login feature"
```

---

## Check available stashes:
```bash
git stash list
```

```bash
git stash apply (Apply the latest stash)
```

---

## Restore a Deleted Git Branch (Local)

### Case 1: Branch deleted locally (`git branch -d`)
```bash
git reflog
git branch my-branch <commit-hash>
git checkout my-branch
```

### Case 2: Branch deleted locally and remotely
```bash
git reflog
git log --all --oneline --decorate
git branch my-branch <commit-hash>
git push origin my-branch
```

### Case 3: Branch still exists on remote
```bash
git fetch origin
git checkout -b my-branch origin/my-branch
```

### Case 4: Branch force-deleted (git branch -D)
```bash
git reflog
git branch my-branch <commit-hash>
```

## Remove node_modules.js file from Git (but keep locally)
```bash
git rm -r --cached node_modules
```



 
