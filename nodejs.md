ubuntu14.04安装最新node.js

# 1.安装最新的nodejs和npm
 

    sudo add-apt-repository ppa:chris-lea/node.js
    sudo apt-get update
    sudo apt-get install nodejs

错误来啦：sudo: add-apt-repository:command not found
网上解决办法是直接安装工具包 命令：
    sudo apt-get install python-software-properties
亲测安装后还是报command not found，所以依赖包还没有安装完全，少了什么呢？
执行命令：add-apt-repository ，除了要安装python-software-properties外还需要software-properties-common
ok,执行安装命令：
    sudo apt-get software-properties-common

# 2.检测版本
  
    node  --version
    npm -v

# 3.升级npm
   
    sudo npm install -g npm

# 4.Install nodejs and npm on Armhf 

    sudo apt-get install curl
    sudo curl -sL https://deb.nodesource.com/setup | bash -
    sudo apt-get install nodejs
