# Sinatra

## Passener + Apache + Sinatra

thinとかよくわからない

```bash
$ gem install sinatra
$ gem install thin
$ gem install passenger

# モジュールのインストールに必要なものらしいのをインストール
$ yum install -y rubygems curl-devel httpd-devel apr-devel apr-util-devel gcc gcc-c++ openssl-devel zlib-devel ruby-devel

# passengerのapacheモジュールのインストール
$ passenger-install-apache2-module
$ passenger-install-apache2-module --snippet

# 以下をPassengerの設定で使うので、コピー
LoadModule passenger_module /usr/local/rvm/gems/ruby-2.1.2/gems/passenger-5.0.4/buildout/apache2/mod_passenger.so
<IfModule mod_passenger.c>
  PassengerRoot /usr/local/rvm/gems/ruby-2.1.2/gems/passenger-5.0.4
  PassengerDefaultRuby /usr/local/rvm/gems/ruby-2.1.2/wrappers/ruby
</IfModule>
```

### httpdでpassngerの設定

```bash
$ vim /etc/httpd/conf.d/passnger.conf

# passenger-install-apache2-module --snippet
LoadModule passenger_module /usr/local/rvm/gems/ruby-2.1.2/gems/passenger-5.0.4/buildout/apache2/mod_passenger.so
<IfModule mod_passenger.c>
  PassengerRoot /usr/local/rvm/gems/ruby-2.1.2/gems/passenger-5.0.4
  PassengerDefaultRuby /usr/local/rvm/gems/ruby-2.1.2/wrappers/ruby
</IfModule>

# Delete Passenger's HTTP Header
Header always unset "X-Powered-By"
Header always unset "X-Rack-Cache"
Header always unset "X-Content-Digest"
Header always unset "X-Runtime"

# この辺の設定は必要なら
PassengerMaxPoolSize 20
PassengerMaxInstancesPerApp 4
PassengerPoolIdleTime 3600
PassengerHighPerformance on
PassengerStatThrottleRate 10

# RailsEnv development  # production か development を設定
# RackBaseURI /app1     # DocumentRootからのアプリケーションフォルダ相対位置
# RackBaseURI /app2     # 複数設定可能

<VirtualHost *:80>
  # Domain
  ServerName 自分のドメイン
  # sinatra app root
  DocumentRoot "/var/www/apps/sinatra/sinatra_sample/public"
  RackEnv production
</VirtualHost>
```

最後にhttpdの再起動

```bash
# Apacheの文法チェック
$ apachectl configtest
Syntax OK

$ /etc/rc.d/init.d/httpd restart
```

```ruby
# vim /var/www/path/to/sinatra/app/config.ru
require './app'
run Sinatra::Application

# vim /var/www/path/to/sinatra/app/app.rb
require 'sinatra'
get '/' do
	'Hello world!'
end
```

これで http://自分のドメイン/
でhello worldが出てるはず



## Gemfile

```bash
# 作業ディレクトリで
$ bundle init

# vim /var/www/path/to/sinatra/app/Gemfile
# A sample Gemfile
source "https://rubygems.org"

# gem "rails"
gem 'sinatra'

# # Assets
gem 'haml'
gem 'sinatra-contrib'
gem 'sass'


$ bundle install --path vendor/bundle --without production
```

``` ruby
# vim /var/www/path/to/sinatra/app/app.rb

require 'rubygems'
require 'sinatra'

get '/' do
	'Hello world!'
end

# httpd 再起動
```


