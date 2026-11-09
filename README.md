# Switchbard downloads

Switchbard is a local-first terminal workspace for tasks, pull requests, and coding agents.
This repository hosts official binary downloads and the public issue tracker. Product source is private.

## Downloads

**Switchbard for Mac:** download the latest `.dmg` from
[Releases](https://github.com/Menantic-Creek-Capital/switchbard-releases/releases/latest), open it and drag
Switchbard into Applications. It is signed and notarized, and updates itself. Apple Silicon only for now.

**Terminal (`sbt`):** releases through **v0.4.0-alpha.4** have been withdrawn. Installation instructions
will be published with the next terminal release.

## Existing installations

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

[Report a problem](https://github.com/Menantic-Creek-Capital/switchbard-releases/issues) with your `sbt build-id`,
OS, terminal, and reproduction steps. Review diagnostics before sharing; they may contain local paths
or task content. In-app bug capture creates a local task and does not post a GitHub issue.

## Licensing

The withdrawn historical releases, through **v0.4.0-alpha.4**, were published under MIT.
The [historical MIT notice](LICENSE-MIT) remains available for existing copies.

Official builds are free to download and use, for personal or commercial work, on any number of your
own devices, under [LICENSE-OFFICIAL-BUILDS](LICENSE-OFFICIAL-BUILDS). They may not be redistributed,
modified or resold. The product source is private and is not licensed.

The installer and documentation in this distribution repository have the separate limited permissions
in [LICENSE](LICENSE). GitHub's automatically generated source archives contain only this distribution
repository, not the Switchbard product source.
