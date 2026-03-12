# /decompose

## 呼び出し方
`/decompose "ゴール"`

## 概要
PM視点でWhy/Whatを確認し、Milestone→Task→Subtaskの3層に分解する。

## 処理手順

### 1. PM確認フェーズ
- **Why**: なぜこのゴールが必要か？達成すると誰が喜ぶか？
- **What**: 完了の定義は何か？スコープ最小化できないか？
- **成功指標**: 定量的な完了条件を設定する

### 2. 3層分解
```
Milestone（〜2週間単位）
  └─ Task（〜1日単位）
       └─ Subtask（〜2時間単位）
```

### 3. スコアリング
各TaskにScoreを付与して優先度を決定：

```
Score = (依存関係 × 3) + (ラベル優先度 × 2) + (タイプ適合度 × 2) + (工数 × 1) + (鮮度 × 1)
```

| 要素 | 説明 |
|------|------|
| 依存関係 | 他タスクのブロッカーになるほど高得点 |
| ラベル優先度 | critical=5, high=4, medium=3, low=2, nice-to-have=1 |
| タイプ適合度 | 現在のコンテキストへの適合度 |
| 工数 | 小さいほど高得点（すぐ終わる） |
| 鮮度 | 最近追加されたほど高得点 |

### 4. 出力・保存
- `20_Projects/[プロジェクト名]/tasks.md` を更新
- `20_Projects/roadmap.md` に Milestone を追加
- GitHub Issue を作成（gh CLI 不可の場合は Markdown 出力）
- git commit する
