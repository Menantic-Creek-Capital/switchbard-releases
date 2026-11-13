---
summary: Answer agents' questions, review what they made, and clear what is waiting on you.
---

# Inbox

When an agent needs a decision, an answer or a review, it waits in the Inbox.

## One card at a time

The Inbox shows one card at a time, most urgent first: questions whose agent
will stop waiting soonest, then agents blocked on you, then everything else.
If an agent said how long it will wait, the card shows the time left and what
the agent will do without you.

## Answer

A card offers the answers the agent expects as buttons. Pick one, or type
your own reply and press **Send**. The agent gets it at once and carries on.
Questions survive restarts, so an answer you give tomorrow still arrives.

Optional questions have **Skip**. **Answer in chat** opens the agent's
conversation instead.

A picture on a card opens all the card's pictures together; ‹ › or the arrow keys step between them.
Click a spot to circle it or drag to box an area, and write a note for each mark.
When you close the pictures, the marked ones and their notes go with your answer.

## Review work an agent handed back

When an agent hands a task back for review, the task waits here with a card that says "Ready for your review".
The card names what the agent did and links its pull requests.

- **Write a reply** to ask for changes. The agent picks the task back up, and its next handback brings a new card.
- **Done** (`e`) clears the card without changing the task's status. The agent does not ask about that task again.
- **Open the task** shows the task and its pull requests.

A task never has two review cards waiting.
A task still in progress sends nothing, and neither does an agent still waiting on work it started in the background.
Work that has already landed sends nothing either: it needs nothing more from you.

A review request about a pull request waits until there is something to try.
It comes into the Inbox once the pull request merges and, for this app, once the build you run has it.
Until then it is in no list and counts toward nothing.

## Approve a pull request

A pull request that carries the label you chose for "needs me" waits here as a card with its number and title.
**Approve** (`1`) adds your approval label on GitHub after a few seconds to undo; **Open on GitHub** (`2`) shows the change first.
Which two labels those are is a setting of each workspace: [Approve pull requests from the Inbox with a GitHub label](pull-request-approval-case-study.md) sets it up from start to finish.

## Clear or set aside

| Key | Action |
|---|---|
| `z` | **Later**: back in an hour, tomorrow at nine, or next Monday at nine |
| `e` | **Done**: clear it for good, unanswered |
| `m` | Move it onto a task |
| `h` | Hand it to an agent |
| `←` `→` | Previous or next card |

On a trackpad, swipe a card left for Later and right for Done. Each of these
can be undone for a few seconds from the line at the foot of the window.

The open icon in a card's header opens the task, page or pull request it is
about.

## Where it shows

The Inbox page (`g5`) lists what is waiting, grouped by workspace, with past
items after them.
A card leaves once you answer or clear it, wherever you did, and the next waiting card takes its place.
A past item shows again only when you pick its row. When an agent needs you, its card also floats over the page
you are on, so you can answer without leaving your work. **Keep beside the
page** docks it as a pane.

For a system notification as well, turn on Settings › General › Notify me
when an agent needs me.

## From a terminal

Agents publish questions with `tuile form`. In the terminal app, `u` opens the
Inbox from any page.
