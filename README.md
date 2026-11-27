# Deferent

Deferent is a desktop hub for AI coding agents such as Codex and Claude Code.
Chat with a Hub that plans work and hands tasks to Workers in your projects.
Workers run locally or over SSH, and you can follow their live transcripts from one window.

**[Download the latest release](https://github.com/rizquuula/deferent-app-release/releases/latest)**

[![Release asset downloads](https://img.shields.io/github/downloads/rizquuula/deferent-app-release/total?label=release%20asset%20downloads&logo=github&color=2f6fbb)](https://github.com/rizquuula/deferent-app-release/releases)

GitHub counts each release file download, including installers, update files, and checksums.

## Features

- **Hub chat.** Read replies as they stream. Type `@` to pick a project or `/` to pick an available command.
- **Workers.** Follow live transcripts, stop running Workers, and resume their sessions. Deferent offers to resume paused Workers when you reopen the app.
- **Projects and sessions.** Keep a registry of your projects and filter sessions by machine, project, and status. See each Worker’s context usage when its harness reports it. Starting with v2.0.3, it also appears on the Worker’s card in the Hub’s Sessions sidebar.
- **Machine Settings.** Choose a default Worker harness for each machine and save settings for each harness. Projects can follow the machine default or pin a supported harness.
- **Usage meters.** See account usage limits and reset times when available for the active Codex or Claude Code Hub.

## Downloads

Choose an installer under **Assets** on the latest release page. Earlier releases use the `ClaudePlay_` prefix.

| System | File |
| --- | --- |
| Linux x64, Debian or Ubuntu | `Deferent_<version>_amd64.deb` |
| Linux x64, AppImage | `Deferent_<version>_amd64.AppImage` |
| macOS, Apple Silicon | `Deferent_<version>_aarch64.dmg` |
| Windows 11 x64, starting with v2.0.3 | `Deferent_<version>_x64-setup.exe` |

Download `SHA256SUMS.txt` from the same release to verify the installer. In the command examples, replace `<version>` with the version in your filename.

## Requirements

- **Coding CLI.** Install the CLI for your chosen harness on your `PATH` and have an account for it. On Linux and macOS, you can use the [Codex CLI](https://learn.chatgpt.com/docs/codex/cli) or [Claude Code CLI](https://code.claude.com/docs/en/overview).
- **Linux.** Use a recent x64 distribution, such as Debian 12 or Ubuntu 22.04 or newer. The `.deb` package requires WebKitGTK 4.1. The AppImage may need FUSE support on your system.
- **Windows 11 x64.** Use native `codex.exe` on your `PATH` for the local Hub and Workers.
- **Remote Workers (optional).** Configure an SSH alias in `~/.ssh/config` that connects without an interactive prompt. Install and sign in to the selected Worker CLI on the remote machine. For Windows SSH hosts, use native Claude Code (`claude.exe`) and an OpenSSH server with PowerShell as its default shell.

## Check the download

Save `SHA256SUMS.txt` alongside the installer and run the command for your system in that folder.

**Linux**

```bash
sha256sum -c SHA256SUMS.txt --ignore-missing
```

**macOS**

```bash
shasum -a 256 -c SHA256SUMS.txt --ignore-missing
```

**Windows (PowerShell)**

```powershell
Get-FileHash -Algorithm SHA256 -LiteralPath '.\Deferent_<version>_x64-setup.exe'
```

On Windows, compare the returned hash with the entry for that installer in `SHA256SUMS.txt`.

## Install

For the Linux commands, open a terminal in the folder where you saved the installer.

**Linux (.deb)**

```bash
sudo apt install "./Deferent_<version>_amd64.deb"
```

**Linux (AppImage)**

```bash
chmod +x "Deferent_<version>_amd64.AppImage"
"./Deferent_<version>_amd64.AppImage"
```

**macOS (.dmg)**

Open the `.dmg` and drag Deferent to Applications. The app has a Developer ID signature and Apple notarization starting with v1.0.1.

**Windows (NSIS .exe)**

Run `Deferent_<version>_x64-setup.exe` to install Deferent for your Windows account. If Microsoft Edge Evergreen WebView2 is missing, setup downloads it from Microsoft and requires internet access. The installer has no Windows publisher signature, so SmartScreen may warn. Deferent verifies a separate signature for in-app updates.

## First run

1. Choose the Hub harness and the default for local Workers. On Windows, choose Codex for both.
2. Follow the Hub sign-in instructions in **First Run**. The Hub has its own sign-in. On Windows, run the sign-in command in PowerShell.
3. Workers use your normal CLI setup on the machine where they run. Use **Machine Settings** to choose the Worker harness for each SSH host.

## Updates

Open **About** (the ⓘ button in the title bar) to check for, download, and install updates. See the [release notes](https://github.com/rizquuula/deferent-app-release/releases) for changes in each version.

## Your data

Deferent stores your project registry, sessions, Hub configuration, and logs (`logs/`) in its app data folder.

| System | Folder |
| --- | --- |
| Linux | `~/.local/share/id.lyralabs.claudeplay/` by default, or `$XDG_DATA_HOME/id.lyralabs.claudeplay/` if set |
| macOS | `~/Library/Application Support/id.lyralabs.deferent/` |
| Windows | `%APPDATA%\id.lyralabs.claudeplay` |

On macOS, quit the older app before upgrading. Starting with v2.0.1, Deferent moves the previous data folder on first launch, keeps a private backup, and leaves a link at the old path. Keep the backup and link in place while using the upgraded app.

For more detail in the logs, start the app with `DEFERENT_LOG_LEVEL=debug`. Earlier releases use `CLAUDEPLAY_LOG_LEVEL`.

## Uninstall

- **Linux (.deb).** Run `sudo apt remove deferent`. For earlier releases, use `sudo apt remove claude-play`.
- **Linux (AppImage).** Delete the AppImage file.
- **macOS.** Move Deferent from Applications to the Trash.
- **Windows.** Open **Settings → Apps → Installed apps**, find **Deferent**, and choose **Uninstall**.
- **App data.** To remove your Deferent settings and session history, quit the app and delete its data folder listed above.

---

© 2026 [Lyralabs ID](https://lyralabs.id/). Not affiliated with Anthropic.
