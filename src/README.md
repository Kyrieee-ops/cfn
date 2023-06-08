# プライベートサブネットにEC2, RDSを配置し、クライアントツールを使用してRDSへ接続

## deploy手順
> note
>
> - StackNameは適宜任意の名称に置き換えてください。
> - rds.cfgファイルにのDBPasswordは適宜任意のパスワードに変更してください
>
>
>

1. ec2_vpcendpoint1.0.ymlをdeployする

aws cli command
```aws cli
aws cloudformation deploy \
--stack-name StackName \
--template-file ec2_vpcendpoint1.0.yml
--capabilities CAPABILITY_NAMED_IAM
```

2. rds1.0.ymlをdeployする

aws cli command
```aws cli
aws cloudformation deploy \
--stack-name StackName \
--template-file rds1.0.yml
--parameter-overrides $(cat rds.cfg)
```
外部ファイル参照ためrds.cfgファイルを
--parameter-overridesで指定しています。