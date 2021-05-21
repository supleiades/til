# VM インスタンスの SSH ターミナルで Logging エージェント インストール
```
curl -sSO https://dl.google.com/cloudagents/add-logging-agent-repo.sh
sudo bash add-logging-agent-repo.sh

# インストール確認
dpkg -l google-fluentd

## 以下不要なのでは？とりあえずコメント
# sudo apt-get update
# sudo apt-get install google-fluentd
```


## windows serverにLoggingエージェントをインストール
```
powershell

invoke-webrequest https://dl.google.com/cloudagents/windows/StackdriverLogging-v1-11.exe -OutFile StackdriverLogging-v1-11.exe;
.\StackdriverLogging-v1-11.exe

# PC再起動
```
