c-kermit是Linux下简单易用的串口工具,配置简单,现说说我的安装使用方法,我用的USB转串口+VM,环境不同可能设备名不一样

# 1.安装: 

    sudo apt-get install ckermit

# 2.设置配置文件 

c-kermit启动时会从当前用户下查找.kermrc配置文件,所以我们先写好一个配置文件,全名为 ~/.kermrc,
OR:/etc/kermit/kermrc
下面是使用U-Boot和Linux时推荐配置:

    set line /dev/ttyUSB0  #如果使用电脑本身的串口,这里可能是ttyS0之类的
    set speed 115200
    set carrier-watch off
    set handshake none
    set flow-control none
    robust
    set file type bin
    set file name lit
    set rec pack 1000
    set send pack 1000
    set window 5
    c

# 3.Use

启动
--------------------------------------
    启动kermit，连接串口:
    # kermit
    C-Kermit>connect
    # 现在就已经成功连接到串口了。
 
切换
--------------------------------------
    按下 Ctrl + \, 再按c可以跳回kermit
    C-Kermit>    
    此时输入c,即connect即可连接到串口
    
* 运行的时候直接进入命令模式： 

    $kermit 

    这里没-c就进入默认的命令模式了。 
    
    kermit在启动时会查找~/.kermrc文件，调用里面的命令来初始化kermit。只要将你所需的命令写到~/.kermrc文件里，启动后就不用手动敲入命令配置了。 

* 运行的时候，直接进入非命令模式: 

    $kermit -c 
    
    这里，加上-c表示进入非命令模式，相当于在命令模式下面运行了connect或者c.在连接好了板子之后，这样就可以连接到串口上面了,当然不要忘记将设备打开，否则你敲入东西的时候是没有反应的。 

* 进入命令模式,步骤如下： 

    1)输入"[Ctrl]\". 
    
    2)输入"c". 
    
    这样进入kermit的命令模式可以进行各种命令(支持TAB补全)，例如HELP可以查看帮助,输入"?"列出所有命令。 


* 从命令模式退回com终端： 

    输入"connect". 
    
    或输入"c". 
    
    这样又切换会了串口界面（例如在uboot下面）。 


* 在命令模式下查看当前主机目录文件： 
    
    输入"ls". 


* 在命令模式下查看当前路径： 

    输入"pwd". 


* 在命令模式下进入指定的主机目录/home/test： 

    输入"cd /home/test". 


* 传输文件file到板子的flash上面： 

    输入"send file". 
    
    这里，在命令行下的发送命令就是send。如果之前在Uboot下使用了loadb 0xc0008000进入的命令模式，那么发送的文件将会被放在了这个地址上面。 


* 退出串口程序： 

    输入"exit". 
    
    当然，这里指的是在命令行下面。 


* 一个简单的完整例子： 

    启动板子uboot之后，我想传一个文件/root/test.sh到地址0xc0008000 
    
    步骤如下： 
    
    1）$kermit -c 
    
    这样，就连接到串口上面了。 
    
    2）输入"loadb 0xc0008000" 
    
    3)输入"[Ctrl]\" 
    
    4)输入"c" 
    
    这样进入命令模式. 
    
    5)输入"send /root/test.sh" 
    
    6)输入"connect". 
    
    这样就传完了。