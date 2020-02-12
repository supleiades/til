### JSON形式で文字列を変数に格納

```
var name = "SuPleades"
var repo = "til"
var lang = "javascript"


var str1 = ('{name:"' + name + '",repo:"' + repo + '",lang:"' + lang +'"}')

var str2 = ('{info:[' + str1 + '],memo: "so good"}')
console.log("( type of str2 )--> " + typeof(str2))
// ( type of str2 )--> string 
```

### 上記で格納した変数（文字列型）をevalを使ってオブジェクト型に変換

```
var obj1 = eval( '(' + str2 + ')' )
console.log("( type of obj1 )--> " + typeof(obj1))
// ( type of obj1 )--> object 
```
