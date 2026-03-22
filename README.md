# claw-templates

OpenClawワークスペースのスターターテンプレート集です。  
セットアップ時間ゼロで、すぐ使える構成を提供します。

## テンプレート一覧

| テンプレート | 説明 |
|---|---|
| [`personal-assistant`](./personal-assistant/) | 📋 個人アシスタント — メール・カレンダー・天気チェック付き |
| [`startup-ideas`](./startup-ideas/) | 💡 スタートアップアイデア番 — ブレスト特化（idea-backlog.md 付き） |
| [`dev-assistant`](./dev-assistant/) | 🛠️ 開発アシスタント — CI/PR監視、コード重視 |
| [`notion-butler`](./notion-butler/) | 📓 Notion執事 — Notion連携特化型 |

## 使い方

```bash
# テンプレートをワークスペースにコピーして使う
cp -r claw-templates/personal-assistant ~/.openclaw/workspace-myproject/
```

各テンプレートは以下のファイルを含みます：

- `SOUL.md` — エージェントのキャラクター・価値観
- `AGENTS.md` — 動作ルール・メモリ管理
- `IDENTITY.md` — 名前・ロール定義
- `USER.md` — ユーザー情報テンプレート
- `MEMORY.md` — 長期記憶の初期値
- `HEARTBEAT.md` — 定期チェックリスト

---

Made with ❤️ for [OpenClaw](https://openclaw.ai) users.
