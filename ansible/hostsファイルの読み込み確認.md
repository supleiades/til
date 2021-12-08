## 
```sh
ansible-inventory --graph -vvv
# ...
# @all:
#  |--@gce_instance:
#  |  |--xxx.xxx.xxx.xxx
#  |--@ungrouped:
```


## 実験
```sh
## 想定通りのコマンドの場合(-i test-hostname, all)
ansible-inventory -i test-hostname, all --graph
# @all:
#   |--@ungrouped:
#   |  |--test-hostname


## 失敗:
ansible-inventory -i test-hostname,all --graph 
# [WARNING]: Found both group and host with same name: all
# @all:
#   |--@ungrouped:
#   |  |--all
#   |  |--test-hostname


## 失敗:
ansible-inventory -i test-hostname --graph    
# [WARNING]: Unable to parse {...ry...}/test-hostname as an inventory source
# [WARNING]: No inventory was parsed, only implicit localhost is available
# @all:
#   |--@ungrouped:
```
