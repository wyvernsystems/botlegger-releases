# BotLegger releases

Downloads for [BotLegger™](https://botlegger.com), a desktop app for AI bots
that chat, research, write, and use tools on your own computer. Bring your own
AI provider key; your bots, chats, and keys stay on your devices.

This repository holds release files only. BotLegger is closed source.

## Download

Get the latest version from [Releases](../../releases/latest).

| Platform | File | Requires |
|----------|------|----------|
| macOS (Apple silicon and Intel) | `BotLegger_<version>_universal.dmg` | macOS 14 or later |
| Windows (x64) | `BotLegger_<version>_windows_x86_64_setup.exe` (or the portable `.zip`) | Windows 11 or Server 2019 and later |
| Linux (x86_64) | `BotLegger_<version>_linux_x86_64.tar.gz` | Debian 12 or 13, Ubuntu 22.04, 24.04 or 26.04 |

BotLegger is in beta. iPhone and Android versions follow.

- **macOS:** open the `.dmg` and drag BotLegger to Applications. The app is
  signed with an Apple Developer ID and notarized by Apple.
- **Windows:** run the setup; it installs for your user and needs no
  administrator. The app is not code-signed yet, so Windows may show a
  SmartScreen prompt: choose **More info**, then **Run anyway**.
- **Linux:** unpack the `.tar.gz` into a folder of your choice and run
  `./botlegger` from inside it.

The app updates itself; the portable Windows `.zip` instead offers the new
version to download.

## Checking a download

- `sha256.sum` lists the SHA-256 of every file in a release.
- `security-report.md` lists the security scans the release passed, signed
  with the same key that signs app updates (`security-report.md.sig`).

## Help

- Guide and tutorials: <https://botlegger.com>
- Support: <support@botlegger.com>

## Legal

Use of BotLegger is subject to the [End User License Agreement](https://botlegger.com/eula),
[Terms of Use](https://botlegger.com/terms), and
[Privacy Policy](https://botlegger.com/privacy). All rights reserved.
BotLegger™ is a trademark of Wyvern Systems LLC.
