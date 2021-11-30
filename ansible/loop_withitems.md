1. with_items: 一段階 flatten される
2. with_list、loop: flatten されない

### with_itemsをloopで置き換える場合
flattenフィルターを通すことでflattenされて、with_itemsと同じ動作になる
```yml
    - name: loop with flatten
      debug:
        msg: "{{ item }}"
      loop: "{{ testitems | flatten(levels=1) }}"
```

### 参考
[with_itemsとloopの違い](https://tekunabe.hatenablog.jp/entry/2019/03/11/ansible_with_items_loop)
