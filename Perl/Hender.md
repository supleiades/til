HTTP::Headers - HTTPメッセージヘッダをカプセル化するクラス

### 概要
require HTTP::Headers;
``` 
$h = HTTP::Headers->new;

$h->header('Content-Type' => 'text/plain');  # set
$ct = $h->header('Content-Type');            # get
$h->remove_header('Content-Type');           # delete
```
