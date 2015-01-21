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
