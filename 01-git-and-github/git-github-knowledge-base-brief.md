# Project Brief: Git & GitHub Knowledge Base

## Project Name
`msaie-git-notes` (suggested repo name)

## Purpose
A personal, living knowledge base documenting Git and GitHub concepts learned during the Quantic MSAIE program. Starts as a course summary and grows into a comprehensive reference as further courses and practical experience are added.

## Goals
- Capture key concepts, commands, and mental models from the Git & GitHub intro course
- Build a habit of documenting learning in a structured, version-controlled way
- Practice Git/GitHub workflows on a real project (eating your own cooking)
- Create a reference that is useful months later when concepts need revisiting
- Demonstrate progression over time through commit history

## Scope

### Phase 1 — Course Summary (now)
Document everything covered in the Quantic Git & GitHub intro course:
- Git fundamentals (data model, working directory, staging, repository)
- Core commands (init, add, commit, log, status, branch, checkout, merge, revert, stash, rebase)
- GitHub workflows (push, pull, fetch, fork, clone, pull requests)
- Key concepts (branches, HEAD, remote vs local, authentication)

### Phase 2 — Expanded Reference (ongoing)
Add depth as experience grows:
- Command cheat sheet with real examples from coursework
- Common mistakes and how to fix them (e.g. wrong branch, forgotten add, merge conflicts)
- Diagrams of Git workflows
- Notes from any additional Git/GitHub content encountered in later MSAIE modules

### Phase 3 — Advanced Topics (future)
As the CI/CD and Software Testing module introduces more:
- Git in CI/CD pipelines
- Branch strategies (GitFlow, trunk-based development)
- Code review best practices via pull requests
- GitHub Actions basics

## Structure
```
msaie-git-notes/
├── README.md               ← project overview and how to navigate
├── 01-fundamentals/
│   ├── data-model.md       ← trees, blobs, commits, repos
│   └── three-areas.md      ← working directory, staging, repository
├── 02-commands/
│   ├── local.md            ← init, add, commit, log, branch, checkout, merge...
│   └── remote.md           ← push, pull, fetch, clone, fork, PR
├── 03-github/
│   ├── workflows.md        ← fork → clone → branch → PR flow
│   └── authentication.md  ← tokens, SSH, credential store
├── 04-cheatsheet.md        ← quick reference card
└── 05-lessons-learned.md   ← mistakes made and how they were fixed
```

## Git Workflow for This Project
Since this project is itself a Git repo, use it to practice:
- Commit after every study session with a meaningful message
- Use branches for major new sections (e.g. `add-cicd-notes`)
- Use pull requests if collaborating with study group peers
- Tag versions to mark completion of each MSAIE module (`v1.0-git-intro`, `v2.0-cicd`)

## Success Criteria
- All Git & GitHub intro course concepts documented by end of module
- Repo is public on GitHub (demonstrates transparency and portfolio building)
- Commit history shows consistent, incremental progress
- Content is written in plain English, not just copied commands — explains the *why*

## Notes
- Write for your future self — assume you'll read this 6 months later having forgotten the details
- Relate concepts to familiar analogies where helpful (e.g. commits as insurance checkpoints, branches as parallel universes)
- This repo itself is proof of Git skills — the commit history tells the story of your learning
