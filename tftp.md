# tftp服务器最简单安装配置

## 1.安装tftp-server

sudo apt-get install tftpd-hpa

sudo apt-get install tftp-hpa(如果不需要客户端可以不安装)

tftp-hpa是客户端

tftpd-hpa是服务器端

## 2.配置TFTP服务器

    sudo vim /etc/default/tftpd-hpa

将原来的内容改为:

    TFTP_USERNAME=”tftp”

    TFTP_ADDRESS=”0.0.0.0:69″

    TFTP_DIRECTORY=”/home/quanpower/dev/tftpboot” #服务器目录,需要设置权限为777,chomd 777 ,sudo chmod 777 -R/home/quanpower/dev/tftpboot

    TFTP_OPTIONS=”-l -c -s”


## 3.重新启动TFTP服务

    sudo service tftpd-hpa restart

## 4.测试

查看69端口是否有打开 ：
    netstat -an | more | grep udp

    udp 0 0 0.0.0.0:69 0.0.0.0:*

###本机测试：
a. 在/tftproot 下新建文件1.txt   
b. 在其他目录下测试：

    tftp 127.0.0.1
    tftp> get 1.txt
    Received 12 bytes in 0.0 seconds
    tftp> quit

## 5.Errors

网上总结出来的常见错误及解决方法：

* 现象一：
    
    tftp> get file
    
    Transfer timed out.
    
    原因：
    
    tftpd服务没有启动
    
    解决方法：启动服务
    
    sudo /etc/init.d/xinetd restart
    
    sudo /etc/init.d/tftpd-hpa restart
    
    
* 现象二：
    
    tftp> get file
    
    Error code 2: Only absolute filenames allowed
    
    原因：
    
    在/etc/xinetd.d/tftpd中设置的server_args为/etc/default/tftpd-hpa
    
    下面是我的机器上/etc/default/tftpd-hpa配置
    
    `# /etc/default/tftpd-hpa`
    
    `RUN_DAEMON="yes"`
    
    `TFTP_ADDRESS="0.0.0.0:69"`
    
    `OPTIONS="-s /home/tftpd -c -p -U 077 -u tftpd"`
    
     
* 现象三：
    
    tftp> put file
    
    Error code 1: File not found
    
    原因：
    
    指定的文件不存在；或tftpd启动参数中没有指定-c选项，允许上传文件～上传的时候一定要确保文件先存在于上传目录下。
    
    
* 现象四：
    
    tftp> get file
    
    tftp: : Permission denied
    
    原因：权限不足