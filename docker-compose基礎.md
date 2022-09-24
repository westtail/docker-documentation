## docker compose 
複数のコンテナを一括で管理するシステム

## docker-compose
"docker-compose.yml"ファイルに複数コンテナの構成情報を定義し、docker-composeコマンドで起動や停止などの管理

docker-compose
```
version: '3'
services:
  web:
    build: .
    ports:
      - "3000:3000"
    depends_on:
      - db
    volumes:
      - .:/API_sample
    command: bundle exec rails s -p 3000 -b '0.0.0.0'
  db:
    image: mysql:5.7
    volumes:
      - mysql_data:/var/lib/mysql/
    environment:
      MYSQL_ROOT_PASSWORD: password
    ports:
      - "3306:3306"
volumes:
  mysql_data:
```

## version
docker-composeのバージョンを指定します。

## services
アプリケーションを動かすための要素です。
ネストされたwebとdbは各要素で、自分で好きな名前をつけることができます。

## build
docker-compose buildのときにビルドするためのDockerfileのパスを指定しています。
ここでは、Dockerfileもdocker-compose.ymlもプロジェクト直下にあるのでこのような書き方をしています。

## ports
各serviceのポート番号を指定しています。
ホストOS(local)のポート番号:dockerコンテナ内のポート番号という書き方ができます。
ここでは、railsのポート番号が3000なので、3000:3000という書き方をしています。
1台のPCでDockerを使った複数のプロジェクトを扱うときに、ポート番号が重複するのを防ぐことができます。
たとえば3001:3001という書き方をすると、localhost:3001でサーバーに接続できます。

## depends_on
コンテナの依存関係を設定します。
今回はdbに依存関係があることを明記しています。
こうすることで、docker-compose upのときにDBを先に起動してくれます。

## volumes
dockerの中でデータを永続化する設定です。
この設定をすることで、コンテナ内のデータは消えずに残ってくれます

## command
docker-compose upで実行されるコマンドです。
upと同時に、bundle exec rails s -p 3000 -b '0.0.0.0'が実行されてサーバーに接続できるようになります。

## image
コンテナ作成に必要なイメージを指定しています。
ここでは、dbのコンテナ作成に、mysql5.7を使用すると設定しています。

## environment
環境変数を設定します。
database.ymlに書かれているパスワードを環境変数として設定し、mysqlに接続できるようにします。

## links
コンテナと他のサービスを繋げる．

## 参考URL

https://qiita.com/mightysosuke/items/c15ecf25307bc93ccd60

# 公式ドキュメント
https://docs.docker.jp/compose/compose-file.html
