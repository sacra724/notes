# 自分のコーディング規則メモ

サンプルコードは基本的には***javascript***でいきます。  
たまに***PHP***で書きます。  

***AngularJsがたまに混ざります。***


## 要確認！

### スペース
* スペースの場所 () の周りやカンマ(,)の周りを要確認

### 改行
* {} の改行場所

### インデント
* どこでインデントするか


## 命名規則

* ***javascript***と***PHP***はキャメル
* クラス名の1文字目は大文字


## インデント
* サイズ2の***タブ***で (表現の仕方はこれで合っているのか？)


## コーテーション
* 'シングルコーテーションでいこう'
* "ダブルコーテーション" は変数を文字列の中に入れたい時

``` php
<?php
$hoge = '例え';
echo "これは{$hoge}です";
?>
```


## 定義
``` js
// this は self に
var self = this;

// $rootScope は e に (factory内でイベントを登録する時)
var e = $rootScope;
```

## 型 (classとかfunction)

### PHP

``` php
<?php
// class
class HogeClass extends ParentHogeClass
{
	public static $hoge = null;

	public function getHoge($val, $val2, ...)
	{
		// code ~~
	}
}
?>
```


### javascipt

``` js
// function
var hoge = function(val, val2, ...)
{
	// code ~~
};
```


## メソッドチェーン

```js
var getHoge = function(url, sendParams)
{
	Api.post(url, sendParams)
		.success(function(data, status)
		{
			// code ~~
		})
		.error(function(data, status)
		{
			// code ~~
		});
};
```


## 制御するやつ

```js
// if
if (val === val2) {
	// code ~~
}

// for
for (var i = 0; i < cnt; i++) {
	// code ~~
}

// switch
switch (val) {
	case 'hoge':
		// code ~~
		break;
	case 'hoge2':
		// code ~~
		break;
	default:
		// code ~~
		break;
}
```


## API : HTTP Status Codes

### 適当に決めてみた

| code | text                  | example
|---   |---                    |---
| 200  | OK                    | Success!
| 400  | Bad Request           | バリデーションではじかれた
| 401  | Unauthorized          | Token, AOuthでTokenの取得に失敗した
| 403  | Forbidden             | DBにアクセスして値は取れたが無効
| 404  | Not Found             | DBにアクセスしてみたが値が取れなかった
| 406  | Not Acceptable        | Token, AOuthでTokenの期限が切れていた
| 500  | Internal Server Error | データベース操作の更新系の失敗


### 参考URL
* [https://dev.twitter.com/overview/api/response-codes](https://dev.twitter.com/overview/api/response-codes)

