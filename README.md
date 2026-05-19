# cc-studio

個人開発者のための、Claude Code 仮想スタジオ管理プラグイン。
**スタジオマネージャー**が窓口となり、**各アプリが独立部署**として管理されます。

## こんな方に

- **複数アプリを並行開発・運営している個人開発者**
- 「どのアプリに何のバグがあったか」を忘れがち
- ロードマップが頭の中だけで管理されている
- ユーザーフィードバックの管理が散らかる
- リリースノートを書くのが面倒
- 「今週どのアプリに集中すべき？」で迷う
- 古いアプリのメンテをサボりがち

## 特徴

- 🎬 **スタジオマネージャーが窓口**：依頼を受け、各アプリ部署に振り分け
- 📱 **アプリ=部署**：各アプリが独立フォルダで管理（roadmap / issues / ideas / releases / feedback / metrics）
- ⚠️ **死蔵アプリのアラート**：「app-c を3週間触ってませんよ」と先回り
- 📝 **リリースノート自動生成**：`issues/` の closed と `ideas/` の implemented から `vX.Y.Z.md` を組み上げ
- 💡 **アイデア転用提案**：app-a で出たアイデアが app-b に活かせそうなら横串で提案
- 🗓 **「今週何やる？」モード**：全アプリ横串で優先度を判断・提案
- 📊 **ポートフォリオ俯瞰**：全アプリの状態・数字を一覧化
- 🔁 **月次レビュー**：月初に俯瞰の時間を促す

## インストール

Claude Code 内で:

```
/plugin marketplace add texia-Inc/cc-studio
/plugin install studio@cc-studio
```

## 使い方

任意のディレクトリで `/studio` を実行すると、初回はオンボーディングが始まります。

### オンボーディング（3問）

1. **既存のアプリ**を登録（複数可、空でも可）
2. **開発スタイル**：専業 / 副業 / 趣味
3. **直近の悩み**：新規開発 / 保守整理 / マネタイズ強化 / 時間配分

### 2回目以降

```
/studio
```

> マネージャー：お疲れさまです。app-b が直近3日 push なし、集中する週にしませんか？

そのまま自然言語で:
- 「app-a に新機能アイデア：○○」
- 「app-b、v1.2.0 リリースした」
- 「今週何やる？」
- 「ポートフォリオ俯瞰したい」
- 「新しいアプリ追加して」

## 生成されるディレクトリ構造

```
.studio/
├── CLAUDE.md
├── studio-info.md
├── studio/                ← マネージャー部署（窓口・横串PM）
│   ├── CLAUDE.md
│   ├── inbox/, todos/, notes/, reviews/
└── [app-name]/            ← 各アプリ = 部署
    ├── CLAUDE.md          ← 概要・スタック・URL・状態
    ├── roadmap.md
    ├── issues/, ideas/, releases/, feedback/, metrics/
```

## アプリ状態

| 状態          | 意味                                |
|--------------|-------------------------------------|
| `developing`  | 開発中                              |
| `operating`   | 運営中（ユーザーがいる）            |
| `maintenance` | 保守のみ                            |
| `sunset`      | 終息予定 or 終息済み                |

マネージャーは状態に応じて振る舞いを変えます。

## アプリの追加

オンボーディング後でも自由に追加できます。

```
あなた: 新しいアプリ作った、todo-zen
マネージャー: 承知しました。種類とスタックを教えてください。
```

## Web ダッシュボード（オプション）

ブラウザでポートフォリオを俯瞰したり、既存リポジトリを GitHub / ローカルから一括取り込みできます。

```bash
npx cc-studio-dashboard
```

詳細: [cc-studio-dashboard](https://github.com/texia-Inc/cc-studio-dashboard)

## 動作要件

- Claude Code（プラグイン対応版）
- 任意: [cc-studio-dashboard](https://github.com/texia-Inc/cc-studio-dashboard) でブラウザ管理を使う場合は Node.js 18+
- 任意: GitHubから一括取り込みを使う場合は `gh` CLI（認証済み）

## ライセンス

MIT License — 詳細は [LICENSE](./LICENSE) を参照。

## 関連プロジェクト

- [cc-concierge](https://github.com/texia-Inc/cc-concierge) — 中小企業社長向け仮想エージェントチーム
- [cc-company](https://github.com/Shin-sibainu/cc-company) — Shin-sibainu 氏作の元祖。本プラグインは大きく影響を受けています
