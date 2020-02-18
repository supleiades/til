端末を開いたら自動的に開いてほしい
bashの場合、~/.bashrcのエイリアスの上の部分、(aliasと書いてある部分が全て下に来るように)に
```
if command -v tmux>/dev/null; then
         [[ ! $TERM =~ screen ]] && [ -z $TMUX ] && exec tmux
fi
```
