## setup
- ansible -i hosts dev -m setup | grep distribution
```py
# コマンド結果
# AmazonLinux2の環境化
...
        "ansible_distribution": "Amazon",
        "ansible_distribution_file_parsed": true,
        "ansible_distribution_file_path": "/etc/os-release",
        "ansible_distribution_file_variety": "Amazon",
        "ansible_distribution_major_version": "2",
        "ansible_distribution_minor_version": "NA",
        "ansible_distribution_release": "NA",
        "ansible_distribution_version": "2",
```
