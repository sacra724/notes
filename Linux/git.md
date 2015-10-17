# git

## インストール

```bash
$ yum -y install git git-daemon git-all
$ git --version
git version 1.8.3.1
```


## 設定

```bash
# centos7 環境では下記ファイルはでは見つからなかったのでスルー
$ vi /etc/xinetd.d/git
disable の値を yes から no に変更

【Xinetd 再起動 or 起動】※ Centos7ではよくわからない
$ /etc/rc.d/init.d/xinetd restart or start
```


## gitグループ追加

```bash
# gitグループに作業をするユーザーを追加

$ groupadd git
$ usermod -G git,wheel <userName>
$ usermod -G git <userName>
$ chown -R root:git . <- 必要？？？
```


## githubと連携

### RSAキー生成

```bash
$ ssh-keygen -t rsa -C "hoge@example.com" <- githubで登録したメールアドレス
Enter file in which to save the key (/Home/userName/.ssh/id_rsa): /Home/userName/.ssh/id_rsa
# あとは全てEnterキー
$ cd

# VirtualBox内とかだと .ssh/config は不要
$ vi .ssh/config

Host github
Hostname github.com
Port 22
User <userName> <- githubのユーザー名でいいかと思う
IdentityFile ~/.ssh/id_rsa

$ chmod 0600 .ssh/config

#中身の文字列をコピー
$ cat .ssh/id_rsa.pub
```


### GitHub に SSH鍵を登録（GitHub側）

会社などで自分のアカウント以外のプライベートリポジトリを使用する際にも
自分のアカウントの設定下で以下の手順を行う

Account setting -> SSH Keys -> Add SSH key

先程コピーした id_rsa.pub の中身をここにてペースト



### ユーザー名とメアドを設定する

```bash
$ git config --global user.name "githubで使ってるユーザー名"
$ git config --global user.email "githubで使ってるメアド"
```



## 色をつける

```bash
# 色をつけて若干見やすくする
$ git config --global color.ui auto

# 他にもこんなのが
$ git config --global color.diff auto
$ git config --global color.status auto
$ git config --global color.branch auto
```
