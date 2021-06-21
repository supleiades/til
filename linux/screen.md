### 環境作成してアタッチ
```
screen -S {任意な環境名}
```

### 環境からデタッチ
```
# 左から順に押す、最終的に全て同時押しの状態になって抜ける
Control + a + d
```

### セッションのデタッチ
- セッションが残ってしまっている場合の対処法
```
screen -d {PID}
```

### 環境を削除
```
screen kill {PID}
```

##シェルで複数のスクリーン作成・その中でコマンド実行
```
#!/bin/bash
# entry_exit
screen -S enter_exit -X quit
screen -dmS enter_exit
sleep 3s
screen -S enter_exit -X stuff 'cd ~/discord/entry_exit/;source .env;python3 enter_exit_bot.py'`echo -ne '\015'`

# musicbot2
screen -S musicbot -X quit
screen -dmS musicbot
sleep 3s
screen -S musicbot -X stuff 'cd ~/MusicBot; python3 run.py'`echo -ne '\015'`
```
