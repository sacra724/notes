# php

## 普通に入れるとPHP5.4がインストールされる

* PHP5.5以上をインストールしたい場合はスルー

```bash
yum install -y php-tcpdf-dejavu-sans-fonts php php-pecl-memcached php-common php-php-gettext php-pear php-tcpdf phpMyAdmin php-mcrypt php-devel php-cli php-process php-pdo php-bcmath php-tidy php-xml php-pecl-igbinary php-gd php-recode php-fpm php-mbstring php-mysqlnd php-pecl-msgpack

$ rpm -qa | grep php
php-tcpdf-dejavu-sans-fonts-6.2.11-1.el7.noarch
php-5.4.16-36.el7_1.x86_64
php-pecl-memcached-2.2.0-1.el7.x86_64
php-common-5.4.16-36.el7_1.x86_64
php-php-gettext-1.0.11-12.el7.noarch
php-pear-1.9.4-21.el7.noarch
php-tcpdf-6.2.11-1.el7.noarch
phpMyAdmin-4.4.15-1.el7.noarch
php-mcrypt-5.4.16-3.el7.x86_64
php-devel-5.4.16-36.el7_1.x86_64
php-cli-5.4.16-36.el7_1.x86_64
php-process-5.4.16-36.el7_1.x86_64
php-pdo-5.4.16-36.el7_1.x86_64
php-bcmath-5.4.16-36.el7_1.x86_64
php-tidy-5.4.16-3.el7.x86_64
php-xml-5.4.16-36.el7_1.x86_64
php-pecl-igbinary-1.2.1-1.el7.x86_64
php-gd-5.4.16-36.el7_1.x86_64
php-recode-5.4.16-36.el7_1.x86_64
php-fpm-5.4.16-36.el7_1.x86_64
php-mbstring-5.4.16-36.el7_1.x86_64
php-mysqlnd-5.4.16-36.el7_1.x86_64
php-pecl-msgpack-0.5.5-5.el7.x86_64
```


# remi入れてPHP5.6にする

```bash
$ yum -y install epel-release
$ rpm -Uvh http://ftp.iij.ad.jp/pub/linux/fedora/epel/7/x86_64/e/epel-release-7-5.noarch.rpm
$ rpm --import http://rpms.famillecollet.com/RPM-GPG-KEY-remi
$ rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
$ yum install --enablerepo=remi gd-last

# PHP関係を1度全てアンインストールする
$ yum remove php-*

$ yum install --enablerepo=remi,remi-php56 php-tcpdf-dejavu-sans-fonts php php-pecl-memcached php-common php-php-gettext php-pear php-tcpdf phpMyAdmin php-mcrypt php-devel php-cli php-process php-pdo php-bcmath php-tidy php-xml php-pecl-igbinary php-gd php-recode php-fpm php-mbstring php-mysqlnd php-pecl-msgpack

# PHP 5.6 か確認
# php x86_64 5.6.14-1.el7.remi remi-php56 2.6 M

$ php -v

$ systemctl start nginx.service
$ nginx -s reload
$ systemctl restart php-fpm
$ systemctl enable  php-fpm
```


# PHP5.6が入らない！

* リポジトリーのプライオリティの設定が邪魔してた

```bash
$ cd /etc/yum.repos.d
$ vim CentOS-Base.repo

# priority=1 をコメントアウトした

[base]
#priority=1
name=CentOS-$releasever - Base
mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=os&infra=$infra
#baseurl=http://mirror.centos.org/centos/$releasever/os/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7

#released updates
[updates]
#priority=1
name=CentOS-$releasever - Updates
mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=updates&infra=$infra
#baseurl=http://mirror.centos.org/centos/$releasever/updates/$basearch/
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
```


# php5.6 + phalcon が使えない！

```bash
# phalcon1.x
$ yum install --enablerepo=remi,remi-php56 php-phalcon

# phalcon2.x
$ yum install --enablerepo=remi,remi-php56 php-phalcon2
```
