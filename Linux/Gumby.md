# Gumby CSS Framework
[Gumby](http://gumbyframework.com/docs/#!/installing-ruby)  
Ruby , Sass , Compass , modular-scale を使えと書いてあるので  
さっそくインストールする  

## 対応ブラウザ
* Chrome
* Firefox
* Opera
* Internet Explorer 8 – 10

## RVM (“Ruby Version Manager”) と Rubyのインストール
RVM は複数の Ruby のインストールと管理を行うことができます。  
このツールは OS X、Linux およびその他 UNIX-like なオペレーティングシステムに対応しています。  

```bash
# これで色々良い感じにしてくれる
$ curl -sSL https://get.rvm.io | bash -s stable --ruby
$ source /usr/local/rvm/scripts/rvm

# バージョン確認
$ ruby -v

# to fix temporarily in this shell session run: 'rvm use ruby-2.1.2'.
$ rvm use ruby-2.1.2
```


### 参考サイト
* [Ruby](https://www.ruby-lang.org/ja/installation/)
* [RVM](http://rvm.io/rvm/install)


## Sass , Compass , modular-scaleのインストール

```bash
$ gem install compass modular-scale sass

# とりあえずアップデート
$ gem update

# バージョン確認
$ sass -v
$ compass -v
```

* [Sass](http://sass-lang.com/)
* [Compass](http://compass-style.org/)
* [modular-scale](https://github.com/Team-Sass/modular-scale)


## Gumbyフレームワークをclone

```bash
# とりあえず適当な場所に落とす
$ git clone git@github.com:GumbyFramework/Gumby.git .
```

### index.html などみながら作業場所に必要なファイルをコピーして移動したり既存ファイルに追加したり

```bash
# 移動、編集したファイル
.gitignore
.jshintrc
.jshintignore
config.rb
bower.json

/sass/
/fonts/
/js/libs/
/js/plugins.js
/js/main.js
```


## Zshで使う場合

```bash
# 上記インストールを終えてから
$vim .zshrc

#--- .zshrc ---
# 1行追加
export PATH=$PATH:$HOME/.rv/bin
#--- /.zshrc ---

# 再起動
# Zshの再起動は新しく画面を開きログインしなおせばいいとか
```

## 上記作業が終わったら
後はCompassとSassを駆使して  
ゴリゴリ作業するだけ  
