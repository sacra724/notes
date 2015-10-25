# mysql

## インストール

```bash
$ yum install http://dev.mysql.com/get/mysql-community-release-el7-5.noarch.rpm

#適当なレポジトリ名を探す
$ cat /etc/yum.repo.d/mysql-community.repo

# v5.6が2015/10現在の最新
$ yum -y install --enablerepo=mysql56-community mysql-community-client.x86_64 mysql-community-devel.x86_64 mysql-community-server.x86_64

$ mysql --version
```


## 起動
```bash
$ systemctl start mysqld.service
$ systemctl enable mysqld.service
```


## ユーザーを作成
``` bash
$ mysql -u [userName] -p	mysqlに接続
$ Enter password: # 初期設定だとパスワードは設定されていないのでエンターキーを押す
```

### パスワードを設定

```bash
# 現在接続しているユーザーのパスワードを設定します
$ SET PASSWORD = PASSWORD('some password');

# 指定したユーザーのパスワードを設定します。
$ SET PASSWORD FOR user = PASSWORD('some password');
```


### ユーザーを作成する

``` bash
$ 
$ GRANT SELECT , INSERT , UPDATE , DELETE ON *.* TO [userName] | Ｄ@"localhost" IDENTIFIED BY "[password]";
```
