# /orchestrate

## 呼び出し方
`/orchestrate` または `/orchestrate --dry-run`

## 概要
自律の核心コマンド。roadmap.md を読み込み、スコアリングして上位3 Issueを順次実行する。

## 処理手順

### 1. 状況把握
- `20_Projects/roadmap.md` を読み込む
- 全 open Issue を取得する

### 2. スコアリング
```
Score = (依存関係 × 3) + (ラベル優先度 × 2) + (タイプ適合度 × 2) + (工数 × 1) + (鮮度 × 1)
```

### 3. ブロッカー検出
| ブロッカー種別 | 対応 |
|--------------|------|
| Issue依存 | スキップ |
| 情報不足 | 人間に質問（最大1回） |
| 権限不足 | スキップ |
| 技術的未知 | 人間に質問（最大1回） |
| 外部依存 | スキップ |

### 4. 実行
- `--dry-run` モード: 実行計画を表示するのみ
- 通常モード: 上位3 Issueを `/work` で順次実行

### 5. 完了後処理
- 各Issue完了後に `roadmap.md` を更新
- 全Issueクローズで **Milestone完了を宣言**
- `10_Journal/retrospective-[日時].md` に振り返りを生成
- 次 Milestone を提案する

## Guardrails
- max_issues_per_chain: 3
- max_time_per_chain: 30分
- consecutive_errors_limit: 3 → 停止
- max_questions_per_chain: 1
