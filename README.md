# README

pyenvに関しての情報をココに書き込むことにする。

- [1. pyenvとは](#1-pyenvとは)
- [2. 'pyenv'のインストールに関して](#2-pyenvのインストールに関して)
- [3. 'pyenv'の使い方に関して](#3-pyenvの使い方に関して)
- [4. 3に記載されていない内容に関して](#4-3に記載されていない内容に関して)
  - [4.1. pyenv local x.x.x とした時の挙動に関して](#41-pyenv-local-xxx-とした時の挙動に関して)
  - [4.2. pyenv でインストールできる python のバージョンの更新に関して](#42-pyenv-でインストールできる-python-のバージョンの更新に関して)


## 1. pyenvとは

　pyenv とは、pythonのバージョンを切り替え出来るソフトである。python は python自体のバージョンが存在し、OSによってデフォルトでインストールされているバージョンが異なる（主にUbuntuの話）。また、使用したいライブラリに対応しているpythonのバージョンが決まっており、現在使っているバージョンと異なる場合、使用できない場合がある。  

　このような問題を解決するための方法としてpythonのバージョンを手軽に切り替えできるソフトとして pyenv が存在している。もちろん pyenv を使用しなくても切り替えが可能であるが、pyenvの手軽さを考えるとコチラをオススメする。  

　例として pyenv での手軽な切り替え方法を以下に記載しよう（必要なバージョンは事前にインストールする必要があるが、ココではインストール済みとする）。  
```bash
# pyenv version で現在の使用中の python のバージョンが表示される
$ pyenv version
3.8.18 (set by /home/fukuhara/.pyenv/version) # 今の python のバージョン
$ pyenv global 3.10.13
$ pyenv version
3.10.13 (set by /home/fukuhara/.pyenv/version) # 今の python のバージョン
```

このように手軽にバージョンを切り替えできる。  

## 2. 'pyenv'のインストールに関して

インストールに関しては以下の公式サイトのインストールの欄に従う。  
- https://github.com/pyenv/pyenv?tab=readme-ov-file#installation

このドキュメントを作成した際のインストール方法は以下のように行う。
```bash
# pyenv のインストール
$ curl https://pyenv.run | bash
# curl is not found の場合は 先に curl をインストール
#$ sudo apt update
#$ sudo apt install curl
# git is not found の場合は 更にgitをインストール
#$ sudo apt install git

# 初期設定
$ echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
$ echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
$ echo 'eval "$(pyenv init -)"' >> ~/.bashrc
# 以下は二回目移行は実行する必要はない
$ source ~/.bashrc
```
以下のコマンドでインストールされたか確認する。
```bash
$ pyenv version
system (set by /root/.pyenv/version)
```
上記は現在はシステム上に既にインストールされているpythonを用いることを意味している。

## 3. 'pyenv'の使い方に関して

以下を参考に使い方を学ぶ
- https://qiita.com/koooooo/items/b21d87ffe2b56d0c589b


## 4. 3に記載されていない内容に関して

### 4.1. pyenv local x.x.x とした時の挙動に関して

`pyenv local x.x.x`としてバージョンを切り替えた際には、実行したディレクトリ上に`.python-version`というファイルが作成される（`ls -l`コマンドで確認できる）。pyenvはコレを見てバージョンを切り替えている。

### 4.2. pyenv でインストールできる python のバージョンの更新に関して

長年使っていると python本体のバージョンの最新版がインストール候補に入っていないことに気づく。　　
このような場合は`pyenv update` コマンドで pyenv 自体をアップデートすることでインストール候補に追加される。  
