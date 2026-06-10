# Changelog

All notable changes to this project are documented here.

This project adheres to [Semantic Versioning](https://semver.org/).

## [Unreleased]

### ⚠️ BREAKING CHANGES

- **Default state file renamed** from `.claude/delta-gate.state.local.json` to
  `.claude/delta-gate.state.local.worktree-specific.json`.

  The `worktree-specific` discriminant makes it explicit that this file, while
  local, must **not** be symlinked/centralized across worktrees (some tools —
  e.g. Conductor — symlink every `.claude/*local*` file to share config across
  worktrees; this state file must stay per-worktree).

  **Migration:** rename your existing state file, or simply delete it — a new one
  will be regenerated on the next run (the first run after deletion treats all
  matching diff files as changed). If you pinned the path explicitly via
  `--state-file`, no change is required.
