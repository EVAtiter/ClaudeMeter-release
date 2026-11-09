[English](README.md) | [日本語](README.ja.md)

# Claude Meter

Claude の**今月の請求額**・**利用枠（5 時間・週間）**と、**いま動いている Claude Code のセッション**を、
メニューバーからいつでも確認できる macOS アプリです。

---

## ダウンロード

最新版は [Releases](https://github.com/EVAtiter/ClaudeMeter-release/releases/latest) からダウンロードできます。

1. `Claude-Meter-x.x.x.zip` を解凍し、`Claude Meter.app` を「アプリケーション」フォルダへ移動
2. 起動すると、メニューバーに ✳ アイコンが出ます
3. 初回の取得で、macOS からキーチェーンの許可を求められることがあります（Claude アプリのログインを使う場合）。
   「常に許可」を選ぶと、以後は表示されません

Homebrew でもインストールできます。

```bash
brew install --cask EVAtiter/tap/claude-meter
```

Homebrew 7 以降で「untrusted tap」と表示されたら、先に次のコマンドで claude-meter を信頼してから、もう一度インストールしてください。

```bash
brew trust --cask evatiter/tap/claude-meter
```

---

## 使い方

- **メニューバー** — スペンドリミットがある契約（Enterprise など）では、今月の使用率を表示します（例: `✳ 55%`）。
  Pro / Max では 5 時間枠の使用率を表示します（例: `✳ 5h 8%`）。週間枠のほうが高く 75% 以上のときは、週間枠を表示します（例: `✳ 週 88%`）
- **色** — 75% 以上で黄、90% 以上で赤のバッジになります
- **クリック** — 詳細のカードが開きます。カードの外をクリックすると閉じます
- **右クリック**（またはカード右上の歯車）— 今すぐ更新 / Keychain の許可をやり直す / Mac ログイン時に自動起動 / バージョン情報 / 終了

Claude アプリ（デスクトップ版）が起動していないときは、メニューバーに数値を出さず、アイコンだけを表示します。

---

## 主な機能

- **今月の請求額** — スペンドリミットに対する使用額と使用率、リセット日時（毎月 1 日 00:00 UTC）。円換算つき
- **利用枠** — 5 時間・週間のゲージとリセット時刻、週間の使用量の内訳
- **動いているセッション** — 直近 30 分に応答があった Claude Code のセッションの一覧（CLI・Claude アプリの Code タブ・VS Code 拡張・SDK）。
  モデル・コンテキストの使用率・直近 30 分と累計の概算額を表示し、サブエージェントの内訳も開けます
- **トークンを消費しない** — 使用量の取得でプロンプトを送りません
- **ライト / ダーク対応** — カードはシステムの外観に合わせて表示します

---

## 必要なもの

- Claude アプリ（デスクトップ版）または Claude Code に、ログインしていること
- セッションの一覧は、Claude Code を使っているときに表示されます

---

## ご注意

- 表示は日本語だけです。金額は米ドルと円で表示します
- セッションの金額は、公式の料金表の単価から計算した概算です。実際の請求額とは一致しないことがあります
- Claude Meter は個人が開発したアプリで、Anthropic とは関係ありません

---

## プライバシー

- 使用量は、あなたの Claude のログインを使って Anthropic（`api.anthropic.com`）から取得します。
  Claude アプリのログインを使う場合は、キーチェーンの「Claude Safe Storage」を読み出します（初回に macOS の許可ダイアログが出ます）
- ログインの情報はメモリの中でだけ扱い、ファイルやログには書きません
- ほかに通信するのは、円換算の為替レート（`open.er-api.com` / `api.frankfurter.app`）と、公式の料金表（`platform.claude.com`）の取得だけです。
  あなたのデータを開発者や第三者へ送ることはありません
- 書き込むのは `~/Library/Application Support/ClaudeMeter/state.json` だけです（`~/.claude/` には書き込みません）

---

## 対応 OS

macOS 14 Sonoma 以降（macOS 27.2 で動作確認）/ Apple Silicon（arm64）専用 / Apple 公証済み

---

Copyright © 2026 EVA Titer. All rights reserved.
