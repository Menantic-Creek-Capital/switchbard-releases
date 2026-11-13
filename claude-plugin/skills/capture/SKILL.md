---
name: capture
description: Add a task to tuile from a short description, or from what was just discussed.
argument-hint: "[what the task is]"
disable-model-invocation: true
---

# Capture a task

Turn the request into one tuile task.

Request: $ARGUMENTS

1. If the request is empty, take the task from the last thing the person and you agreed needs doing in this conversation.
   If there is nothing clear, ask for one sentence and stop.
2. Write:
   - a title under ten words, starting with a verb;
   - a description of one to three sentences saying why it matters, with any file, error or link from this conversation that the next agent will need;
   - one to three Definition of Done items, each a checkable outcome.
3. Create it with the tuile `create` tool (or `tuile create "Title" -d "Why" --dod "Outcome"`), in the repository of the current folder.
   Never guess a task prefix or another repository.
   If tuile says this folder has no workspace, ask before setting one up with `init --yes`.
4. Reply with the new ID and title on one line.
   Don't claim it, rank it or start the work unless the person asks: where it goes in the work order is their call.

If the tuile tools are not available, say tuile isn't installed or running and suggest `/tuile:setup`.
