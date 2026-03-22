---
name: repo-routing
description: |
  Routing skill for repository discovery and reuse. Use when the user refers to a repository in natural language and the agent must decide whether to reuse an existing local clone via ghq, search GitHub via gh, create a repo, or clone it into the shared ghq root.
allowed-tools: Bash
---

# Repo Routing

この skill は `gh` と `ghq` の使い分けを決める。GitHub 上の探索は `gh`、ローカル固定配置は `ghq` を使う。

## 判断順

1. ユーザーが既存 repo を開きたい、参照したい、場所を知りたいと言っている場合:
   `ghq list -p` を先に見る。
2. ローカルに見つかった場合:
   その絶対パスを再利用する。再 clone しない。
3. ローカルに見つからず、GitHub 上の repo を探す必要がある場合:
   `gh repo list`, `gh search repos`, `gh repo view` を使って特定する。
4. repo が見つかり、ローカルに必要な場合:
   `ghq get` で `/home/kento/repos` 配下へ入れる。
5. ユーザーが新規 repo 作成を求めた場合:
   `gh repo create` を使い、公開指定がなければ private にする。

## 強いルール

- `/tmp` への一時 clone は避ける
- 現在の repo 配下への場当たり clone は避ける
- GitHub repo は原則 `/home/kento/repos` 配下で再利用する
- repo パスを返すときは絶対パスを優先する

## 委譲ルール

- GitHub 上の探索や作成の詳細は `gh-skill` に従う
- ローカル固定配置や clone 再利用の詳細は `ghq-skill` に従う
