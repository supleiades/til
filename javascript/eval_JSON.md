// In the third stage we use the eval function to compile the text into a
// JavaScript structure. The "{" operator is subject to a syntactic ambiguity
// in JavaScript: it can begin a block or an object literal. We wrap the text
// in parens to eliminate the ambiguity.

                j = eval("(" + text + ")");
                
                
#JavascriptのオブジェクトとJSONの形式の違い
JSONはKeyに""(ダブルコーテーション)をつける
                
// object
var d = { name: "Ronald", number: 7, nation: "Portugal" };
// JSON
var d = { "name": "Ronald", "number": 7, "nation": "Portugal" };
