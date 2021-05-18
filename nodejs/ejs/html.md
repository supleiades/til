## cssはスタイルシート（外部CSS)を読み込む
relでファイルとの関係性を、hrefで そのファイルがある場所（URL）を指定

href = Hypertext Reference
```
<title> </title>
<link rel="stylesheet"
      href="{filepath}">
```

## Webサイトのアイコン指定
```
<link rel="icon" href="画像のURL" sizes="32x32" />
<link rel="icon" href="画像のURL" sizes="192x192" />
<link rel="apple-touch-icon-precomposed" href="画像のURL" />

```

## 変数を使用するには
変数名を隠す
```
<% {変数名} %>
```
変数名を表示する
```
<%= {変数名} %>
```
