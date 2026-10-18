---
tags: [todoit-expert/worktree-lanes]
summary: "How lane open lays out a worktree lane beside the main checkout and what it forks from, and how to remove or resume a lane by hand on Windows"
---

# Worktree lanes

The [`CLAUDE.md` `Lanes`](../../../CLAUDE.md) line runs every lane as a worktree, so building work starts with `lane open {slug}` from the main checkout, never inside the main checkout. The two repos a lane spans are in [repo layout](repo-layout.md).

## What `lane open` makes

- A code worktree at `../todoit-{slug}`. It is a sibling of the main checkout (`D:/dev/github/todoit-{slug}` beside `D:/dev/github/todoit`), not a subfolder, and it is detached at the main checkout's current `HEAD`.
- Inside it, a worktree of the scratch repo at `scratch/`, detached at scratch `main`.
- `receive.denyCurrentBranch updateInstead` in both repos' config. This setting lets `/end-lane` push into the main checkout while that checkout has the base branch checked out, so leave it set.
- Last, it starts `claude` in the new folder with `/begin-lane {slug}`, which puts both worktrees on `lane/{slug}`. `--no-launch` makes the worktrees and starts nothing.

The code worktree forks from the main checkout's `HEAD`, so put the main checkout on `develop` before running `lane open`. From any other branch, the lane forks from the wrong base.

Source: `open`, `worktreePath` and `begin` in the `lane-methodology` skill's `lane.mjs`, which the `lane` command on PATH runs. Observed with `lane open smoke-test --no-launch` on 2026-10-18.

## Removing and resuming a lane on Windows

On Windows, `lane remove {slug}` stops with `<path> is not a worktree of this repo` (exit 2), even for a worktree `lane open` made. `lane open {slug}` on an existing worktree stops with `exists but is not a worktree of this repo`. The cause is `lane.mjs` `isWorktreeOf`: it compares the backslash path that Node's `path.join` builds against the forward-slash paths that `git worktree list --porcelain` prints. Opening a new lane works. The upstream issue is `lane-remove-and-lane-open-reuse-fail-on` in claude-code-ref's `scratch/issues/`.

After `/end-lane`, remove the worktrees by hand from the main checkout:

```bash
git -C scratch worktree remove ../../todoit-{slug}/scratch
git worktree remove ../todoit-{slug}
```

`git -C scratch` resolves a relative path from `scratch/`, so the scratch worktree's path climbs two levels.

To resume a lane whose session closed, `cd ../todoit-{slug}` and start `claude` there.
