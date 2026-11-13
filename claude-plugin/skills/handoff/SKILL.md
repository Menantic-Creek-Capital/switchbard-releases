---
name: handoff
description: Write this session's progress back to its tuile task, so the next session or person can pick up without this chat.
argument-hint: "[task ID]"
disable-model-invocation: true
---

# Hand off

Record where the work stands on its task, so it survives this conversation.

Task: $ARGUMENTS

1. Find the task: the ID given, else the one `work list` shows claimed by this session (match its session id, never another session's claim), else ask which task, and stop.
2. Read it with `view` first: its notes, Definition of Done and verification checks.
3. Append one progress note with `edit` and `--append-notes`: what changed, what was tried and didn't work, and anything the next session must know.
   Name files and commands, not chat history.
4. Set `--next` to at most three one-line actions, rewritten whole.
5. If a pull request or branch exists, record it in the task's Git fields as the task-workspace skill describes, reading the old value first.
6. Don't tick Definition of Done items, record verification results or mark the task Done: a reviewer or the person decides that.
   Release the claim only if the person says this session is handing the task back.
7. Reply with the ID and a two-sentence summary of what you recorded.

If tuile says this folder has no workspace, ask which project and task, and pass that repository with `--repo`.
If the tuile tools are not available, suggest `/tuile:setup`.
