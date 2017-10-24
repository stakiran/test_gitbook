# test_gitbook
gitbook.com のテスト。

- [GitBook サンプル](https://stakiran.gitbooks.io/testbook_from_github/)
- [GitHub リポジトリ](https://github.com/stakiran/test_gitbook)
- [ビルドステータス](https://www.gitbook.com/book/stakiran/testbook_from_github/activity) 要ログイン

# 雑感
- お手軽で良い
  - gitbook.com へのログインは github アカウントのみでいける
  - github repo に push したら、book 側でもビルドされるよう sync できる(github repo の master branch と sync できる)
  - 文法は普通の markdown ファイルを書く＆ `SUMMARY.md` ファイルからリンク張る（これが目次になる）だけ
- npm 製の gitbook コマンドも使ってみたけど、別に要らなくない？
  - せいぜい `gitbook build` でローカルビルドして確かめるくらいか
  - でもローカルビルドで生成された index.html、リンクが正しく機能しないんだけど…… in ver 2.3.2
- aタグで任意アンカー名のアンカーリンク使えないのは痛いなぁ

# やりたいこと
- アンカーリンクで飛んだ時にアニメーション入るのうざい、消せませんかね
- mybook.md という一冊の本を書いた単一ファイルから SUMMARY.md を構築するスクリ
  - 見出しに日本語が入ってても問題なくリンクしてくれる
  - [アンカー名アルゴリズムは github と同じ](http://qiita.com/sta/items/9481c94e0fc36f27fa92) に見えるがはてさて……
