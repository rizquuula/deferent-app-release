# Deferent

Deferent is a desktop hub for Codex and Claude Code on Linux and macOS.
You chat with one hub. The hub plans the work and hands each task to a worker, on
this machine or on another machine over SSH. You watch every worker live from one window.

**[Download the latest version](https://github.com/rizquuula/deferent-app-release/releases/latest)**

This repo holds only the downloads. It has no source code.

## Features

- **Hub chat.** Answers stream in as the hub writes them. A "Thinking" timer shows how long the hub has been working.
- **Workers.** Run workers on this machine or over SSH. Watch each live transcript, and stop a worker at any time.
- **Pause and resume.** Workers pause when you quit, and the app offers to resume them on the next start.
- **Projects and sessions.** Keep a registry of your projects. Filter sessions by machine, project, and status.
- **Pickers.** Type `@` to pick a project, or `/` to pick a command.
- **Usage meters.** See your Claude plan usage, with the reset time and the time of the last refresh.
- **Update check.** The About screen tells you when a new version is out.

## Downloads

Deferent installers use these filenames. Earlier releases use the `ClaudePlay_` prefix.

| System | File |
|---|---|
| Linux, Debian or Ubuntu (x64) | `Deferent_<version>_amd64.deb` |
| Linux, other distributions (x64) | `Deferent_<version>_amd64.AppImage` |
| macOS, Apple Silicon | `Deferent_<version>_aarch64.dmg` |
| All | `SHA256SUMS.txt` |

## Requirements

- The CLI and account for the coding agent you choose, such as [Codex](https://developers.openai.com/codex/) or [Claude Code](https://code.claude.com).
- **Linux:** WebKitGTK 4.1, for example Debian 12 or later, or Ubuntu 22.04 or later.
- **macOS:** a Mac with Apple Silicon.
- **Remote workers (optional):** an SSH host alias in `~/.ssh/config` that logs in without a password, and a supported coding agent CLI on that host.

## Install

**Linux (.deb)**

```bash
sudo apt install ./Deferent_<version>_amd64.deb
```

**Linux (AppImage)**

```bash
chmod +x Deferent_<version>_amd64.AppImage
./Deferent_<version>_amd64.AppImage
```

**macOS (.dmg)**

Open the `.dmg`, then drag Deferent to Applications. From version 1.0.1, the app has a Developer ID signature and Apple notarization, so it opens with a normal double-click.

## Check the download

```bash
sha256sum -c SHA256SUMS.txt --ignore-missing
```

On macOS, use `shasum -a 256 -c SHA256SUMS.txt --ignore-missing`.

## First run

1. Deferent checks the CLI you choose, your login, your SSH hosts, and its data folder.
2. **The hub has its own login.** Follow the sign-in instructions for the hub CLI in First Run.
3. **Workers use your normal CLI setup** on the machine where they run.

## Updates

Open **About** (the ⓘ button in the title bar). Deferent checks this repo for a newer release. When an update is available, About can download and install it.

## Your data

Deferent keeps all its data on your machine:

| System | Folder |
|---|---|
| Linux | `~/.local/share/id.lyralabs.claudeplay/` |
| macOS | `~/Library/Application Support/id.lyralabs.claudeplay/` |

The folder holds the project registry, the sessions, the hub's own configuration, and the logs (`logs/`).
For more detail in the logs, start the app with `DEFERENT_LOG_LEVEL=debug`. Earlier releases use `CLAUDEPLAY_LOG_LEVEL`.

## Uninstall

- **Linux (.deb):** `sudo apt remove deferent`. For earlier releases, use `sudo apt remove claude-play`.
- **AppImage or macOS:** delete the app.
- **Data:** delete the data folder above.

---

© 2026 [Lyralabs ID](http://lyralabs.id). Not affiliated with Anthropic.
