---
summary: Use tuile from a terminal, a script or an agent with the tuile command.
---

# The tuile command

`tuile` is how scripts and agents use tuile. Run it with no
arguments inside a repository to open tuile's terminal app.

`tuile --help` lists every command, and `tuile <command> --help` explains one.
The help is the reference: it is generated from the same code that runs.

## Tasks

```sh
tuile create "Add a search filter"           # prints the new ID, e.g. WEB-13
tuile list --ready                           # tasks with nothing blocking them
tuile view WEB-13                            # one task in full
tuile edit WEB-13 --status "In Progress"
tuile edit WEB-13 --dod "Search works with an empty query"
tuile edit WEB-13 --append-notes "Filter added; tests pass."
tuile rank task WEB-13 --top                 # first in your order
```

A task ID works from any folder. Most commands take `--json` for output a
script can read.

## Agents

An agent claims a task before it starts and releases it when it hands back.
The claim is what shows you who is on what.

```sh
tuile work claim WEB-13
tuile work release WEB-13
```

`tuile skill install --agent all` teaches Claude Code, Codex and Pi to do this
on their own. `tuile mcp` offers every command as a tool to any agent that
speaks the Model Context Protocol. It runs locally and opens no port.

## Everything else

| Command | What it does |
|---|---|
| `tuile doctor` | Checks your setup and changes nothing |
| `tuile wiki` | Reads and edits the Library |
| `tuile form` | Publishes a question to the Inbox |
| `tuile pr` | Reads and merges pull requests |
| `tuile wait` | Waits for checks or for your answer, with a timeout |
| `tuile jobs` | Manages scheduled jobs |
| `tuile share` | Exports and imports task lists |
| `tuile paths` | Prints where settings and logs live |
| `tuile stats` | Summarizes what you used, what was slow and what failed |

## Read this guide from a terminal

```sh
tuile skill show user-guide               # the page list
tuile skill show user-guide --topic tasks # one page
```
