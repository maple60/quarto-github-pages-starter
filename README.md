# Quarto GitHub Pages Starter

Quarto と GitHub Pages で、ブログや情報公開サイトをすぐに始めるためのテンプレートです。

文章中心のサイトなら、R や Python の環境を用意しなくても GitHub 上の操作だけで公開できます。Quarto をローカルに入れると、自分の PC で表示確認もできます。

## まず公開する

一番簡単な方法は、clone ではなく GitHub の **Use this template** を使う方法です。

### 1. 新しいリポジトリを作る

1. このテンプレートリポジトリのページを開きます。
2. **Use this template** をクリックします。
3. **Create a new repository** を選びます。
4. Repository name を決めます。
5. Public を選びます。
6. **Create repository** をクリックします。

リポジトリ名は、公開したいサイトの種類に合わせて選びます。

- 個人サイトにする場合: `USERNAME.github.io`
- プロジェクトサイトにする場合: 好きな名前。例: `my-blog`

`USERNAME` は自分の GitHub ユーザー名です。

### 2. 最初に編集するファイル

新しく作ったリポジトリで、まず次のファイルを書き換えます。

| ファイル | 何を書くか |
| --- | --- |
| `_quarto.yml` | サイト名、URL、GitHub URL、フッター |
| `index.qmd` | トップページの文章 |
| `about.qmd` | プロフィールや連絡先 |
| `posts/2026-01-01-welcome/index.qmd` | サンプル記事。自分の記事にするか削除する |

特に `_quarto.yml` の `site-url` は、自分の公開 URL に合わせます。

個人サイトの場合:

```yaml
website:
  title: "My Website"
  site-url: "https://USERNAME.github.io/"
```

プロジェクトサイトの場合:

```yaml
website:
  title: "My Website"
  site-url: "https://USERNAME.github.io/REPOSITORY_NAME/"
```

### 3. 変更を保存して push する

GitHub の画面上で編集した場合は、各ファイルの編集画面で **Commit changes** をクリックします。

ローカルで編集した場合は、次のように push します。

```bash
git add .
git commit -m "Update site content"
git push
```

### 4. GitHub Actions の成功を確認する

1. リポジトリ上部の **Actions** を開きます。
2. **Quarto Publish** という workflow を開きます。
3. 最新の実行が緑色のチェックになっていることを確認します。

この workflow は Quarto でサイトを作り、公開用の `gh-pages` ブランチへ出力します。

### 5. GitHub Pages を有効化する

初回だけ、GitHub の GUI で Pages の公開元を設定します。

1. リポジトリ上部の **Settings** を開きます。
2. 左側メニューの **Pages** を開きます。
3. **Build and deployment** の **Source** で **Deploy from a branch** を選びます。
4. **Branch** で `gh-pages` を選びます。
5. フォルダは `/ (root)` を選びます。
6. **Save** をクリックします。

`gh-pages` が選べない場合は、先に **Actions** で **Quarto Publish** が一度成功しているか確認してください。

### 6. 公開 URL を確認する

しばらく待ってから、次の URL を開きます。

- 個人サイト: `https://USERNAME.github.io/`
- プロジェクトサイト: `https://USERNAME.github.io/REPOSITORY_NAME/`

GitHub Pages の画面にも公開 URL が表示されます。

## 記事を書く

新しい記事は `posts/` の下に作ります。

`posts/00-template/` をコピーして、日付と短い名前を付けたディレクトリを作ります。

```text
posts/
  2026-01-01-my-first-post/
    index.qmd
```

記事ファイルの先頭には YAML front matter があります。

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

下書きの間は `draft: true` にします。公開するときは `draft: false` にします。

## ローカルで確認する

Quarto をインストールしている場合は、自分の PC で表示確認できます。

```bash
quarto preview
```

HTML を生成するだけなら次を実行します。

```bash
quarto render
```

生成されたサイトは `_site/` に出力されます。`_site/` は Git に追加しません。

## R や Python を使う場合

このテンプレートの GitHub Actions は、最初は Quarto だけをセットアップします。

R や Python のコードを GitHub Actions 上で実行したい場合は、あとから workflow と依存関係ファイルを追加します。

- R を使う: `r-lib/actions/setup-r` や `r-lib/actions/setup-renv` を追加する
- Python を使う: `actions/setup-python` と `requirements.txt` を追加する

まずは文章中心で公開し、必要になった時点で実行環境を足す方が管理しやすいです。

## 含まれているもの

- `_quarto.yml`: Quarto website の設定
- `index.qmd`: トップページ
- `posts.qmd`: 記事一覧ページ
- `about.qmd`: 自己紹介ページ
- `custom.scss`: 簡単なテーマ調整
- `posts/00-template/`: 記事テンプレート
- `posts/2026-01-01-welcome/`: サンプル記事
- `.github/workflows/publish.yml`: GitHub Actions による自動公開
- `.nojekyll`: GitHub Pages で Jekyll 処理を無効化するためのファイル

## ライセンス

このテンプレートのコードと設定ファイルは MIT License です。

記事本文や画像など、あなたが追加するコンテンツのライセンスは自分で決めてください。フッターのライセンス表示も必要に応じて変更してください。

## REFERENCE / Q&A

### 新しいリポジトリをこのテンプレートから作りたい

GitHub の **Use this template** を使います。

公式ドキュメント: [Creating a repository from a template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)

### GitHub Pages の公開元を設定したい

`Settings > Pages` で、`Deploy from a branch`、`gh-pages`、`/ (root)` を選びます。

公式ドキュメント: [Configuring a publishing source for your GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

### Quarto サイトを GitHub Pages で公開したい

このテンプレートでは GitHub Actions が Quarto をレンダリングし、`gh-pages` ブランチへ公開します。

公式ドキュメント: [GitHub Pages - Quarto](https://quarto.org/docs/publishing/github-pages.html)

### Quarto website の基本を知りたい

`_quarto.yml` でサイト名、ナビゲーション、テーマ、フッターなどを設定します。

公式ドキュメント: [Creating a Website - Quarto](https://quarto.org/docs/websites/)

### トップページを変えたい

`index.qmd` を編集します。最近の記事一覧は `listing` 設定で表示しています。

### ナビゲーションを変えたい

`_quarto.yml` の `website.navbar.left` を編集します。

### サイト名を変えたい

`_quarto.yml` の `website.title` と、必要に応じて `index.qmd` の `title` を編集します。

### 公開 URL を変えたい

`_quarto.yml` の `website.site-url` を編集します。プロジェクトサイトでは末尾にリポジトリ名を含めます。

### 記事一覧に記事が出ない

記事の YAML を確認します。`draft: true` の記事は公開サイトには出ません。公開する場合は `draft: false` にします。

### `gh-pages` ブランチが選べない

先に **Actions** で **Quarto Publish** が成功しているか確認します。成功すると、公開用の `gh-pages` ブランチが作られます。

### Actions が失敗する

**Actions > Quarto Publish** を開き、失敗した実行のログを確認します。R や Python のコードを追加した場合は、必要な実行環境やパッケージが workflow に入っているか確認します。

### 自分の PC で確認したい

Quarto をインストールして、リポジトリの中で `quarto preview` を実行します。

公式ドキュメント: [Quarto command reference](https://quarto.org/docs/reference/)

### 独自ドメインを使いたい

Quarto プロジェクトのルートに `CNAME` ファイルを置き、ドメイン名を書きます。GitHub Pages 側と DNS 側の設定も必要です。

公式ドキュメント: [GitHub Pages - Quarto: Custom Domain](https://quarto.org/docs/publishing/github-pages.html#custom-domain)
