# ClaudePlay

ClaudePlay is a desktop hub for your Claude Code work, on Linux and macOS.
You chat with one hub. The hub plans the work and hands each task to a Claude Code worker, on
this machine or on another machine over SSH. You watch every worker live from one window.

**[Download the latest version](https://github.com/rizquuula/claudeplay-app-release/releases/latest)**

This repo holds only the downloads. It has no source code.

## Features

- **Hub chat.** Answers stream in while Claude writes them. A "Thinking" timer runs while Claude thinks.
- **Workers.** Run Claude Code workers on this machine or over SSH. Watch each live transcript, and stop a worker at any time.
- **Pause and resume.** Workers pause when you quit, and the app offers to resume them on the next start.
- **Projects and sessions.** Keep a registry of your projects. Filter sessions by machine, project, and status.
- **Pickers.** Type `@` to pick a project, or `/` to pick a command.
- **Usage meters.** See your Claude plan usage, with the reset time and the time of the last refresh.
- **Update check.** The About screen tells you when a new version is out.

## Downloads

Each release has these files:

| System | File |
|---|---|
| Linux, Debian or Ubuntu (x64) | `ClaudePlay_<version>_amd64.deb` |
| Linux, other distributions (x64) | `ClaudePlay_<version>_amd64.AppImage` |
| macOS, Apple Silicon | `ClaudePlay_<version>_aarch64.dmg` |
| All | `SHA256SUMS.txt` |

## Requirements

- The [Claude Code CLI](https://code.claude.com), installed and on your machine.
- Your own Claude account. ClaudePlay uses your own login and never sees your password.
- **Linux:** WebKitGTK 4.1, for example Debian 12 or later, or Ubuntu 22.04 or later.
- **macOS:** a Mac with Apple Silicon.
- **Remote workers (optional):** an SSH host alias in `~/.ssh/config` that logs in without a password, and the Claude Code CLI on that host.

## Install

**Linux (.deb)**

```bash
sudo apt install ./ClaudePlay_<version>_amd64.deb
```

**Linux (AppImage)**

```bash
chmod +x ClaudePlay_<version>_amd64.AppImage
./ClaudePlay_<version>_amd64.AppImage
```

**macOS (.dmg)**

1. Open the `.dmg`, then drag ClaudePlay to Applications.
2. The app is not signed yet. To open it the first time, right-click ClaudePlay in Applications and choose **Open**. You can also run this command:

```bash
xattr -dr com.apple.quarantine /Applications/ClaudePlay.app
```

## Check the download

```bash
sha256sum -c SHA256SUMS.txt --ignore-missing
```

On macOS, use `shasum -a 256 -c SHA256SUMS.txt --ignore-missing`.

## First run

1. ClaudePlay checks your machine: the Claude Code CLI, your login, your SSH hosts, and its data folder.
2. **The hub has its own login.** Click **Sign in** on the "Hub signed in" row, then sign in on the page that opens in your browser. The hub keeps its own settings and does not load your personal `~/.claude` setup.
3. **Workers use your normal Claude Code setup,** including your skills and your `CLAUDE.md` files.

## Updates

Open **About** (the ⓘ button in the title bar). ClaudePlay checks this repo for a newer release. If one exists, the button opens its download page.

## Your data

ClaudePlay keeps all its data on your machine:

| System | Folder |
|---|---|
| Linux | `~/.local/share/id.lyralabs.claudeplay/` |
| macOS | `~/Library/Application Support/id.lyralabs.claudeplay/` |

The folder holds the project registry, the sessions, the hub's own Claude config, and the logs (`logs/`).
For more detail in the logs, start the app with `CLAUDEPLAY_LOG_LEVEL=debug`. The logs never contain your login token or your email address.

## Uninstall

- **Linux (.deb):** `sudo apt remove claude-play`
- **AppImage or macOS:** delete the app.
- **Data:** delete the data folder above.

---

© 2026 [Lyralabs ID](http://lyralabs.id). Not affiliated with Anthropic.
