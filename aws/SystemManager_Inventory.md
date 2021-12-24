# SSM - Inventory 

## アプリケーションの情報を取得する
- [ssmインベントリで取得した情報をaws cliから確認する](https://dev.classmethod.jp/articles/show-installed-appilications-by-ssm-inventory/)
- [ssmインベントリで取得したアプリ情報をconfigで判定して通知する](https://dev.classmethod.jp/articles/config-rule-ec2-application-check-and-sns-publish/)


## Automation - Documents

```sh
aws ssm list-documents --output table \
 --filters Key=Owner,Values=Amazon Key=DocumentType,Values=Automation\
 --query 'DocumentIdentifiers[*].{DocumentName:Name, DocumentType:DocumentType,Platform1:PlatformTypes[0],Platform2:PlatformTypes[1],Platform3:PlatformTypes[2],Format:DocumentFormat,TargetType:TargetType,DocVer:DocumentVersion,Schema:SchemaVersion}'

## -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## |                                                                                               ListDocuments                                                                                               |
## +--------+------------------------------------------------------------------------+---------------+---------+------------+------------+------------+---------+----------------------------------------------+
## | DocVer |                             DocumentName                               | DocumentType  | Format  | Platform1  | Platform2  | Platform3  | Schema  |                 TargetType                   |
## +--------+------------------------------------------------------------------------+---------------+---------+------------+------------+------------+---------+----------------------------------------------+
## |  1     |  AWS-ASGEnterStandby                                                   |  Automation   |  YAML   |  Windows   |  Linux     |  None      |  0.3    |  /AWS::EC2::Volume                           |
## |  1     |  AWS-ASGExitStandby                                                    |  Automation   |  YAML   |  Windows   |  Linux     |  None      |  0.3    |  /AWS::EC2::Volume                           |
## |  1     |  AWS-AttachEBSVolume                                                   |  Automation   |  JSON   |  Windows   |  Linux     |  None      |  0.3    |  None                                        |
## |  1     |  AWS-AttachIAMToInstance                                               |  Automation   |  YAML   |  Windows   |  Linux     |  None      |  0.3    |  /AWS::EC2::Instance                         |
## ...
```
