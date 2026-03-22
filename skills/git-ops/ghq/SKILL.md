---
name: ghq-skill
description: |
  Local repository routing skill using ghq. Use when the user wants to reuse an existing local clone, keep repositories in a stable location, list managed repositories, or clone a GitHub repository into the shared ghq root instead of /tmp or the current repo.
allowed-tools: Bash
---

# GHQ Skill

`ghq` はローカル repo の固定配置と再利用に使う。未知の repo 探索は `gh` に任せる。

## この環境の前提

- `ghq.root` は `/home/kento/repos`
- GitHub repo は原則 `ghq` 管理下へ置く
- `/tmp` や現在の repo 配下への場当たり clone は避ける

## 使う場面

- 既存の local clone を探したい
- repo を固定場所に clone したい
- いまどこに clone されているか知りたい
- 別 repo を参照するときに、同じ repo を何度も clone したくない

## 基本方針

1. まず `ghq list -p` で既存 clone を確認する。
2. 既に存在するなら、そのパスを再利用する。
3. 存在しないなら `ghq get <owner>/<repo>` または `ghq get <url>` で取得する。
4. 作業対象 repo のパスを答えるときは、絶対パスで返す。

## よく使うコマンド

```bash
ghq root
ghq list
ghq list -p
ghq get <owner>/<repo>
ghq get <url>
```

## 実行ルール

- repo を探すときは、まず `ghq list -p` を優先する
- 既存 clone があれば再 clone しない
- GitHub 上で repo を探す必要がある場合だけ `gh-skill` の流儀で `gh` を使う
- 最終的な作業パスは `/home/kento/repos/...` 配下に寄せる
