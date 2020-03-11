## mysqlのログイン時に
```
mysql --pager='less -S' -u {user} -p {password} -h {host}
```

## Select時に結果を縦に見やすく表示
### 文末の「;」を「\G」にする
```
mysql> select * from test_table \G
************ 1. row ************
  id: 1
  teamid: 1
  status: no
  a: 200

************　2. row ************
  id: 2
  teamid: 1
  status: ok
  a: 250
```
