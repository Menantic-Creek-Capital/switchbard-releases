---
summary: Your project's docs as pages you and agents read, edit and discuss.
---

# Library

The Library (`g8`) turns a repository's docs folder into pages you can read,
edit, link and discuss. The pages stay ordinary Markdown files in your
repository, so Git is their history and your docs site publishes the same
files. This guide is a Library.

## Where pages come from

tuile reads the folder your docs site publishes: `docs_dir` from
`zensical.toml` or `mkdocs.yml`, otherwise `docs/`. Every `.md` file in it is
a page. A folder's `index.md` is the folder's own page, and the pages inside
it nest under it. A repository with no docs folder gets one when you create
its first page.

## Edit

Pages are always formatted. Click anywhere and type: there is no edit mode
and no save button. tuile saves as you type, and a save never overwrites a
newer change made elsewhere. Saved pages are uncommitted changes in your
repository; commit them like any other file.

Select words for the formatting toolbar: bold, italic, code, colour, lists,
links, comments and reactions.

## Link

Links are ordinary relative Markdown links, such as `install.md` or
`../index.md#start-here`. A link to a page that does not exist offers to
create it. Each page lists the pages that link to it.

## Discuss

Select text and choose **Comment**, or press `⌘⇧M`. Reply, then **Resolve**
when you are done. Comments are kept on your computer, beside the page
rather than in it, and never appear on a published site.

## Ask an agent to write

Start a line with `@tuile` and say what to write, such as "fill in the Linux
install steps", then press Enter. The agent writes into the page as you
watch. You can keep editing elsewhere in the page meanwhile.

- `Esc` or **Stop** stops it and keeps what it wrote.
- `⌘Z` takes all of it back out.
- Every request is filed as a task, so you can see what was asked and when.

The agent can read your repository's files but can change only the place it
is writing. You can also start a comment with `@tuile` to ask for a change to
that passage.

## Page facts

A page can start with front matter that the Library shows as a card:

```yaml
---
summary: One line on what the page is for.
status: current    # draft, current or outdated
owner: Sam
covers:
  - src/billing/
---
```

When the page last changed, and who changed it, comes from Git. If a path the
page `covers` changes after the page did, the card says so, which tells you
the page may be out of date.

## Agent context

Under the pages, each repository has a folder of its agent context: the
`AGENTS.md`, `CLAUDE.md`, skills and settings that agents read there, each
with when it last changed. Edit them here like any page.

## From a terminal

```sh
tuile wiki list                 # every page as a tree
tuile wiki show guide/tasks.md  # one page
tuile wiki search "work order"  # find pages
```

`tuile wiki --help` lists the commands for creating, editing, moving and
deleting pages.
