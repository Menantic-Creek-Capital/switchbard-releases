# Analysis and connected apps

## Put a chart on the owner's Home

A chart is SQL over a registered SQLite file, never code. Register the file (`analysis dataset add <NAME> <FILE>`), define what the number means once as a metric over a model so other charts reuse it (`analysis model add <MODEL> --dataset <NAME> --from <TABLE|SELECT>`, `analysis metric add <METRIC> --expr "sum({field})" -d "What it means"`), then `analysis sheet add <SHEET> --workbook <DASHBOARD> --model <MODEL> --metric <METRIC> --by <GROUPING> --chart line|bar|number`, or `--dataset <NAME> --sql <SELECT>` for a one-off. Check it with `analysis run <SHEET>`; Home in tuile and in the desktop window shows new sheets within seconds. To ask the owner about charts you filed, set the question's `open` to `analysis/<worksheet>` so its card opens them. Data that needs collecting gets a scheduled job naming its file, so the chart says when it was last and will next be refreshed: `jobs add <NAME> --description "..." --schedule "every 1h" --refreshes <FILE> -- <ARGV>`. `analysis code refresh` collects the lines each commit added and removed into `~/.tuile/code.sqlite3`.

## Build a metric the owner asks for

When the owner asks for a new measure, such as how long agents wait, first say in one line what it counts and what it divides by, using names that say what they are (`wait_on_user_review_hours`, not `owner_wait`).
Find the tables with `analysis source` and `analysis model view`, and prototype the SELECT as a one-off sheet run with `analysis run` before you save a model.
Sanity-check the result's units: hours in one week across parallel tasks can exceed 168, but millions mean a bug.
In SQLite, `strftime` returns text, and text sorts after every integer, so `CAST(strftime(...) AS INTEGER)` before comparing it with a timestamp column.
Clip intervals that began before the window to the window, and count each stretch of time from one source only, or the same hour is added twice.
Then save the model, one metric per number with a one-sentence description, and a sheet, and show the owner the SQL and one week's numbers.
The Friction workbook's agent wait model (`tuile analysis model view friction_agent_time`) is a worked example.

## Change a widget the owner points at

A request that starts with `Widget: <Title> (<sheet>), on the <worksheet> worksheet` came from notes the owner pinned on that widget with Analysis's pencil: the lines after it say what it draws and from what, so start from them rather than searching. Read it with `analysis sheet view <SHEET>`, change only what was asked with `analysis sheet edit <SHEET>` (flags you leave out keep their values; a metric or model change affects every sheet that uses it, so say which), and run it with `analysis run <SHEET>` before you answer. Report what the chart shows now in a sentence. The window draws `table`, `line`, `bar`, `number` and `calendar` only: for any other kind, say so instead of approximating it.

## Use the owner's accounts and apps

Before a job that needs one of the owner's apps, such as email, ask `tuile apps lookup <JOB>` (`--account <ADDRESS>` for one account) and use the app and account it returns; never pick your own. With no row, or an app you can't reach, tell the owner rather than working around it.
