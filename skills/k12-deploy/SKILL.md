---
name: k12-deploy
description: |
  Deploy a K12 service by triggering GitHub Actions CI via workflow_dispatch.
  Use when the user wants to deploy, redeploy, or restart a K12 service.
  Services: youtube-auto, auto-matome, twitter-collector, otakuracy-service, claude-gateway.
  Examples: "youtube-autoをデプロイして", "auto-matomeを再デプロイ", "deploy twitter-collector", "全サービスデプロイ"
allowed-tools: Bash
---

# K12 Deploy Skill

GitHub Actions の `workflow_dispatch` を使って K12 サービスをデプロイする。

## サービス → リポジトリ マッピング

| サービス名 | リポジトリ |
|---|---|
| youtube-auto | ishii2026buziness/youtube-auto |
| auto-matome | ishii2026buziness/auto-matome |
| twitter-collector | ishii2026buziness/twitter-collector |
| otakuracy-service | ishii2026buziness/otakuracy-service |
| claude-gateway | ishii2026buziness/claude-gateway |

## デプロイ手順

```bash
# 単一サービス
gh workflow run build.yml --repo ishii2026buziness/<repo>

# 実行状況確認
gh run list --repo ishii2026buziness/<repo> --limit 1
```

## 基本方針

1. ユーザーがサービス名を言ったら上のマッピングでリポジトリを特定する
2. `gh workflow run build.yml --repo <repo>` でデプロイをトリガーする
3. 実行後は run ID を取得して状況を報告する
4. 「全サービス」と言われたら全リポジトリを順次トリガーする
5. デプロイは CI（test → build → deploy）が全部通って初めて完了

## ステータス確認

```bash
gh run list --repo ishii2026buziness/<repo> --limit 1 --json status,conclusion,url
```

## 注意

- `claude-gateway` はワークフローが未設定の可能性あり。エラーが出たらユーザーに伝える
- deploy ジョブは K12 の self-hosted runner（k12）で実行される。runner がオフラインだと失敗する
