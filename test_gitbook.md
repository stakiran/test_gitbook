# GitBook を試用してみた

# 前提
- Windows 10 Home

# gitbook でアカウント作って設定する（手順一部うろ覚え）
- https://www.gitbook.com/ にアクセスして、github アカウントでサインインする
- github 上で、gitbook へのアクセス権を付与する
  - この時どの repo を gitbook から見えるようにするか設定できるはず(Repository access)
  - 「All repositories」がてっとり早いが、不安なら「Only select repositories」にて必要な repo だけ指定する
- gitbook から連携先候補となる github repo を登録する
  - 連携したい github repo を github でテキトーに作る(仮に bookrepo と名付ける)
  - gitbook 側で settings > github > install github integration により、作った repo を追加
- 新しく book をつくる
  - 初回時は https://www.gitbook.com/@stakiran/settings/github の create a book from github から bookrepo を選んで new book する
  - 初回以外の時は https://www.gitbook.com/@stakiran/dashboard の New Book からいったん book を作った後、settings > github から bookrepo と sync させる
    - ここで [sync error](https://help.gitbook.com/github/how-can-i-resolve-github-sync-errors.html) が出る時があるが、GitHub 側のボタンをクリックする（GitHub Repo 側を使って Sync が実行される。この辺よーわからん）

# gitbook コマンドを入れる
gitbook のプロジェクト構成（どんなファイルをどんなフォーマットで用意してリポジトリに push すればええの？）がわからんので、その辺をラップしてる gitbook コマンドを使うことにした。

まずは https://nodejs.org/en/ より npm インストーラをダウンロード＆インストール。

続いてコマンドを叩いて gitbook をインストールしていく

```
$ npm -g install gitbook
$ npm -g install gitbook-cli
```

# bookrepo 上で gitbook の構成をつくる

```
$ git clone https://github.com/stakiran/test_gitbook
$ cd test_gitbook

$ gitbook init
Installing GitBook 3.2.3 ← 初回起動なんで gitbook npm module に必要な分が
                            色々インストールされてるんだと思う。1分くらいかかったよ。
gitbook@3.2.3 C:\Users\stakiran\AppData\Local\Temp\tmp...W\node_modules\gitbook
├── escape-string-regexp@1.0.5
├── escape-html@1.0.3
├── destroy@1.0.4
...

$ dir
2017/09/18  07:43                14 README.md
2017/09/18  07:47                40 SUMMARY.md
```

# gitbook 上に反映させるところまで
bookrepo に push すればいいだけ。（既に sync してるはずなので） bookrepo への push 時に、gitbook 側でもビルドが自動で走る。

bookrepo に push して、

```
$ git add -A
$ git commit -m "first commit."
$ git push origin master
```

成果物を見てみようか.

- ブック名: testbook_from_github
- [ビルド状況](https://www.gitbook.com/book/stakiran/testbook_from_github/activity)
- [製本ページ](https://stakiran.gitbooks.io/testbook_from_github/content/)

# 次やること
- サンプル見ながらページを構築していく
  - https://github.com/gomachan46/gitbook-example
  - https://gomachan46.gitbooks.io/how-to-use-gitbook/content/gitbook-cli/rule.html
- markdown の表記一通り試す
- SUMMARY.md って既存ファイルから自動生成できへんの？

# 以下はゴミ

# Github Pages で使う（まだ試してない）
```
$ gitbook build
$ dir *book*
2017/09/18  07:56    <DIR>          _book
```

この _book フォルダを丸ごと github pages 用 repo にぶちこめばいいらしい。試してない。

ただローカルで _book\index.html を開いてみると、目次クリックしても他ページが開かれないんだけど……。
