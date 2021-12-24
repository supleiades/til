# System Manager

## ログ
- ssmエージェントのデフォルトのログレベルはINFO
  - [SSM Agentデバッグログの有効化](https://docs.aws.amazon.com/ja_jp/systems-manager/latest/userguide/sysman-agent-logs.html#ssm-agent-debug-log-files)
- ログの場所
```
# mac or linux
/var/log/amazon/ssm/amazon-ssm-agent.log
/var/log/amazon/ssm/errors.log
/var/log/amazon/ssm/audits/amazon-ssm-agent-audit-YYYY-MM-DD
```
