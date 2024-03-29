### subelements
- ２つのリストの要素分(1,2,10,20）４回繰り返す処理
```yml
  vars:
    lists:
      sum_l:
        - value:
          - 1
          - 2
        - value:
          - 10
          - 20
  tasks:
    - name: addition
      debug:
        # msg: "{{ item.0 }} + {{ item.1 }} "
        msg: "{{ item }}"
      loop: "{{ lists.sum_l | subelements('value') }}"
      
# ok: [private_target] => (item=[{'value': [1, 2]}, 1]) => 
#   msg: '{''value'': [1, 2]} + 1 '
# ok: [private_target] => (item=[{'value': [1, 2]}, 2]) => 
#   msg: '{''value'': [1, 2]} + 2 '
# ok: [private_target] => (item=[{'value': [10, 20]}, 10]) => 
#   msg: '{''value'': [10, 20]} + 10 '
# ok: [private_target] => (item=[{'value': [10, 20]}, 20]) => 
#   msg: '{''value'': [10, 20]} + 20 '
```
- pythonで書くと
```py
lists = {"sum_l": [{"value": [1,2]}, {"value": [10,20]}]}
print(lists)

for l in lists["sum_l"]:
    for i in l["value"]:
        print(f"{l} / {i}")
        
# {'sum_l': [{'value': [1, 2]}, {'value': [10, 20]}]}
# {'value': [1, 2]} / 1
# {'value': [1, 2]} / 2
# {'value': [10, 20]} / 10
# {'value': [10, 20]} / 20
```




## 参考
[多重ループの方法3選](https://hutene.com/ansible_loop/)
[subelements+loopからの要素取り出し方](https://dev.classmethod.jp/articles/looping_over_subelements/)
[サブ要素をループさせる](https://dev.classmethod.jp/articles/looping_over_subelements/)
