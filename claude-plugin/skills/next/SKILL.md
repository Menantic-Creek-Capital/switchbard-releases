---
name: next
description: Show the next ready tasks in the person's tuile work order and offer to start the first.
disable-model-invocation: true
---

# What's next

Show what the person has said comes next, in their order.

1. Read the person's work order with the tuile `order` tool (`tuile order`): one line a task, across all their projects, top first.
   Read which tasks are ready (nothing blocking them, not done) with `list` and `--ready`, in each repository the order names.
   Walk the order and keep the ready ones, in that order.
   Never re-rank, re-sort or reorder tasks, and never suggest a different order unless asked.
2. Show at most five, one line each: ID, title, and a status or claim only if it matters (someone is already on it, or it is waiting on the person).
3. For the first unclaimed one, read it with the `view` tool and say in one sentence what doing it would involve.
4. Ask whether to start it.
   If the person says yes, claim it first (`work claim`), read its notes and Definition of Done, then begin.

If tuile says this folder has no workspace, say that `/tuile:next` works inside a project tuile manages, and that opening tuile here (or the window's Add project) sets one up.
If nothing is ready, say so and offer `/tuile:capture`.
If the tuile tools are not available, suggest `/tuile:setup`.
