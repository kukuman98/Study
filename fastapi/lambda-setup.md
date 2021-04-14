# Lambda Setup

設定好deploy參數後執行deploy

到AWS 的 Lambda 設定 Env

prod要設定VPC

首先到IAM的role，找到project用的role後點進去

在permission點擊attach policy

選者AWSLambdaVPCAccessExecutionRole

再去到lambda找到project的lambda以及project用到的lambda設定VPC

* Vpc:name:vpc-to-atlas
* Subnet: Name:services-prod-private-01,services-prod-private-02
* Security groups:default VPC security group

