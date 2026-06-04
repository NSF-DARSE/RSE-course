# Git Workflow Guidance for Case Study Teams and Students

## Purpose

This document recommends a practical Git workflow for case-study teams, students, and collaborators. The goal is to make code development reproducible, reviewable, and easy to maintain without adding unnecessary process overhead.

## Recommended default: GitHub Flow with short-lived branches

For most cases, use a simple GitHub Flow model:

1. Keep `main` stable.
2. Create a short-lived branch for each task.
3. Commit small, meaningful changes.
4. Push the branch to GitHub.
5. Open a pull request.
6. Review, test, and revise.
7. Merge into `main` after approval.
8. Delete the branch after merge.

**Work on branch → PR → review → squash merge.**

This is the best default because most case-study projects are collaborative research/software projects, not formal product-release projects. The workflow is simple enough for students but still supports review, reproducibility, and traceability.

## Branch structure

Use `main` as the stable shared branch with branch protection rules and continious integration.

Recommended branch prefixes:

| Prefix      | Use for                                     |
| ----------- | ------------------------------------------- |
| `feature/`  | New code, analysis, or functionality        |
| `fix/`      | Bug fixes or corrections                    |
| `docs/`     | Documentation-only changes                  |
| `analysis/` | Exploratory or case-study analysis work     |
| `refactor/` | Code cleanup that should not change results |
| `test/`     | Adding or modifying tests                   |

## Standard workflow

### 1. Start from an updated `main`

```bash
git checkout main
git pull origin main
```

### 2. Create a new branch

```bash
git checkout -b feature/descriptive-branch-name
git switch -c feature/descriptive-branch-name
```

Use one branch for one logical task. Avoid putting unrelated work into the same branch.

### 3. Make changes and commit regularly

Stage and commit:

```bash
git add path/to/file
git commit -m "Add descriptive commit message"
```

### 4. Push the branch

```bash
git push -u origin feature/descriptive-branch-name
```

### 5. Open a pull request

* What changed
* Why it changed
* How it was tested
* Any files, figures, or outputs reviewers should inspect

## Notes for reviewers
Mention anything uncertain, incomplete, or requiring special attention.

### 6. Review and revise

Reviewers should check:

* Does the code run?
* Are results reproducible?
* Are file paths portable?
* Are large/generated files avoided unless necessary?
* Is documentation updated?
* Are assumptions clearly described?

**Authors should respond to comments by pushing more commits to the same branch. The pull request updates automatically.**

### 7. Merge and delete the branch

After approval, merge into `main`. Then delete the feature branch from GitHub.

Deleting merged branches keeps the repository clean. The branch history remains available through the pull request.

### Merge, Rebase, and Squash Merge Comparison

| Method | What it does | Keeps all commits? | Creates merge commit? | Best use |
|-------|---------------------------|-----|-----|--------------------------|
| Merge | Combines branch histories | Yes | Yes | Full development history |
| Rebase | Replays commits on top of updated `main` | Yes | No | Cleaning/updating branch history |
| Squash merge | Combines branch commits into one commit | No | No | Clean project history for PRs |


## When to use other workflows

## Option A: GitHub Flow — recommended default

Use this for:

* Most case studies
* Student projects
* Research code
* Analysis pipelines
* Documentation projects
* Small to medium teams

### Branch pattern:

```text
main
 ├── feature/task-1
 ├── fix/task-2
 └── docs/task-3
```

### Advantages:

* Simple
* Easy to teach
* Works well with pull requests
* Keeps `main` stable
* Avoids long-lived branches

### Disadvantages:

* Requires discipline to keep branches short-lived
* Less suitable for complex versioned software releases

### Recommended reading

GitHub flow: https://docs.github.com/en/get-started/using-github/github-flow

## Option B: Gitflow — use only for formal releases

Gitflow uses multiple long-lived branches, usually including:

```text
main
develop
feature/*
release/*
hotfix/*
```

Use Gitflow only when a project has:

* Formal versioned releases
* Separate development and production versions
* Release candidates
* Hotfixes to already-released versions

Do not use Gitflow for most case studies. It is usually too heavy and creates unnecessary branch-management overhead.

### Recommended reading

A successful Git branching model (by Vincent Driessen): https://nvie.com/posts/a-successful-git-branching-model/

## Option C: Trunk-based development — advanced option

Trunk-based development keeps almost all work close to the main branch. Developers use very short-lived branches or commit directly to the trunk when allowed by team rules.

Use this only when the team has:

* Strong automated tests
* Continuous integration
* Experienced contributors
* Small, frequent changes
* Clear review expectations

| GitHub Flow                  | Trunk-based                          |
| ---------------------------- | ------------------------------------ |
| short-lived feature branches | extremely short-lived branches       |
| PR-driven workflow           | often direct integration or tiny PRs |
| branches may live days       | branches live hours or <1 day        |
| review before merge          | integrate continuously               |
| simpler for teams/students   | optimized for rapid CI/CD            |

### Recommended reading

Trunk Based Development: 
- https://trunkbaseddevelopment.com/
- https://www.atlassian.com/continuous-delivery/continuous-integration/trunk-based-development

## Recommended DARSE policy

### Default rule

Use GitHub Flow unless there is a specific reason not to.

Use Gitflow only for projects that need formal software releases. Use trunk-based development only for teams with strong automated testing and contributors comfortable with frequent integration.

For most teams, the main goal is not to use the most complex Git model. The goal is to keep work organized, reviewed, reproducible, and easy for future students or collaborators to understand.

### Required practices

1. `main` should always be runnable or clearly documented.
2. Work should happen on short-lived branches.
3. Pull requests should be used before merging into `main`.
4. At least one reviewer should approve substantive changes.
5. Branches should be deleted after merge.
6. Large data files should not be committed unless explicitly approved.
7. Generated outputs should be committed only when they are part of the deliverable.
8. README or documentation should be updated when usage changes.

### Suggested repository structure

```text
project-name/
├── README.md
├── environment.yml or requirements.txt
├── data/
│   ├── raw/              # usually not committed
│   └── processed/        # commit only if small and useful
├── scripts/
├── notebooks/
├── results/
├── figures/
├── docs/
└── tests/
```

## Rules for notebooks

Notebooks are acceptable for exploration, but final or reusable work should be moved into scripts when possible.

Recommended practice:

* Use notebooks for exploration and figures.
* Use scripts for reproducible pipelines.
* Clear unnecessary notebook output before committing, unless the output is part of the review.
* Keep notebook names descriptive.

Example names:

```text
01_qc_summary.ipynb
02_pca_timepoint_analysis.ipynb
03_marker_gene_plots.ipynb
```

## Rules for data

Do not commit large raw datasets directly to Git.

Use Git for:

* Code
* Documentation
* Small configuration files
* Small example datasets
* Metadata tables when appropriate
* Scripts that download or generate data

Avoid committing:

* Large raw files
* Large binary files
* Temporary outputs
* Local environment folders
* Sensitive or private data

If data must be tracked, discuss whether to use Git LFS, institutional storage, cloud storage, or a documented download path.

## Pull request review checklist

Before requesting review, the author should confirm:

* The code runs from a clean checkout.
* Required packages or environment files are updated.
* The README explains how to run the relevant workflow.
* Outputs are reproducible or clearly described.
* Large/private files are not included.
* The PR description explains what changed and why.

Reviewer checklist:

* Does the change solve the stated problem?
* Is the code understandable?
* Are assumptions documented?
* Are file paths relative rather than hard-coded to one person's machine?
* Are results or figures consistent with the code?
* Is the repository cleaner after this change?

## Decision guide

| Project situation                                     | Recommended workflow        |
| ----------------------------------------------------- | --------------------------- |
| Student case study                                    | GitHub Flow                 |
| Small research-code project                           | GitHub Flow                 |
| Analysis pipeline with collaborators                  | GitHub Flow                 |
| Documentation-only project                            | GitHub Flow                 |
| Mature software package with releases                 | Gitflow or release branches |
| Project with automated tests and frequent integration | Trunk-based or GitHub Flow  |

