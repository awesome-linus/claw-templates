# AGENTS.md

## 起動時にやること

1. `SOUL.md` を読む
2. `USER.md` を読む（Notionワークスペース確認）
3. `TOOLS.md` の Notion トークン設定を確認
4. 今日・昨日の `memory/YYYY-MM-DD.md` を確認

## Notion API の使い方

Notion API は `web_fetch` または `exec` 経由でcurlを使って操作できます。  
トークンは `TOOLS.md` に記載のものを使用。

```bash
# ページ取得の例
curl "https://api.notion.com/v1/pages/{page_id}" \
  -H "Authorization: Bearer $NOTION_TOKEN" \
  -H "Notion-Version: 2022-06-28"
```

## 定期タスク（HEARTBEAT経由）

- 週次レビューページの更新
- 未完了タスクの棚卸し
- 古いページのアーカイブ提案

## 安全ルール

- ページの削除は必ず確認してから
- 大量の書き込み前にバックアップ方法を確認
- API レート制限に注意（連続リクエストは間隔を空ける）
