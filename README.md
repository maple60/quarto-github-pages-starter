# Quarto GitHub Pages Starter

Quarto と GitHub Pages で、ブログや情報公開サイトをすぐに始めるためのテンプレートです。

このテンプレートは、最初に公開するための最小構成にしています。R や Python の実行環境は入れていないので、文章中心のブログなら GitHub Actions だけで公開できます。解析コードを実行する記事を追加する場合は、あとから依存関係を足してください。

## このテンプレートでできること

- Quarto website として記事一覧、トップページ、自己紹介ページを作る
- `posts/` に記事を追加してブログとして公開する
- GitHub Actions で自動レンダリングし、`gh-pages` ブランチへ公開する
- 日本語記事と英語記事のどちらにも使う
- GitHub の Template repository として再利用する

## 使い方

1. GitHub でこのリポジトリから新しいリポジトリを作成します。
2. 個人サイトにする場合は、リポジトリ名を `USERNAME.github.io` にします。
3. プロジェクトサイトにする場合は、任意のリポジトリ名にします。
4. `_quarto.yml` の `title`、`site-url`、GitHub URL、フッターを自分用に書き換えます。
5. `index.qmd` と `about.qmd` を自分用に書き換えます。
6. `posts/00-template/` をコピーして、新しい記事ディレクトリを作ります。
7. 変更を `main` ブランチへ push します。
8. GitHub の `Settings > Pages` で、公開元を `gh-pages` ブランチの `/` にします。

公開 URL は次のようになります。

- 個人サイト: `https://USERNAME.github.io/`
- プロジェクトサイト: `https://USERNAME.github.io/REPOSITORY_NAME/`

## ローカルで確認する

Quarto をインストールしている場合は、次のコマンドで確認できます。

```bash
quarto preview
```

静的ファイルだけを生成する場合は、次を実行します。

```bash
quarto render
```

生成されたサイトは `_site/` に出力されます。

## 記事を追加する

`posts/00-template/` をコピーして、日付と短い名前を付けたディレクトリを作ります。

```text
posts/
  2026-01-01-my-first-post/
    index.qmd
```

`index.qmd` の先頭にある YAML を編集します。

```yaml
---
title: "My First Post"
description: "Short description"
date: "2026-01-01"
date-modified: "2026-01-01"
draft: false
categories: [quarto, blog]
---
```

下書きの間は `draft: true` にしてください。公開する時に `draft: false` にします。

## R や Python を使う場合

このテンプレートの GitHub Actions は、Quarto だけをセットアップします。

R のコードを GitHub Actions 上で実行したい場合は、workflow に `r-lib/actions/setup-r` や `r-lib/actions/setup-renv` を追加してください。Python のコードを実行したい場合は、`actions/setup-python` と `requirements.txt` を追加してください。

まずは文章中心で公開できる形にして、必要になった時点で実行環境を足す方が、初心者には管理しやすいです。

## テンプレート公開者向け

このリポジトリをテンプレートとして公開する場合は、GitHub で次を設定します。

1. リポジトリを Public にする。
2. `Settings > General` で `Template repository` を有効にする。
3. README の `USERNAME`、`REPOSITORY_NAME`、サンプル文言がテンプレートとして自然か確認する。

## ライセンス

このテンプレートのコードと設定ファイルは MIT License です。

記事本文や画像など、あなたが追加するコンテンツのライセンスは自分で決めてください。フッターのライセンス表示も必要に応じて変更してください。
