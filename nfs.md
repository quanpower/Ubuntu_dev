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


1. nfs server端的安装和配置
(1)安装nfs server
sudo apt-get install nfs-kernel-server nfs-common
（2）重启nfs server
sudo service nfs-kernel-server restart
 
 （3）设置nfs共享目录
 sudo vim /etc/exports
 //在文件末尾添加一行
 /path-to-share *(rw,sync)   //path-to-share是要共享的目录，根据自己情况修改
 修改完成后，重启nfs server 即可，方法见（2）！
  
  2. nfs client端安装和配置
  (1)安装nfs client
  sudo apt-get install nfs-common
  （2）查看nfs server上共享的目录
   
   showmount -e 192.168.xx.xx
   (3)创建共享挂载点，并执行挂载
   mkdir /path-to-mount
   mount -t nfs 192.168.xx.xx:/path-to-share /path-to-mount
   （4）修改/etc/fstab文件
    
    192.168.35.17:/data3/nfsroot/data3/nfsroot nfs defaults 0 0
     
     3. 在共享目录下创建一个文件，看看另外一端能不能看到。


     ubuntu@arm:~/dev$ showmount -e 192.168.7.1
     Export list for 192.168.7.1:
     /d/downloads                           -readonly
     /d/BaiduYunDownload                    -readonly
     /e/KuGou                               -readonly
     /f/360Downloads/新建文件夹/kankan -readonly
     ubuntu@arm:~/dev$ sudo mkdir /mnt/Y400
     ubuntu@arm:~/dev$ sudo mount -t nfs 192.168.7.1:/d/downloads /mnt/Y400
