---
name: stack-x-scraper
description: |
  A compound skill (stack) that provisions a Hetzner Cloud instance as a persistent database and uses Apify to collect X (Twitter) data at high frequencies. 
  Orchestrates 'provider-hetzner' and 'collector-x-apify'.
allowed-tools: Bash Node Python
---

# Stack: X-Scraper (Hetzner + Apify)

このスキルは、インフラ構築（Hetzner）とデータ収集（Apify）を組み合わせた上位の「スタック」を定義します。

## 構成コンポーネント
1.  **Storage Engine**: `provider-hetzner` を使用して、収集データを永続化するARM64サーバーを確保。
2.  **Collection Engine**: `collector-x-apify` を使用して、以下のモードでデータを取得：
    - Search (演算子検索)
    - User (ターゲット追跡)
    - List (バルク監視)
    - URL (スレッド・バズ投稿)
    - Profile (属性抽出)

## 動作フロー
1.  **Provisioning**: `provider-hetzner` でサーバーが未構築なら作成。
2.  **Environment Setup**: `.env` 情報をサーバーまたは実行環境に同期。
3.  **Collection Loop**: `collector-x-apify` を定期的に叩き、指定されたルールでXからデータを抽出。
4.  **Save**: JSONL 形式でストレージに保存。

## メリット
- **自律性**: インフラの準備からデータ収集まで、エージェントがこのスキル一つで完結できる。
- **堅牢性**: APIの仕様変更はApifyが、コスト最適化はHetzner（ARM）が吸収。
