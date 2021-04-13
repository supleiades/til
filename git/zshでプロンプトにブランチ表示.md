# 手順
```sh
cd /usr/local/
sudo mkdir git-tools/
cd git-tools/

sudo wget https://raw.githubusercontent.com/git/git/master/contrib/completion/git-prompt.sh
sudo wget https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash
wget -O _git https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.zsh


sudo chown root. ./*git*
sudo chmod 775 ./*git*

vi ~/.zshrc
#### write ######

# git-promptの読み込み
source /usr/local/git-tools/git-prompt.sh
# git-completionの読み込み
fpath=(~/.zsh $fpath)
zstyle ':completion:*:*:git:*' script /usr/local/git-tools/git-completion.bash
autoload -Uz compinit && compinit
# プロンプトのオプション表示設定
GIT_PS1_SHOWDIRTYSTATE=true
GIT_PS1_SHOWUNTRACKEDFILES=true
GIT_PS1_SHOWSTASHSTATE=true
GIT_PS1_SHOWUPSTREAM=auto
# プロンプトの表示設定(好きなようにカスタマイズ可)
setopt PROMPT_SUBST ; PS1='%F{green}%n:%F{cyan}%~%f %F{red}$(__git_ps1 "(%s)")%f \$ '

#################


```

# 参考
https://qiita.com/mikan3rd/items/d41a8ca26523f950ea9d
