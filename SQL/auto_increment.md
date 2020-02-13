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
