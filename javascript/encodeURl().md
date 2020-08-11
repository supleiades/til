## エンコード
```
const uri = 'https://twitter.com/share?url=https://mo9mo9study.github.io/discord.web/&text=おはよう';
const encoded = encodeURI(uri);
console.log(encoded);
// https://twitter.com/share?url=https://mo9mo9study.github.io/discord.web/&text=%E3%81%8A%E3%81%AF%E3%82%88%E3%81%86

```

## デコード
```
try {
  console.log(decodeURI(encoded));
  // https://twitter.com/share?url=https://mo9mo9study.github.io/discord.web/&text=おはよう
} catch (e) { // catches a malformed URI
  console.error(e);
}
```
