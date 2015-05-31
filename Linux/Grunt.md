# Grunt

## 準備
grunt-cli グローバルインストール

```bash
$ npm install -g grunt-cli
```



## Grunt + Karma

### はじめに
* [karmaの導入「AngularJsテスト (Karma + phantomjs)」](AngularJsTest(Karma-and-phantomjs).md)

### package.json
package.json の devDependenciesに以下を追加

#### karmaのバージョンを0.10に設定した場合

```json
// package.json
{
 "devDependencies": {
 	"karma": "~0.10",
    "karma-phantomjs-launcher": "~0.1",
    "grunt": "~0.4.5",
    "grunt-karma": "~0.6.x"
  }
}
```

書き換えたら、

```bash
$ npm install
```

を、実行


### Gruntfile.js

```js
module.exports = function (grunt) {
    // Project configuration.
    grunt.initConfig({
        // Task configuration.
        karma: {
            unit: {
                options: {
                    configFile: 'karma.conf.js',
                    autoWatch: false,
                    browsers: ["PhantomJS"],
                    reporters: ["progress"],
                    singleRun: true,
                    keepalive: true
                }
            }
        }
    });
    // These plugins provide necessary tasks.
    grunt.loadNpmTasks('grunt-karma');
    grunt.registerTask('test', ['karma']);
};
```

#### registerTask で test コマンドに karma を登録したので

```bash
$ grunt test
```

