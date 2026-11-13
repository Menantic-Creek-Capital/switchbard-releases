# Code work and delivery

## Start an isolated task worktree

For repositories using the integration-base policy, `tuile --repo <DIR> worktree base` prints the selected local branch. The owner selects it once with `worktree base <LOCAL-BRANCH>`; agents must not change it to bypass a failure. `tuile --repo <DIR> worktree create <NEW-BRANCH> --json` returns `{branch, base, base_commit, path}` from its exact tip; omit `--json` for path-only stdout. The default is `<primary-parent>/.worktrees/<repo-name>/<branch>`; `--path` overrides the location, not the base. Missing policy/base and occupied branches/paths refuse. No fetch, checkout switch, task claim, queue submission, installation or completion is implied. Claim the task from the returned worktree before editing. Existing worktrees stay untouched; this command alone does not block raw Git or legacy dispatch creation. Land finished, committed work with `tuile --repo <DIR> worktree land <BRANCH> [--json]`: it waits for earlier landings, takes any commits `origin/<base>` has that the base lacks, merges onto the exact base tip, runs the owner's `worktree check` command, advances the base only on success (stdout is the new base commit) and pushes it. As an agent, land with `--background` instead (stdout is the state file) and follow it with `tuile --repo <DIR> worktree landing <BRANCH> --wait`, a command of its own given at least 16 minutes, until it reads `landed`: the queue can take longer than your commands may run, and a landing left running in your own shell dies when you stop. Never report work landed while it reads `queued`, `failed` or `interrupted`. Conflicts or a failed check change nothing; merge the base (and `origin/<base>` when the refusal names it) into the task branch, resolve there, and land again: a branch that already holds origin's tip lands with its own resolution. Never move the base by hand, and never ask the owner to reconcile it. Verify availability with `tuile worktree --help` before using an older binary.

## Record delivery evidence

Every repository has stock text fields `branch`, `prs` and `commits`; no field declaration is needed.
Before completing code work, record actual PR URLs (when a PR exists) and full commit
hashes or commit URLs, then verify with `tuile view <ID> --json` (`custom.prs` /
`custom.commits`). Both `create` and `edit` accept:

```sh
tuile edit <ID> --set "branch=sbt-42-deliver" --set "prs=https://github.com/OWNER/REPO/pull/42" --set "commits=FULL_SHA FULL_SHA:landing"
```

Tag the commit that landed on the base with `:landing`. `tuile view` then shows
Landed, Pushed and Installed, read from git each time, so never write those
facts into notes or the summary.

Multiple entries are space-separated text. `--set` replaces the entire field:
read first and preserve existing evidence. Use `--unset prs` / `--unset commits`
only to remove incorrect evidence. Never invent a PR, store "none" as a link, or
treat a recorded hash as proof of acceptance, landing, pushing or deployment.
For local integration delivery, leave `prs` unset and explain "no PR: local
integration workflow" in notes; record implementation and landing commits.
Documentation/non-code tasks need no fabricated delivery fields. Keep acceptance
results and remaining limitations in notes / Final Summary, not in these fields.

## Next Steps and the Final Summary

```sh
tuile edit <ID> --next "Rebase onto the base" --next "Land it"   # replaces the list
tuile edit <ID> --clear-next                                      # nothing left to do
```

Next Steps holds at most three one-line actions, nothing else. The Final Summary
is at most three plain sentences on what shipped. tuile refuses hashes, PR or
commit links, file paths, session ids and test counts in both, and says which
field takes them instead.

## Verification

```sh
tuile verify add <ID> --group intent "Contract names the proof per DoD item" --dod 1
tuile verify add <ID> --group e2e "Journey drives the window through real keys" --dod 2
tuile verify proof <ID> 2 crates/tui/tests/my_journey.rs
```

Write the intent checks before code, one per DoD item, naming the proof each
needs. Attach proof as you go. Results (`tuile verify record <ID> <N> --result
pass|fail|n/a --as gate|reviewer|owner`) are recorded by someone other than
the session holding the claim; tuile refuses yours. A DoD item linked to a check
can't be checked until that check passes or does not apply.

## Split delivered work from future validation

Only when delivery is proved and what remains is an independent later observation, never for failed tests, unfinished requirements or pending review. Steps, each a separate write, resumable without duplicates:

1. Classify every unchecked criterion (unfinished delivery, future validation, inapplicable conditional) in the source notes with reasons. Delivery and required acceptance stay on the source.
2. Reuse an existing linked follow-up (`list --all`, source notes) or create a **top-level** one carrying the source's project, labels and context plus the exact obligation, evidence expected, owner, failure action and wake time. No `dispatch` label.
3. Note on the source each moved criterion's number and text, the follow-up id and the evidence; add the reciprocal reference. Then `edit --edit-dod` / `--remove-dod` (numbers are pre-edit; removal renumbers, so read back between numbered edits). For an existing legacy AC section only, use `--edit-ac` / `--remove-ac`. Never check a transferred criterion.
4. Complete the source only when retained criteria are met; its Final Summary names the follow-up and the unverified outcome. Report delivery credit separately from pending validation. Inspect all remaining work before completing a project.
