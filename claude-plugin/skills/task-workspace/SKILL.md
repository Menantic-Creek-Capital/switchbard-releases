---
name: task-workspace
description: Use the tuile CLI or MCP tools to manage a tuile workspace's tasks, claims, verification and delivery. Apply when tuile (once called Switchbard or sbt), one of its task IDs, or a tuile-managed repository is involved.
---

# tuile

`tuile` is the task write path. Bare `tuile` opens the terminal app; subcommands and
MCP tools use the same native behavior. `sb` and the external `backlog` CLI are
retired. Never edit task Markdown or storage databases directly. This skill
grants no additional authority.

Use documented commands directly. Read specific `--help` only for an unfamiliar
operation, compatibility concern or syntax error; reuse help already read, and
let the installed CLI win over stale instructions. Load only the reference for
the current workflow. Without installed reference files, read the same text with
`tuile skill show --topic <name>`.

## Ordinary task work

```sh
tuile --repo <DIR> view <ID>
tuile --repo <DIR> list
tuile --repo <DIR> create "Title" -d "Why" --dod "Checkable outcome"
tuile --repo <DIR> edit <ID> --append-notes "Progress and remaining work"
```

Read the task and its notes before changing it; newer notes may correct its
original description. Preserve intent, plans and existing evidence. Create tasks
when asked, keep the returned ID, and use `--repo` for the intended workspace.
Never assume a task prefix.

A problem you notice outside your current task gets filed, not fixed: create a
task whose description says where you found it, with a checkable `--dod`, name
the new ID in your reply and carry on. Fix it in place only when it blocks the
task you are on.

Claim before editing using the actual session and long-lived PID. Keep the claim
through progress replies, questions, pauses and sign-in waits. Release last,
after delivery or an explicit handback; a released claim does not mean Done.
Pi subagents work under their parent's ownership and never claim tasks.
For harness-specific identity or `/tuile-execute`, read
[setup-and-harness](references/setup-and-harness.md).

The universal order belongs to the owner. Never rank or reorder tasks unless
asked. Planning, status, due dates, snooze and dispatch permission are separate.
For projects, milestones, planning or snooze, read
[tasks-and-planning](references/tasks-and-planning.md).

## Verification and handoff

Check only requirements actually proved. Add Verification checks linked to the
DoD, attach proof as work proceeds, and leave results to a reviewer, the owner or
the check runner. A session holding the claim cannot pass its own checks. A linked
DoD item stays unchecked until its checks pass or do not apply.

Testing is the normal agent handoff; use In Review when human judgment is needed.
Older workspaces may use In Review for both. Handing back is how the owner hears
of finished work: `tuile work release` on a task in Testing or In Review, or a
turn that ends holding one, puts it in their Inbox as ready for review, with the
final summary and the `prs` field. So set both first, and never end with work
waiting on the owner while the task still says In Progress. Checking the last obligation can
advance to that handoff, never directly to Done. A completion timer does not prove
acceptance, and delivery, review, landing and installation remain separate facts.

Before code work or closeout, read
[code-and-delivery](references/code-and-delivery.md) for isolated worktrees,
background landing, Git evidence and future-validation splits. Keep `--next` to
three one-line actions and `--final-summary` to three plain sentences. Put full
hashes and actual PR URLs in stock Git fields, read before replacing them, and
verify the task's JSON readback. Never move unfinished delivery, failed tests or
required review to a follow-up just to finish the source task.

## Conditional workflows

| When needed | Read, or use its name with `tuile skill show --topic` |
| --- | --- |
| Readiness, installation, harness identity, Pi execution | [setup-and-harness](references/setup-and-harness.md) |
| Code work, worktrees, verification, delivery, future validation | [code-and-delivery](references/code-and-delivery.md) |
| Projects, milestones, planning, snooze, DoD versus legacy AC | [tasks-and-planning](references/tasks-and-planning.md) |
| GitHub waits, timers, owner questions and Inbox responses | [waiting-and-inbox](references/waiting-and-inbox.md) |
| Charts, datasets, metrics or the owner's connected apps | [analysis-and-apps](references/analysis-and-apps.md) |
| Older storage, migration or command compatibility | [storage-and-compatibility](references/storage-and-compatibility.md) |
