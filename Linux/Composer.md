# Composer

phpの色んな使えそうななにがしを  
インストールしてバージョン管理するやつ

[Composer](https://getcomposer.org)

## インストール

### composer.phar作成

[Getting Started](https://getcomposer.org/doc/00-intro.md)

```bash
# 作業ディレクトリで
$ php -r "readfile('https://getcomposer.org/installer');" | php
```

### composer.json作成

```bash
# composer.pharと同じところでconposer.jsonを新規作成
$ vim conposer.json

# もしくは
$ php composer.phar init
```

#### conposer.json例
```json
{
	"require": {
		"symfony/browser-kit": "~2.1",
        "symfony/css-selector": "~2.1",
        "symfony/dom-crawler": "~2.1",
        "guzzlehttp/guzzle": ">=4,<6",
        "fabpot/goutte": "~2.0"
	}
}
```

### 上記を作成したら

```bash
$ php composer.phar install
```

## アップデートしたい時

```bash
$ php composer.phar update
```

## さっそく使う

インストールしたものを使うには

```php
<?php
require 'vendor/autoload.php';
?>
```

