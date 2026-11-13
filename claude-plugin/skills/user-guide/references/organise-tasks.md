---
summary: What the Tasks pane holds, workspaces to views, and which one to use for what.
---

# How Tasks is organised

Your tasks live in workspaces and are grouped into projects.
Everything else on the Tasks page helps you look at them: which workspaces, which tasks, and how far along your bigger aims are.

The pane beside the task list, top to bottom:

| Row | What it is | What it shows at its end |
|---|---|---|
| **Goals** | Numbers you aim to hit each week | This week's progress, such as `2/3` |
| **Projects** | Your projects, each with the projects inside it, then **All projects** | Tasks done out of the total |
| **Views** | Your saved lists, numbered 1 to 9 | How many tasks each shows now |

Click a section's heading to fold it away.

**Coming soon:** projects inside projects, as this page describes them, replace initiatives.
Until your tuile has them, the pane shows **Initiatives** above one **Projects** row.
An initiative is a group of projects, and clicking it shows them; **Projects** shows every task under its project's heading.

## Workspaces: where tasks live

A workspace is a named group of folders you work on together, such as an app and its website; a folder you have not grouped is a workspace of its own.
Each task belongs to one folder, and its ID starts with that folder's prefix, such as `WEB-12`.

The picker beside the view's name at the top of the page reads **All workspaces**, one workspace's name, or a count such as **3 workspaces**.
Click it and tick the workspaces you want this page to show.
Click a workspace's colour square there to change its colour; views in the pane wear the squares of the workspaces their tasks are in.

## Goals: what you're aiming at this week

A goal is a number to reach each week, such as three releases.
Click a goal to see the tasks that count toward it.
Make one with `tuile goal create`, or ask an agent to.

## Projects: work with an end

A project groups the tasks of one piece of work, and it is done when they are.
Coming soon, a project can also hold projects: "Launch the beta" can hold "Window polish" and "Docs", and its progress counts all their tasks.
You'll pick a project's parent under **Parent project** in its settings, click a project to see its tasks, and click **All projects** to see every task under its project's heading.

Drag a task onto a heading to move it into that project.
Milestones split a project into ordered steps.

## Views: your saved lists

A view is a saved way of looking at tasks: which ones show, their order, the columns, the outline and the row colours.
No task belongs to a view: a view shows whichever tasks match it, so one task can show in many views, and deleting a view deletes no tasks.
A view with no tasks right now leaves the pane until it has some, unless it's the one open; it stays in the views menu.

### Switch views

- Click the view in the pane.
- Or press `v`, then the view's number.
- Or click the view's name at the top of the page.

### Change a view

Filter, sort or rearrange the list from the bar at the top of the page.
A dot after the view's name in the pane means it has changes you haven't saved.

- **Update**, at the top of the page, keeps them in this view.
- **Reset** drops them.
- **Save New…**, in the **Filter** panel, keeps them as a new view instead.

### Make, rename, move or delete one

- **Make:** click **+** beside **Tasks** at the top of the pane, then name it.
  It starts as the view on screen, with nothing filtered out.
- **Rename:** double-click it.
- **Move:** drag it up or down; its number changes with its place.
- **Delete:** right-click it, then **Delete**; first **Update** or **Reset** any unsaved changes.

## Which to use

The three that get mixed up:

| | A task belongs to | Use it for |
|---|---|---|
| Workspace | Exactly one | Where the work's files are |
| Project | One at most | A piece of work that will finish |
| View | None: a view shows whichever tasks match it | A question you ask often |

Make a view for each question you ask often, such as "what's next?" or "what's waiting on someone?", not one per project.
Keep three to five, in the order you use them, and each is two keys away: `v` and its number.

| You want to | Use |
|---|---|
| See only one repository's tasks | The workspace picker |
| See what's next across everything | A view sorted by your order |
| See everything in one piece of work | Its project |
| Track a number week by week | A goal |
| Group projects under one aim | A project that holds them |
| Take a quick, one-off look | Type in the filter field, then **Reset** |
