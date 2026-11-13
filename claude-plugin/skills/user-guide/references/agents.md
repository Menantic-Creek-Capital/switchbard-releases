---
summary: Ask for work, follow agents while they work, and choose which AI does it.
---

# Agents

An agent works on one task at a time. It reads the task, claims it so you
can see who is on it, and writes its progress back to the task. You can
start one from a task, from the composer, or from a terminal.

## Ask for work

Type a request in the composer at the bottom of any page. Add what it is
about:

- **Tasks:** type `@` and pick one, or drag a task row onto the composer.
- **Pictures:** paste, drop, or press **Picture**.

Then send it.

| Key | What happens |
|---|---|
| `↵` | Send it. The chat opens in the middle of Home and its agent starts. |
| `⌥↵` | Start it in the background. Follow it on Agents & jobs. |
| `⌘↵` | File it as a task. No agent starts. |
| `⇧↵` | New line. |

The send button shows the key it will answer to, so holding `⌥` or `⌘` says what happens before you press `↵`.
`⌘↵` takes words only: a request with tasks or pictures attached goes with `↵`.

With no task attached, tuile files one from your first line, named as a short
action ("the export button does nothing" becomes **Fix export button**).
With several tasks attached, each gets its own agent.

## Start from a task

Select a task and press `a`. Its agent opens in a pane beside the list. If
none is running, one starts.

## Talk to an agent

The conversation shows replies as they stream in, with each tool the agent
used and its result.

- Type while it works to steer it. `↵` sends at its next step.
- `⌥↵` queues a message for when it is done.
- **Stop** ends the current run. The conversation stays.
- `Esc` puts the conversation away. The agent keeps working.
- **Resolve** ends the agent and closes the conversation for good. Its
  history stays with the task.

A message the agent has not read yet shows above the composer with **Edit**,
**Cancel** and **Send now**.

## See who is working

When an agent is working, it shows at the top of the window. Click it to
open its conversation.

**Agents & jobs** lists the agent sessions in your workspaces, including
Claude Code and Codex sessions you started yourself in a terminal. Each says where it
stands:

| State | Meaning |
|---|---|
| Waiting on you | It asked a question and is paused for the answer |
| Failed | Its last reply failed, it stopped moving, or it was cut off partway |
| Ready for review | It finished and left work for you to look at: a pull request, commits or edits |
| Working | In the middle of a turn |
| Not started | It waits for its turn to start |
| Done | It finished and nothing is left to look at, or its work was merged |
| Stopped | It ended or went quiet without finishing; it can be continued |

A run reads the same seven states.
Where a state has a narrower word, it follows the state: "Waiting on you · Question open", "Done · Merged", "Working · PR queued".

A task an agent hands back for review also waits in the [Inbox](inbox.md#review-work-an-agent-handed-back).

The same page has **Scheduled**, for jobs that run on a timer, and
**History**, for past runs.

## Let an agent drive the window

An agent you start from the window can see the page you are on, change the
list you are looking at, and open pages for you. Ask it "show me what is in
review" and it filters Tasks.

## Where agents keep files

Each conversation gets a dated folder in `~/.tuile/sessions/`, such as
`2026-11-09-fix-safari-export`. The agent works in its `scratch` folder and
moves a file to `deliverables` only after you approve it. New versions sit
beside old ones (`plan.v2.md`) instead of replacing them.

## Choose the AI

tuile's agents run on Pi, which works with the provider you already use:
Anthropic, OpenAI, Google and others. You connect one during the first run.
An idle conversation stops its agent after 30 minutes to free memory; your
next message picks it up where it left off.

You can use Claude Code or Codex instead. Set `agent_harness` to `claude`,
`codex` or `pi` in `~/.tuile/settings.toml`. Claude Code and Codex run
in a terminal pane rather than a chat.

## Teach your own agent about tuile

If you run Claude Code, Codex or Pi yourself, install tuile's skills so they
know how to read and update tasks:

```sh
tuile skill install --agent all
```

This writes skill files to each agent's personal skills folder. It adds no
hooks and stores no credentials.
