- 正規表現で値のチェック
```yml
# https://docs.aws.amazon.com/servicecatalog/latest/adminguide/getstarted-template.html
Parameters:
  SSHLocation:
    Description : The IP address range that can SSH to the EC2 instance.
    Type: String
    MinLength: 9
    MaxLength: 18
    Default: 0.0.0.0/0
    AllowedPattern: (\\d{1,3})\\.(\\d{1,3})\\.(\\d{1,3})\\.(\\d{1,3})/(\\d{1,2})
    ConstraintDescription: Must be a valid IP CIDR range of the form x.x.x.x/x.
```
