# My Agent Skills

自分専用の汎用AIエージェント・スキル集（モノレポ）。
個別の「部品（Atom）」と、それらを組み合わせた「スタック（Compound）」を管理します。

## 収録スキル

### 🛠️ Stacks (Compound Skills)
複数の部品を組み合わせて特定の目的を達成する上位スキル。
- **[stack-x-scraper](file:///home/kento/.gemini/antigravity/playground/luminescent-pulsar/repos/my-agent-skills/skills/stack-x-scraper/SKILL.md)**: 
  HetznerインフラとApify収集エンジンを統合した、Xデータ収集のフルスタック・ソリューション。

### 🧩 Atomic Skills (Base Skills)
単一の機能を提供する疎結合な部品。
- **[provider-hetzner](file:///home/kento/.gemini/antigravity/playground/luminescent-pulsar/repos/my-agent-skills/skills/provider-hetzner/SKILL.md)**: Hetzner Cloud プロビジョニング。
- **[collector-x-apify](file:///home/kento/.gemini/antigravity/playground/luminescent-pulsar/repos/my-agent-skills/skills/collector-x-apify/SKILL.md)**: Apify を使った X (Twitter) データ収集。

## 使用方法 (OpenSkills)

```bash
npx openskills install ishii2025buziness/my-agent-skills
npx openskills sync
```

---

# SKILL.md (Root Discovery)

---
name: my-agent-skills-discovery
description: Index for my personal agent skills monorepo.
---

## 収録スキル一覧
- **stack-x-scraper**: Hetzner + Apify による垂直統合型 X スクレイパー。
- **provider-hetzner**: Hetzner上でのサーバー構築。
- **collector-x-apify**: 多種多様なモードに対応した X データの収集。
