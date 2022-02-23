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