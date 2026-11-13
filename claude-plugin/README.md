# tuile for Claude Code

[tuile](https://tuile.dev) keeps one ordered list of your work across every project, hands tasks to Claude Code, and keeps each task's notes and Definition of Done after the chat ends.
This plugin connects Claude Code to it.

## Install

In Claude Code:

```
/plugin marketplace add tuilehq/releases
/plugin install tuile@tuile
```

## What you get

| Command | What it does |
| --- | --- |
| `/tuile:setup` | Checks that tuile is installed and connected, and says what to do next |
| `/tuile:capture [what]` | Turns a sentence, or what you just discussed, into a task with a Definition of Done |
| `/tuile:next` | Shows your next ready tasks in your own order, and offers to start the first |
| `/tuile:handoff [task]` | Writes this session's progress and next steps back to the task |

Claude can also use every tuile command as a tool, and it reads tuile's user guide when you ask how something works.

## Setup

tuile is a free Mac app (Apple silicon).
Download it from [tuile.dev/download](https://tuile.dev/download), drag it to Applications, open it once and click **Set it up**.
Then restart Claude Code and run `/tuile:setup`.

## License

This plugin is MIT licensed ([LICENSE](LICENSE)).
The tuile app it connects to has its own license, which comes with the download.

Your tasks stay on your Mac.
The plugin changes no Claude Code settings; `tuile harness install --agent claude` adds tuile's claim hooks and status line if you want them.
