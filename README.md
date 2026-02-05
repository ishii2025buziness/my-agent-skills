# My Agent Skills

自分専用の汎用AIエージェント・スキル集（モノレポ）。

## 構成

## 収録スキル

### 1. [provider-hetzner](file:///home/kento/.gemini/antigravity/playground/luminescent-pulsar/repos/my-agent-skills/skills/provider-hetzner/SKILL.md)
Hetzner Cloud 上に最適なサーバーを自動構築します。
- **特徴**: 2026年現在の高コスパインスタンス（ARM64/CAX系列）を優先選択。
- **機能**: サーバー作成、SSHキー登録、IPアドレスの返却。

### 2. [collector-x-apify](file:///home/kento/.gemini/antigravity/playground/luminescent-pulsar/repos/my-agent-skills/skills/collector-x-apify/SKILL.md)
Apify を介して X (Twitter) からあらゆる公開データを根こそぎ収集します。
- **網羅的な収集モード**:
    - **Search**: 高度な検索クエリ（キーワード、言語、エンゲージメント指定）による広域収集。
    - **User**: 特定アカウントのタイムラインを時系列で追跡。
    - **List**: 指定した X リスト（URL）内の複数アカウントを一括監視。
    - **URL**: 特定のバズ投稿やスレッド、複雑な検索結果をピンポイントで取得。
    - **Profile**: フォロワー数や自己紹介などのアカウント情報のメタデータを抽出。
- **運用方法**: 2026年の制限環境下で最も確実な「高頻度ポーリング」方式を採用。

## 使用方法 (OpenSkills)

```bash
# 全スキルをまとめてインストール
npx openskills install ishii2025buziness/my-agent-skills
npx openskills sync
```

---

# SKILL.md (Root Discovery)

---
name: my-agent-skills-discovery
description: Index for my personal agent skills monorepo. Includes advanced X collection and cloud provisioning.
---

## 収録スキル一覧
- **provider-hetzner**: インフラ構築の自動化。
- **collector-x-apify**: 検索・リスト・スレッドを含む X データの「フルカバー」収集。
