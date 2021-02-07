# template-deployer

- [ot-nemoto/aws-cloudformation-templates](https://github.com/ot-nemoto/aws-cloudformation-templates) のテンプレートをmasterにコミットした際に、自動でS3のBucket(ot-nemoto.aws-cloudformation-templates)へデプロイするためだけのやつ。

## architecture

![architecture](https://github.com/ot-nemoto/template-deployer/blob/images/template-deployer.png)

- CodeBuildではS3Bucketを一旦削除し、yamlファイルのみS3Bucketにdeploy

## parameters

|Name|Type|Description|Default|
|--|--|--|--|
|BucketName|String|ot-nemoto.aws-cloudformation-templates|The name of the bucket to store the template.|

## deploy

```sh
aws cloudformation create-stack \
    --stack-name template-deployer \
    --capabilities CAPABILITY_IAM \
    --template-body file://template.yaml
```

**GitHubバージョン2のソースアクションの為の接続を設定**

- CloudFormationの出力 `ConnectionURL` のリンクをクリック
- デベロッパー用ツールで `Update pending connection` をクリック
- GitHub接続設定で `Install a new app` をクリック
- Install AWS Connector for GitHubでリポジトリを選択し `Install` をクリック
- GitHub接続設定で `connect` をクリック
