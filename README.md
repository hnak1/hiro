# 🧠 Second Brain

> 「思考のパートナー」として機能する、Claude Code連携の第2の脳

---

## フォルダ構造

```
brain/
├── 00_Inbox/          # 未分類・とりあえずのメモ
├── 10_Journal/        # 日記・振り返り・会議メモ（日付付き）
├── 20_Projects/       # ゴール・期限・Issueがあるもの
│   └── roadmap.md    # 全プロジェクトのロードマップ
├── 30_Tech_Notes/     # 技術知識・永続的な参照資料
├── 50_Business_Context/  # ビジネス文脈・意思決定ログ
├── 90_System/         # 運用ルール・brain設定
├── 99_Archives/       # 完了・凍結したもの
├── .claude/
│   ├── CLAUDE.md     # Claude Code 動作設定
│   ├── commands/     # カスタムコマンド（14個）
│   └── agents/       # サブエージェント（13体）
└── .github/workflows/ # GitHub Actions（3本）
```

---

## コマンド一覧

| コマンド | 機能 | カテゴリ |
|---------|------|---------|
| `/decompose "ゴール"` | PM視点でMilestone→Task→Subtaskに3層分解 | 計画 |
| `/work [Issue#]` | Issueを取得して実行・完了させる | 実行 |
| `/orchestrate` | 自律実行の核心。上位3 Issueを順次実行 | 実行 |
| `/kickoff "テーマ"` | プロジェクト開始前にbrainを並列探索 | 計画 |
| `/deep-research "テーマ"` | 3エージェント並列Web調査 | 調査 |
| `/weekly-review` | 週次振り返りを自動生成 | レビュー |
| `/brain-status` | brain健全性ダッシュボード | モニタリング |
| `/stale-check` | 停滞プロジェクトを診断して次アクション提示 | モニタリング |
| `/idea "テーマ"` | 12フレームワークでアイデア生成 | 創造 |
| `/new-project "名前"` | PM視点でプロジェクト骨格を作成 | 計画 |
| `/sync` | brain↔GitHub Issue状況を同期 | 管理 |
| `/voice-note "テキスト"` | メモを構造化してInboxへ保存 | 記録 |
| `/meeting "名前" "書き起こし"` | 会議録を構造化してJournalへ保存 | 記録 |
| `/issue "やりたいこと"` | 自然言語からGitHub Issueを作成 | 管理 |

---

## エージェント一覧

| エージェント | 役割 | 介入タイミング |
|------------|------|-------------|
| `note-writer` | 思考を構造化ノートに変換 | ノート作成時 |
| `knowledge-explorer` | brain横断探索・関連情報発見 | 調査・kickoff時 |
| `project-orchestrator` | プロジェクト優先度判断 | /orchestrate時 |
| `inbox-organizer` | Inbox自動分類・移動 | 毎朝自動実行 |
| `deep-researcher` | Web深層調査 | /deep-research時 |
| `pm-advisor` | Why/What問いかけ（PdM視点） | 新PJ作成・停滞時 |
| `pj-manager` | How/When管理（PjM視点） | タスク分解・遅延時 |
| `socrates` | ソクラテス式問答で思考深化 | 思考が詰まったとき |
| `marketer` | マーケティング分析・提案 | マーケ施策検討時 |
| `writer` | 文章構成・表現改善 | 文章作成・レビュー時 |
| `retrospective-facilitator` | KPT振り返り構造化 | MS完了・週次レビュー時 |
| `idea-generator` | 12フレームワークでアイデア無限生成 | /idea時 |
| `context-builder` | 作業前コンテキスト収集・整理 | /work・/orchestrate時 |

---

## GitHub Actions

| ワークフロー | トリガー | 処理 |
|------------|---------|------|
| `morning-inbox.yml` | 毎朝7:00 JST | Inboxを自動整理してcommit |
| `weekly-review.yml` | 毎週金曜18:00 JST | 週次レビューを生成してcommit |
| `issue-chain.yml` | Issueクローズ時 | 次の優先Issueを自動チェーン |

---

## 始め方

### 1. GitHubリポジトリを作成

```bash
cd ~/brain
gh repo create brain --private --source=. --remote=origin --push
```

または GitHub で新しいリポジトリを作成してから：

```bash
git remote add origin https://github.com/[username]/brain.git
git push -u origin main
```

### 2. ANTHROPIC_API_KEY を登録

GitHub リポジトリの Settings → Secrets and variables → Actions → New repository secret

- Name: `ANTHROPIC_API_KEY`
- Value: Anthropic コンソールで取得したAPIキー

### 3. gh CLI をインストール・認証

```bash
# Windows (winget)
winget install --id GitHub.cli

# 認証
gh auth login
```

### 4. Claude Code をインストール

```bash
npm install -g @anthropic-ai/claude-code
```

### 5. 最初のプロジェクトを作成

```bash
cd ~/brain
claude
> /new-project "最初のプロジェクト名"
```

---

## スコアリング式

優先度計算に使用：

```
Score = (依存関係 × 3) + (ラベル優先度 × 2) + (タイプ適合度 × 2) + (工数 × 1) + (鮮度 × 1)
```

---

## Guardrails

| ルール | 値 |
|-------|---|
| 1チェーンあたりの最大Issue数 | 3 |
| 1 Issueの最大実行時間 | 10分 |
| 1チェーンの最大実行時間 | 30分 |
| 連続エラー上限 | 3回 → 停止 |
| 1チェーンあたりの最大質問数 | 1回 |
