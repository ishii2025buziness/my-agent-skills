---
name: gh-skill
description: |
  GitHub CLI skill for discovering repositories and GitHub resources from natural language. Use when the user wants to find a repo on GitHub, inspect repo metadata, list repos for an owner, search repositories, or create a new GitHub repository. Default to creating repositories as private unless the user explicitly asks for public.
allowed-tools: Bash
---

# GH Skill

`gh` は GitHub 上の探索と確認に使う。ローカル clone の配置管理は `ghq` に任せる。

## 使う場面

- ユーザーが repo 名や owner をうろ覚えで、GitHub 上から探したい
- owner 配下の repo 一覧を見たい
- repo の URL、default branch、visibility などを確認したい
- 新しい GitHub repo を作りたい
- clone 前に対象 repo を特定したい

## 基本方針

1. まず `gh auth status` で利用可能か確認する。
2. repo の候補出しには `gh repo list <owner>` または `gh search repos <query>` を使う。
3. repo の詳細確認には `gh repo view <owner>/<repo>` を使う。
4. 新規 repo 作成には `gh repo create` を使う。
5. 新規 repo は、ユーザーが明示しない限り `private` で作る。
6. repo が確定したら、ローカル導入は `ghq-skill` の流儀に従って `ghq get` を使う。

## よく使うコマンド

```bash
gh repo list <owner> --limit 200
gh search repos <query> --limit 20
gh repo view <owner>/<repo>
gh repo view <owner>/<repo> --json name,owner,url,defaultBranchRef,isPrivate
gh repo create <name> --private
```

## 出力のしかた

- repo 候補は `owner/repo` 形式で短く出す
- 必要なら URL も添える
- repo を新規作成するときは、公開指定がない限り private を使う
- clone やローカル移動が必要なら、その時点で `ghq-skill` に処理を渡す
