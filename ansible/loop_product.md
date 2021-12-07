- ２つの配列から要素を取り出して全てのパターンを検証する場合に便利
- 各配列から取得した値を最後にlistでまとめてitem変数に格納して、item[0],item[1]の形で取得する
- ちなみに、item[0]は角括弧がないitem.0でも取得できる

## ９９掛け算
```yml
  vars:
    left_nu: "{{ (range(1, 9+1)|list) }}"
    right_nu: "{{ (range(1, 9+1)|list) }}"

  tasks:
    - name: make direcrory
      debug:
        msg: “{{ item[0] * item[1] }}"
      loop: "{{ left_nu | product(right_nu) | list }}"
      
# ok: [private_target] => (item=[1, 1]) => 
#   msg: “1"
# ok: [private_target] => (item=[1, 2]) => 
#   msg: “2"
# ok: [private_target] => (item=[1, 3]) => 
#   msg: “3"
# ok: [private_target] => (item=[1, 4]) => 
# ...
# .....
# ok: [private_target] => (item=[9, 7]) => 
#   msg: “63"
# ok: [private_target] => (item=[9, 8]) => 
#   msg: “72"
# ok: [private_target] => (item=[9, 9]) => 
#   msg: “81"
```

## 参考
[pythonでの掛け算](https://www3.cuc.ac.jp/~nagaoka/2017/prg1aki/04/99/index.html)
[dosc-product/with_nested](https://docs.ansible.com/ansible/latest/porting_guides/porting_guide_2.5.html#with-nested-with-cartesian)
