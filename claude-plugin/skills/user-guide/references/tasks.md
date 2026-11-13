---
summary: Add tasks, put them in order, organize them into projects and finish them.
---

# Tasks

A task is one piece of work: a title, what done looks like, and everything
learned along the way. It is what you hand an agent, and where the agent
reports back.

## Add a task

- On **Tasks**, press **New**, then **Task**, or `t` then `n`.
- In the composer, describe the work and send it. tuile files a task from your
  words.
- From a terminal: `tuile create "Fix the login timeout"`.

Each task gets an ID from its workspace's prefix, such as `WEB-12`. The ID
never changes, even if the task moves.

## Your order

All your tasks, across every workspace, sit in one order that only you set.
Status, priority and due dates never reorder it, and agents leave it alone
unless you ask. The top of the list is what comes next.

Move a task from a terminal, or ask an agent to:

```sh
tuile rank task WEB-12 --top
tuile rank task WEB-12 --after WEB-7
```

## What a task holds

Open a task to see its detail. Click any field to edit it in place.

| Field | Use it for |
|---|---|
| Status | Where the task is, from the workspace's stages |
| Definition of Done | The checks that must pass before it is done |
| Waiting on | Who or what it is blocked by |
| Depends on | Tasks that must finish first |
| Project and milestone | The larger piece of work it belongs to |
| Priority, due date, labels | Your own signals; none of them change the order |
| Notes and final summary | What the agent did and found |

A checked Definition of Done, a merged pull request and a finished agent are
separate facts. None of them moves a task to Done on its own. If you want
tasks in Testing or In Review to become Done after a delay, set it in
Settings › Tasks › Automatic completion.

## Projects and views

Projects group tasks into larger pieces of work; views are saved ways of looking at tasks.
[How Tasks is organised](organise-tasks.md) explains both, with workspaces and goals, and which to use when.

## Several at once

Shift-click selects a range, and `⌘`-click adds or removes one row. Right-click
the selection to act on all of it.

## Set aside or drop

- To set a task aside, give it a date in its Detail's **Snoozed until**; it leaves your views until then.
- **Cancel task…** (`t`, then `c`) drops a task you won't do.
- **Move to completed…** (`t`, then `m`) takes a Done task out of the open list.
