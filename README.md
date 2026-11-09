[English](README.md) | [日本語](README.ja.md)

# Claude Meter

A macOS menu bar app that keeps **this month's Claude spend**, your **usage limits (5-hour and weekly)**, and
**the Claude Code sessions running now** in view at all times.

---

## Download

Download the latest version from [Releases](https://github.com/EVAtiter/ClaudeMeter-release/releases/latest).

1. Unzip `Claude-Meter-x.x.x.zip` and move `Claude Meter.app` to the Applications folder
2. When you open it, a ✳ icon appears in the menu bar
3. The first time it fetches your usage, macOS may ask for Keychain access (when it uses the Claude app's login).
   Choose Always Allow and you will not be asked again

You can also install it with Homebrew.

```bash
brew install --cask EVAtiter/tap/claude-meter
```

If Homebrew 7 or later reports an "untrusted tap", trust claude-meter first with the command below, then install again.

```bash
brew trust --cask evatiter/tap/claude-meter
```

---

## How to use

- **Menu bar** — On plans with a spend limit (such as Enterprise), shows how much of this month's limit you have used (for example, `✳ 55%`).
  On Pro / Max, shows the 5-hour limit (for example, `✳ 5h 8%`). When the weekly limit is higher and at 75% or more, shows the weekly limit instead (`✳ 週 88%`, "週" means weekly)
- **Colors** — The badge turns yellow at 75% and red at 90%
- **Click** — Opens the detail card. Click outside the card to close it
- **Right-click** (or the gear at the top right of the card) — Refresh now (今すぐ更新) / Retry Keychain access (Keychain の許可をやり直す) / Open at login (Mac ログイン時に自動起動) / About (バージョン情報) / Quit (終了)

When the Claude desktop app is not running, the menu bar shows only the icon, without numbers.

---

## Features

- **This month's spend** — Amount and percentage of your spend limit, and when it resets (00:00 UTC on the 1st of each month). Also shown in yen
- **Usage limits** — 5-hour and weekly gauges with reset times, and a breakdown of weekly usage
- **Running sessions** — Claude Code sessions that responded in the last 30 minutes (CLI, the Code tab of the Claude app, the VS Code extension, and the SDK).
  Shows the model, context usage, and estimated cost for the last 30 minutes and in total. You can open a breakdown of subagents
- **Uses no tokens** — Sends no prompts to fetch your usage
- **Light / Dark** — The card follows the system appearance

---

## What you need

- You are logged in to the Claude desktop app or Claude Code
- The session list appears when you use Claude Code

---

## Notes

- The app is shown in Japanese only. Amounts are shown in US dollars and yen
- Session costs are estimates calculated from the official pricing. They may differ from your actual bill
- Claude Meter is an independent app made by an individual and is not affiliated with Anthropic

---

## Privacy

- Claude Meter fetches your usage from Anthropic (`api.anthropic.com`) with your own Claude login.
  When it uses the Claude app's login, it reads "Claude Safe Storage" in your Keychain (macOS asks for permission the first time)
- Your login is kept in memory only and is never written to files or logs
- The only other network access is for the exchange rate to yen (`open.er-api.com` / `api.frankfurter.app`) and the official pricing (`platform.claude.com`).
  Your data is never sent to the developer or any third party
- It writes only `~/Library/Application Support/ClaudeMeter/state.json` (nothing under `~/.claude/`)

---

## Requirements

macOS 14 Sonoma or later (tested on macOS 27.2) / Apple Silicon (arm64) only / Notarized by Apple

---

Copyright © 2026 EVA Titer. All rights reserved.
