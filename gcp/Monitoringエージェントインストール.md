# VM インスタンスの SSH ターミナルで Monitoring エージェント インストール 
```
curl -sSO https://dl.google.com/cloudagents/add-monitoring-agent-repo.sh
sudo bash add-monitoring-agent-repo.sh
sudo apt-get update
sudo apt-get install stackdriver-agent
```

## windows serverにMonitoringエージェントをインストール
```
powershell

invoke-webrequest https://repo.stackdriver.com/windows/StackdriverMonitoring-GCM-46.exe -OutFile StackdriverMonitoring-GCM-46.exe;
.\StackdriverMonitoring-GCM-46.exe

# PC再起動
```
