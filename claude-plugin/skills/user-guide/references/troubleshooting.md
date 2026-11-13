---
summary: Check your setup, find the logs, undo a recent change and report a problem.
---

# Troubleshooting

## Check your setup

```sh
tuile doctor            # agents, tmux, skills and what agents load here
tuile doctor --github   # also checks your GitHub sign-in
```

`tuile doctor` changes nothing. It ends with a numbered list of what to fix
first. It also warns when a repository loads an unusually large amount of
instructions into every agent session.

## An agent is stuck

**Agents & jobs** marks an agent **Trouble** when its reply failed, it has
written nothing for 15 minutes, or its context is nearly full. Open it and
read its last words, send it a message to steer it, or press **Stop**.

## The window will not respond

If tuile's background process doesn't answer within ten seconds of quitting,
the window offers **Quit anyway**. Running agents keep going and reconnect
the next time you open tuile.

## Logs

Each time you open the window, tuile starts a folder in `~/.tuile/logs/`.

| File | Holds |
|---|---|
| `host.jsonl` | Failed or slow requests, crashes, and each agent's start and end |
| `window.jsonl` | What the window saw happen to itself |
| `agents/<agent>.log` | An agent's error output |

`tuile stats` summarizes recent failures and slow actions, the newest first.

## Report a problem

Open an issue at
[tuilehq/releases](https://github.com/tuilehq/releases/issues).
Include the output of `tuile build-id`, what you did, and what happened.
If you attach a log folder, read it first: it can name your tasks and
folders.
