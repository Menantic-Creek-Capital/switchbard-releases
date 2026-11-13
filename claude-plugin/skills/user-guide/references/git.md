---
summary: See your pull requests and their checks, and merge them with a confirmation.
---

# Git

The Git page (`g3`) lists your repositories' pull requests: their checks,
reviews and whether they can merge. It opens on open pull requests. Sort,
filter and search work as they do on Tasks, and you can save views.

The page needs the [GitHub CLI](https://cli.github.com/), signed in with
`gh auth login`. tuile uses that sign-in and keeps no token of its own.

## Merge

Select a pull request and press `m`, or press **Merge**. tuile checks it with
GitHub first and shows what will happen: the repository, the branches, the
account you are signed in as, and anything GitHub warns about. Nothing merges
until you confirm.

Choose squash, merge commit or rebase, whichever the repository allows, and
confirm. The list stays usable while it merges, and the result appears when
GitHub confirms it.

If you always merge the same way, tick **Always use this method** to skip the
choice for clean merges. Undo that in Settings › General.

A pull request that can't merge, such as a draft, one with conflicts or one
blocked by checks or reviews, says why when you hover **Merge**.

## From a terminal

```sh
tuile pr list                  # recent pull requests, as JSON
tuile pr checks 42             # checks, reviews and whether it can merge
tuile pr merge 42              # preview a merge; add --confirm to do it
tuile wait pr 42 --until checks-settled --timeout 30m
```

`tuile wait` lets a script or agent wait for checks to finish without polling.
It exits 0 when they settle and 2 on timeout.
