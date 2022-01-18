# Conditions
```yml
AWSTemplateFormatVersion: 2010-09-09
Description: ---
Metadata: 

Parameters: 

Mappings: 

Conditions: 

Resources: 

Outputs:
```

## !If 以外の条件関数はConditionでしか使用できない
- !IfはResourcesやOutputsでも使用できる
- 以下の条件はConditionsセクションでしか使用できない
  - Fn::And
  - Fn::Equals
  - Fn::If
  - Fn::Not
  - Fn::Or


## Parametersで取得したtrueの値で条件分岐する
- Conditionsを使用せずにParametersのBool値を使用してResourcesで条件分岐しようとすると以下のエラーが発生する
  - `first element must be a condition and a string.`
- そのため、一旦Conditionsセクションでtrueであるかを判定した結果を元にResourceで指定する値の分岐をおこなっている
```yml
...
Parameters:
  AmazonLinuxOSBool:
    Description: Enter true or false. True if the OS is Amazon Linux, false otherwise.
    Type: String
    AllowedValues: [true, false]

Conditions:
  IsAmazonLinuxOS: !Equals [!Ref AmazonLinuxOSBool, true]

Resources:
  myEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      ...
      BlockDeviceMappings:
      - DeviceName: !If [IsAmazonLinuxOS, "/dev/xvda", "/dev/sda1"]
      ...
```
