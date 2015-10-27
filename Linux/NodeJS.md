# NodeJs


## yumでインストール (Nodebrewのほうがしっくりきたのでスルー)

```bash
$ yum install nodejs npm

#epelたん
$ yum install nodejs npm --enablerepo=epel

#remiたん
$ yum install nodejs npm --enablerepo=remi

#バージョン確認（control + z で終了）
$ node -v
```



## 最新版をインストール (個人的に微妙なやり方なのでスルー)

```bash
g++が入っていない場合はインストールしておく

$ yum install gcc-c++
$ wget http://nodejs.org/dist/v0.12.2/node-v0.12.2.tar.gz
$ tar xvf node-v0.12.2.tar.gz
$ rm node-v0.12.2.tar.gz
$ cd node-v0.12.2
$ ./configure
$ make
$ make install

$ node -v
```


## nodebrewでNodeJsのバージョンを管理する (こっちのほうが好き)

```bash
# もしNodeが既にインストールされていたら削除する
$ node -v

# 削除方法 その1
$ curl -o uninstall-node.sh https://gist.githubusercontent.com/nicerobot/2697848/raw/uninstall-node.sh
$ chmod u+x uninstall-node.sh
$ ./uninstall-node.sh
$ rm uninstall-node.sh
$ sudo rm -rf /usr/local/include/node
$ sudo rm -rf /usr/local/lib/dtrace
$ rm -rf ~/.node-gyp
$ rm -rf ~/.npm
$ rm -rf ~/.sourcemint

# 削除方法 その2
$ yum remove -y nodejs npm

# 削除方法 その3
$ npm uninstall npm -g

# 削除方法 その4
$ cd node/package/dir/
$ make uninstall


# nodebrewのインストール
$ curl -L git.io/nodebrew | perl - setup
$ export PATH=$HOME/.nodebrew/current/bin:$PATH
$ nodebrew -v

# nodejsのインストール
$ nodebrew ls-remote
$ nodebrew install-binary v4.2.0
$ nodebrew ls
$ nodebrew use v4.2.0
$ node -v

# migrate-package コマンドは npm install -g したパッケージを移行してくれる
$ nodebrew migrate-package v4.2.0

# bash or zsh にパスを通す
$ vi .zshrc
# もしくは
$ vi .bashrc

# 下記の行を追加
export PATH=$HOME/.nodebrew/current/bin:$PATH
```



