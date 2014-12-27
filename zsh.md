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

## 3.3 plugins
plugins=(git ruby autojump)

### 3.3.1 install autojump

	git clone git://github.com/joelthelion/autojump.git

Run the installation script and follow on screen instructions.
	cd autojump
	./install.py or ./uninstall.py

### 3.3.2 autojump configure
Please manually add the following line(s) to ~/.zshrc:

	[[ -s /home/quanpower/.autojump/etc/profile.d/autojump.sh ]] && source /home/quanpower/.autojump/etc/profile.d/autojump.sh

	autoload -U compinit && compinit -u

Please restart terminal(s) before running autojump.

## 4. Use zsh

1、兼容 bash，原来使用 bash 的兄弟切换过来毫无压力，该咋用咋用。

2、强大的历史纪录功能，输入 grep 然后用上下箭头可以翻阅你执行的所有 grep 命令。

3、智能拼写纠正，输入gtep mactalk * -R，系统会提示：zsh: correct ‘gtep’ to ‘grep’ [nyae]? 比妹纸贴心吧，她们向来都是让你猜的……

4、各种补全：路径补全、命令补全，命令参数补全，插件内容补全等等。触发补全只需要按一下或两下 tab 键，补全项可以使用 ctrl+n/p/f/b上下左右切换。比如你想杀掉 java 的进程，只需要输入 kill java + tab键，如果只有一个 java 进程，zsh 会自动替换为进程的 pid，如果有多个则会出现选择项供你选择。ssh + 空格 + 两个tab键，zsh会列出所有访问过的主机和用户名进行补全

5、智能跳转，安装了autojump之后，zsh 会自动记录你访问过的目录，通过 j + 目录名 可以直接进行目录跳转，而且目录名支持模糊匹配和自动补全，例如你访问过hadoop-1.0.0目录，输入j hado 即可正确跳转。j –stat 可以看你的历史路径库。

6、目录浏览和跳转：输入 d，即可列出你在这个会话里访问的目录列表，输入列表前的序号，即可直接跳转。

7、在当前目录下输入 .. 或 … ，或直接输入当前目录名都可以跳转，你甚至不再需要输入 cd 命令了。

8、通配符搜索：ls -l **/*.sh，可以递归显示当前目录下的 shell 文件，文件少时可以代替 find，文件太多就歇菜了。

reference:http://zhuanlan.zhihu.com/mactalk/19556676
