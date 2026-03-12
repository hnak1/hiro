# 🗺️ Brain Roadmap

最終更新: 2026-03-12（教授選プロジェクト追加）

---

## MS1: 基盤構築 ✅ 完了

**目標**: brainの骨格を作り、自律運用の基盤を整備する
**期間**: 2026-03-12
**状態**: 🟢 完了

### 完了ファイル

#### ディレクトリ構造
- [x] `00_Inbox/`
- [x] `10_Journal/`
- [x] `20_Projects/`
- [x] `30_Tech_Notes/`
- [x] `50_Business_Context/`
- [x] `90_System/`
- [x] `99_Archives/`
- [x] `.claude/commands/`
- [x] `.claude/agents/`
- [x] `.github/workflows/`

#### 設定ファイル
- [x] `.claude/CLAUDE.md` — プロジェクト設定・自律動作ルール
- [x] `.gitignore`
- [x] `README.md`

#### カスタムコマンド（14個）
- [x] `/decompose` — ゴールをMilestone→Task→Subtaskに分解
- [x] `/work` — Issueを実行して完了させる
- [x] `/orchestrate` — 自律実行の核心コマンド
- [x] `/kickoff` — プロジェクト開始前のbrain探索
- [x] `/deep-research` — 3エージェント並列Web調査
- [x] `/weekly-review` — 週次振り返り自動生成
- [x] `/brain-status` — brain健全性ダッシュボード
- [x] `/stale-check` — 停滞プロジェクト診断
- [x] `/idea` — 12フレームワークでアイデア生成
- [x] `/new-project` — PM視点でプロジェクト骨格作成
- [x] `/sync` — brain↔GitHub Issue同期
- [x] `/voice-note` — 音声メモ構造化
- [x] `/meeting` — 会議録構造化
- [x] `/issue` — 自然言語→GitHub Issue構造化

#### エージェント（13体）
- [x] `note-writer` — 思考→構造化ノート変換
- [x] `knowledge-explorer` — brain横断探索
- [x] `project-orchestrator` — プロジェクト優先度判断
- [x] `inbox-organizer` — Inbox自動分類
- [x] `deep-researcher` — Web深層調査
- [x] `pm-advisor` — Why/What問いかけ
- [x] `pj-manager` — How/When管理
- [x] `socrates` — ソクラテス式問答
- [x] `marketer` — マーケティング分析
- [x] `writer` — 文章改善
- [x] `retrospective-facilitator` — KPT振り返り
- [x] `idea-generator` — アイデア無限生成
- [x] `context-builder` — 作業前コンテキスト収集

#### GitHub Actions（3本）
- [x] `morning-inbox.yml` — 毎朝7:00 JST Inbox自動整理
- [x] `weekly-review.yml` — 毎週金曜18:00 JST 週次レビュー
- [x] `issue-chain.yml` — Issueクローズ→次Issue自動チェーン

---

## MS2: 運用自動化 🔲 未完了

**目標**: GitHub Actionsを実際に動かし、日常運用を自動化する
**状態**: 🟡 進行中

### Issues
- [x] GitHubリポジトリ（hnak1/hiro）を作成してpush ✅
- [x] `gh` CLI をインストール・認証（hnak1） ✅
- [ ] #1 `ANTHROPIC_API_KEY` を GitHub Secrets に登録する `priority:critical`
- [ ] #2 morning-inbox.yml の動作確認（手動実行） `depends on #1`
- [ ] #3 weekly-review.yml の動作確認（手動実行） `depends on #1`
- [x] #1 `ANTHROPIC_API_KEY` を GitHub Secrets に登録する ✅
- [x] #2 morning-inbox.yml の動作確認（手動実行） ✅
- [x] #3 weekly-review.yml の動作確認（手動実行） ✅
- [x] #4 最初のプロジェクトを `/new-project` で作成する ✅ → 教授選
- [ ] #5 `/orchestrate` の初回実行 `depends on #4`

---

## MS3: 自律運用 🔲 未完了

**目標**: Claudeが能動的に提案・実行し、人間の介入を最小化する
**状態**: ⬜ 未開始

### Issues
- [ ] `/orchestrate` の定期自動実行設定
- [ ] `/stale-check` の定期通知設定
- [ ] brain健全性モニタリング
- [ ] ノートの自動リンク・タグ強化
- [ ] 意思決定ログの自動収集

---

---

## 教授選 応募プロジェクト 🟡 進行中

**目標**: 琉球大学教授選考への応募書類（様式1〜9）を完成・提出する
**状態**: 🟡 書類ブラッシュアップ中
**詳細**: `20_Projects/教授選/`

### Issues
- [ ] #6 様式6（研究内容・今後の展開）ブラッシュアップ `priority:high`
- [ ] #7 様式7（教育実績及び抱負）ブラッシュアップ `priority:high`
- [ ] #8 様式8（診療に関する抱負）ブラッシュアップ `priority:high`
- [ ] #9 様式5（主要論文要旨）確認
- [ ] #10 数値系書類（様式2・3・4・9）最終確認
- [ ] #11 推薦書（様式1）推薦者確定・依頼
- [ ] #12 全書類最終チェック・提出

---

## 完了プロジェクト

（完了時に99_Archives/へ移動）
