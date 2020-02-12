# 用途

文字列をJavascriptのコードとして解析して実行する

基本的な例
```
var str = "console.log('hello')"
// 変数strに格納されたものは文字列('～'）

eval(str)
// hello
// 変数strに格納された文字列をコードとしてevalが解析し、実行
```
