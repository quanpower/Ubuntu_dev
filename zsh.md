# 1.Install zsh
Use
	cat /etc/shells
to find if is there has a zsh?If not,to install one by
	sudo apt-get install zsh

# 2.Default shell
	chsh -s /bin/zsh

# 3.Configure oh_my_zsh
## 3.1 install oh_my_zsh:

via curl:
curl -L http://install.ohmyz.sh | sh
via wget:
wget --no-check-certificate http://install.ohmyz.sh -O - | sh

## 3.2 .zshrc

## 3.3 .zshrc.local
alias gaa='git add --all'
alias gcm='git commit -m '
alias gp='git push'
alias cls='clear'
alias ll='ls -l'
alias la='ls -a'
alias vi='vim'
alias grep="grep --color=auto"
alias -s html=vi   # 在命令行直接输入后缀为 html 的文件名，会在 vim 中打开
alias -s rb=vi     # 在命令行直接输入 ruby 文件，会在 vim 中打开
alias -s py=vi     # 在命令行直接输入 python 文件，会用 vim 中打开，以下类似
alias -s js=vi
alias -s c=vi
alias -s java=vi
alias -s txt=vi
alias -s gz='tar -xzvf'
alias -s tgz='tar -xzvf'
alias -s zip='unzip'
alias -s bz2='tar -xjvf'

## 3.4 plugins

reference:http://zhuanlan.zhihu.com/mactalk/19556676
