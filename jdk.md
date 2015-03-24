今天尝试在ubuntu14.04 LTS上安装jdk-8u25-linux-x64.tar.gz，并配置环境变量，献给新手，亲测有效，下面是具体的安装方法！
##工具/原料

    jdk-8u25-linux-x64.tar.gz
    Ubuntu 14.04LTS操作系统

##方法/步骤

    ###下载JDK 1.8

    打开http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html  下载最新的JDK安装文件
    
    ###ubuntu14.04安装配置jdk1.8.0_25

    找到你下载文件的目录，使用下面的命令我的是用firefox下载的，在下载文件夹敲命令sudo tar zxvf  jdk-8u25-linux-x64.tar.gz  -C  /usr/lib/jvm

    解压之后，可以看到jvm文件夹里面有jdk文件了.

    下面配置系统环境变量

    sudo gedit /etc/profile

    在文本编辑器最后添加如下的语句

`#set java environment
export JAVA_HOME=/usr/lib/jvm/jdk1.8.0_25  
export JRE_HOME=${JAVA_HOME}/jre  
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib  
export PATH=${JAVA_HOME}/bin:$PATH` 

    保存退出，下面输入以下命令配置默认JDK版本

    sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.8.0_25 /bin/java 300  

    sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.8.0_25 /bin/javac 300 

    执行代码：

    sudo update-alternatives --config java 


    最后，测试环境变量有没有配置成功

    输入java -version （会显示如下信息，说明已配置成功）

##注意事项

    注意选择对版本，32位的操作系统选择32位的JDK版本下载，64位的对应下载64位的JDK


