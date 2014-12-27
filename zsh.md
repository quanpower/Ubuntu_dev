# 1.Install zsh
Use
	cat /etc/shells
to find if is there has a zsh?If not,to install one by
	sudo apt-get install zsh

# 2.Switch shells
	chsh -s /bin/zsh

# 3.Configure oh_my_zsh
## 3.1 install oh_my_zsh:

via curl:
curl -L http://install.ohmyz.sh | sh
via wget:
wget --no-check-certificate http://install.ohmyz.sh -O - | sh

## 3.2 .zshrc

