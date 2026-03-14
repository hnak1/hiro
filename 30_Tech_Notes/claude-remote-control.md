# Claude リモートコントロール

> GitHub Issue/コメントからClaude Codeをリモート起動する仕組み

## 概要

`claude-remote-control.yml` ワークフローにより、GitHub上から直接Claudeに指示を出せる。

## 起動方法

### 方法1: Issueコメントで `@claude` メンション

```
@claude 00_Inbox/の未整理ファイルを確認して整理してください
```

```
@claude 教授選プロジェクトの進捗をまとめてください
```

### 方法2: Issueに `claude` ラベルを付与

Issue作成時またはラベル追加時に、Issue本文の内容をそのまま指示として実行。

## ワークフロー

```
GitHub Event
  ↓
issue_comment (@claude メンション) or
issues (claudeラベル付与)
  ↓
claude-remote-control.yml 起動
  ↓
Claude Code CLI 実行
  ↓
git commit & push (変更があれば)
```

## 制約

- ANTHROPIC_API_KEY が Secrets に設定されていること
- CLAUDE.md の Guardrails を遵守（max 30ターン）
- 実行時間はGitHub Actions の制限内（最大6時間）

## 既存ワークフロー一覧

| ファイル | トリガー | 役割 |
|---|---|---|
| `morning-inbox.yml` | 毎日 JST 7:00 | Inbox自動整理 |
| `weekly-review.yml` | 毎週金曜 JST 18:00 | 週次レビュー生成 |
| `issue-chain.yml` | Issue クローズ時 | 次のIssueへ自動チェーン |
| `claude-remote-control.yml` | @claude メンション / claude ラベル | **リモートコントロール** |

## セットアップ確認

- [ ] `ANTHROPIC_API_KEY` を GitHub Secrets に登録
- [ ] リポジトリに `claude` ラベルを作成（色: `#1d76db`）
- [ ] Actions の権限: `contents: write`, `issues: write` が有効
