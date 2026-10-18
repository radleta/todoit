---
tags: [todoit-expert/repo-layout]
summary: "The checkout holds two git repos, code at the root on develop and planning in a nested scratch/ repo on main, and which one each change and git command belongs to"
---

# Repo layout

The checkout holds two independent git repos, each with its own base branch:

| Repo | Where | GitHub | Base branch | Holds |
|---|---|---|---|---|
| Code | checkout root | `radleta/todoit` | `develop` | the app |
| Scratch | `scratch/` | `radleta/todoit-scratch` | `main` | planning, issues, session handoffs, lane records, `learned/` captures |

- Code work lands on `develop`, the lane baseline the [`CLAUDE.md` `Lanes`](../../../CLAUDE.md) line sets and the GitHub default branch (`gh repo view radleta/todoit`, observed 2026-10-18). Open pull requests against `develop`, not `main`. Nothing in the lane workflow moves the code repo's `main`; promoting `develop` to `main` is a manual step.
- The code repo's [`.gitignore` `scratch/`](../../../.gitignore) excludes the scratch repo, so a plain `git` command at the root never sees scratch files. Run every scratch git command as `git -C scratch ...`; scratch work lands on scratch `main`.

A lane spans both repos; how a lane's worktrees sit on disk is [worktree lanes](worktree-lanes.md).
