# 1. 连接ftp服务器

格式：ftp [hostname| ip-address]
a)在linux命令行下输入：
ftp 192.168.1.1

b)服务器询问你用户名和密码，分别输入用户名和相应密码，待认证通过即可。

# 2. 下载文件

下载文件通常用get和mget这两条命令。
a) get
格式：get [remote-file] [local-file]
将文件从远端主机中传送至本地主机中。
如要获取远程服务器上/usr/your/1.htm，则
ftp> get /usr/your/1.htm 1.htm (回车)


b) mget　　　　　　
格式：mget [remote-files]
从远端主机接收一批文件至本地主机。
如要获取服务器上/usr/your/下的所有文件，则
ftp> cd /usr/your/
ftp> mget *.* (回车)


此时每下载一个文件，都会有提示。如果要除掉提示，则在mget *.* 命令前先执行:prompt off

注意：文件都下载到了linux主机的当前目录下。比如，在　/usr/my下运行的ftp命令，则文件都下载到了/usr/my下。

# 3.上传文件

a) put
格式：put local-file [remote-file]
将本地一个文件传送至远端主机中。
如要把本地的1.htm传送到远端主机/usr/your,并改名为2.htm
ftp> put 1.htm /usr/your/2.htm (回车)


b) mput
格式：mput local-files
将本地主机中一批文件传送至远端主机。
如要把本地当前目录下所有html文件上传到服务器/usr/your/ 下
ftp> cd /usr/your （回车）
ftp> mput *.htm　（回车）


注意：上传文件都来自于主机的当前目录下。比如，在　/usr/my下运行的ftp命令，则只有在/usr/my下的文件linux才会上传到服务器/usr/your 下。

# 4. 断开连接
bye：中断与服务器的连接。
ftp> bye (回车)
