- 存在しないパッケージの場合
```py
    - name: chronyd確認
      yum:
        list: chronyd
      register: hoge_package_info

## 結果
    "msg": {
        "changed": false,
        "failed": false,
        "results": []
    }
}
```

- 存在するパッケージ
```py
    - name: 確認
      yum:
        list: httpd
      register: hoge_package_info
    - name: 結果
      debug:
        msg: "{{ hoge_package_info }}"

## 結果
    "msg": {
        "changed": false,
        "failed": false,
        "results": [
            {
                "arch": "x86_64",
                "envra": "0:httpd-2.4.33-2.amzn2.0.2.x86_64",
                "epoch": "0",
                "name": "httpd",
                "release": "2.amzn2.0.2",
                "repo": "amzn2-core",
                "version": "2.4.33",
                "yumstate": "available"
            },
...
```
