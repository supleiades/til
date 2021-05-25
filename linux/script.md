WSLのターミナル操作ログを行う
```
# ログ用のディレクトリを作成
mkdir -p {ログを保存するパス}

vim ~/.profile
# 以下のコマンドを出力
# Windowsのメモ帳などで開くと正常に文字が表示されない
script -f {出力先のパス}/$(date +%Y%m%d%H%M%S).log
```
