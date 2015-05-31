# Guzzle
[Guzzle](http://guzzle.readthedocs.org/en/latest/index.html)  
HttpRequest的なやつ  

## インストール

```bash
# 作業するディレクトリまで移動してインストール
# composer.json あったら別の場所に一度落とすのがいいのかなぁ
$ curl -sS https://getcomposer.org/installer | php

# Guzzle関係のを入れる
$ php composer.phar require guzzlehttp/guzzle:~4

# 作成されるファイル群
composer.json
composer.lock
composer.phar
vendor/
```

## 早速使う

```php
<?php
require 'vendor/autoload.php';

class HttpRequest
{
  protected function post($arr)
  {
  	// body は投げるもの key => value で指定する
    $response = \GuzzleHttp\post('http://httpbin.org/post' , [
      'body' => $arr
    ]);
    return $response->getBody();
  }
}
$hr = new HttpRequest();
var_dump(
	$hr->post(array(
		'key1' => 'value1',
		'key2' => 'value2'
	))
);
?>
```

使いやすいかも