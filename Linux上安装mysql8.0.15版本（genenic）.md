## Linux上安装mysql8.0.15版本（genenic）

**1.现在mysql Linux （genenic）版本 **

​	地址：https://dev.mysql.com/downloads/mysql/

**2.解压到/usr/local/mysql中**

​	将压缩包拷贝到  /usr/local 中 

​	tar xvJf mysql-8.0.15-linux-glibc2.12-x86_64.tar.xz 

​	mv  mysql-8.0.15-linux-glibc2.12-x86_64  mysql

**3.增加mysql的组和用户,并修改/usr/local/mysql下面的文件的权限**

​	groupadd mysql

​	useradd -r -g mysql mysql

​	chown -R mysql:mysql ./

**4.初始化mysql，并记录临时密码登录**

​	bin/mysqld  --initialize  --user=mysql  --basedir=/usr/local/mysql  --datadir=/usr/local/mysql/data

**5.查看是否在/etc 下面生成my.cnf文件，如果没有则需要创建该文件并设置权限**

​	chmod 755 my.cnf  //权限设置方式

**6.编辑my.cnf**

​	[mysqld]
	basedir=/usr/local/mysql
	datadir=/usr/local/mysql/data
	port=3306
	socket=/tmp/mysql.sock
	pid-file=/usr/local/mysql/slave2.pid

​	sql_mode=NO_ENGINE_SUBSTITUTION,STRICT_TRANS_TABLES

**7.配置mysql环境变量**

​	vim /etc/profile

​	export  MYSQL_HOME
	MYSQL_HOME=/usr/local/mysql
	export  PATH=$PATH:$MYSQL_HOME/lib:$MYSQL_HOME/bin

​	sourcr /etc/profile

**8.设置开机启动项**

​	cp /usr/local/mysql/support-files/mysql.server   /etc/init.d/mysql
	chmod +x  /etc/init.d/mysql  //添加可执行权限。

​	chkconfig  --add mysql   // 注册启动服务

**9.开启mysql服务**

service mysql start   //开启服务器。
mysql -uroot -p      //登录进入mysql，然后提示输入密码。

**10.修改密码**

alter user  'root'@'localhost' identified by 'your_password';

​	

## 通过xshell来连接数据库

1.本人的数据库是安装在本地的虚拟机上的，所以只需要通过xshell 连接虚拟机的ip，密码登录上去就可以了

2.如果你是安装在其他服务器，可以查看linux 上面是否ssh端口开通

​	如果没有 则需要安装ssh

​	sudo apt-get install openssh-server   (回车-->输入"y"-->回车-->安装完成)

​	查看ssh 是否启动   ps -e |grep ssh  有sshd,说明ssh服务已经启动

​	如果没有启动，输入"sudo service ssh start"