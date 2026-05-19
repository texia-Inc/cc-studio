# アプリ部署テンプレート

各アプリは独立した部署フォルダ `[app-name]/` として配置される。
フォルダ名は kebab-case。

各アプリフォルダの構成:

```
[app-name]/
├── CLAUDE.md         ← 概要・スタック・URL・状態
├── roadmap.md        ← 次やること
├── issues/           ← バグ・課題
├── ideas/            ← 機能アイデア
├── releases/         ← リリースノート
├── feedback/         ← ユーザーフィードバック
└── metrics/          ← 月次の数字
```

---

## [app-name]/CLAUDE.md

```markdown
---
type: department
role: app
name: {{APP_NAME}}
state: developing      # developing / operating / maintenance / sunset
app_type: web          # web / mobile / cli / extension / saas / game / other
---

# {{APP_NAME}}

## 概要

{{ONE_LINER}}

## 状態

- **現在の状態**: developing
- **作成日**: {{CREATED_DATE}}
- **最終リリース**: なし

## スタック

- **言語**: 
- **フレームワーク**: 
- **ホスティング**: 
- **DB**: 

## URL

- **本番**: 
- **GitHub**: 
- **ランディングページ**: 
- **ダッシュボード**: 

## サブフォルダ

- `roadmap.md` - 次やること（中長期）
- `issues/` - バグ・課題（YYYY-MM-DD.md）
- `ideas/` - 機能アイデア（YYYY-MM-DD.md）
- `releases/` - リリースノート（vX.Y.Z.md）
- `feedback/` - ユーザーフィードバック（YYYY-MM-DD.md）
- `metrics/` - 月次の数字（YYYY-MM.md）

## このアプリの方針

- ターゲットユーザー: 
- 主要機能: 
- マネタイズ: 

## メモ

```

---

## [app-name]/roadmap.md

```markdown
---
app: "{{APP_NAME}}"
type: roadmap
updated: "{{YYYY-MM-DD}}"
---

# {{APP_NAME}} - ロードマップ

## 直近（今月〜来月）

- [ ] 

## 中期（3ヶ月）

- [ ] 

## 将来（やる確証はないが残しておく）

- [ ] 

## 終わったこと（最近）

- [x] (YYYY-MM-DD)
```

---

## [app-name]/issues/_template.md

```markdown
---
date: "{{YYYY-MM-DD}}"
app: "{{APP_NAME}}"
type: issues
---

# Issues - {{YYYY-MM-DD}}

## バグ

- [ ] [bug] 説明... | 重要度: 高/通常/低 | 報告者: 
- [x] [bug] (リリース済 vX.Y.Z) ...

## 改善

- [ ] [enhancement] 説明...
- [x] [enhancement] (リリース済 vX.Y.Z) ...

## メモ
```

---

## [app-name]/ideas/_template.md

```markdown
---
date: "{{YYYY-MM-DD}}"
app: "{{APP_NAME}}"
type: ideas
---

# Ideas - {{YYYY-MM-DD}}

## 機能アイデア

- [ ] アイデア名: 説明... | 興味度: ★★★ | タグ: ui, growth
- [implemented] 実装済 → released in vX.Y.Z

## ペンディング
```

---

## [app-name]/feedback/_template.md

```markdown
---
date: "{{YYYY-MM-DD}}"
app: "{{APP_NAME}}"
type: feedback
---

# Feedback - {{YYYY-MM-DD}}

## ユーザー声

- **{{ユーザー名 or 匿名}}** ({{チャネル: Twitter/メール/Discord/レビュー}})
  - 内容: 
  - 反応: 未対応 / 対応中 / 対応済
  - 紐づく issue: 

## トレンド観察
```

---

## [app-name]/releases/_template.md

セマンティックバージョンファイル（v1.2.0.md）として保存。

```markdown
---
version: "vX.Y.Z"
app: "{{APP_NAME}}"
released: "{{YYYY-MM-DD}}"
type: release
---

# vX.Y.Z - {{YYYY-MM-DD}}

## 新機能

- 

## 改善

- 

## バグ修正

- 

## その他

- 

## 元になった issue/idea

- `issues/...`
- `ideas/...`
```

**自動生成のヒント**: `issues/` の closed + `ideas/` の implemented を集約して上記フォーマットに当てはめる。

---

## [app-name]/metrics/_template.md

月次ファイル（YYYY-MM.md）として保存。

```markdown
---
month: "{{YYYY-MM}}"
app: "{{APP_NAME}}"
type: metrics
---

# {{APP_NAME}} メトリクス - {{YYYY-MM}}

## 主要指標

| 指標 | 値 | 前月比 |
|------|-----|--------|
| {{METRIC_1}} | | |
| {{METRIC_2}} | | |
| {{METRIC_3}} | | |

## アプリタイプ別の推奨指標

タイプ別に追跡するとよい指標のヒント（埋めるかどうかは開発者次第）:

### web / saas
- 月間アクティブユーザー (MAU)
- 新規登録数
- MRR / 売上
- チャーン率
- 主要機能の利用率

### mobile app
- DAU / MAU
- インストール数
- レビュー平均
- 課金額 / IAP
- リテンション (D1/D7/D30)

### cli / oss
- GitHub Stars
- weekly downloads (npm, pypi etc)
- issue 数 / PR 数
- contributor 数

### extension / web tool
- 利用ユーザー数
- 訪問数
- 滞在時間
- 主要アクションのコンバージョン

### game
- DAU / MAU
- セッション時間
- 課金額 / ARPU
- リテンション

## 観察・コメント

## 次月のアクション
- [ ]
```
