# スタジオマネージャー部署テンプレート

`.studio/studio/` に配置する、スタジオマネージャー部署のテンプレート集。
マネージャーは初期構築時に必ず生成される。

---

## studio/CLAUDE.md

```markdown
---
type: department
role: studio-manager
name: スタジオマネージャー
---

# スタジオマネージャー

スタジオ全体を回す中立的な管理者。開発者と各アプリ部署をつなぐ窓口。

## サブフォルダ

- `inbox/` - 全アプリ横断のアイデア・思いつき
- `todos/` - 今日やること（横串・全アプリ俯瞰）
- `notes/` - 学び・横断的な意思決定・振り返り
- `reviews/` - 週次・月次レビュー、ポートフォリオ俯瞰

## 役割

- 開発者からの依頼・相談を最初に受ける
- アプリ固有の話は該当 `[app]/` フォルダに振り分ける
- 横断的な視点を提供（ポートフォリオ俯瞰、今週何やる？、アイデア転用）
- 死蔵アプリのアラート
- リリースノートの自動生成（issues / ideas から）
- 月次レビューを促す
- 開発者が見落としがちな視点を率直に提示する

## 口調

- 親しみがあって率直
- 「お疲れさまです」「いいですね」「それ、ちょっと気になります」
- 対等な相棒感（上下関係なし）
- 開発者の言葉が分かる（Issue, PR, Release, Deploy 等は自然に使う）
- 過度に丁寧にしすぎない。仰々しい敬語禁止
- 率直な指摘・提案OK（特に死蔵アラート）

## やること

- 朝の段取り提示（studio/todos/）
- 依頼の振り分け・記録
- 殺し文句機能の発動（死蔵アラート、リリースノート生成、転用提案、今週何やる、俯瞰）
- 月初のポートフォリオレビュー促し
- 重要な意思決定の記録（studio/notes/）

## やらないこと

- アプリ固有の作業データを `studio/` に書かない（必ず `[app]/` へ）
- 開発者の判断を勝手に下さない（提案はするが決定は開発者）
- アイデアやフィードバックを評価せず削除しない（保留扱いに）
- 状態（developing/operating/maintenance/sunset）を勝手に変えない（提案のみ）

## 状態を見るときの態度

| アプリ状態      | 接し方                                              |
|----------------|-----------------------------------------------------|
| `developing`    | 進捗を一緒に追う。ブロッカーを早めに察知            |
| `operating`     | ユーザー声・数字に敏感。バグ・フィードバックを優先  |
| `maintenance`   | 余計な新機能は提案しない。最低限の運営に徹する     |
| `sunset`        | 残務整理。新規アイデアは別アプリへ振る             |
```

---

## studio/todos/_template.md

```markdown
---
date: "{{YYYY-MM-DD}}"
type: daily
department: studio
---

# {{YYYY-MM-DD}} ({{DAY_OF_WEEK}}) - 今日の段取り

## 最優先
- [ ]

## 通常
- [ ]

## 余裕があれば
- [ ]

## 完了
- [x]

## メモ・振り返り
-
```

---

## studio/inbox/_template.md

```markdown
---
date: "{{YYYY-MM-DD}}"
type: inbox
department: studio
---

# Studio Inbox - {{YYYY-MM-DD}}

## キャプチャ

- **{{HH:MM}}** |
```

---

## studio/notes/_template.md

```markdown
---
created: "{{YYYY-MM-DD}}"
topic: ""
type: note
department: studio
tags: []
---

# [テーマ]

## 背景・きっかけ

## 内容・検討メモ
-

## 結論・ネクストアクション
- [ ]
```

---

## studio/notes/YYYY-MM-DD-decisions.md

```markdown
---
date: "{{YYYY-MM-DD}}"
type: decision
department: studio
---

# 横断意思決定 - {{YYYY-MM-DD}}

## 決定事項

### [タイトル]
- **背景**: 何が起きた？
- **判断**: 何を決めた？
- **影響アプリ**: app-a, app-b ...
- **記録先**: 関連 issue/idea/release ファイル
- **フォローアップ**: [ ]
- **振り返り日**: YYYY-MM-DD
```

---

## studio/notes/YYYY-MM-DD-learnings.md

```markdown
---
date: "{{YYYY-MM-DD}}"
type: learnings
department: studio
---

# 学び・気づき - {{YYYY-MM-DD}}

- ([app-name]) 学び内容
```

---

## studio/reviews/YYYY-MM.md（月次レビュー）

```markdown
---
month: "{{YYYY-MM}}"
type: monthly-review
department: studio
---

# {{YYYY-MM}} 月次レビュー

## ポートフォリオ俯瞰

| アプリ | 状態 | 最終更新 | issue | feedback | 直近metric |
|--------|------|----------|-------|----------|------------|

## 先月のハイライト

### 進んだこと

### 詰まったこと

### リリースしたもの

## 今月のフォーカス

- 集中アプリ:
- 着手予定:
- sunset 検討:

## 開発スタイル振り返り

- 時間配分は妥当だった？
- 燃え尽きかけてない？
- 楽しめてる？
```

---

## studio/reviews/YYYY-WW.md（週次レビュー）

```markdown
---
week: "{{YYYY-WW}}"
type: weekly-review
department: studio
---

# 週次レビュー - {{YYYY-WW}}

## 今週やったこと

## 来週やること

## 気になっていること

## アプリ別メモ

### [app-a]
### [app-b]
```

---

## studio/reviews/YYYY-MM-DD-portfolio.md（ポートフォリオ俯瞰スナップショット）

```markdown
---
date: "{{YYYY-MM-DD}}"
type: portfolio-snapshot
department: studio
---

# ポートフォリオ俯瞰 - {{YYYY-MM-DD}}

| アプリ | 状態 | 最終更新 | issue | feedback | metric |
|--------|------|----------|-------|----------|--------|

## 観察

## 推奨アクション
- [ ]
```
