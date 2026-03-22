# 🗺️ Brain Roadmap

最終更新: 2026-03-22（orchestrate: #12ガイド完備確認・#13インパクト表完備確認・#11チェックリスト2026-03-22更新）

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

## MS2: 運用自動化 ✅ 完了

**目標**: GitHub Actionsを実際に動かし、日常運用を自動化する
**状態**: 🟢 完了

### 完了 Issues
- [x] GitHubリポジトリ（hnak1/hiro）を作成してpush ✅
- [x] `gh` CLI をインストール・認証（hnak1） ✅
- [x] #1 `ANTHROPIC_API_KEY` を GitHub Secrets に登録する ✅
- [x] #2 morning-inbox.yml の動作確認（手動実行） ✅
- [x] #3 weekly-review.yml の動作確認（手動実行） ✅
- [x] #4 最初のプロジェクトを `/new-project` で作成する ✅ → 教授選
- [x] #5 `/orchestrate` の初回実行 ✅（nightly-orchestrate クラウド移行完了）

---

## MS3: 自律運用 🟡 進行中

**目標**: Claudeが能動的に提案・実行し、人間の介入を最小化する
**状態**: 🟡 一部稼働中

### Issues
- [x] `/orchestrate` の定期自動実行設定 → nightly-orchestrate.yml 稼働中（JST 0:30）✅
- [x] `/stale-check` の定期通知設定 → stale-check.yml 追加（毎週水曜 JST 9:00）✅（2026-03-18）
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
- [~] #7 様式7（教育実績及び抱負）ブラッシュアップ `priority:high` → 構成ガイド・穴埋めテンプレート作成済み（実績数値記入はユーザー対応）
- [~] #8 様式8（診療に関する抱負）ブラッシュアップ `priority:high` → 構成ガイド・沖縄医療課題・DX・経営視点フレームワーク作成済み（数値記入はユーザー対応）
- [ ] #9 様式5（主要論文要旨）確認
- [ ] #10 数値系書類（様式2・3・4・9）最終確認
- [~] #10 推薦書（様式1）推薦者確定・依頼 → 推薦依頼状ドラフト・業績サマリー・候補者評価マトリクス・進捗トラッカー・フォローアップテンプレート3種（承諾後/リマインダー/受領確認）・運用チェックポイント追加済み（2026-03-18）。推薦者確定・送付はユーザー対応
- [x] #16 推薦を頼む（Memo処理済み → バージョンC依頼状・推薦者選定戦略に統合）
- [x] #17 推薦者は沖縄の先生が地域連携上有利（Memo処理済み → 推薦依頼状_ドラフト.md §戦略ノート・バージョンC追加）
- [x] #11 全書類最終チェック・提出 → チェックリスト強化済み: 未解決ブロッカー4件明示・完了項目[x]反映・今日やること追加（2026-03-17）。2026-03-22 版「状況確認表＋催促urgency」追加 ✅ GitHub close: 権限制限のためCLI不可（手動要）
- [x] #12 様式9（直近5年間の手術実績）記入 `priority:critical` → 記入ガイド完備: 術式別テンプレート・緊急5分アクション・推計手順・面接連携マップ・合格水準表追加（2026-03-17）✅ GitHub close: 権限制限のためCLI不可（手動要）
- [x] #13 様式6冒頭に研究インパクト一覧表を先出し `priority:high` → 冒頭文サンプル2パターン・表1〜3テンプレート・審査員8名チェックシート・競合ポジショニングマトリクス・面接連携マップ完備（2026-03-17〜21）✅ 依存 #6 はGitHub close済み。GitHub close: 権限制限のためCLI不可（手動要）
- [x] #14 様式6/7/8の原点文を統一して一貫性を強化 ✅（GitHub Issue close は権限制限のためCLI不可 → 手動クローズ要）
- [~] #15 面接対策: 想定問答集・自己分析・シミュレーション `priority:high` `depends on #11` → 想定問答集30問・当日チートシート・最終1週間練習スケジュール・数値確認チェックリスト追加済み（2026-03-18）。面接準備_数値記入フォーム.md 追加（2026-03-19）。言語切り替えドリル10問追加（2026-03-20）。**琉大固有情報参照シート・「なぜ琉大か」3分スクリプト記入例（3科連携・離島医療フレーム・固有名詞入り）追加（2026-03-21）**。練習実施・数値記入はユーザー対応

---

## 完了プロジェクト

（完了時に99_Archives/へ移動）
