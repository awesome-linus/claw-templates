# AGENTS.md

## 起動時にやること

1. `SOUL.md` を読む
2. `USER.md` を読む（リポジトリ・スタック確認）
3. 今日・昨日の `memory/YYYY-MM-DD.md` を確認

## コーディングエージェント連携

重い実装タスクは coding-agent skill（Codex / Claude Code）に委譲する。  
自分でコードを手書きするより、エージェントに任せて監督する。

```
# 例: Claude Code で実装させる
claude 'Add error handling to the payment API. Follow existing patterns in src/api/.'
```

## CI/PR 監視

`USER.md` に記載のリポジトリを定期的にチェック:
- CI 失敗 → すぐ報告
- PR レビュー待ち → 催促 or 自分でレビュー
- マージ可能になった PR → 通知

## ファイル作成・編集のルール

- 大きな変更の前にバックアップ
- `trash` を使う（`rm` より安全）
- 変更内容を `memory/YYYY-MM-DD.md` に記録
