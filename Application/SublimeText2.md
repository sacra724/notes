# SublimeText2

## カスタマイズ

### Package Control のインストール
ggrks  
「Package Control インストール」  

## パッケージのインストール
* Ctrl + Shift + p
* "install" で絞り込み
* 「Package Control:Install Package」を選択する
* 使いたいものをインストール

## アンインストール
* Ctrl + Shift + p
* "remove"で絞り込み
* 「Package Control:Remove Package」を選択する
* アンインストールしたいものをクリック

## インストールしてよかったなと思ったプラグイン

### Emmet
ショートカットを簡単にカスタマイズできる。  

ex) 以下のコードを保存し、phpファイルかhtmlファイル内にて var を入力して tabキー

``` json
// Preferences -> Package Setting -> Emmet -> Settings - User
{
	"snippets":
		{
			"php":
			{
				"snippets": {
					"var" : "echo \"<pre>\";\nvar_dump(\\$|);\necho \"</pre>\";"
				}
			},
			"html":
			{
				"snippets": {
					"var" : "<?php\necho \"<pre>\";\nvar_dump(\\$|);\necho \"</pre>\";\n?>",
					"php" : "<?php\n|\n?>",
					"echo" : "<?php echo |?>"
				}
			}
		}
}
```

### OmniMarkupPreviewer
* mdファイルのプレビュープラグイン
* alt + command + o でプレビューしてくれる
* リアルタイムで更新が見れる

### Trailing Spaces
* Markdownの改行がわかりやすくなる（行の最後尾の半角スペース2つ分に色がつく）

### Markdown Extended
* mdファイルのカラーマネージメント的なやつ

### monokai extended
（多分同上）

### Volt
* Phalconを使うのでなんとなく

### SublimeLinter
* シンタックスエラーで怒られると行番号のところに●がつく
* チェックが厳しすぎるのでエラーじゃないだろ！って思うものにも●がつく
