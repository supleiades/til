データの整形

.split()
.slice()


.split()
```
// 文字列やデータで「分ける」ことができます。
// そして分けたものを、リストとして出力してくれるのが.splitメソッドの特徴です。
```


.slice()
```
// リストに対して使えるメソッドです。
// リストの何番目から何番目までの指定された範囲の部分文字列を出力

// 不要な要素をsliceで削る
var fruits = ["Banana", "Orange", "Lemon", "Apple"];
var cutfruits = fruits.slice(0,-1);  //一番最後の要素から1番目を削除
console.log(cutfruits);  //["Banana", "Orange", "Lemon"]
```
