```
git log --oneline --name-status
```
参考: https://git-scm.com/book/ja/v2/Git-%E3%81%AE%E5%9F%BA%E6%9C%AC-%E3%82%B3%E3%83%9F%E3%83%83%E3%83%88%E5%B1%A5%E6%AD%B4%E3%81%AE%E9%96%B2%E8%A6%A7


# コミットの差分を表示
```
git log --no-merges master..iceE-1591-chenge/pin --oneline
```


## いい感じのコード
```sh
git log --graph --pretty=format:'%x09%C(auto) %h %Cgreen %ar %Creset%x09by"%C(cyan ul)%an%Creset" %x09%C(auto)%s %d'

## link
## https://qiita.com/kawasaki_dev/items/41afaafe477b877b5b73
```
