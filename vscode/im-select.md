# 前提
- homebrewがインストールされている
## 前提条件の注意
- CPU/AppleSiliconの場合、rosettaのインストールが必要
 - 今回は、GUIからアプリのインストールをしている時にたまたまRosettaをインストールした後で確認したら正常に動いたため

# 手順
## 概要
1. brewでim-selectをインストールするための外部リポジトリを追加する
1. brewでim-selectをインストールする
1. im-selectが想定通り動く事を確認
1. 「英字/かな」それぞれの入力ソースを確認する
1. 必要に応じて、Macの環境設定からKotorinの入力ソースに変更する
1. vscodeのsetting.jsonの内容を確認

## 手順
```sh
# 必要なリポジトリを追加
# 今回追加するリポジトリ： https://github.com/mscharley/homebrew-homebrew
brew tap mscharley/homebrew

# curlでもインストールできるが、今回はbrewで管理する
brew install --HEAD mscharley/homebrew/im-select

brew list | grep im-select
# 以下のような結果が返ってきていればインストールされている
## im-select

im-select
# 以下のような結果が返ってきて、想定通り動作していることを確認
## com.apple.inputmethod.Kotoeri.RomajiTyping.Roman

# キーボードの入力を「英字」に切り替えて現在の入力ソースを確認
im-select
## 英字の例
## com.apple.inputmethod.Kotoeri.RomajiTyping.Roman

# キーボードの入力を「かな」に切り替えて現在の入力ソースを確認
im-select
## かなの例
## com.apple.inputmethod.Kotoeri.RomajiTyping.Japanese

# CPU/AppleSiliconの新しいmacbookでim-selectを行なった際
# 英字の入力ソースが
# com.apple.keylayout.ABC
# だったため、macの環境設定から変更する必要がある

# 入力ソースの変更手順
# https://pc-karuma.net/mac-keyboard-input-source/

# vscodeのsetting.jsonを開いて設定の確認
{
    "vim.autoSwitchInputMethod.enable": true,
    "vim.autoSwitchInputMethod.defaultIM": "com.apple.inputmethod.Kotoeri.RomajiTyping.Roman",
    "vim.autoSwitchInputMethod.obtainIMCmd": "/usr/local/bin/im-select",
    "vim.autoSwitchInputMethod.switchIMCmd": "/usr/local/bin/im-select {im}",
}



```
