
# MongoDB

##️ インストール

``` bash

$ vim /etc/yum.repos.d/mongodb-org.repo

# mongodb-org.repo

[mongodb-org]
name=MongoDB Repository
baseurl=http://downloads-distro.mongodb.org/repo/redhat/os/x86_64/
gpgcheck=0
enabled=1

$ yum install -y mongodb-org
$ mongo --version

# Centos6
$ service mongod start
$ chkconfig mongod on

# Centos7
$ systemctl start mongod

$ mongo

> exit

```
