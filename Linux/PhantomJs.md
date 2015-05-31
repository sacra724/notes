# PhantomJs
[PhantomJs](http://phantomjs.org/)

VirtualBox + CentOs6 での  
ユニットテストに使う予定  

## インストール

[Build](http://phantomjs.org/build.html)

```bash
# 事前に色々インストール (Remiを使ってるのでとりあえずRemiつけてインストール)
$ yum install fontconfig freetype libfreetype.so.6 libfontconfig.so.1 libstdc++.so.6 --enablerepo=remi
$ yum install gcc gcc-c++ make git openssl-devel freetype-devel fontconfig-devel --enablerepo=remi

# 適当な場所にPhantomJsをcloneする (ここでは /var/ にcloneしようと思う)
$ mkdir /var/phantomjs
$ cd /var/phantomjs
$ git clone git://github.com/ariya/phantomjs.git .

$ ./build.sh

# 上記の方法だとけっこう時間がかかるから下記のダウンロードページの内容から
# 一旦ダウンロードしてからビルドするのががおすすめと書いてある
# が、http://phantomjs.org/download.html どうせ最終的にやることは一緒では
Building PhantomJS from source takes a very long time, anywhere from 30 minutes
to several hours (depending on the machine configuration). It is recommended to
use the premade binary packages on supported operating systems.

For details, please go the the web site: http://phantomjs.org/download.html

# buildが自分の環境だと2時間強かかった

# rpm-build パッケージがインストールされているか確認
$ rpm -qa | grep build

# ない場合
$ yum install rpm-build

$ cd rpm
$ ./mkrpm.sh phantomjs

# /tmp/phantomjs-1.9/bin/ あたりに phantomjs があるので /usr/bin/ にコピーする
$ cp /tmp/phantomjs-1.9/bin/phantomjs /usr/bin/phantomjs
```

### その他参考URL
* [CentOSにPhantomJSをインストールする](http://konboi.hatenablog.com/entry/2013/07/05/173957)

## 動作確認

手始めに[Quick Start](http://phantomjs.org/quick-start.html)のHello, World!を試す。

```bash
$ phantomjs hello.js
```

が動いたら、  
[Screen Capture](http://phantomjs.org/screen-capture.html)のgithub.jsを試す。

スクショ保存されてたら完了

