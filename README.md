# Switchbard downloads

Switchbard is a local-first terminal workspace for tasks, pull requests, and coding agents.
This repository hosts official binary downloads and the public issue tracker. Product source is private.

## Install

The current public release is **v0.4.0-alpha.4**. It includes `sbt` and the compatible `sb` command
for macOS Apple Silicon, macOS Intel, and Linux x86_64. No Rust, Node, or Python installation is needed.
Windows and Linux ARM binaries are not available.

```sh
installer=$(mktemp)
curl -fsSL https://raw.githubusercontent.com/benpchandler/switchbard-releases/main/install-release.sh -o "$installer"
bash "$installer" --version v0.4.0-alpha.4
rm -f "$installer"
```

The installer checks the archive's SHA-256 checksum and installs into `~/.local/bin`.
If needed, add that directory to your PATH. To replace an existing installation, add `--replace`.
These are alpha builds; they are not signed or notarized, and public installations do not update automatically.

[All downloads and release notes](https://github.com/benpchandler/switchbard-releases/releases)

## First use

From your project directory, run:

```sh
sbt doctor
sbt
```

Switchbard explains setup before creating a workspace. GitHub features require an authenticated
GitHub CLI (`gh`). Agent integrations use your existing agent tools and subscriptions.
The agent side pane requires tmux. Installation does not install these tools or sign you in.

In the app, press `?` for help, `u` for Inbox, `i` to capture an idea, and `b` to capture a bug.
Use `sbt agent-prompt` for a setup prompt to give your agent. Optional agent instructions can be
installed with `sbt skill install --agent both`.

## Backups and support

Before upgrading, back up important task data:

```sh
sbt --repo /path/to/project storage backup --file /path/to/backup.sqlite3
```

[Report a problem](https://github.com/benpchandler/switchbard-releases/issues) with your `sbt build-id`,
OS, terminal, and reproduction steps. Review diagnostics before sharing; they may contain local paths
or task content. In-app bug capture creates a local task and does not post a GitHub issue.

## Licensing

The historical releases hosted here, through **v0.4.0-alpha.4**, were published under MIT.
Their binary archives and original license notices are unchanged. See [the historical MIT license](LICENSE-MIT).
The older v0.1.1, v0.2.0, and v0.3.0 GUI builds are retained for reference; the desktop GUI is deprecated.

Future product versions use restrictive proprietary terms. Always check the license included with the
specific release; downloading a file does not grant permission beyond those terms.
The installer and documentation in this distribution repository have the separate limited permissions
in [LICENSE](LICENSE). GitHub's automatically generated source archives contain only this distribution
repository, not the Switchbard product source.
