# Git & GitHub — Practical Notes
*Based on hands-on work during the Quantic MSAIE Git & GitHub intro module*
*Environment: Windows 11 / WSL2 (Ubuntu) / VS Code*

---

## Environment Setup

### Where Git lives in this setup
Git is installed in **Ubuntu (WSL2)**, not Windows. All Git commands are run in the Ubuntu terminal, not PowerShell. This mirrors the Linux path in any course instructions.

### Verify Git is installed
```bash
git --version
```

### Key locations
| What | Where |
|---|---|
| Project files | `~/MSAIE/<project>` in Ubuntu |
| Git credential store | `~/.git-credentials` |
| Git global config | `~/.gitconfig` |

---

## First Time Setup (run once)

```bash
# Set your identity — use the same email as your GitHub account
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# Set default branch name to main (avoids the master warning)
git config --global init.defaultBranch main

# Set VS Code as default editor (avoids being dropped into Vim)
git config --global core.editor "code -w"

# Store credentials so you don't re-enter your token every time
git config --global credential.helper store
```

---

## Starting a New Local Repo

```bash
mkdir my-project
cd my-project
git init
git branch -M main      # rename branch to main if not set globally
```

---

## The Two-Step Commit (the step courses often skip)

Git requires **two steps** before anything is saved — many courses assume you know this:

```bash
git add .               # Step 1: stage all changes (put things in the box)
git commit -m "message" # Step 2: commit with a message (seal and label the box)
```

Shortcut for files already tracked by Git:
```bash
git commit -am "message"  # add + commit in one step
                          # WARNING: does NOT work for brand new files
```

---

## Connecting to GitHub

### GitHub now requires a Personal Access Token (not your password)
1. GitHub → Settings → Developer Settings → Personal Access Tokens → Tokens (classic)
2. Generate new token → tick **repo** scope → copy immediately (shown once only)
3. Use the token as your password when Git prompts

### Linking a local repo to GitHub
```bash
git remote add origin https://<username>@github.com/<username>/<repo>.git
git push -u origin main
```

### Managing multiple GitHub accounts
If you have more than one GitHub account (e.g. personal + work), store both tokens in `~/.git-credentials`:
```
https://account1:TOKEN1@github.com
https://account2:TOKEN2@github.com
```
Use the account username in the remote URL to tell Git which one to use:
```bash
git remote set-url origin https://account2@github.com/account2/repo.git
```

---

## Common Gotchas Encountered

### 1. Running commands in the wrong place
Git commands must be run in the **project folder**, not inside the `.git` folder itself.
```bash
# Wrong — you're inside Git's internals
root@container:/workspace/.git$ git status
fatal: this operation must be run in a work tree

# Fix — go up one level
cd ..
```

### 2. Linux spaces matter
Unlike Windows, Linux commands are exact — every character counts:
```bash
cd..    # WRONG — command not found
cd ..   # CORRECT — space between cd and ..
```

### 3. Forgetting to save files before committing
If VS Code doesn't auto-save, Git sees no changes even after you've edited a file.
Always **Ctrl+S** before running `git add`.

### 4. VPN blocking GitHub pushes
Symptom: `Connection reset by peer` or long timeouts when pushing.
Fix: Disable VPN before pushing to GitHub. Re-enable after.

### 5. Angle brackets in commands are placeholders
```bash
git checkout --detach <commit-hash>   # WRONG — don't type the < >
git checkout --detach a3f8c21d        # CORRECT — use your actual hash
```

### 6. Running out of `git log`
The log viewer is interactive — press **q** to quit and return to your prompt.

### 7. `code .` not found in Ubuntu
VS Code needs to be linked to Ubuntu's PATH:
```bash
echo 'export PATH="$PATH:/mnt/c/Users/<yourname>/AppData/Local/Programs/Microsoft VS Code/bin"' >> ~/.bashrc
source ~/.bashrc
```

---

## Key Concept Clarifications

### Fork vs Clone — easy to confuse
| | Fork | Clone |
|---|---|---|
| What it does | Copies a repo on GitHub to your GitHub account | Downloads a repo from GitHub to your local machine |
| Where it happens | GitHub → GitHub (stays in the cloud) | GitHub → your computer |
| Command | Done via GitHub UI (Fork button) | `git clone <url>` |
| When to use | When you want your own copy to modify independently | When you want to work on it locally |

### git fetch vs git pull
| | git fetch | git pull |
|---|---|---|
| What it does | Downloads remote changes to local repo | Downloads AND applies changes to working directory |
| Safe? | Yes — review before applying | Applies immediately |
| Equivalent to | First half of pull | fetch + merge in one step |

### Rebase vs Merge
- **Merge** — combines two branches, creates a merge commit, history shows the branch existed
- **Rebase** — moves your branch commits to the front of another branch, no merge commit, cleaner history

---

## Daily Workflow Reference

```bash
# Start work
cd ~/MSAIE/my-project
git status                          # see what's changed

# Make changes, then save and commit
git add .
git commit -m "describe what changed"

# Push to GitHub
git push

# Get latest from GitHub
git pull

# Work on a new feature
git checkout -b feature-name        # create and switch to new branch
# ... make changes ...
git add .
git commit -m "feature description"
git checkout main                   # switch back to main
git merge feature-name              # merge feature in
git push                            # push to GitHub
```

---

## Pull Requests (PRs)

A PR is a formal request to merge your changes into someone else's (or a protected) branch.

**When you use them:**
- Contributing to someone else's repo (fork → change → PR)
- Merging into a protected branch within your own repo
- Collaborative work — Capstone project will use these heavily

**Process:**
1. Fork the repo (GitHub UI)
2. Clone your fork locally
3. Create a branch, make changes, commit
4. Push branch to your fork
5. Open PR on GitHub from your branch → original repo's main

---

## Shortcuts Set Up

```bash
msaie           # cd ~/MSAIE && claude (fresh Claude Code session)
msaie-resume    # cd ~/MSAIE && claude --continue (resume last session)
```
