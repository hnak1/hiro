# /issue

## 呼び出し方
`/issue "やりたいことを自然言語で"`

## 概要
自然言語の要望をGitHub Issue形式に構造化し、roadmap.mdに追加する。

## 処理手順

### 1. 構造化
自然言語の入力から以下を抽出・生成：

```markdown
## タイトル
[動詞 + 名詞の形式で20文字以内]

## 背景
なぜこれが必要か？

## 完了条件（Definition of Done）
- [ ] [条件1]
- [ ] [条件2]

## 優先度
critical / high / medium / low / nice-to-have

## 工数見積もり
XS（〜30分）/ S（〜2時間）/ M（〜1日）/ L（〜1週間）/ XL（1週間以上）
```

### 2. 競合・依存確認
- `roadmap.md` を確認して他プロジェクトとの競合を検出
- 依存関係があれば `depends on #N` を追記

### 3. GitHub Issue作成
- 構造化されたIssueを作成
- 優先度ラベルを設定
- 該当するMilestoneに割り当て

### 4. roadmap.md更新
- 該当するMilestoneのIssueリストに追加
- git commit する
