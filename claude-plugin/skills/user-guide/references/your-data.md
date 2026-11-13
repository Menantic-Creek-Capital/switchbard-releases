---
summary: What tuile stores, where it lives, and what leaves your computer.
---

# Your data

tuile needs no account. Your tasks, settings and logs stay on your computer.

## Where it lives

Everything tuile keeps is in `~/.tuile`:

| What | Where |
|---|---|
| Tasks, projects and your work order | One database shared by all your workspaces |
| Settings | `settings.toml` |
| Agent conversations' files | `sessions/` |
| Scheduled jobs | `jobs.toml` and `jobs/` |
| Logs | `logs/`, the last ten runs or two weeks, at most 256 MB |

`tuile paths` prints the exact locations. Library pages are the exception: they
are files in your own repository.

tuile writes into your repositories only the files you edit through it, such
as Library pages, and the work agents do there.

## What leaves your computer

tuile itself sends nothing anywhere. It has no analytics and no cloud service.
Data leaves only when you use something that needs the network:

| When you | tuile talks to |
|---|---|
| Use an agent | The AI provider you connected, as that agent always does |
| Use the Git page | GitHub, through your `gh` sign-in |
| Connect an app, such as Slack | That app, with the access you grant |
| Run the Mac app | GitHub's release page, every four hours, to check for updates |

tuile records which actions you use and how long they take, so you can see what
is slow with `tuile stats`. That record stays in `~/.tuile` and is never
uploaded.

## Back up and move

Back up the task database while tuile is running with:

```sh
tuile storage backup --file ~/Backups/tuile.sqlite3
```

`tuile storage restore` brings a backup back. To send a set of tasks to another
person or computer, export them from Settings › Import & export.
