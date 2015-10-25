# Nginx

```bash
# リポジトリを追加するらしい
$ vi /etc/yum.repos.d/nginx.repo

[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/$releasever/$basearch/
gpgcheck=0
enabled=1

# インストール
$ yum install -y nginx
$ nginx -v

# 起動
$ systemctl start nginx.service
$ systemctl enable nginx.service
$ nginx

# ファイアーウォール
$ firewall-cmd --permanent --zone=public --add-service=http
$ firewall-cmd --permanent --zone=public --add-service=https

# これやる意味わからないので放置
$ firewall-cmd --permanent --zone=public --add-service=ssh

$ systemctl restart firewalld
```

## 確認 (VirtualBoxの場合)

ssh などでログインしたipアドレスにブラウザからアクセスしてみる


## バーチャルホストの設定

```bash
$ cd /etc/nginx/conf.d/
$ vi default.conf

server {
	listen       80;
	server_name  localhost;

	access_log  /var/log/nginx/logs/localhost.access.log  main;

	location / {
        root   /var/www/html/default;
        index  index.html index.htm;
    }
}

# syntaxチェック
$ nginx -t

# 停止
$ nginx -s stop

# 再起動
$ systemctl start nginx.service
$ nginx -s reload
```


## PHPが使えない！

```bash
# php-fpm が必要らしい
$ vi /etc/php-fpm.d/www.conf
; RPM: apache Choosed to be able to access some dir as httpd
user = apache
; RPM: Keep a group allowed to write in log dir.
group = apache

# apache を nginx に変更

; RPM: apache Choosed to be able to access some dir as httpd
user = nginx
; RPM: Keep a group allowed to write in log dir.
group = nginx

$ systemctl start php-fpm
$ systemctl enable php-fpm
$ systemctl status php-fpm


# vi /etc/nginx/conf.d/default.conf
server {
	listen       80;
	server_name  localhost;

	access_log  /var/log/nginx/logs/localhost.access.log  main;

	location / {
		root   /var/www/html/default;
		index  index.php index.html;
	}
	location ~ \.php$ {
		root           /var/www/html/default;
		fastcgi_pass   127.0.0.1:9000;
		fastcgi_index  index.php;
		fastcgi_param  SCRIPT_FILENAME  /var/www/html/default$fastcgi_script_name;
		include        fastcgi_params;
	}
}

$ nginx -t
$ systemctl start nginx.service
$ nginx -s reload
```
