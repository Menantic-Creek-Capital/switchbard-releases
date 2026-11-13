---
summary: "A worked example: have GitHub label the pull requests that need you, then approve them from the Inbox, which adds a second label your checks wait for."
---

# Approve pull requests from the Inbox with a GitHub label

This case study connects two GitHub labels to an Inbox card, so you approve a risky pull request without leaving your work.
GitHub puts the first label on a pull request that needs you; **Approve** on its Inbox card adds the second, and your checks let it merge.

The example uses `needs-approval` and `approved`, on changes to an `infra/`, `migrations/` or `.github/` folder.
Use your own labels and folders.

## How the two labels work together

GitHub adds the first label and you add the second.

| Label | Who adds it | What it means |
|---|---|---|
| `needs-approval` | A GitHub workflow, when a pull request changes a folder you chose | This change waits for you |
| `approved` | You, with **Approve** on the Inbox card | You have seen it; let it merge |

tuile only looks for the first label and adds the second.
Which changes need you, and what your approval allows, are decided by your repository's own workflow.

## What you need

You need a GitHub repository you can add a workflow to, and the GitHub CLI signed in on your computer.

- **A workspace** whose folder is that repository.
- **The [GitHub CLI](https://cli.github.com/)**, signed in with `gh auth login` to an account that may label pull requests there. tuile adds the label through that sign-in.
- **Permission on GitHub** to merge a workflow into the main branch and to change the branch's rules.

## 1. Have GitHub label and hold the pull requests that need you

Add this workflow to the repository as `.github/workflows/approval.yml`, and merge it into your main branch.
It labels a pull request that changes one of the folders, and reports an **Approval** status that stays pending until the pull request also carries `approved`.

```yaml
name: Approval

on:
  pull_request_target:
    types: [opened, reopened, ready_for_review, synchronize, labeled, unlabeled]

permissions:
  contents: read
  pull-requests: write
  statuses: write

concurrency: approval-${{ github.event.pull_request.number }}

jobs:
  approval:
    runs-on: ubuntu-latest
    env:
      GH_TOKEN: ${{ github.token }}
      GH_REPO: ${{ github.repository }}
      PR: ${{ github.event.pull_request.number }}
      HEAD: ${{ github.event.pull_request.head.sha }}
    steps:
      - name: Label a change that needs approval
        run: |
          set -euo pipefail
          count="$(gh api "repos/$GH_REPO/pulls/$PR" --jq '.changed_files')"
          files="$(gh api "repos/$GH_REPO/pulls/$PR/files" --paginate \
            --jq '.[] | .filename, (.previous_filename // empty)')"
          # GitHub lists at most 3,000 files, so a larger change needs approval too.
          if (( count >= 3000 )) || grep -qE '^(infra|migrations|\.github)/' <<<"$files"; then
            gh label create needs-approval --color d73a4a --force
            gh label create approved --color 0e8a16 --force
            gh pr edit "$PR" --add-label needs-approval
          fi

      - name: Report whether it may merge
        run: |
          set -euo pipefail
          labels="$(gh pr view "$PR" --json labels --jq '.labels[].name')"
          state=success
          description="No approval needed"
          if grep -qxF needs-approval <<<"$labels"; then
            description="Approved"
            if ! grep -qxF approved <<<"$labels"; then
              state=pending
              description="Waiting for the approved label"
            fi
          fi
          gh api "repos/$GH_REPO/statuses/$HEAD" \
            -f state="$state" -f context=Approval -f description="$description"
```

Then try it and make it required:

1. Open a test pull request that changes one of the folders. It gets the `needs-approval` label and a pending **Approval** status.
2. In the repository's **Settings** on GitHub, under **Rules** › **Rulesets**, add a rule for your main branch that requires the **Approval** status check. GitHub offers a check there once it has reported at least once.
3. Confirm the test pull request can no longer merge.

Without that rule the status shows as pending but nothing stops the merge.

Two details keep a pull request from approving itself:

- **`pull_request_target`** runs the workflow as it is on your main branch, so a pull request cannot edit the check that judges it. The workflow never checks out or runs the pull request's code; keep it that way.
- **`.github/` is one of the folders**, so a change to the workflow itself needs you too.

Treat the workflow as a starting point, and change the folders in the `grep` line to your own.

## 2. Tell tuile which labels to use

In **Settings**, add two settings to the workspace: the label to look for and the label to add.

1. Open **Settings** from the sidebar, or press `g9`, and choose **Workspaces**.
2. Click **View** beside the workspace, then open **Advanced**.
3. In the empty row at the end of the list, enter the key `approval_needed_label` and the value `needs-approval`, then click **Add**.
4. Add a second setting the same way: the key `approval_label`, the value `approved`, then **Add**.

From a terminal in the workspace's folder, the same two settings are:

```sh
tuile workspace-settings set approval_needed_label needs-approval
tuile workspace-settings set approval_label approved
```

Each workspace keeps its own pair, so two repositories can use different labels.
Set both: with only one, tuile looks for or adds a label your workflow does not use.

## 3. Approve from the Inbox

Click **Approve** on the pull request's card, or press `1`; you have a few seconds to undo.

The card appears in **Inbox** a minute or two after GitHub labels a pull request, with the pull request's number and title.

1. To read the change first, click **Open on GitHub**, or press `2`.
2. Click **Approve**, or press `1`.
3. To take it back, click **Undo** at the foot of the window before it goes away.

When the undo runs out, tuile adds `approved` to the pull request on GitHub.
The card leaves, the workflow runs again and reports **Approval** as passed, and the pull request can merge.

Draft pull requests get no card until they are ready for review.
**Later** and **Dismiss** put the card away without approving anything.

## When an approval is refused

If the pull request changed after its card appeared, tuile refuses the approval and says why at the foot of the window.
It reads the pull request again before adding the label, so you approve the change you saw; a refusal writes nothing to GitHub.

| What happened since the card appeared | What to do |
|---|---|
| New commits were pushed | The card now shows them: look again, then **Approve** |
| It was merged or closed | Nothing: there is nothing left to approve |
| It went back to draft | Approve it once it is ready for review again |
| The `needs-approval` label was removed | Nothing: it no longer waits on you |

## What the label does and does not prove

- **tuile gives agents no way to approve.** Only the **Approve** button adds the label; no `tuile` command or agent tool does.
- **GitHub does not record why a label is there.** Anyone with write access to the repository can add `approved` on GitHub itself, and so can an agent or script that uses your GitHub sign-in. Limit that access if the approval must be yours alone.
- **Once you approve, later pushes are approved too.** The label stays on the pull request when new commits arrive after your approval.

See [Inbox](inbox.md) for the rest of a card's keys and [Git](git.md) for merging.
