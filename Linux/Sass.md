# Sass
[Sass](http://sass-lang.com/install)
css内で変数とか使って動的に書けるやつ。  
書き終わったらコンパイルしてcssに書き出す必要がある。  

Compassと一緒に使った方がいいと思うので  
一度Compassをチェック  

## インストール

```bash
# 先にRVMとRubyをインストールしなければならない
$ gem install sass

#バージョン確認
$ sass -v
```

## コンパイル

```bash
# sass [作業したファイル] [書き出すファイル]
$ sass test.scss test.css
```

### 参考サイト
* [Web制作者のためのSassの教科書](http://book.scss.jp/code/)
* [CSSの常識が変わる！「Compass」、基礎から応用まで！](http://liginc.co.jp/designer/archives/11623)
