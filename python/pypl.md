# pyplについて
- 本番環境とテスト環境がある
- 本番環境
  - https://pypi.org
- テスト環境
  - https://test.pypi.org

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
