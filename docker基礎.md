
# Docker
* 仮想環境の構築ツール  
* コンテナと呼ばれる仮想環境を構築してその中でアプリを動かす。  
* データやプログラムを隔離できる仕組み  

# 概要 Dockerとは？

* データやプログラムを分割できる仕組み
* OSやwebサーバー、データベースサーバー、システムサーバーそれぞれに分割
### プログラムを分割する理由
* 一つのサーバーではバージョンは一つしか扱うことができない
* 複数のプログラムのバージョンの違いを解決するにはプログラムを分けてそれぞれのプログラムに合う環境にしてあげればいい

### Dockerエンジン
* dockerそのものでdockerのイメージやコンテナを動かすことができる。  
* dockerデーモンとして動作する
* コンテナ(container)を扱える仕組み
* コンテナはイメージと呼ばれるコンテナの元から作成される
* Dockerを扱う際はどこかでlinuxOSを扱うことになる
    * (windows,macだとしても必ず扱うことになる)

# サーバーとDockerについて
* サーバー(server) 何かサービス(service)を提供(serve)する物
* サーバーは機能的な意味と物理的な物としての意味の二つある
* 物理的なサーバーに機能的なサーバーが複数入ることがある
* そのためDockerによるサーバーの分割にメリットを持つ
* また複数の同じサーバーをサーバー同士の環境干渉をさせずに存在させることができる  
* さらに共有したい開発環境を簡単に共有することができる

# Dockerが動く仕組み
* linuxOSの上にDockerエンジン、その上でコンテナが動くことを前提としている
* 基本的にwindows,macのOSでは動かない
* なのでwindwsとmacなどは無理矢理linuxOSのパッケージを入れて動かしているもの

# イメージとコンテナ
* コンテナはイメージから作成される
* 逆にコンテナからイメージを作成することもできる
* またイメージを他の人と共有することでコンテナの複製、共有が可能である
* DockerHubはイメージを共有するプラットフォーム
* 種類としてOSだけ、OS＋ソフトウェアやOS+複数のソフトウェアなど
* 公式のイメージ、コンテナが安全ではある
* 自分で全ての部分を作成する必要がなくて簡単に利用することができる
* また利用するイメージを組み合わせて自分なりのイメージを作成可能

# コンテナのライフサイクル
* 作成→起動→停止→削除 = ライフサイクル
* コンテナのデータは物理的なマシンにマウントしてそこに保存する

# Dockerのメリットとデメリット

* 重要な部分はOS、ソフトウェアを隔離することができる
* 独立している　同じアプリや複数のアプリを入れれる
* イメージ化可能　コンテナを共有しやすく、もらいやすく、入れ替えしやすい
* コンテナにカーネルを入れなくて済む　Dockerやコンテナが軽くなる
### メリット
* 物理サーバーに複数の仮想的なサーバーを互いの干渉なく扱うことができる
* それぞれのアプリが干渉しないので管理がしやすい
* サーバーのある程度のレベルでも管理がしやすくなる
### デメリット
* linuxOSのサーバーでしか扱いが簡単で無いのでwindosサーバーは扱えない
* 物理サーバーが影響を受けると中の全ての仮想サーバーが影響を受ける

# Dockerの利用意図
* 開発現場で、全員に同じ開発環境を提供する
* 新しいバージョンを隔離された開発環境で実験する
* 複数のサーバーが必要な場面で物理サーバーに複数の仮想的サーバーを設置

# Dockerを扱うには
* linuxOS上でエンジンをインストール
* 仮想マシン、レンタルマシン上でdockerを入れて扱う
* windowsやmac用のデスクトップ版を扱う
* デスクトップ版は仮想環境も追加でインストールしている

# Dockerの起動と停止
* Dockerエンジンは自動起動のオンオフがある
* コンテナはdockerが落ちると停止してしまうなので再起動時はスクリプトが必要

## dockrコンテナ
dockerエンジン上で動く仮想環境  
ホストOSのカーネルを利用して動いているので、ホストマシンのリソースを節約しながら動いている。  
なのでdockerエンジンは仮想マシンlinuxを上で動いている

## dockerイメージ
dockerコンテナを作るためのレシピ、設計図  
ベースイメージにレイヤと呼ばれるイメーシを重ねることで新しいイメージを作成できる。  

## docker レジストリ
dockerイメージを保管している所

## リンク機能
コンテナなどはdocker上で動いているためコンテナ間の通信は可能
## virtualboxとの違い
ホスト型仮想化、ハイパーバイザ型仮想化の両方は、ホストOS上で仮想ソフト、ゲストOS、アプリの順番で重なっている  
ホストOSの上にゲストOSがあるので非常に手間がかかる  

* dockerにより環境構築を手軽に行うことができる
    * 環境構築をファイルに記述できる
    * 環境構築を破棄しても、同じものが作れる
    * 軽くて早く以上のことを行うことができる

# コマンドについて
Dockerの操作はコマンドラインで扱う

```docker
docker ~ 
docker 上位コマンド 副コマンド -オプション 対象 --引数
```

* 上位コマンド　省略することができる場合も
    * conatiner,image,volume,etwork
* 副コマンド　何をするかのコマンド
    * start,stiop,run,pullcreate,ete
* オプション　コマンドに対して細かい設定を加える
* 対象　どの対象に対して行うか
* 引数　対象に対して持たせたい値を指定する

# コマンドの種類
* docker run = docker image pull → docker create → docker start
* docker image pull イメージをダウンロードする
* docker contaner create イメージからコンテナを作成する
* docker contaner start コンテナを起動する
* docker stop  コンテナを停止する
* docker rm  コンテナを削除する

# dockerfileのコマンド説明

## レイヤー 
build時にイメージを１から作るのではなく、すでにあるイメージはそのままで、差分を積み重ねて管理している  

### FROM
ベースイメージを指定 このベースイメージにレイヤーを重ねる

```
FROM centos
```

### ENV
コンテナ内の環境変数を設定する

```
ENV hoge=hogehoge
```

### RUN
コンテナの中で実行するコマンドを載せる  
Dockerイメージからコンテナを作成するためのコマンド  
コンテナを作成するために必要なインストールなどのコマンド

```
RUN yum -y install httpd
```

### ADD
ファイル/ディレクトリの追加  
ファイルやディレクトリを取得する命令。

### COPY
ローカルファイルのコンテナへのコピー  
ホストOS上のローカルファイルのみ可

### WORKDIR	
場所(ディレクトリ)を移動する命令  
コンテナ起動時の作業ディレクトリの指定


### EXPOSE	
ホストのPORTの割り当て  
コンテナにアクセスする公開ポート番号を設定する


### CMD
コンテナ起動時に実行するコマンドの定義  
Dockerイメージが起動してから実行されるコマンド  
イメージが出来上がってからのインストール以外のコマンドなど

### VOLUME
コンテナは削除されると中のデータもなくなってしまうので
保存したいデータはvolumeに保存する
https://qiita.com/namutaka/items/f6a574f75f0997a1bb1d#dockerfile%E3%81%A7%E3%81%AEvolume%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89

## 参考URL
* 公式ドキュメント
    * https://docs.docker.jp/engine/reference/run.html
一番役に立った
* https://qiita.com/gold-kou/items/44860fbda1a34a001fc1#docker-compose%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89

その他
* https://kitsune.blog/docker-summary
* https://qiita.com/gold-kou/items/44860fbda1a34a001fc1
* https://qiita.com/tanan/items/e79a5dc1b54ca830ac21

# dockerfile

```
FROM ruby:2.4.2 # rubyのイメージをベースイメージとして持ってくる

RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs
# イメージ作成のためのイメージインストールなどを実行

RUN mkdir /

WORKDIR /app-name

ADD Gemfile /app-name/Gemfile
ADD Gemfile.lock /app-name/Gemfile.lock

RUN bundle install

ADD . /app-name
```

### apt-get
パッケージの操作・管理を行うコマンド https://webkaru.net/linux/apt-get-command

* install　パッケージ 指定したパッケージをインストールします
* update　ライブラリのインデックスを更新
* -q　quietモードです。進捗状況を表示しません
* -y　インタラクティブ（ユーザーへの問い合わせ）に「yes」と答えます

### build-essential
名前の通り, 開発に必須のビルドツールを提供しているパッケージ.

### libpq-dev 
PostgreSQLの略語でPostgreSQLインストールパッケージ

### node.js
node.jsはjavascript用のランタイム サーバーサイドのJavaScript実行環境です。
