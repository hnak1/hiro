# /new-project

## 呼び出し方
`/new-project "プロジェクト名"`

## 概要
PM視点でプロジェクトの骨格を作成し、brain内に構造化されたプロジェクトフォルダを作る。

## 処理手順

### 1. PM確認（pm-advisorエージェント介入）
- **Why**: なぜこのプロジェクトが必要か？
- **What**: 完成形はどんな状態か？
- **Who**: 誰が恩恵を受けるか？
- **Risk**: 失敗するとしたら何が原因か？

### 2. フォルダ・ファイル作成

```
20_Projects/[プロジェクト名]/
├── pm_brief.md      # Why/What/Who/Risk
├── tasks.md         # タスク一覧（decompose結果）
└── decisions.md     # 意思決定ログ
```

#### pm_brief.md テンプレート
```markdown
# [プロジェクト名]
作成日: [日時]

## Why（なぜやるか）

## What（何をするか）

## Who（誰のため）

## 成功指標

## リスク

## スコープ外
```

#### decisions.md テンプレート
```markdown
# 意思決定ログ: [プロジェクト名]

## [日時] [決定事項]
- **背景**:
- **選択肢**:
- **決定**:
- **理由**:
```

### 3. roadmap.md 更新
- `20_Projects/roadmap.md` にプロジェクトとMS1を追加

### 4. GitHub Issue作成
- 最初のMilestone（MS1）をIssueとして作成
- git commit する
