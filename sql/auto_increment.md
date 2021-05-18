## auto_increment

DB側で自動で値を割り当てるもの

AUTO_INCREMENT を設定するカラムは、主キー（PRIMARY KEY）か、ユニークキー（UNIQUE KEY）であることが必要

INDEXに指定することで作成可能

## auto_incrementの細かい設定

参考サイト：
https://qiita.com/sakuraya/items/0dd0bb4114e56f42556d


## 設定

### 設定内容確認
```
SHOW VARIABLES LIKE '%auto_increment%';

+------------------------------+-------+
| Variable_name                | Value |
+------------------------------+-------+
| auto_increment_increment     | 3     |
| auto_increment_offset        | 3     |
| wsrep_auto_increment_control | ON    |
+------------------------------+-------+
```

### Variable_nameの説明
|||
|:-|:-|
|auto_increment_increment|更新する値（何づつ足すか的な）|
|auto_increment_offset|一番最初にinsertしたときに採番される値|
|wsrep_auto_increment_control|Primary Componentsに接続しているノードの数にincrementとoffsetを調節|

### 設定変更

```

```



### 次にauto_incrementで採番される値を確認

```
mysql> show table status like 'incident_TestUser1'\G
*************************** 1. row ***************************
           Name: incident_TestUser1
         Engine: InnoDB
        Version: 10
     Row_format: Compact
           Rows: 2
 Avg_row_length: 8192
    Data_length: 16384
Max_data_length: 0
   Index_length: 16384
      Data_free: 0
 Auto_increment: 9
    Create_time: 2020-02-13 10:13:54
    Update_time: NULL
     Check_time: NULL
      Collation: utf8_general_ci
       Checksum: NULL
 Create_options:
        Comment:
1 row in set (0.00 sec)

mysql> SELECT auto_increment FROM information_schema.tables WHERE table_name = 'incident_TestUser1';
+----------------+
| auto_increment |
+----------------+
|              9 |
+----------------+
1 row in set (0.05 sec)
```

### 次にauto_incrementで採番される値を変更

```
mysql> ALTER TABLE TestUser1.incident_TestUser1 AUTO_INCREMENT=1;
Query OK, 0 rows affected (0.00 sec)
```
