検索して対象を配列にする

.match()


.match()
```
{stringObj}.match({regExp})
// {regExp}は/と/で括る。文字列全体に複数回マッチさせたい場合は/ /gを付ける
// 戻り値
// マッチしない場合はnullを返します
```


```
{stringObj} ---> 文字列のオブジェクト 
{arrayOjb} ---> 配列のオブジェクト 
{searchValue}　---> 検索する文字列 
{fromIndex}　---> 検索する最初の位置 
{regExp}　---> 正規表現
```

オプションフラグを付与せずmatchを行った場合

```
var str = "aaaaaaaaaaaaaaa111-1111";
var strReg = new RegExp("111-111.");
var result = str.match(strReg); //?
result.index // 

// 以下がresultの中身
// [ '111-1111',  
// index: 15, 
// input: 'aaaaaaaaaaaaaaa111-1111', 
// groups: undefined ] 
```

上記の様にmatchを行った場合、結果は以下の型になる
regexp が g 属性を伴わない場合

　match() メソッドは文字列でマッチングを１つ検索します。
　配列の要素 0 にはマッチした文字列全体が入ります。
　その他の要素（要素 1 から n ）には、マッチした配列内のカッコの付きのサブ表現のテキストが入ります。
　この動作は、グローバル フラグが設定されていない場合の exec() メソッド  の動作と同じです。
　match() メソッドが返す配列には input、および index の 2 つのプロパティがあります。
　input プロパティには、検索された文字列全体が格納されます。
　index プロパティには、検索された文字列内の一致した部分文字列の位置が格納されます。
　（https://www.webdesignleaves.com/pr/jquery/jq_basic_07.html）

以下が正規表現の中で()を3セット用いてmatchさせた結果
　0はマッチした全体、1以降は先頭の()から順に1以降の数字が付与され、結果が代入される
```  
var text = "https://www.webdesignleaves.com/wp/"; 
var reg = /(\w+):\/\/([\w.]+)\/(\S*)/;
var result = text.match(reg);

// result[0] : https://www.webdesignleaves.com/wp/
// result[1] : https
// result[2] : www.webdesignleaves.com
// result[3] : wp/
// result.input : https://www.webdesignleaves.com/wp/
// result.index : 0
// result.length : 4
```
0 : マッチした文字列全体が入る

1~ : それぞれのキャプチャ

index : マッチした場所 (bite値 じゃなくて 0から数えて何番目の文字か？)

オプションフラグを付与せずmatchを行った場合

```
var str = "aaaaaaaaaaaaaaa111-1111";
var strReg = new RegExp("111-111.");
var result = str.match(strReg); //?
result.index // 

// 以下がresultの中身
// [ '111-1111',  
// index: 15, 
// input: 'aaaaaaaaaaaaaaa111-1111', 
// groups: undefined ] 
```

上記の様にmatchを行った場合、結果は以下の型になる
regexp が g 属性を伴わない場合
　match() メソッドは文字列でマッチングを１つ検索します。
　配列の要素 0 にはマッチした文字列全体が入ります。
　その他の要素（要素 1 から n ）には、マッチした配列内のカッコの付きのサブ表現のテキストが入ります。
　この動作は、グローバル フラグが設定されていない場合の exec() メソッド  の動作と同じです。
　match() メソッドが返す配列には input、および index の 2 つのプロパティがあります。
　input プロパティには、検索された文字列全体が格納されます。
　index プロパティには、検索された文字列内の一致した部分文字列の位置が格納されます。
　（https://www.webdesignleaves.com/pr/jquery/jq_basic_07.html）

以下が正規表現の中で()を3セット用いてmatchさせた結果
　0はマッチした全体、1以降は先頭の()から順に1以降の数字が付与され、結果が代入される
```  
var text = "https://www.webdesignleaves.com/wp/"; 
var reg = /(\w+):\/\/([\w.]+)\/(\S*)/;
var result = text.match(reg);

// result[0] : https://www.webdesignleaves.com/wp/
// result[1] : https
// result[2] : www.webdesignleaves.com
// result[3] : wp/
// result.input : https://www.webdesignleaves.com/wp/
// result.index : 0
// result.length : 4
```
