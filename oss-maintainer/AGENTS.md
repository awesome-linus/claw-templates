# AGENTS.md — OSS Maintainer Workspace

## 起動時にやること

1. `SOUL.md` を読む
2. `USER.md` を読む（リポジトリ・スタック確認）
3. 今日・昨日の `memory/YYYY-MM-DD.md` を確認
4. メインセッションなら `MEMORY.md` も読む

## GitHub監視

`USER.md` に記載のリポジトリを定期チェック:

```
# GitHub CLI でIssue確認
gh issue list --repo [your-org/your-repo] --state open
gh pr list --repo [your-org/your-repo] --state open
```

チェック内容:
- 🚨 `security` ラベルのIssue → **即報告**
- 🐛 新しいバグレポート → 優先度付けして報告
- 📬 新しいPR → レビュー待ちを確認
- ✅ CI失敗 → すぐ報告
- 💬 長期間未返信のIssue → フォローアップ

## リリース管理

```bash
# リリース前チェックリスト
# 1. CHANGELOGを更新 (CHANGELOG.md)
# 2. バージョンをbump (package.json / pyproject.toml など)
# 3. タグを作成
git tag -a vX.Y.Z -m "Release vX.Y.Z"
git push origin vX.Y.Z
# 4. GitHub Releasesを作成
gh release create vX.Y.Z --notes-file CHANGELOG_latest.md
```

セマンティックバージョニング (semver) を遵守:
- **MAJOR**: Breaking change
- **MINOR**: 後方互換の機能追加
- **PATCH**: バグfixのみ

## Issue トリアージ

新しいIssueに対して:
1. ラベルを付ける (`bug`, `enhancement`, `question`, `good first issue` など)
2. 優先度を判断 (`priority: high/medium/low`)
3. マイルストーンに割り当てる（必要な場合）
4. 24時間以内に初回返信（「確認します」でもOK）

## PR レビュー基準

- [ ] テストが通っているか（CI緑）
- [ ] 変更内容がIssueと一致しているか
- [ ] Breaking changeがあればCHANGELOGに記載されているか
- [ ] ドキュメントの更新が必要か
- [ ] コードスタイルがプロジェクトに合っているか

## コーディングエージェント連携

重い実装タスクはACP coding agentに委譲:

```
# Claude Code で実装
sessions_spawn(runtime="acp", task="Fix the bug in issue #123...")

# Codex で実装
sessions_spawn(runtime="acp", agentId="codex", task="...")
```

## メモリ管理

- 重要な決定・変更は `memory/YYYY-MM-DD.md` に記録
- リリース履歴は `MEMORY.md` に蓄積
- コントリビューター情報も記録しておく

## 安全ルール

- 破壊的な操作（force push, タグ削除など）は必ず確認してから
- `main`/`master` への直接pushは避ける
- セキュリティIssueはprivateに扱う
