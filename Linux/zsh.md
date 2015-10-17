# Zsh

``` bash
$ yum -y install zsh

# zsh にしたいユーザーに切り替える

# 現在のシェルの確認
$ echo $SHELL

# 利用可能なシェルを表示
$ cat /etc/shells

# zshに変更
$ chsh -s /bin/zsh

vi .zshrc

autoload -U compinit
compinit
setopt auto_cd
setopt auto_pushd
setopt correct
```

# oh my zsh インストール
[https://github.com/robbyrussell/oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)

```bash
$ git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
$ cp ~/.zshrc ~/.zshrc.origin
$ cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
$ chsh -s /bin/zsh

Start / restart zsh (open a new terminal is easy enough…)
```


# bash に戻したい時

```bash
echo $SHELL
cat /etc/shells
chsh -s /bin/bash
```
