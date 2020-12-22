- 大元のブランチの最新とプルリク出したブランチのコミットログに差分が生まれてしまっていた時の解決先
```
git clone {fork先}
git remote add upstream {fork元}
git fetch upstream
git checkout -b {ブランチ名} origin/{fork先での対象ブランチ名}
git merge upstream/{fork元のブランチ名}
```
