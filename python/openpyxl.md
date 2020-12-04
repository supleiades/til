# 参考
https://office54.net/python/excel/python-excel-openpyxl


# エクセルを操作するライブラリ

## メソッド
### excelファイルを取得
```
import openpyxl
book = openpyxl.load_workbook('{ファイル名}')
```

## （例） 
```
import openpyxl

file_name = "{対象fileのPath}"

wb =openpyxl.load_workbook('/tmp/example.xlsx')
sheet = wb.get_sheet_by_name('シート1')


obj = {
# cell()で取得したいセルを指定する
    "{no}"        : sheet.cell(row=1, column=2).value,
    "{name}"       : sheet.cell(row=2, column=2).value,
}
print(obj)

# 置換する標準ライブラリ
import shutil

# バックアップファイルの保存
back_name = file_name + ".bak"
shutil.copy(file_name, back_name)

with open(file_name, encoding="utf-8") as f:
    data_lines = f.read()

# 文字列置換
data_lines = data_lines.replace("{xlsx_replace_project_id}", obj["project_id"])
data_lines = data_lines.replace("{xlsx_replace_mailaddress}", obj["mailaddress"])
data_lines = data_lines.replace("{xlsx_replace_path}", obj["https_path"])
data_lines = data_lines.replace("{xlsx_replace_host}", obj["https_host"])
data_lines = data_lines.replace("{xlsx_replace_uptime_duration}", obj["uptime_duration"])
data_lines = data_lines.replace("{xlsx_replace_region}", obj["region"])

# 同じファイル名で保存
with open(file_name, mode="w", encoding="utf-8") as f:
    f.write(data_lines)
```
