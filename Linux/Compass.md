# Compass
[Compass](http://compass-style.org/)
sassと一緒に使うとパネェ  
書く量が減る  

## インストール

```bash
$ gem install compass

#バージョン確認
$ compass -v
```

## 早速使おう

```bash
#cssやらjsやら置く予定の場所まで移動
$ cd [cssやらjsやら置く予定の場所]

#プロジェクト生成
$ compass create .

---
directory ./sass/
directory ./stylesheets/
   create ./config.rb
   create ./sass/screen.scss
   create ./sass/print.scss
   create ./sass/ie.scss
   create ./stylesheets/ie.css
   create ./stylesheets/print.css
   create ./stylesheets/screen.css
.....
...
..

---

# コンパイル
$ compass compile

# ウォッチ。ファイルに変更があると自動でcompileしてくれる
$ compass watch
```

### config.rb
でディレクトリ名の変更など色々設定できる

### コンパイルするとき

```bash
compass compile [path/to/project]
```

### ファイルに変更があったら自動でコンパイルする機能もある

```bash
compass watch [path/to/project]
```


### 下記のcssを追加
してくださいと書いてあったので適当に追加

``` html
<head>
  <link href="/stylesheets/screen.css" media="screen, projection" rel="stylesheet" type="text/css" />
  <link href="/stylesheets/print.css" media="print" rel="stylesheet" type="text/css" />
  <!--[if IE]>
      <link href="/stylesheets/ie.css" media="screen, projection" rel="stylesheet" type="text/css" />
  <![endif]-->
</head>
```

### 参考サイト
* [Web制作者のためのSassの教科書](http://book.scss.jp/code/)
* [CSSの常識が変わる！「Compass」、基礎から応用まで！](http://liginc.co.jp/designer/archives/11623)



## アップデート

```bash
# バージョン確認
$ gem -v
$ sass -v
$ compass -version

# アップデート ※最新版であれば必要なし
$ sudo gem update --system
$ sudo gem update sass
$ sudo gem update compass
```
