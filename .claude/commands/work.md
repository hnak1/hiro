# /work

## 呼び出し方
`/work [Issue番号]` または `/work`（次の優先Issueを自動選択）

## 概要
Issueを取得してbrainからコンテキストを収集し、タスクを実行して完了させる。

## 処理手順

### 1. コンテキスト収集
- 指定Issue（または最高スコアのIssue）を取得
- `context-builder` エージェントを起動してbrain内関連情報を収集
- `roadmap.md` から現在の状況を確認

### 2. 事前確認（最大1回）
- 不明点がある場合のみ1回質問する
- 明確なら即実行

### 3. タスク実行
- Issue の完了条件を満たすまで作業する
- **1 Issue 最大10分** のガードレールを遵守
- ブロッカーがあれば即報告してスキップ

### 4. 完了処理
- 完了報告を Issue にコメント
- Issue をクローズ
- 関連ノートを brain 内に更新
- `git commit` & `push`

## Guardrails
- max_time_per_issue: 10分
- consecutive_errors_limit: 3
- max_questions_per_chain: 1（実行前のみ）
