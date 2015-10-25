# Phalcon

```bash
# インストール
$ cd /var/
$ git clone --depth=1 git://github.com/phalcon/cphalcon.git
$ cd cphalcon/build
$ sudo ./install

# php.ini に追加
$ cd /etc/php.d/
$ vi phalcon.ini

extension=phalcon.so

$ systemctl restart nginx.service
$ nginx -s reload
$ systemctl restart php-fpm

$ php -r "print_r(get_loaded_extensions());" |grep phalcon

# こんな感じのでればおk
[38] => phalcon

# phalcon コマンドを使えるようにする
$ cd /var/
$ mkdir cphalcon-devtools
$ cd cphalcon-devtools/
$ vim composer.json

{
    "require": {
        "phalcon/devtools": "dev-master"
    }
}

$ curl -s http://getcomposer.org/installer | php
$ php composer.phar install
$ ln -s /var/cphalcon-devtools/vendor/bin/phalcon.php /usr/bin/phalcon
$ chmod ugo+x /usr/bin/phalcon
$ phalcon
```


## プロジェクト

* [phalcon-devtools](https://docs.phalconphp.com/en/latest/reference/tools.html)

```bash
$ cd /your/project/dir/
$ phalcon project <project name> <options>
--directory=[directory path] (プロジェクト作成ディレクトリを指定)
--type=[micro|simple|modules] (プロジェクトの雛型タイプを指定する)
--enable-webtools (作成したプロジェクトでGUIツールを利用可能にする)


$ phalcon project --type=simple --directory=.
```
