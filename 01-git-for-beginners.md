# Git for Beginners: Basics and Essential Commands

## What is Git?
Git is the free and open source distributed version control system that's responsible for everything GitHub related that happens locally on your computer.

## Why is Git Used?
Git is used to manage changes to files in a way that is safe, auditable and collaborative.

For example:

- It has all the versions and history recorded such as what is changed, who changed it and what and why the change happened. And if the changes are not right or buggy, we can rollback to earlier versions where the code works correctly.
- Multiple people can collaborate and work parallelly on the same code base. And when merge conflicts occur, during merge/rebase workflow, Git isolates them to lines and files affected.
- Git branching helps teams to work parallelly, independently and yet collaboratively.
- Each commit is submitted with a comment where the intention of the change is submitted. And with `git blame` and `git bisect`, you can audit the change and its behavior.
- And many more features like CI/CD pipelines and testing gates etc.

---

## Git Basics - Terminology

### Repository (repo)
A repo is the database Git uses to track a project's files and full change history.

- **Local repo:** where you can work on your local copy
- **Remote repo:** hosted copy for backup and cloning

### Working directory
A folder in your local machine that contains project files.

### Staging
It is a place where all your changes reside and you can choose to commit which changes will go next in your commit.

### Commit
A commit is a recorded snapshot that is stored in the repo history. It contains an ID (hash value) and a meaningful commit message.

### HEAD
A pointer that points to your current position or current branch's latest commit.

---

## Branching and Merging

### Branch
Common branches: `main` or `master`

If when a new feature needs to be implemented, it often happens on a feature branch e.g., `feature/signup`

### Checkout / Switch
Move your working directory to match another branch or commit.

Modern Git uses `git switch` (branches) and `git restore` (files).
`git checkout` is older but still widely used.

### Merge
Combines changes from one branch into another, creating a merge commit (in many cases).
Used when integrating completed work into `main`.

### Rebase
Reapplies commits on top of another base commit, rewriting history.

Often used to keep a linear history on feature branches.

**Caution:** don't rebase commits that others are already using (shared branches) unless your team explicitly allows it.

### Merge conflict
Happens when Git can't automatically reconcile changes (usually same lines changed differently).

You manually edit to resolve, then commit the result.

---

## Remotes and Synchronization

### Remote
A named reference to another repo (commonly `origin`).
`origin` usually points to the primary hosted repository.

### Clone
Creates a local copy of an existing remote repository, including history.

### Fetch
Downloads new commits/branches from a remote without modifying your local branches automatically.

### Pull
Typically means fetch + merge (or fetch + rebase if configured). Updates your current branch with remote changes.

### Push
Upload your local commits to a remote repo.

### Upstream tracking branch
A relationship between your local branch and a remote branch (e.g., local `feature/x` tracks `origin/feature/x`). Enables simpler `git pull`/`git push` without specifying remote/branch each time.

---

## File States :- Important Terms in Git Files Terminology
A file in Git is typically in one of these states:

### Untracked
Git sees the file in your working directory but it is not in the repository yet.

### Modified
You changed the file in your working directory, but those changes are not staged.

### Staged
Changes selected in the staging area, ready to be committed.

### Committed
Changes are stored permanently in the repo history.

---

## Inspecting and Identifying Changes

### Diff
A line-by-line view of what changed. Between working directory and staging, staging and last commit, or between commits/branches.

### Log
Commit history listing (hash, author, date, message).

### Blame
Shows which commit last changed each line of a file (useful for debugging and ownership context).

### Tag
A named pointer to a specific commit, often used for releases.

---

## Undoing and Cleanup Terms

### Restore / Checkout
Revert file content in the working directory back to a previous state (often last commit or staged version).

### Revert
Creates a new commit that undoes a prior commit (safe for shared history).

### Stash
Temporarily shelves uncommitted changes so you can switch branches cleanly, then re-apply later.

### Pull request / Merge request
A code review and merge workflow request to integrate changes from one branch into another.

---

## Common Git Commands
Here are some very common git commands to use on a daily basis:

```bash
git switch main
git pull
git switch -c feature/my-change
# edit files
git add .
git commit -m "My change"
git push -u origin feature/my-change
# open PR on GitHub, merge
git switch main
git pull
git branch -d feature/my-change
```

---

## An Example Workflow
Here is a practical beginner daily workflow for GitHub, assuming you already have a repository on GitHub and you work from your laptop.

### 1) First-time setup (do once)

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Clone the repo:

```bash
git clone <repo_url>
cd <repo_folder>
```

### 2) Start your day: sync with GitHub
Update your local main branch:

```bash
git switch main
git pull
```

If your default branch is master, use master instead of main.

### 3) Create a branch for your work (recommended)

```bash
git switch -c feature/<short-description>
```

Example: `feature/login-fix`

### 4) Make changes, then check what changed

```bash
git status
git diff
```

### 5) Stage changes and commit
Stage everything (simple approach):

```bash
git add .
```

Or stage specific files (safer):

```bash
git add path/to/file1 path/to/file2
```

Commit:

```bash
git commit -m "Describe what you changed"
```

### 6) Push your branch to GitHub
First push (sets upstream):

```bash
git push -u origin feature/<short-description>
```

Later pushes:

```bash
git push
```

### 7) Open a Pull Request (PR) on GitHub
On GitHub (web UI):

1. You'll see a prompt to "Compare & pull request"
2. Create the PR into main
3. Request review if needed
4. Ensure checks/tests pass
5. Merge when approved

### 8) After merge: update your local main and clean up

```bash
git switch main
git pull
git branch -d feature/<short-description>
```

(Optional) Delete the remote branch too:

```bash
git push origin --delete feature/<short-description>
```
