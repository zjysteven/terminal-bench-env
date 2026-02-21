# TermiGen Environments for Harbor

This repository adapts the [TermiGen terminal-bench-env](https://github.com/ucsb-mlsec/terminal-bench-env) dataset for integration with [Harbor](https://github.com/laude-institute/harbor).

For the original dataset, paper, model, and BashAgent, please refer to the upstream repository: https://github.com/ucsb-mlsec/terminal-bench-env

---

## What's in this repo

- `environments_harbor/` -- 3,566 tasks in Harbor 2.0 format, ready to use with `harbor run`.
- `bash_agent.py` -- Minimal ReAct-style agent (from upstream).

---

## Changes from the original `termigen_env_harbor2.zip`

The `environments_harbor/` directory is derived from the upstream `termigen_env_harbor2.zip` with one systematic change: **`.git` directories inside task environments have been renamed to `dot_git`** so they can be tracked by this Git repository. The corresponding Dockerfiles have been updated to `COPY` from `dot_git/` instead of `.git/` (container-side destination paths remain `.git/`, so built images are functionally identical).

### Affected tasks (13 out of 3,566)

| Task | Renamed path(s) |
|------|-----------------|
| `diff_whitespace_only_changes_medium` | `environment/.git` |
| `git_detached_head_recovery_hard` | `environment/project_repo/.git` |
| `git_detached_head_recovery_medium` | `environment/project/.git` |
| `git_merge_conflict_binary_hard` | `environment/home/user/project-repo/.git` |
| `git_merge_conflict_binary_medium` | `environment/repo/.git` |
| `git_rebase_interactive_conflict_medium` | `environment/calculator/.git` |
| `git_rebase_interactive_squash_hard` | `environment/messy-repo/.git` |
| `git_reflog_expire_lost_commits_hard` | `environment/repo/.git` |
| `git_reflog_expire_lost_commits_medium` | `environment/.git` |
| `git_reflog_history_recovery_hard` | `environment/project-repo/.git` |
| `git_reflog_history_recovery_medium` | `environment/workspace/payment-service/.git` |
| `git_submodule_sync_mismatch_medium` | `environment/workspace/project/.git` and `environment/workspace/project/lib/shared/.git` |

All other 3,553 tasks are identical to the upstream archive.

---