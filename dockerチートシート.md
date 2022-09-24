### コンテナの削除
```
docker rm コンテナ名またはコンテナID
```

### イメーシの削除
```
docker rmi イメージ名またはイメージID
```

### 起動中のコンテナを表示
```
docker ps
```

### 停止中のコンテナを含め、すべてのコンテナを表示
```
docker ps -a
```

### dockerのイメージからコンテナ作成
```
docker-compose build
```
### コンテナ起動
```
docker-compose up
```
### コンテナ破棄
```
docker-compose down
```
### コンテナ停止
```
docker-compose stop
```
### プログラムのコマンド実行
```
docker-compose run web コマンド名
```

プロセス状況確認
```
docker-compose ps 
```

### volumeの確認
```
docker volume ls