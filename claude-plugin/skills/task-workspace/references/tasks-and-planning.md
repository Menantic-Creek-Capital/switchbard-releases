# Task structure and planning

## Projects, milestones, order

For a new board, use `tuile project apply --help`: after authorized `init`, one JSON plan creates the project, milestones, tasks, local-key dependencies and initial planning atomically. Pass `--file <PATH>` or `--file -` for stdin. Read the returned key-to-ID mapping. On an uncertain outcome, inspect the named project before retrying; an existing project is refused. This requires central storage and never migrates an existing board.

A project exists the moment a task names it (`-m`); `project create` with the same name adopts the members. Rollups are computed from member tasks. Projects have no delete verb: `archive` sets Canceled, `complete` sets Completed. `tuile --repo <DIR> --view-preset project` (TUI `v b`) opens the built-in Project view; `project naming --help` covers milestone numbering, and `create --no-prefix` keeps a title literal.

Planning is separate from status: tasks start `Considering` (the icebox); `planning set <ID> Planned` commits them and `planning rank` orders the Planned tier. The **universal order** is the one cross-repo ranking, owner-set only: `rank task <repo:ID> --top|--bottom|--before|--after` when the owner asks, never on your own initiative. `expedite`, `unrank` and `rank project` are removed. When the backlog has outgrown throughput, follow `docs/playbooks/backlog-reset.md` in the switchbard repo.

## Snooze

A per-task wake time, separate from status, due date and rank: `snooze <ID> --until <RFC 3339 with offset>`, `wake <ID>`, `create --snoozed-until`. Choose the time the missing evidence is expected, and record the basis in notes. Until then default lists and dispatch skip the task; `view`, `list --snoozed` and the TUI `snoozed:yes|any` filter still show it. Wake restores eligibility only: no status change, no dispatch permission, no completion. Never substitute a due date or Waiting status.

## Command details

- Run bulk loops under `bash -c`: zsh does not word-split, so `for id in $ids` passes the whole list as one id. Check every exit status; `while read` drops a final line without a newline.
- `create` has no `--ref` (set with `edit --ref`, which replaces the whole list); `list` has no label, assignee or priority filter, so filter TSV columns with `awk -F'\t'`.
- New requirements use `create --dod` or `edit --dod`; `--ac` is an append alias that also writes DoD. `--check-dod`/`--uncheck-dod` and `--edit-dod`/`--remove-dod` target DoD only. Legacy `--check-ac`/`--uncheck-ac` and `--edit-ac`/`--remove-ac` target existing AC only, never fall back to DoD. Removals cannot combine with check/uncheck toggles on the same list; run them separately. Text edits may combine atomically with checks, with edits applied before toggles.
- Every DoD and legacy AC item counts toward progress, review and unfinished-work handback. Checking the final obligation can move an open task to Testing (In Review in older workspaces or with Testing handoffs disabled), never Done. Testing is the normal agent handoff for observation and checks; use In Review when a human review or decision is needed. A configured status timer may later move an eligible task to Done; do not claim that elapsed time proves a check passed. `pare --keep-dod` (or `--keep-ac` for legacy AC) retains the selected list's requirements and leaves the other list untouched.
- Set a task's project before completing it. Weekly goals, order and all records live in central storage, never in git-tracked files.
