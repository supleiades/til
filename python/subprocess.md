# subprocessモジュール

Pythonから外部ファイルを実行可能にする

## call メソッド



## runメソッド

戻り値が不要でコマンドを実行する時に有効

## check_outputメソッド

戻り値が必要な時に有効

```
import subprocess

result =subprocess.check_output(['/bin/ls', '-la'])

print(result.decode())
# コマンド結果は「.decode()」を使うことで日本語の文字化けや改行等が正しく表示される
```

### シェルのパイプラインの処理をsubprocessで記述するなら

---> ls -la | grep aaa
```
import subprocess

p1 = subprocess.Popen([ '/bin/ls', '-la' ], stdout=subprocess.PIPE)
p2 = subprocess.Popen([ 'grep', 'aaa' ], stdin=p1.stdout, stdout=subprocess.PIPE)
p1.stdout.close()
result = p2.communicate()[0]

print(result.decode())
```

