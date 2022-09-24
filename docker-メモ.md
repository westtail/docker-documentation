
```

### volumeの全削除
```
docker volume rm $(docker volume ls -qf dangling=true)
```
https://qiita.com/Ikumi/items/b319a12d7e2c9f7b904d
https://qiita.com/reflet/items/5caa88abcf1e8964783a


# その他
## dbの永続化
https://note.com/wankoromochi0628/n/nae90aa1d036f

https://note.com/wankoromochi0628/n/nae90aa1d036f

やり方
vokumesを作成して
その出力先を物理メモリに保存する
```
serviecs
  db:
	images:
	volumes:
      - pgdatavol:/var/lib/postgresql/data
      ~~~~~
volumes:
  pgdatavol:
```
