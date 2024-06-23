# ローカル環境のセットアップ

このページでは、Wiki の執筆に必要なローカル環境のセットアップ方法を説明します。

## セットアップ

### 前提条件

このリポジトリは `rye` で管理されています。リポジトリを管理するために `rye` CLI がインストールすることを推奨します。

なお、これは必須ではなく、`pip -r` に `requirements.lock` を指定して、必要なライブラリをインストールすることも可能です。また、お好みの仮想環境を使用しても構いませんが、それらの生成するファイルをコミットしないように注意しましょう。

以下の例では、次のソフトウェアがインストール・セットアップされている前提で説明します。

- [rye CLI](https://rye.astral.sh/)
- [GitHub CLI](https://github.com/cli/cli/blob/trunk/README.md#installation)
- [Git](https://git-scm.com/)

### リポジトリのクローン

このリポジトリをクローンします。

```zsh
gh repo clone ichipro-hcu/docs.ichipro.sasakulab.com # GitHub CLI
cd docs.ichipro.sasakulab.com
```

### 必要なライブラリのインストール

必要なライブラリをインストールします。

```zsh
rye sync
```

### プレビューの配信

下記のように `mkdocs serve` を実行するとサーバが起動します。

`http://localhost:8000` にアクセスすることで、プレビューを確認します。終了時は `Ctrl+C` キーを押下します。

```zsh
mkdocs serve # Start the live-reloading docs server.
```

## ドキュメントの編集

### ブランチをチェックアウトする

```sh
git pull
git switch -c new-docs
# git checkout -b new-docs // 古い書き方
```

### ドキュメントを書く

ドキュメントは `src/docs` にあり、そのディレクトリ構成は次のようになっています。

```
docs
  ├── document # この Wiki に関すること
  ├── developers # 開発者マニュアル
  ├── users # ユーザマニュアル
  └── index.md # トップページ
```

適切な場所にディレクトリやファイルを作成したり、すでにあるファイルを編集したりします。

### コミット、プッシュする

編集したドキュメントを、コミットします。

```zsh
git pull -r
git add docs
git commit -m "Update: API について、誤りを変更"
```

### プルリクエストを提出する

文章に対するどのような変更も、Pull Request (PR) を提出して編集権限のあるメンバーからレビューを受けます。PR のレビュアーは自動で割り当てられます。

PR 提出前に、作業中のブランチが main ブランチの最新コミットから分岐しているか必ずチェックしましょう。

もし、最新コミットから分岐していなかった場合は、以下のようにして rebase します。

```zsh
git switch master
git pull
git switch {作業中のブランチ}
git rebase master
```

終わったら、`push` します。

```zsh
git push
```

## レビュー

PR のレビューは、CODEOWNERS によって行われます。

レビューされた後、変更依頼があれば議論・編集し、再度 push し、レビューを依頼します。

変更が承認されたら、`main` ブランチにマージされます

# GitHub Pages へのデプロイ

あなたがコミットした変更は、`main` ブランチにマージされた時に、自動的に GitHub Pages によってデプロイされます。それまでお待ちください。お疲れ様でした。

# 追記

ここまでの説明にわからない点があれば、[超説明・開発フロー](https://scrapbox.io/brain-hackers/%E8%B6%85%E8%AA%AC%E6%98%8E%E3%83%BB%E9%96%8B%E7%99%BA%E3%83%95%E3%83%AD%E3%83%BC) を参照すると良いでしょう。それでもわからなければ、ご相談ください。

# 備考

2024年6月現在、このリポジトリの `CODEOWNERS` は次のメンバーです。

- @m-tsuru
