### JSON.stringify
JavaScriptのオブジェクトをJSON文字列に変換する関数。 

### JSON.parse
JSON文字列をJavaScriptオブジェクトに変換する関数。

## Result
出力を見ると、JSON文字列はキーがどちらもダブルクォーテーションで囲まれていることがわかると思います。
```
var jsVar = {
  id: 1,
  title: "title"
};

var jsonStr = JSON.stringify(jsVar);

var jsParsed = JSON.parse(jsonStr);

console.log(jsVar); // {id: 1, title: "title"}
console.log(jsonStr); // {"id":1,"title":"title"}
console.log(jsParsed); // {id: 1, title: "title"}
```
