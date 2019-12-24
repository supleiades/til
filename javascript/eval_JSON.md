In the third stage we use the eval function to compile the text into a JavaScript structure. The "{" operator is subject to a syntactic ambiguity in JavaScript: it can begin a block or an object literal. We wrap the text in parens to eliminate the ambiguity.

//3番目の段階では、eval関数を使用してテキストをJavaScript構造にコンパイルします。 「{」演算子は、JavaScriptの構文のあいまいさの影響を受けます。ブロックまたはオブジェクトリテラルを開始できます。あいまいさを排除するために、テキストを括弧で囲みます。

                j = eval("(" + text + ")");
                
                
JavaScriptのオブジェクトは、オブジェクトという形式の型の値です。オブジェクトである変数のメンバーとしてオブジェクト内の値を参照したり、代入したりすることができる

JSONデータは、オブジェクトのメンバーを参照するときのように扱うことができません。JSONデータは、JavaScriptのオブジェクトと違って、オブジェクトを定義するときのプロパティをダブルクォーテーションでくくる必要があるという特徴を持つ
                
// object
var d = { name: "Ronald", number: 7, nation: "Portugal" };
// JSON
var d = { "name": "Ronald", "number": 7, "nation": "Portugal" };
