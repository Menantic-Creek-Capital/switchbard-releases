---
summary: The first run, your first task and your first agent.
---

# Get started

## The first run

The first time you open tuile it asks three things.

1. **Set up this Mac.** tuile checks for the `tuile` command, Apple's command
   line tools and Pi, the agent it runs. **Set it up** adds what is missing.
   If everything is there, this step is skipped.
   It is also skipped on a Mac that has no Git, as long as Pi is there: a folder with no Git in it needs none of the three, and nothing is installed.
2. **Open your first workspace.** Choose a folder: a project's Git repository, or any folder you keep work in.
   **New folder…** makes one if you have none.
   tuile suggests a **task prefix** (three letters or digits, so
   `WEB` makes tasks `WEB-1`, `WEB-2`) and the **stages** a task moves
   through. New tasks start in the first stage. Change either now or later.
3. **Connect the AI you already use.** Pick a provider and sign in, or paste
   an API key. **Test** checks a key works.
   The common providers are cards, each with its own mark, under the names you know them by: **ChatGPT** for OpenAI and **Claude** for Anthropic.
   ChatGPT comes first: **Sign in with ChatGPT** opens OpenAI's page in your browser, and the sheet closes once you have signed in there.
   If the browser doesn't come back, press **The browser didn’t come back** and paste the address it ended on.
   Any other provider is behind **Other providers**, the last card, which opens a search over all of them.

tuile writes nothing into your repository during setup.
A three-stop tour then shows where to ask, where the AI's questions come back and where your tasks are listed.
Skip it if you like; Settings › General plays it again.

## Your first task

1. Go to **Tasks** and press **New task**, or press `t` then `n`.
2. Type a title, such as "Fix the login timeout", and press Enter.
3. Open the task and say what done looks like. Add each check to its
   **Definition of Done**.

## Hand it to an agent

Select the task and press `a`. An agent starts on it beside the list. It
reads the task, claims it so you can see who is on it, and writes its
progress back to the task as it goes.

Or type what you want in the composer at the bottom of any page, such as
"the export button does nothing on Safari", and press `⌘↵`. tuile files a task
from your words and starts an agent on it.

If no AI is connected yet, tuile says so and offers **Connect an AI**.
The middle of Home carries the same button until one is connected.
It opens the same screen as the first run; once one is connected, send again.

## When it needs you

An agent with a question or a result to review puts it in the
[Inbox](inbox.md). Answer there, read what it did, and move the task to Done
when you are satisfied.

## Next

- [Find your way around](the-window.md) the window.
- [Tasks](tasks.md) and [Agents](agents.md) in more depth.
