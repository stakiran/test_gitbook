# github markdown grammers
gitbook はどこまで対応しているかな？

要約:

- アンカーリンクは使えません
- リストインデントは space 2 個単位
- テーブルはセル中の文字数が少なくても横長いっぱいまで引き伸ばされる
- コードハイライトは (GitHubほどじゃないが) 一応対応してる

# 文字整形
**太字** は `**太字**` と書き、 *イタリック* は `*イタリック*` と書く。 ~~打ち消し線~~ は `~~打ち消し線~~` と書く。

文章中に挿入する場合は前後に空白を入れること。

# 空行と改行

 改行したい場合、行末にスペース2個を書くか、空行を一つ書く。

# リスト

* リストは行頭に `*` あるいは `-` を書く
* サブリスト(nested list)はスペース2個(Gitbucketの場合は4個)でインデントする
* なお、リストを認識させるには、本文との間に空行を一つ以上入れる必要がある

リスト例

* 項目1
* 項目2
  * サブ項目1
    * サブサブ項目
  * サブ項目2

リスト例(ハイフン使用)

- 項目1
- 項目2
  - サブ項目1
    - サブサブ項目
  - サブ項目2

番号付きリストは行頭に `0.` や `1.` を書く。

1. ほげ
1. ふが
  1. サブ番号リスト
    1. サブサブ番号リスト
1. サブ番号リスト2

# 引用

* 引用は行頭に `>` を書く
* `>` を重ねると(例:`>>`)インデントできる

> 引用文です
> ほげほげほげ
>> 重ねて書くこともできます
>> ふがふが
> 一度重ねて書いたらインデントを戻すことができません(この行は > 一つなのに >> とみなされている) 

引用機能は、本来は改行無しの長い文章をこのように引用したい場合に使うみたい。

>0123456789012345678901234567890123456789012345678901234567890123456789012345678901234567890123456789長い行のサンプルです

# 水平線

水平線は三つ以上の `-` または `*` を連続で書く。文章と重なると見出しになっちゃうので、空行を入れて離して書いてあげて。

***

# pre記法とコードハイライト

行頭にスペース四個 or タブを書く。

	#include <stdio.h>

	int main(){
		printf("Hello world.\n");
		return 0;
	}

あるいは ``` で囲ってもいい。コードハイライトにもなる。

以下は c 言語ソース。

```c
include <stdio.h>

int main(){
	printf("Hello world.\n");
	return 0;
}
```

以下は python ソース。

```python
import sys

argv = sys.argv
argc = len(argv)

for i in range(argc):
	print '%d argument:%s' % (i, argv[i])
```

一行のインラインコード(いわゆるリテラル)を書きたいなら backtick で囲む。`python -c "print 'hello.'"` 

リテラルの場合、前後にスペースは不要。

# <a name="section_link">リンク

ウィキ内他ページへのリンク: [[AnotherPage]]

	[[AnotherPage]]

ただし拡張子は .html が補われるため .md などの場合はこうする:[AnotherPage](another_page.md)

	[AnotherPage](another_page.md)

アンカーリンク:[Goto Link Section](#section_link)

	アンカー先:
	# <a name="section_link"></a>リンク
	
	アンカー利用者:
	[Goto Link Section](#section_link)

ウィキ外他ページへのリンク:[Example.com](http://example.com/)

	[Example.com](http://example.com/)

# テーブル

テーブルは以下のように書く。属性と区切り('---'とその上の部分)は必ず書かないといけない(これがないとテーブルとみなされない)。

| 項目 | 内容   |
| ---- | ------ |
| key1 | value1 |
| key2 | value2 |

```
| 項目 | 内容   |
| ---- | ------ |
| key1 | value1 |
| key2 | value2 |
```

実は区切り部分は `| --- | --- | ...` のように最低三つのハイフン `---` をスペース区切りで繋げればよいし、行頭と行末の `|` も要らないし、無理に見栄えをプロポーショナルに合わせる必要もない。

項目 | 内容
---- | ---
key1 | value1
きー２ | ばりゅー２

```
実は最低限以下で済む

項目 | 内容
--- | ---
key1 | value1
きー２ | ばりゅー２
```

セルが長い場合、改行はされずに横長になってしまう。

attr1 | attr2 | attr3
--- | --- | ---
key1 | value1 | value2
key2 | value2-verylooooooooooooooooooooooooooooooooooooooooooooooooong | value2

セル内改行は `<br>` を使う

attr1 | attr2 | attr3
--- | --- | ---
key1 | value1 | value2
key2 | value2-veryloooo<br>ooooooooooooooooooooooooo<br>oooooooooooooooooooong | value2

# 見出し

見出しの書き方は以下の二種類があります。

	# 見出し
	
	見出し
	======

サブ見出しは以下のとおり。

	## 中見出し       ← '#'を増やす
	
	中見出し
	--------          ← 大見出しとは違う記号('#','=','-'のいずれか)を使う

一般的には二行表記を使う人が多いですが、テキストエディタのアウトライン機能で捕捉したい場合は一行表記が(正規表現を書きやすいという意味で)楽です。

# 画像

```
![AltText](image_uri)

[image1]: imagepath.png "Title"

<img src="IMAGE-URL" alt="ALTTEXT" width="96" height="96" />
```

以下は内部リンク `![myavatar](myavatar.jpg)`

![myavatar](myavatar.jpg)

以下は外部リンク `![myavatar](https://avatars1.githubusercontent.com/u/23325839)`

![myavatar](https://avatars1.githubusercontent.com/u/23325839)

以下は内部リンク:  `![myavatar](/myavatar.jpg)`

![myavatar](/myavatar.jpg)

以下は内部リンク:  `![myavatar](.myavatar.jpg)`

![myavatar](.myavatar.jpg)

以下は内部リンク:  `![myavatar](./myavatar.jpg)`

![myavatar](.myavatar.jpg)
