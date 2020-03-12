## basic
```
const express = require('express');
const app = express();
// ejsファイルのデフォルトのディレクトリは「views」になる
```


### cssや画像などのファイルを読み込み
```
// 今回はフォルダ名を「public」とする
app.use(express.static('public'));
```

### クライアントからのGETに対しての返答
```
// ルートにアクセスした場合は「(./views/)top.ejs」を表示する
app.get('/' (req, res) => {
  res.render('top.ejs');
});
```
