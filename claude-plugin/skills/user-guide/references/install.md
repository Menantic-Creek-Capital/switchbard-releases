---
summary: Install tuile on a Mac, or build it on Linux.
---

# Install

## Mac

tuile runs on Macs with Apple silicon.
It is free to download and use, for personal or commercial work.

1. Download [the newest tuile for Mac](https://github.com/tuilehq/releases/releases/latest/download/tuile-macos-arm64.dmg).
   Earlier versions are on [releases](https://github.com/tuilehq/releases/releases).
2. Open it and drag **Tuile** to Applications.
3. Open Tuile from Applications.

The app is signed and notarized by Apple, so it opens without a warning. It
updates itself: it checks for a new version every four hours, downloads it in
the background, and installs it when you click **Update ready** or next quit.

The app brings everything it needs, including the `tuile` command. On first
open it offers to set up what your Mac is missing; see
[Get started](get-started.md).

## Linux

There is no Linux download yet. You can build the `tuile` command and the
desktop window from source if you have access to the source repository.
You need Git, a C compiler, tmux, [rustup](https://rustup.rs) and, for the window, Node 24.
Clone the repository you were given, then run these from its folder:

```sh
cargo build --locked --release -p app-tui
mkdir -p ~/.local/bin
install -m 755 target/release/tuile ~/.local/bin/tuile
tuile --version
```

Make sure `~/.local/bin` is on your `PATH`. That is the whole terminal app.
For the window, run `npm ci` and then `npm run app` in `web/desktop`; the
repository's `docs/INSTALL-LINUX.md` lists the system libraries it needs.

## Optional extras

| For | Install |
|---|---|
| The Git page and pull requests | The [GitHub CLI](https://cli.github.com/), then run `gh auth login` |
| Claude Code or Codex as your agent | The agent itself, signed in as usual |

tuile never asks for your GitHub password and keeps no GitHub token of its own.
It uses the `gh` sign-in you already have.

## Uninstall

Drag **tuile** from Applications to the Bin. Your tasks and settings stay
in `~/.tuile`; delete that folder too if you want them gone. See
[Your data](your-data.md).
