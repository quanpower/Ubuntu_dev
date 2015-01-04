在Server端的设置如以下步骤

1. 安装NFS server软件

sudo apt-get install nfs-kernel-server

2. 创建共享目录并将目录的权限改为777

mkdir -p share
chmod 777 share

3. 配制文件vi /etc/exports

sudo vi /etc/exports

添加以下条目

/home/lisp/share *(rw,sync,no_root_squash)

其中/home/lisp/share为共享目录, rw为可读写操作

4. 开启nfs服务

sudo /etc/init.d/nfs-kernel-server start

在Client端,配制如下

1. 安装nfs-common (在另一台机器执行以下命令)

sudo apt-get install nfs-common

2. 远程mount

sudo mount 10.141.247.133:/home/lisp/share /media/share

把远程目录mount到本地/media/share下,结果如下：
