# /sync

## 呼び出し方
`/sync` または `/sync "プロジェクト名"`

## 概要
brain内の20_Projects/と対応するprojectリポジトリのIssue状況を比較し、差分を検出・修正する。

## 処理手順

### 1. 対象特定
- `/sync` → 全アクティブプロジェクトを対象
- `/sync "プロジェクト名"` → 指定プロジェクトのみ

### 2. 比較
brain側（tasks.md）とGitHub Issue側を比較：

| 状態 | 説明 |
|------|------|
| brain側のみ | GitHubにIssueがない → 作成を提案 |
| GitHub側のみ | brainに記録がない → brain更新を提案 |
| 内容乖離 | 両方あるが内容が異なる → 差分を表示 |

### 3. 差分レポート
```markdown
## 同期レポート: [プロジェクト名] [日時]

### brain側のみ（GitHub未登録）
- [ ] [タスク名]

### GitHub側のみ（brain未記録）
- [ ] Issue #N: [タイトル]

### 内容乖離
- Issue #N: brain「[A]」← →GitHub「[B]」
```

### 4. 自動修正
- 自動修正可能なもの（ステータス更新等）は修正
- 内容乖離は確認後に修正
- git commit する
