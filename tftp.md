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

    TFTP_DIRECTORY=”tftp根目录” #服务器目录,需要设置权限为777,chomd 777

    TFTP_OPTIONS=”-l -c -s”

## 3.重新启动TFTP服务

    sudo service tftpd-hpa restart

## 4.测试

最后tftp 127.0.0.1/localhost　
输入get xxx
看能否下载某个文件。
