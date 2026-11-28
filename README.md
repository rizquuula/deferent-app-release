# Deferent

Deferent is a desktop hub for AI coding agents such as Codex and Claude Code.
Chat with a Hub that plans work and hands tasks to Workers in your projects.
Workers run locally or over SSH, and you can follow their live transcripts from one window.

**[Download the latest release](https://github.com/rizquuula/deferent-app-release/releases/latest)**

[![Release asset downloads](https://img.shields.io/github/downloads/rizquuula/deferent-app-release/total?label=release%20asset%20downloads&logo=github&color=2f6fbb)](https://github.com/rizquuula/deferent-app-release/releases)

GitHub counts each release file download, including installers, update files, and checksums.

## Features

- **Hub chat.** Read replies as they stream. Type `@` to pick a project or `/` to pick an available command. Messages sent while the Hub is busy queue and run one at a time.
- **File previews.** Zoom images in Hub previews and select **Fit** to return to the fitted view. Hover over a previewable file link or focus it with the keyboard to see its filename.
- **Workers.** Follow live transcripts, stop running Workers, and resume their sessions. Deferent offers to resume paused Workers when you reopen the app.
- **Projects and sessions.** Keep a registry of your projects and filter sessions by machine, project, and status. See context usage in each Worker session and on its card in the Hub’s Sessions sidebar when the harness reports it.
- **Machine Settings.** Choose a default Worker harness for each machine and save settings for each harness. Projects can follow the machine default or pin a supported harness.
- **Usage meters.** See account usage limits and reset times when available for the active Codex or Claude Code Hub. With fresh usage data, the Codex Hub estimates when a quota will run out if the current window’s average pace would exhaust it before reset.
- **[Web access](#web-access).** Open Deferent in a paired browser while the desktop app is running.

## Downloads

Choose an installer under **Assets** on the [Deferent v2.0.5 release page](https://github.com/rizquuula/deferent-app-release/releases/tag/v2.0.5). Older ClaudePlay releases use the `ClaudePlay_` prefix.

| System | File |
| --- | --- |
| Linux x64, Debian or Ubuntu | `Deferent_2.0.5_amd64.deb` |
| Linux x64, AppImage | `Deferent_2.0.5_amd64.AppImage` |
| macOS, Apple Silicon | `Deferent_2.0.5_aarch64.dmg` |
| Windows 11 x64 | `Deferent_2.0.5_x64-setup.exe` |

Download `SHA256SUMS.txt` from the same release to verify the installer.

## Requirements

- **macOS and Linux desktop.** Install the [Codex CLI](https://learn.chatgpt.com/docs/cli) or [Claude Code CLI](https://code.claude.com/docs/en/setup) and make `codex` or `claude` available on your `PATH`. Both are supported for the Hub and local Workers. The Hub also offers OpenCode, OpenCode v2, Pi, and OhMyPi as experimental choices.
- **Linux packages.** Use a recent x64 distribution, such as Debian 12 or Ubuntu 22.04 or newer. The `.deb` package requires WebKitGTK 4.1. The AppImage may need FUSE support on your system.
- **Windows desktop.** Use native `codex.exe` on your `PATH` for the Hub and local Workers.
- **SSH Workers (optional).** Add an SSH alias in `~/.ssh/config` on the desktop machine and make sure you can connect without an interactive prompt. Install and sign in to the selected CLI on the SSH host. Linux and macOS SSH hosts can run Codex or Claude Code Workers. Windows SSH hosts run Claude Code Workers only and need native `claude.exe` and an OpenSSH server with PowerShell as its default shell.

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
Get-FileHash -Algorithm SHA256 -LiteralPath '.\Deferent_2.0.5_x64-setup.exe'
```

The Linux and macOS commands should report `OK` for your installer. On Windows, the returned hash must match the entry for that installer in `SHA256SUMS.txt`.

## Install

For the Linux commands, open a terminal in the folder where you saved the installer.

**Linux (.deb)**

```bash
sudo apt install "./Deferent_2.0.5_amd64.deb"
```

**Linux (AppImage)**

```bash
chmod +x "Deferent_2.0.5_amd64.AppImage"
"./Deferent_2.0.5_amd64.AppImage"
```

**macOS (.dmg)**

Open the `.dmg` and drag Deferent to Applications. The app has a Developer ID signature and is notarized by Apple.

**Windows (NSIS .exe)**

Run `Deferent_2.0.5_x64-setup.exe` to install Deferent for your Windows account. If Microsoft Edge Evergreen WebView2 is missing, setup downloads it from Microsoft and requires internet access. The installer has no Windows publisher signature, so SmartScreen may warn. Deferent verifies a separate signature for in-app updates.

When upgrading manually, choose **Do not uninstall** if setup asks. This preserves your legacy data. The older uninstaller can remove the legacy profile if you select **Delete the application data**.

## First run

1. Open Deferent and review **Setup checks** on the welcome screen. To switch to Codex, select **Use Codex for the Hub** or **Use Codex for local Workers** where shown. On Windows, use Codex for both.
2. Follow the separate Hub sign-in in **Setup checks**. For Codex, copy the sign-in command, run it in your terminal (PowerShell on Windows), then select **Recheck sign-in**. For Claude Code, select **Sign in** and follow the prompts.
3. Sign in to the Worker CLI as usual on each machine that runs Workers. Use **Machine Settings** to choose the Worker harness for each SSH host.

## Web access

Web access is off by default. On the desktop, open **Settings → Web access**, turn it on, and select **Save**. To connect from another device, set **Host** to the desktop’s private-network address before saving. Web access uses plain HTTP, so use a private network such as a VPN. Select **Make link** and open the one-time link in the browser you want to pair. Keep the desktop app running.

To pair multiple browser profiles with the same link, select **Reusable pairing link → Create link**. The link works until you select **Replace link** or **Revoke link**. Paired browsers keep access and can be revoked individually.

A macOS or Linux desktop host can also serve file previews to paired browsers. In **Settings → Web access → Project file previews**, select an active local project, enter an output folder relative to the project, and select **Approve folder**. Every paired browser can open supported files linked in Hub replies from that folder after confirming the preview. Static HTML opens in a sandbox.

## Updates

Open **About** (the ⓘ button in the title bar) to check for and install signed in-app updates. Select **Restart now** when prompted. If your version has no in-app updater, download the matching package from the [latest release](https://github.com/rizquuula/deferent-app-release/releases/latest) and follow the [installation steps](#install). For a manual AppImage upgrade, replace the old AppImage with the new executable file. See the [release notes](https://github.com/rizquuula/deferent-app-release/releases) for changes in each version.

Select **About → Licenses** to view third-party licenses.

## Your data

Deferent stores your project registry, sessions, Hub configuration, and logs (`logs/`) in its app data folder.

| System | Folder |
| --- | --- |
| Linux | `~/.local/share/id.lyralabs.deferent/` by default, or `$XDG_DATA_HOME/id.lyralabs.deferent/` when `XDG_DATA_HOME` is an absolute path |
| macOS | `~/Library/Application Support/id.lyralabs.deferent/` |
| Windows | `%APPDATA%\id.lyralabs.deferent\` for application data and `%LOCALAPPDATA%\id.lyralabs.deferent\` for WebView data |

Deferent v2.0.5 leaves legacy data in place without migrating it. On Linux and Windows, Deferent shows first-run setup if the new profile is empty. The engine still honors `--data-dir` when run directly.

On macOS, quit the previous version before upgrading. Deferent uses the existing data at the path above directly. If your Claude Code Hub previously signed in through the old data path, it may ask you to sign in again. macOS may also ask for permissions again. An earlier migration may have left a link at the old location and a private backup at `~/Library/Application Support/.id.lyralabs.deferent-migration-v1/legacy-backup/`.

For more detail in the logs, start the app with `DEFERENT_LOG_LEVEL=debug`. Existing launchers can still use `CLAUDEPLAY_LOG_LEVEL`.

## Uninstall

- **Linux (.deb).** Run `sudo apt remove deferent`. If you still have the old ClaudePlay package, use `sudo apt remove claude-play`.
- **Linux (AppImage).** Delete the AppImage file.
- **macOS.** Move Deferent from Applications to the Trash.
- **Windows.** Open **Settings → Apps → Installed apps**, find **Deferent**, and choose **Uninstall**.
- **App data.** To remove your current Deferent settings and session history, quit the app and delete its application data folder listed above. On Windows, delete the WebView data folder as well to remove browser preferences. An earlier macOS migration may also have left the backup described above.

---

© 2026 [Lyralabs ID](https://lyralabs.id/).
