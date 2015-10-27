## RVM (“Ruby Version Manager”) と Rubyのインストール
RVM は複数の Ruby のインストールと管理を行うことができます。  
このツールは OS X、Linux およびその他 UNIX-like なオペレーティングシステムに対応しています。  

```bash
# これで色々良い感じにしてくれる
$ gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
$ curl -sSL https://get.rvm.io | bash -s stable --ruby
$ source /usr/local/rvm/scripts/rvm

# バージョン確認
$ ruby -v
$ gem -v

# to fix temporarily in this shell session run: 'rvm use ruby-2.2.1'.
# この時点の最新版を使ってみる
$ rvm list known
$ rvm use ruby-2.2.1
```


### 参考サイト
* [Ruby](https://www.ruby-lang.org/ja/installation/)
* [RVM](http://rvm.io/rvm/install)


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
