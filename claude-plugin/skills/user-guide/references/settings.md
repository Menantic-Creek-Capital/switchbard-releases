---
summary: What each Settings section changes, and the settings file.
---

# Settings

Open Settings from the sidebar (`g9`). Each change saves as you make it.

| Section | What you change there |
|---|---|
| Appearance | Light, dark or system mode, palette, corners, motion, row spacing, the Dock icon |
| General | Notifications, merge method, automatic completion, the tour |
| Workspaces | Which folders tuile tracks, and their colours |
| Panes | How panes split and what opens from the title bar |
| Pages | Which pages the sidebar shows |
| Keys | Every key, rebindable |
| Prompts | The instructions the Library's writing agent follows |
| Connections | The apps and accounts agents may use, with your notes for each |
| Models | Which model new Pi chats and agents run on |
| Import & export | Task lists to send to someone, or to bring in |
| About | Your version and build |

## Connections

A connection is an app or account an agent can use, such as Gmail or a
calendar. Add notes to it, like "archive, never delete" or "new events are
blue". An agent reads them before it first uses that connection, and adds
to them as it learns your preferences.

## Models

**Models** has two choices, and both lists show the models Pi is signed in to.
Sign in to more under **Connections**.

- **Default model** is what a new Pi chat or agent starts on.
  **Pi’s default** leaves the choice to Pi.
  A chat that is already running keeps the model it started with.
- **Subagent model** is what a subagent runs on when the agent that starts it names no model.
  **Same as the session** leaves it as it is.
  It applies the next time a chat is started or continued.

## Share a task list

**Import & export** saves a workspace's open tasks, one project's tasks or
the ones you pick as a `.tasklist` file. Sign-ins, connections, chats,
history and your work order never go in. Importing shows exactly what will be
added before anything changes, and new tasks get IDs from your workspace.

```sh
tuile share export launch.tasklist --in-project Launch
tuile share import launch.tasklist   # a preview; nothing is written yet
```

## The settings file

Every setting lives in `~/.tuile/settings.toml`, which the window and
the terminal app both read. You can edit it by hand. For example:

```toml
[global]
agent_harness = "pi"            # claude, codex or pi
hide_statuses = ["Done"]
notify_agents = true
agent_idle_stop_minutes = 30    # 0 never stops an idle agent
agent_max_running = 16          # chat agents running at once, 1 to 64
outside_answer_wait_minutes = 60  # 0 hands an unread answer to a new agent at once
auto_clean_database_copies = true  # delete tuile's older copies of the database
database_copies_kept = 2        # how many it keeps, 1 to 50
```
