whenの中で変数は「{{ }}」で囲む必要なし

## 複数条件 & 条件結果の反転(not)
- and で繋げる
 ```py
      when: # AmazonLinux2以外の環境でインストールされることを想定
        not ansible_distribution == "Amazon"
        and ansible_distribution_version == "2"
```

## 未定義の判定
- original_varという変数が定義されている想定
```yml
when: original_var is defined
```
