```
// Unixtimestamp
10桁は秒
13桁はミリ秒

// Dateがミリ秒なので1000倍が必要
let dateTime = new Date(unixtime * 1000);

// .toString()や.toLocaleDateString()、.toLocaleTimeStringでうまくいく
// 以下、unixtime = 1567566215 でのサンプル
console.log(dateTime.toString()); // => Wed Sep 04 2019 12:03:35 GMT+0900 (日本標準時)
console.log(dateTime.toLocaleDateString()); // => 2019/9/4
console.log(dateTime.toLocaleDateString('ja-JP').slice(5)); // => 9/4
console.log(dateTime.toLocaleTimeString()); // => 12:03:35
console.log(dateTime.toLocaleTimeString('ja-JP')); // => 12:03:35
```



# Date型を出力
```
//const unixtime = {13桁のunixtime}
const unixtime = '1583336223099'
var d = new Date(parseInt(unixtime,10));
var year = d.getFullYear();
var month = ( ( d.getMonth() + 1 ) < 10 ) ? '0' + (d.getMonth() + 1) : d.getMonth() + 1;
var day  = ( d.getDate() < 10 ) ? '0' + d.getDate() : d.getDate();
var hour = ( d.getHours()   < 10 ) ? '0' + d.getHours()   : d.getHours();
var min  = ( d.getMinutes() < 10 ) ? '0' + d.getMinutes() : d.getMinutes();
var sec   = ( d.getSeconds() < 10 ) ? '0' + d.getSeconds() : d.getSeconds();
console.log( year + '-' + month + '-' + day + ' ' + hour + ':' + min + ':' + sec );
//結果 2020-03-05 00:37:03
```

# unixtimeを出力
```
print( parseInt( new Date() /1000 ) );
//結果 1318518000
```

# Dateをunixtimeに変換
```
var ts = "2011-10-14 00:00:00";
print( Date.parse( ts.replace( /-/g, '/') ) / 1000 );
//結果 1318518000
```