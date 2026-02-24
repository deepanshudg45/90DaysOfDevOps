# Git Commands Reference

## Setup & Config

### git --version
Shows installed Git version
Example:
git --version

### git config --global user.name
Sets global username
Example:
git config --global user.name "John Doe"

### git config --global user.email
Sets global email
Example:
git config --global user.email "john@email.com"

---

## Basic Workflow

### git init
Initializes a new Git repository
Example:
git init

### git status
Shows current repository state
Example:
git status

### git add
Stages changes for commit
Example:
git add git-commands.md

### git commit
Creates a commit from staged changes
Example:
git commit -m "Add initial Git commands reference"

---

## Viewing Changes

### git log
Shows commit history
Example:
git log

### git log --oneline
Shows compact commit history
Example:
git log --oneline

### git diff
Shows unstaged changes
Example:
git diff

---

## Added Commands

### git rm
This command removes a file from both your computer's folders and the Git "index" (the list of tracked files) in one step.
Example:
git rm old_notes.md

### git mv
This command renames or moves a file while preserving its entire history, automatically staging the change for your next commit.
Example:
git mv readme.md README.md

### git show
Displays the detailed contents and metadata of a specific Git object, such as a commit, tag, or file version.
Example:
git show HEAD:README.md

### git restore
Reverts files in your working directory or staging area to their last committed state.
Example:
If you made a mistake while editing README.md in nano and want to discard those unsaved changes: git restore README.md