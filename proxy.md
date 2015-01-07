# 1.AWS SSH

edit ~/.ssh/config

    Host aws
    HostName 54.254.228.240
    User ubuntu
    IdentityFile ~/.ssh/smartlinkcloud.pem
    CompressionLevel 6
    DynamicForward localhost:3128

use it :
    ssh aws

# 2.Global proxy

system settings - network - network proxy

127.0.0.1 3128 socks5


# 3.ProxyChains

假设代理为127.0.0.1，端口为3128。我在Ubuntu下安装。

安装很简单：

    sudo apt-get install proxychains

配置：

    sudo vi /etc/proxychains.conf

把最后的“[ProxyList]”部分配置为自己的代理即可：

    socks5  127.0.0.1 3128

使用方法：

    proxychains <程序名>

即可让程序使用代理。
    
# [后记]
    当然终端下使用http代理并不需要使用ubuntu系统自带的全局代理工具,直接

    export http_proxy="http://127.0.0.1:8084"wget www.google.com

    #访问https加密的需要设置https_proxy变量export https_proxy="http://127.0.0.1:8084"wget https://www.google.com

    https_proxy="http://127.0.0.1:8084"和https_proxy="https://127.0.0.1:8084"是不一样的,后者需要你的代理支持https
