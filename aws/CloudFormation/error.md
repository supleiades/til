# Error lists

## AMI
- 指定されたAMIのCPUアーキテクチャが指定したインスタンスファミリーに対応していない場合
  - 以下のエラーは「armのアーキテクチャのAMI」「t3.micro」の２つの要素を選択した際、そのAMIでt3.microを対応していなかった

> The architecture 'x86_64' of the specified instance type does not match the architecture 'arm64' of the specified AMI. Specify an instance type and an AMI that have matching architectures, and try again. You can use 'describe-instance-types' or 'describe-images' to discover the architecture of the instance type or AMI.
