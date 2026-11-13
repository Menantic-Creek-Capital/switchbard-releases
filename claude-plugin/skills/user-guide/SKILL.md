---
name: user-guide
description: The tuile user guide. Use when someone asks how tuile works or how to do something in it, such as installing it, adding or ordering tasks, handing work to an agent, answering the Inbox, editing Library pages, changing settings, using the tuile command, where tuile keeps data, or fixing a problem.
metadata:
  version: "1"
---

# tuile user guide

tuile is one place for a person's work and the AI agents doing it:
one ordered list of tasks across all their projects, agents that work on
those tasks, an Inbox where agents wait for answers, and a Library of the
project's docs. Everything stays on the person's computer.

Read only the page the question needs. Each page is short. Answer in the
guide's words and name the key or menu the person would use.

| Page | Read it for |
|---|---|
| [install](references/install.md) | Installing on a Mac or Linux, updates, uninstalling |
| [get-started](references/get-started.md) | The first run, a first task, a first agent |
| [the-window](references/the-window.md) | Pages and their keys, workspaces, panes, right-click |
| [tasks](references/tasks.md) | Adding tasks, the work order, task fields |
| [organise-tasks](references/organise-tasks.md) | The Tasks pane: workspaces, goals, projects, views, and which to use |
| [agents](references/agents.md) | The composer, agent conversations, Agents & jobs, choosing the AI |
| [inbox](references/inbox.md) | Answering questions, Later and Done, card keys |
| [analysis-case-study](references/analysis-case-study.md) | Creating a sales chart, answering its question and asking for a monthly table |
| [analysis-result](references/analysis-result.md) | The case study's final table as rendered HTML and inspectable source |
| [library](references/library.md) | Docs pages, editing, links, comments, `@tuile` writing |
| [git](references/git.md) | Pull requests, checks and merging |
| [pull-request-approval-case-study](references/pull-request-approval-case-study.md) | Connecting two GitHub labels to an Inbox card that approves a pull request |
| [settings](references/settings.md) | Settings sections, connections, sharing tasks, `settings.toml` |
| [command-line](references/command-line.md) | The `tuile` command for scripts and agents |
| [your-data](references/your-data.md) | What is stored where, what leaves the computer, backups |
| [troubleshooting](references/troubleshooting.md) | `tuile doctor`, logs, stuck agents, reporting a problem |

Without the skill installed, read a page with
`tuile skill show user-guide --topic <page>`, such as `--topic tasks`.

For anything the guide does not cover, `tuile --help` and
`tuile <command> --help` are the reference for the command line.
