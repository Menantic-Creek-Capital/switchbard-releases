---
name: setup
description: Check that tuile is installed and connected to Claude Code, and say what to do next.
disable-model-invocation: true
---

# Set up tuile

Check whether this Claude Code can reach tuile, then tell the person, in a few plain sentences, what works and the one next step.

1. Call the tuile `doctor` tool.
   If the tuile tools are missing or fail to start, run `"${CLAUDE_PLUGIN_ROOT}/bin/find-cli" --version` instead.
2. If tuile is not installed, say what it is in two sentences:
   tuile is a free Mac app that keeps one ordered list of your work across projects, hands tasks to Claude Code, and collects agents' questions in one Inbox; everything stays on your Mac.
   Then give the steps: download it from https://tuile.dev/download (Macs with Apple silicon), drag it to Applications, open it once and click **Set it up**, then restart Claude Code.
   Stop there.
3. If tuile is installed, summarize what `doctor` reported in at most five lines, problems first.
   If the current folder is a Git repository that tuile does not manage yet, say that opening tuile in it (`tuile` in a terminal here, or the window's Add project) sets it up.
4. Mention, once, that `tuile harness install --agent claude` adds tuile's claim hooks and status line to Claude Code's user settings, so the Agents page shows this session.
   Never run it yourself: it changes the person's settings, so only they decide.

Don't install, change or create anything in this skill.
