# pyplについて
- 本番環境とテスト環境がある
- 本番環境
  - https://pypi.org
- テスト環境
  - https://test.pypi.org
- テスト環境にpushしたパッケージインストール時に「install_requires」で取得するパッケージは同一名のテスト環境にあるものを取得するためエラーが起きる
  - テスト環境にpushしたパッケージを動かす場合は手動でpipインストールが必要になる

## pyplにアップロード
```py
# pyplにアップロードする為に必要なライブラリインストール
pip install wheel twine

# setup.pyを作り...
# PyPI登録用のパッケージを作成
python setup.py bdist_wheel

### vi .gitignore
##build/
##dist/
##*.egg-info/ 

# テスト環境のPyPIへのパッケージ登録が開始
twine upload --repository testpypi dist/*

# テスト環境のPyPIからのpip install
# pip install --index-url https://test.pypi.org/simple/{あなたのパッケージ名}
pip install -i https://test.pypi.org/simple/ mo9mo9db
```


# 本番環境のPyPiへのパッケージ登録をする場合
`twine upload --repository pypi dist/*`



## 参考
- https://qiita.com/shonansurvivors/items/0fbcbfde129f2d26301c
