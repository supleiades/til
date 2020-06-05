Mongoは書き込みを伴う処理の戻り値として、WriteResult()を返す

プロパティ  | 内容
---         | ---
nInserted   | 挿入された件数
nMatched    | 更新対象となった件数
nModified   | 更新された件数
nRemoved    | 削除された件数


## 日付
- 文字列で保持する方法: `Date()` を使う
- Unixエポックミリ秒で保持する方法: `ISODate()`を使う

比較/計算は後者のほうが簡単にできそうだが標準時刻になってしまうのが難点

参考：
https://qiita.com/drafts/8bcb5b0fc643267d6bcf/edit
