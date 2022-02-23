# MacBook_setting
## ターミナル設定方法

1. Solarizedをダウンロード
```
git clone https://github.com/tomislav/osx-terminal.app-colors-solarized solarized.git
```

2. Solarizedをターミナルで読み込んでデフォルトに設定

3. Vimの配色設定
```
# SolarizedのVimカラーをダウンロードする
$ git clone https://github.com/altercation/vim-colors-solarized.git
$ cd vim-colors-solarized/colors
$ mkdir -p ~/.vim/colors

# SolarizedのVimカラーを設定する
$ mv solarized.vim ~/.vim/colors/

# .vimrcに以下3行を追加する
$ vi ~/.vimrc
syntax enable
set background=dark #light or dark を選択
colorscheme solarized
```

4. lsの配色設定
```
# GNU版のlsをインストールする
$ brew install coreutils

# Solarizedのlsカラーテーマをダウンロードする
$ git clone https://github.com/seebi/dircolors-solarized.git ~/.dircolors-solarized

# .bashrcに以下1行を追加する（lsでカラー表示するための設定）
$ vi ~/.zshrc
alias ls='gls --color=auto'

# .bash_profileに以下1行を追加する（好みのlsカラーテーマを読み込む）
$ vi ~/.zprofile
eval `gdircolors ~/.dircolors-solarized/dircolors.256dark`

# 設定反映（ターミナルを開き直すでもOK）
$ source ~/.zprofile
```

5. lsカラーテーマに関するファイルをカスタマイズ

dircolors.256darkを参照
（色確認のコマンドは以下）

```
for c in {000..255}; do echo -n "\e[38;5;${c}m $c" ; [ $(($c%16)) -eq 15 ] && echo;done;echo
```

6. プロンプトの変更
```
# .zshrcに以下を追加する（カレントディレクトリ ユーザー種別）
$ vi ~/.zshrc
export PS1=$'\n'"%~ %# "
```

7. Gitのブランチ表示
```
# .zshrcに以下を追加する
$ vi ~/.zshrc
# git ブランチ名を色付きで表示させるメソッド
function rprompt-git-current-branch {
  local branch_name st branch_status
 
  if [ ! -e  ".git" ]; then
    # git 管理されていないディレクトリは何も返さない
    return
  fi
  branch_name=`git rev-parse --abbrev-ref HEAD 2> /dev/null`
  st=`git status 2> /dev/null`
  # ブランチ名を表示する
  echo "[$branch_name]"
}
 
# プロンプトが表示されるたびにプロンプト文字列を評価、置換する
setopt prompt_subst
 
# プロンプトの右側にメソッドの結果を表示させる
RPROMPT='`rprompt-git-current-branch`'
```
