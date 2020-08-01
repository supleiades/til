- docker rmi [イメージID]

## imageの削除
```
# イメージIDの確認
docker images
> REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
> centos              test                d04f5cbd1bce        14 minutes ago      409MB

# イメージ削除
docker rmi d04f5cbd1bce
> Untagged: centos:test
> Deleted: sha256:d04f5cbd1bceef9c649d7a41bc04f8ae47dd2e7955d4d6e5797f6fba4cb9795d
> Deleted: sha256:7f2872793df001ed4122f9f1e5dfc2a6077cf6c8ed03cc86e95dc9104042c600

# イメージが削除されたことを確認
docker images 
> REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
```
