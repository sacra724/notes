# AngularJsテスト (Karma + phantomjs)
[Unit Testing](https://docs.angularjs.org/guide/unit-testing)  
[E2E Testing](https://docs.angularjs.org/guide/e2e-testing)  
[Testing Example](https://docs.angularjs.org/tutorial/step_08)  

AngularJsのテスト構築から  
テスト実装まで  

karma + phantomjs でテストを書いてみる  

今回はunitテストのみ  
e2eテストは一旦オキで


## PhantomJs

### インストール

* [自分のインストールメモ](https://github.com/masa69/Notes/blob/master/Linux/PhantomJs.md)

## Karma

[Karma](http://karma-runner.github.io/)

### Karma runs on Node.js and is available as an NPM package.

Node.js と npm が必要なのでインストールする  

* [自分のインストールメモ](https://github.com/masa69/Notes/blob/master/Linux/NodeJS.md)

### インストール

[Karma Installation](http://karma-runner.github.io/0.12/intro/installation.html)

```bash
# 作業するディレクトリ直下で行う
$ npm install karma --save-dev
$ npm install -g karma-cli

# バージョン確認
$ karma --version

# 初期化
$ npm init
$ bower init
$ karma init

# エンターで次の項目にいける
# Chrome から PhantomJS に変更。カーソルキー上下で変更し、エンター
---

Which testing framework do you want to use ?
Press tab to list possible options. Enter to move to the next question.
> jasmine

Do you want to use Require.js ?
This will add Require.js plugin.
Press tab to list possible options. Enter to move to the next question.
> no

Do you want to capture any browsers automatically ?
Press tab to list possible options. Enter empty string to move to the next question.
> PhantomJS
>

What is the location of your source and test files ?
You can use glob patterns, eg. "js/*.js" or "test/**/*Spec.js".
Enter empty string to move to the next question.
>

Should any of the files included by the previous patterns be excluded ?
You can use glob patterns, eg. "**/*.swp".
Enter empty string to move to the next question.
>

Do you want Karma to watch all the files and run the tests on change ?
Press tab to list possible options.
> yes

---

```

## テストに必要なファイル

https://github.com/angular/angular-seed を参考  

### package.json

```json
{
  "name": "Tidy",
  "private": true,
  "version": "0.0.0",
  "description": "service by masa69",
  "main": "karma.conf.js",
  "devDependencies": {
    "karma": "0.10",
    "protractor": "~0.20.1",
    "http-server": "^0.6.1",
    "bower": "^1.3.1",
    "shelljs": "^0.2.6",
    "karma-junit-reporter": "^0.2.2",
    "karma-jasmine": "~0.*",
    "karma-phantomjs-launcher": "~0.1",
    "karma-coffee-preprocessor": "~0.1.*",
    "grunt": "~0.4.5",
    "grunt-karma": "~0.6.x"
  },
  "scripts": {
    "postinstall": "bower install",
    "pretest": "npm install",
    "test": "karma start karma.conf.js",
    "preupdate-webdriver": "npm install",
    "update-webdriver": "webdriver-manager update",
    "update-index-async": "node -e \"require('shelljs/global'); sed('-i', /\\/\\/@@NG_LOADER_START@@[\\s\\S]*\\/\\/@@NG_LOADER_END@@/, '//@@NG_LOADER_START@@\\n' + cat('bower_components/angular-loader/angular-loader.min.js') + '\\n//@@NG_LOADER_END@@', 'app/index-async.html');\""
  },
  "repository": {
    "type": "git",
    "url": "git://github.com/masa69/Tidy.git"
  },
  "author": "masa69",
  "license": "MIT",
  "bugs": {
    "url": "https://github.com/masa69/Tidy/issues"
  }
}
```


### .bowerrc

```json
{
  "directory": "bower_components"
}
```


### bower.json

```json
{
  "name": "Tidy",
  "description": "service by masa69",
  "version": "0.0.0",
  "homepage": "git://github.com/masa69/Tidy.git",
  "authors": [
    "masa69"
  ],
  "license": "MIT",
  "private": true,
  "dependencies": {
    "jquery": "~2.x",
    "angular": "~1.3.x",
    "angular-route": "~1.3.x",
    "angular-loader": "~1.3.x",
    "angular-animate": "~1.3.x",
    "angular-mocks": "~1.3.x",
    "angular-sanitize": "~1.3.x",
    "angular-material": "~0.x"
  }
}
```


### karma.conf.js

```js
// Karma configuration
// Generated on Sat Aug 30 2014 17:10:37 GMT+0900 (JST)

module.exports = function(config) {
  config.set({

    // base path that will be used to resolve all patterns (eg. files, exclude)
    basePath: '',


    // frameworks to use
    // available frameworks: https://npmjs.org/browse/keyword/karma-adapter
    frameworks: ['jasmine'],


    // list of files / patterns to load in the browser
    files: [
        '../public/js/bower_components/angular/angular.min.js',
        '../public/js/bower_components/angular-*/*.min.js',
        '../public/js/bower_components/angular-mocks/angular-mocks.js',
        '../public/js/bower_components/jquery/dist/jquery.min.js',
        '../public/js/ngApp.js',
        '../public/js/controllers/*.js',
        '../public/js/models/*.js',
        'test/unit/*.js'
    ],


    // list of files to exclude
    exclude: [
    ],


    // preprocess matching files before serving them to the browser
    // available preprocessors: https://npmjs.org/browse/keyword/karma-preprocessor
    preprocessors: {
    },


    // test results reporter to use
    // possible values: 'dots', 'progress'
    // available reporters: https://npmjs.org/browse/keyword/karma-reporter
    reporters: ['progress'],


    // web server port
    port: 9877,


    // enable / disable colors in the output (reporters and logs)
    colors: true,


    // level of logging
    // possible values: config.LOG_DISABLE || config.LOG_ERROR || config.LOG_WARN || config.LOG_INFO || config.LOG_DEBUG
    logLevel: config.LOG_INFO,


    // enable / disable watching file and executing tests whenever any file changes
    autoWatch: true,


    // start these browsers
    // available browser launchers: https://npmjs.org/browse/keyword/karma-launcher
    browsers: ['PhantomJS'],


    // Continuous Integration mode
    // if true, Karma captures browsers, runs the tests and exits
    //singleRun: false,

    // If browser does not capture in given timeout [ms], kill it
    // CLI --capture-timeout 5000
    captureTimeout: 5000,

    // Auto run tests on start (when browsers are captured) and exit
    // CLI --single-run --no-single-run
    singleRun: true,

    // report which specs are slower than 500ms
    // CLI --report-slower-than 500
    reportSlowerThan: 500,

    //load the needed plugins (according to karma docs, this should not be needed tho)
    plugins: [
      'karma-jasmine',
      'karma-phantomjs-launcher',
      'karma-junit-reporter'
    ]
  });
};
```


## Unitテスト開始

### テストするファイルを生成
[angular-seed](https://github.com/angular/angular-seed)が参考になるかも


### 実際にテストを書いた

Contorollerを軸にしてテストを書こうかなと思います。


```js
'use strict';

describe('BasicpostController as basic, Test', function()
{
	beforeEach(module('AngularApp'));

	var controller, scope;

	beforeEach(inject(
		function($controller, $rootScope)
		{
			scope = $rootScope.$new();

			controller = $controller('BasicpostController', {
				$scope: scope
			});
		}
	));

	it('basic.sayHello() is to put `Hello!` to self.textField', inject(
		function()
		{
			expect(controller.textField).toEqual('');
			controller.sayHello();
			expect(controller.textField).toEqual('Hello!');
		}
	));

});
```

$httpのテストについては、実データは扱わずに***$httpBackend***を利用し、  
仮想のバックエンド（API）の振る舞い（何を投げたら何が返ってくるか）を書き、  
テストで実際にContorllerで呼び出しているメソッドを呼び、
返ってくる結果が意図した値なのかチェックします。

```js
'use strict';

describe('BasicpostController as basic, API Test', function()
{
	beforeEach(module('AngularApp'));

	var $httpBackend, controller, scope, sendParams, returnParams;

	beforeEach(inject(
		function($controller, $rootScope, $injector)
		{
			sendParams = {
				textField: 'test',
				textField2: 'test2'
			};

			returnParams = {
				result: 'success',
        message: '',
				params: {
          'test',
          'test2'
        }
			}

			$httpBackend = $injector.get('$httpBackend');
			$httpBackend
				.expectPOST('receive.php' , sendParams)
				.respond(returnParams);

			scope = $rootScope.$new();

			controller = $controller('BasicpostController', {
				$scope: scope
			});
		}
	));

	afterEach(
		function()
		{
			$httpBackend.verifyNoOutstandingExpectation();
			$httpBackend.verifyNoOutstandingRequest();
		}
	);

	it('basic.doSend() is to get input text data',
		function()
		{
			controller.textField = sendParams.textField;
			controller.textField2 = sendParams.textField2;

			controller.doSend();

			$httpBackend.flush();

			expect(controller.result).toEqual(returnParams);
		}
	);

});
```


### ひとまずテストを開始してみる

```bash
# package.json がある場所でこのコマンドを叩くとまず package.json を見に行く
$ npm test


```

package.json -> scripts.test が実行される  
"test": "karma start karma.conf.js"  

次に karma.conf.js が実行される  


## エラーでた場合

### PhantomJS 1.9.7 (Linux) ERROR ReferenceError: Can't find variable: exports

* [Cannot run unit tests](https://github.com/rubenv/angular-gettext/issues/44)

### バージョンの解決ができないと怒られた場合

```
npm ERR! peerinvalid The package karma does not satisfy its siblings' peerDependencies requirements!
npm ERR! peerinvalid Peer karma-junit-reporter@0.2.2 wants karma@>=0.9
npm ERR! peerinvalid Peer karma-jasmine@0.1.5 wants karma@>=0.9
npm ERR! peerinvalid Peer karma-phantomjs-launcher@0.1.4 wants karma@>=0.9
npm ERR! peerinvalid Peer karma-chrome-launcher@0.1.4 wants karma@>=0.9.3
npm ERR! peerinvalid Peer karma-firefox-launcher@0.1.3 wants karma@>=0.9
npm ERR! peerinvalid Peer karma-html2js-preprocessor@0.1.0 wants karma@>=0.9
npm ERR! peerinvalid Peer karma-requirejs@0.2.2 wants karma@>=0.9
npm ERR! peerinvalid Peer karma-script-launcher@0.1.0 wants karma@>=0.9
npm ERR! peerinvalid Peer karma-coffee-preprocessor@0.2.1 wants karma@>=0.11.14
```

例えば上記の例だと***karma-coffee-preprocessor***のみ、  
求めているkarmaのバージョンが違う（9.x系ではない）ので、  
***node_modules/karma-coffee-preprocessor/package.json***内の  

```json
"peerDependencies": {
    "karma": "0.11.14"
 },
```

を、下記に書き直すか、

```json
"peerDependencies": {
    "karma": "0.9"
 },
```


npm test で呼び出される package.json 内の devDependencies にて、  
バージョンを下げたりする。  

今回は、karma-coffee-preprocessor が 0.2.*系だったので、  
下記のようにバージョンを 0.1.*系にしてみた。

```json
"devDependencies": {
	"karma": "0.9",
	"protractor": "~0.20.1",
	"http-server": "^0.6.1",
	"bower": "^1.3.1",
	"shelljs": "^0.2.6",
	"karma-junit-reporter": "^0.2.2",
	"karma-jasmine": "~0.*",
	"karma-phantomjs-launcher": "~0.*",
	"karma-coffee-preprocessor": "~0.1.*"
},
```



#### 説明不足もいいとこな糞記事だけど日本語で原因が書いてあるので一応
* [npm installでpeerinvalidエラーが出た時の解消方法](http://qiita.com/todogzm/items/e965c47f888c23da1c0a)

#### 解決方法もちゃんと書いてある
* [Strange version problems with npm and karma](http://stackoverflow.com/questions/23586698/strange-version-problems-with-npm-and-karma)

